

---

# **Java Constructor vs Setter – Student Examples**

---

## **Example 1: Basic Constructor Initialization**

```java
class Student {
    private String name;
    private int rollNo;

    // Constructor initializes all fields
    public Student(String name, int rollNo) {
        this.name = name;
        this.rollNo = rollNo;
    }

    public void printStudent() {
        System.out.println("Name: " + name + ", Roll No: " + rollNo);
    }
}

public class Main {
    public static void main(String[] args) {
        // Object fully initialized in one step
        Student s1 = new Student("Alice", 101);
        s1.printStudent();
    }
}
```

**Output:**

```
Name: Alice, Roll No: 101
```

**Takeaway:** Constructor ensures **all mandatory fields are set immediately**.

---

## **Example 2: Setter-based Initialization**

```java
class Student {
    private String name;
    private int rollNo;

    public Student() {} // default constructor

    public void setName(String name) { this.name = name; }
    public void setRollNo(int rollNo) { this.rollNo = rollNo; }

    public void printStudent() {
        System.out.println("Name: " + name + ", Roll No: " + rollNo);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s2 = new Student();
        s2.setName("Bob");
        // forgot to set rollNo
        s2.printStudent(); // Roll No = 0 (default)
    }
}
```

**Output:**

```
Name: Bob, Roll No: 0
```

**Takeaway:** Object is **partially initialized**, risk of missing mandatory data.

---

## **Example 3: Constructor with Validation**

```java
class BankAccount {
    private String accountNo;
    private double balance;

    public BankAccount(String accountNo, double balance) {
        if(balance < 0) throw new IllegalArgumentException("Balance cannot be negative");
        this.accountNo = accountNo;
        this.balance = balance;
    }

    public void printAccount() {
        System.out.println("Account: " + accountNo + ", Balance: " + balance);
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount a1 = new BankAccount("A123", 5000);
        a1.printAccount();
        // BankAccount a2 = new BankAccount("A124", -100); // throws exception
    }
}
```

**Takeaway:** Constructor **enforces validation**, setters alone can’t prevent invalid states automatically.

---

## **Example 4: Immutability with Constructor**

```java
class Book {
    private final String title;
    private final String author;

    public Book(String title, String author) {
        this.title = title;
        this.author = author;
    }

    public String getTitle() { return title; }
    public String getAuthor() { return author; }
}

public class Main {
    public static void main(String[] args) {
        Book b = new Book("Java Basics", "Alice");
        System.out.println(b.getTitle() + ", " + b.getAuthor());
        // Cannot change fields, no setters
    }
}
```

**Takeaway:** Using **constructor + `final` fields** makes objects **immutable** and safe.

---

## **Example 5: Constructor vs Setter Comparison in One Class**

```java
class Employee {
    private String name;
    private double salary;

    // Constructor sets mandatory fields
    public Employee(String name, double salary) {
        this.name = name;
        this.salary = salary;
    }

    // Optional fields can use setters
    private String department;
    public void setDepartment(String department) { this.department = department; }

    public void printEmployee() {
        System.out.println("Name: " + name + ", Salary: " + salary + ", Department: " + department);
    }
}

public class Main {
    public static void main(String[] args) {
        // Using constructor for mandatory fields
        Employee e1 = new Employee("John", 30000);
        // Using setter for optional field
        e1.setDepartment("HR");
        e1.printEmployee();
    }
}
```

**Output:**

```
Name: John, Salary: 30000.0, Department: HR
```

**Takeaway:**

* **Constructor → mandatory fields**
* **Setter → optional fields**
* Combination ensures **safety + flexibility**.

---

✅ **Summary for Students**

1. **Constructor:** Always initialize **mandatory fields**, can include **validation**, supports **immutability**.
2. **Setter:** Good for **optional or changeable fields**, but **object may be incomplete** if not used carefully.
3. **Best Practice:**

   * Use **constructor for required fields**.
   * Use **setters only for optional fields**.



Do you want me to make that diagram?
