# Проект: Library System (Библиотечна система)

## Общо описание

Library System е малък проект на C++, който симулира работа на библиотека чрез няколко взаимосвързани класа: Author, Book, Member, Loan и Library.
Проектът демонстрира основни принципи на обектно-ориентираното програмиране:

- използване на конструктори, копиране и преместване (Rule of 3/5);
- добра капсулация чрез гетъри и сетъри;
- коректно използване на const;
- работа със статични променливи и методи;
- използване на STL контейнери;
- прилагане на добри ООП практики в реалистичен пример.

---

## Структура на проекта

library/                                                                                                                                                       
├── Author.h                                                                                                                                                        
├── Book.h                                                                                                                                                       
├── Member.h                                                                                                                                                       
├── Loan.h                                                                                                                                                         
├── Library.h                                                                                                                                                       
├── Library.cpp                                                                                                                                                     
├── README.md                                                                                                                                                       
├── image.png                                                                                                                                                       
└── main.cpp                                                                                                                                                       


---

## Изпълнение с g++

1. g++ -std=c++17 main.cpp Library.cpp -o library_app
2. g++ -std=c++17 *.cpp -o library_app
3. ./library_app


---

## Примерен изход

Library summary:                                                                                                                                                    
Books: 2                                                                                                                                                       
Members: 1                                                                                                                                                       
Active loans: 0                                                                                                                                                     
Loan created.                                                                                                                                                       
Available ISBN-001? false                                                                                                                                           
Available ISBN-001? true                                                                                                                                            


---

## Класове

### Клас `Author`

Моделира автор и основните му данни.

**Полета:**
- `std::string name` — име  
- `int birthYear` — година на раждане  

**Методи:**
- конструктори
- `валидация на birthYear`
- `getName() const`
- `to_string() const` 

---

### Клас `Book`

Описва книга и нейните атрибути.

**Полета:**
- `std::string title`
- `Author author`
- `int year`
- `double price`
- `std::string isbn`
- `static int totalBooks`

**Методи:**
- параметризирани и default конструктори 
- Rule of 5 (копиране / преместване) 
- копиращ и преместващ оператор (`= default`)  
- деструктор (`= default`)  
- проверки на price и year
- `to_string()`
- `getTotalBooks()`

---

### Клас `Member`

Представя читател.

**Членове:**
- `std::string name`  
- `std::string memberId`  
- `int yearJoined`  

**Методи:**
- конструктори  
- проверка на memberId  
- `to_string() const`  

---

### Клас `Loan`

Описва заемането на книга.

**Членове:**
- `std::string isbn`  
- `std::string memberId`  
- `std::string startDate`  
- `std::string dueDate`  
- `bool returned`  

**Методи:**
- конструктор с проверка на дати 
- `markReturned()`  
- `isOverdue(const std::string& today) const` 
- `to_string() const`  

---

### Клас `Library`

Централният клас, управляващ всички елементи.

**Членове:**
- `std::vector<Book> books`  
- `std::vector<Member> members`  
- `std::vector<Loan> loans`  

**Методи:**
- `addBook(const Book&)`  
- `addMember(const Member&)`  
- `hasBook(const std::string& isbn) const`  
- `isBookAvailable(const std::string& isbn) const`  
- `loanBook(const std::string& isbn, const std::string& memberId, const std::string& start, const std::string& due)`  
- `returnBook(const std::string& isbn, const std::string& memberId)`  
- `findByAuthor(const std::string& authorName) const`  
- `to_string() const`  

---

## Образователни цели

Проектът демонстрира:

- разделяне на интерфейс и имплементация;
- initialization lists;
- Rule of 3/5;
- работа със std::vector;
- коректна обработка на данни;
- добре структурирано ООП решение.

---

## Екранна снимка

![screenshot](/image.png)

---

## Автор

**Име:** Пламен Драганов
**Номер:** 22322
**Курс:** Обектно-ориентирано програмиране (C++)  
**Дата:** 04.12.2025г.
