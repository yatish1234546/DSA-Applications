# Application of Queues

## Supermarket Checkout Queue
Explanation: In a supermarket, customers wait in a queue at the checkout counter. The first customer to arrive is the first to be served.
    
    #include <stdio.h>
    #include <stdlib.h>
    
    #define MAX_CUSTOMERS 10
    
    struct Queue {
    int items[MAX_CUSTOMERS];
    int front;
    int rear;
    };
    
    void initializeQueue(struct Queue *queue) {
    queue->front = -1;
    queue->rear = -1;
    }
    
    int isQueueEmpty(struct Queue *queue) {
    return queue->front == -1;
    }
    
    int isQueueFull(struct Queue *queue) {
    return queue->rear == MAX_CUSTOMERS - 1;
    }
    
    void enqueue(struct Queue *queue, int value) {
    if (isQueueFull(queue)) {
    printf("Queue is full. Cannot enqueue.\n");
    return;
    }
    if (isQueueEmpty(queue)) {
    queue->front = 0;
    }
    queue->rear++;
    queue->items[queue->rear] = value;
    }
    
    int dequeue(struct Queue *queue) {
    if (isQueueEmpty(queue)) {
    printf("Queue is empty. Cannot dequeue.\n");
    return -1;
    }
    int value = queue->items[queue->front];
    if (queue->front == queue->rear) {
    queue->front = -1;
    queue->rear = -1;
    } else {
    queue->front++;
    }
    return value;
    }
    
    int main() {
    struct Queue checkoutQueue;
    initializeQueue(&checkoutQueue);
    
        enqueue(&checkoutQueue, 1);
        enqueue(&checkoutQueue, 2);
        enqueue(&checkoutQueue, 3);
    
        printf("Customer at the front of the queue: %d\n", checkoutQueue.items[checkoutQueue.front]);
    
        int servedCustomer = dequeue(&checkoutQueue);
        printf("Served customer: %d\n", servedCustomer);
    
        printf("Customer at the front of the queue: %d\n", checkoutQueue.items[checkoutQueue.front]);
    
        return 0;
    }

## Print Queue

Explanation: In a printer system, print jobs are placed in a queue. The printer processes the print jobs in the order they were added to the queue.
    
    #include <stdio.h>
    #include <stdlib.h>
    
    #define MAX_PRINT_JOBS 10
    
    struct Queue {
    int jobs[MAX_PRINT_JOBS];
    int front;
    int rear;
    };
    
    void initializeQueue(struct Queue *queue) {
    queue->front = -1;
    queue->rear = -1;
    }
    
    int isQueueEmpty(struct Queue *queue) {
    return queue->front == -1;
    }
    
    int isQueueFull(struct Queue *queue) {
    return queue->rear == MAX_PRINT_JOBS - 1;
    }
    
    void enqueue(struct Queue *queue, int jobNumber) {
    if (isQueueFull(queue)) {
    printf("Queue is full. Cannot enqueue.\n");
    return;
    }
    if (isQueueEmpty(queue)) {
    queue->front = 0;
    }
    queue->rear++;
    queue->jobs[queue->rear] = jobNumber;
    }
    
    int dequeue(struct Queue *queue) {
    if (isQueueEmpty(queue)) {
    printf("Queue is empty. Cannot dequeue.\n");
    return -1;
    }
    int jobNumber = queue->jobs[queue->front];
    if (queue->front == queue->rear) {
    queue->front = -1;
    queue->rear = -1;
    } else {
    queue->front++;
    }
    return jobNumber;
    }
    
    int main() {
    struct Queue printerQueue;
    initializeQueue(&printerQueue);
    
        enqueue(&printerQueue, 101);
        enqueue(&printerQueue, 102);
        enqueue(&printerQueue, 103);
    
        printf("Print job at the front of the queue: %d\n", printerQueue.jobs[printerQueue.front]);
    
        int printedJob = dequeue(&printerQueue);
        printf("Printed job: %d\n", printedJob);
    
        printf("Print job at the front of the queue: %d\n", printerQueue.jobs[printerQueue.front]);
    
        return 0;
    }

## Bank ATM Queue:

Explanation: In a bank ATM, customers form a queue to access the ATM machine. The customer at the front of the queue is the next one to use the ATM.

    #include <stdio.h>
    #include <stdlib.h>
    
    #define MAX_CUSTOMERS 10
    
    struct Queue {
    int customerIDs[MAX_CUSTOMERS];
    int front;
    int rear;
    };
    
    void initializeQueue(struct Queue *queue) {
    queue->front = -1;
    queue->rear = -1;
    }
    
    int isQueueEmpty(struct Queue *queue) {
    return queue->front == -1;
    }
    
    int isQueueFull(struct Queue *queue) {
    return queue->rear == MAX_CUSTOMERS - 1;
    }
    
    void enqueue(struct Queue *queue, int customerID) {
    if (isQueueFull(queue)) {
    printf("Queue is full. Cannot enqueue.\n");
    return;
    }
    if (isQueueEmpty(queue)) {
    queue->front = 0;
    }
    queue->rear++;
    queue->customerIDs[queue->rear] = customerID;
    }
    
    int dequeue(struct Queue *queue) {
    if (isQueueEmpty(queue)) {
    printf("Queue is empty. Cannot dequeue.\n");
    return -1;
    }
    int customerID = queue->customerIDs[queue->front];
    if (queue->front == queue->rear) {
    queue->front = -1;
    queue->rear = -1;
    } else {
    queue->front++;
    }
    return customerID;
    }
    
    int main() {
    struct Queue atmQueue;
    initializeQueue(&atmQueue);
    
        enqueue(&atmQueue, 201);
        enqueue(&atmQueue, 202);
        enqueue(&atmQueue, 203);
    
        printf("Customer at the front of the queue: %d\n", atmQueue.customerIDs[atmQueue.front]);
    
        int servedCustomer = dequeue(&atmQueue);
        printf("Served customer: %d\n", servedCustomer);
    
        printf("Customer at the front of the queue: %d\n", atmQueue.customerIDs[atmQueue.front]);
    
        return 0;
    }

## Traffic Signal Queue:

Explanation: At a traffic signal, vehicles form a queue at the intersection. Vehicles wait their turn to proceed through the signal.

    #include <stdio.h>
    #include <stdlib.h>
    
    #define MAX_VEHICLES 10
    
    struct Queue {
    int vehicleIDs[MAX_VEHICLES];
    int front;
    int rear;
    };
    
    void initializeQueue(struct Queue *queue) {
    queue->front = -1;
    queue->rear = -1;
    }
    
    int isQueueEmpty(struct Queue *queue) {
    return queue->front == -1;
    }
    
    int isQueueFull(struct Queue *queue) {
    return queue->rear == MAX_VEHICLES - 1;
    }
    
    void enqueue(struct Queue *queue, int vehicleID) {
    if (isQueueFull(queue)) {
    printf("Queue is full. Cannot enqueue.\n");
    return;
    }
    if (isQueueEmpty(queue)) {
    queue->front = 0;
    }
    queue->rear++;
    queue->vehicleIDs[queue->rear] = vehicleID;
    }
    
    int dequeue(struct Queue *queue) {
    if (isQueueEmpty(queue)) {
    printf("Queue is empty. Cannot dequeue.\n");
    return -1;
    }
    int vehicleID = queue->vehicleIDs[queue->front];
    if (queue->front == queue->rear) {
    queue->front = -1;
    queue->rear = -1;
    } else {
    queue->front++;
    }
    return vehicleID;
    }
    
    int main() {
    struct Queue trafficQueue;
    initializeQueue(&trafficQueue);
    
        enqueue(&trafficQueue, 301);
        enqueue(&trafficQueue, 302);
        enqueue(&trafficQueue, 303);
    
        printf("Vehicle at the front of the queue: %d\n", trafficQueue.vehicleIDs[trafficQueue.front]);
    
        int passedVehicle = dequeue(&trafficQueue);
        printf("Passed vehicle: %d\n", passedVehicle);
    
        printf("Vehicle at the front of the queue: %d\n", trafficQueue.vehicleIDs[trafficQueue.front]);
    
        return 0;
    }

## Call Center Queue

Explanation: In a call center, incoming customer calls are placed in a queue and are answered in the order they were received.

    #include <stdio.h>
    #include <stdlib.h>
    
    #define MAX_CALLS 10
    
    struct Queue {
    int callIDs[MAX_CALLS];
    int front;
    int rear;
    };
    
    void initializeQueue(struct Queue *queue) {
    queue->front = -1;
    queue->rear = -1;
    }
    
    int isQueueEmpty(struct Queue *queue) {
    return queue->front == -1;
    }
    
    int isQueueFull(struct Queue *queue) {
    return queue->rear == MAX_CALLS - 1;
    }
    
    void enqueue(struct Queue *queue, int callID) {
    if (isQueueFull(queue)) {
    printf("Queue is full. Cannot enqueue.\n");
    return;
    }
    if (isQueueEmpty(queue)) {
    queue->front = 0;
    }
    queue->rear++;
    queue->callIDs[queue->rear] = callID;
    }
    
    int dequeue(struct Queue *queue) {
    if (isQueueEmpty(queue)) {
    printf("Queue is empty. Cannot dequeue.\n");
    return -1;
    }
    int callID = queue->callIDs[queue->front];
    if (queue->front == queue->rear) {
    queue->front = -1;
    queue->rear = -1;
    } else {
    queue->front++;
    }
    return callID;
    }
    
    int main() {
    struct Queue callQueue;
    initializeQueue(&callQueue);
    
        enqueue(&callQueue, 401);
        enqueue(&callQueue, 402);
        enqueue(&callQueue, 403);
    
        printf("Call ID at the front of the queue: %d\n", callQueue.callIDs[callQueue.front]);
    
        int answeredCall = dequeue(&callQueue);
        printf("Answered call ID: %d\n", answeredCall);
    
        printf("Call ID at the front of the queue: %d\n", callQueue.callIDs[callQueue.front]);
    
        return 0;
    }

# Application of Stacks

## Plate Stack in a Cafeteria
Explanation: When plates are stacked in a cafeteria, the last plate that's placed becomes the first one to be used.
    
    #include <stdio.h>
    #include <stdbool.h>
    
    #define MAX_PLATES 100
    
    struct PlateStack {
    int plates[MAX_PLATES];
    int top;
    };
    
    void initStack(struct PlateStack *stack) {
    stack->top = -1;
    }
    
    bool isEmpty(struct PlateStack *stack) {
    return stack->top == -1;
    }
    
    void push(struct PlateStack *stack, int plate_number) {
    if (stack->top < MAX_PLATES - 1) {
    stack->top++;
    stack->plates[stack->top] = plate_number;
    }
    }
    
    int pop(struct PlateStack *stack) {
    if (!isEmpty(stack)) {
    int plate = stack->plates[stack->top];
    stack->top--;
    return plate;
    }
    return -1;
    }
    
    int main() {
    struct PlateStack cafeteriaStack;
    initStack(&cafeteriaStack);
    
        push(&cafeteriaStack, 1);
        push(&cafeteriaStack, 2);
        push(&cafeteriaStack, 3);
    
        while (!isEmpty(&cafeteriaStack)) {
            printf("Using plate: %d\n", pop(&cafeteriaStack));
        }
    
        return 0;
    }

## Browser Back Button History

Explanation: When you navigate through web pages using the back button in your browser, each page you visit is added to a stack. Pressing the back button pops the most recent page from the stack.
    
    #include <stdio.h>
    #include <stdbool.h>
    #include <string.h>
    
    #define MAX_PAGES 100
    
    struct PageStack {
    char pages[MAX_PAGES][50];
    int top;
    };
    
    void initStack(struct PageStack *stack) {
    stack->top = -1;
    }
    
    bool isEmpty(struct PageStack *stack) {
    return stack->top == -1;
    }
    
    void push(struct PageStack *stack, char page[]) {
    if (stack->top < MAX_PAGES - 1) {
    stack->top++;
    strcpy(stack->pages[stack->top], page);
    }
    }
    
    char* pop(struct PageStack *stack) {
    if (!isEmpty(stack)) {
    return stack->pages[stack->top--];
    }
    return NULL;
    }
    
    int main() {
    struct PageStack browserHistory;
    initStack(&browserHistory);
    
        push(&browserHistory, "Page 1");
        push(&browserHistory, "Page 2");
        push(&browserHistory, "Page 3");
    
        while (!isEmpty(&browserHistory)) {
            char* page = pop(&browserHistory);
            if (page != NULL) {
                printf("Visited page: %s\n", page);
            }
        }
    
        return 0;
    }

## Undo/Redo Functionality in Text Editors

Explanation: Text editors often use a stack to implement undo and redo functionality. Every text change is added to the undo stack, and pressing the undo button pops changes from the stack.
    
    #include <stdio.h>
    #include <stdbool.h>
    #include <string.h>
    
    #define MAX_CHANGES 100
    
    struct TextEditStack {
    char changes[MAX_CHANGES][100];
    int top;
    };
    
    void initStack(struct TextEditStack *stack) {
    stack->top = -1;
    }
    
    bool isEmpty(struct TextEditStack *stack) {
    return stack->top == -1;
    }
    
    void push(struct TextEditStack *stack, char change[]) {
    if (stack->top < MAX_CHANGES - 1) {
    stack->top++;
    strcpy(stack->changes[stack->top], change);
    }
    }
    
    char* pop(struct TextEditStack *stack) {
    if (!isEmpty(stack)) {
    return stack->changes[stack->top--];
    }
    return NULL;
    }
    
    int main() {
    struct TextEditStack undoStack;
    initStack(&undoStack);
    
        push(&undoStack, "Added paragraph");
        push(&undoStack, "Deleted sentence");
    
        while (!isEmpty(&undoStack)) {
            char* change = pop(&undoStack);
            if (change != NULL) {
                printf("Undoing: %s\n", change);
            }
        }
    
        return 0;
    }

## Call Stack in Function Execution

Explanation: When functions are called in a program, their execution is added to a call stack. The most recently called function's execution is completed before moving to the previous one.

    
    #include <stdio.h>
    
    void functionA() {
    printf("Function A\n");
    }
    
    void functionB() {
    printf("Function B\n");
    functionA();
    }
    
    void functionC() {
    printf("Function C\n");
    functionB();
    }
    
    int main() {
    printf("Main Function\n");
    functionC();
    return 0;
    }


## Browser Tabs (Tab Stack)
Explanation: A browser's tab navigation can be implemented using a stack. Opening a new tab pushes its information onto the stack, and closing a tab pops its information from the stack.
    
    #include <stdio.h>
    #include <stdbool.h>
    #include <string.h>
    
    #define MAX_TABS 10
    
    struct TabStack {
    char tabNames[MAX_TABS][50];
    int top;
    };
    
    void initializeTabStack(struct TabStack *stack) {
    stack->top = -1;
    }
    
    bool isTabStackEmpty(struct TabStack *stack) {
    return stack->top == -1;
    }
    
    bool isTabStackFull(struct TabStack *stack) {
    return stack->top == MAX_TABS - 1;
    }
    
    void openTab(struct TabStack *stack, const char tabName[]) {
    if (isTabStackFull(stack)) {
    printf("Tab stack is full. Cannot open tab.\n");
    return;
    }
    stack->top++;
    strcpy(stack->tabNames[stack->top], tabName);
    }
    
    void closeTab(struct TabStack *stack) {
    if (isTabStackEmpty(stack)) {
    printf("Tab stack is empty. Cannot close tab.\n");
    return;
    }
    printf("Closed tab: %s\n", stack->tabNames[stack->top]);
    stack->top--;
    }
    
    int main() {
    struct TabStack browserTabs;
    initializeTabStack(&browserTabs);
    
        openTab(&browserTabs, "Tab 1");
        openTab(&browserTabs, "Tab 2");
        openTab(&browserTabs, "Tab 3");
    
        closeTab(&browserTabs);
    
        return 0;
    }

# Application of Linked Lists

## Singly Linked List Examples:

### Employee List

Explanation: A list of employees in a company can be implemented using a singly linked list. Each employee is a node with details like name, ID, and position.

    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct Employee {
    char name[100];
    int id;
    char position[100];
    struct Employee *next;
    };
    
    struct Employee *head = NULL;
    
    void addEmployee(char name[], int id, char position[]) {
    struct Employee *newEmployee = (struct Employee *)malloc(sizeof(struct Employee));
    strcpy(newEmployee->name, name);
    newEmployee->id = id;
    strcpy(newEmployee->position, position);
    newEmployee->next = head;
    head = newEmployee;
    }
    
    void printEmployees() {
    struct Employee *current = head;
    while (current != NULL) {
    printf("Name: %s, ID: %d, Position: %s\n", current->name, current->id, current->position);
    current = current->next;
    }
    }
    
    int main() {
    addEmployee("Alice", 101, "Manager");
    addEmployee("Bob", 102, "Engineer");
    addEmployee("Carol", 103, "Designer");
    
        printEmployees();
    
        return 0;
    }

### Queue Implementation

Explanation: A queue data structure can be implemented using a singly linked list. It follows the First-In-First-Out (FIFO) principle.
    
    #include <stdio.h>
    #include <stdlib.h>
    
    struct Node {
    int data;
    struct Node *next;
    };
    
    struct Node *front = NULL;
    struct Node *rear = NULL;
    
    void enqueue(int data) {
    struct Node *newNode = (struct Node *)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    
        if (rear == NULL) {
            front = rear = newNode;
        } else {
            rear->next = newNode;
            rear = newNode;
        }
    }
    
    void dequeue() {
    if (front == NULL) {
    return;
    }
    struct Node *temp = front;
    front = front->next;
    free(temp);
    if (front == NULL) {
    rear = NULL;
    }
    }
    
    void printQueue() {
    struct Node *current = front;
    while (current != NULL) {
    printf("%d ", current->data);
    current = current->next;
    }
    printf("\n");
    }
    
    int main() {
    enqueue(10);
    enqueue(20);
    enqueue(30);
    
        printQueue(); // Output: 10 20 30
    
        dequeue();
        printQueue(); // Output: 20 30
    
        return 0;
    }

### Student Record List

Explanation: A list of student records with details like name, roll number, and marks can be implemented using a singly linked list.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct Student {
    char name[100];
    int roll_number;
    float marks;
    struct Student *next;
    };
    
    struct Student *head = NULL;
    
    void addStudent(char name[], int roll_number, float marks) {
    struct Student *newStudent = (struct Student *)malloc(sizeof(struct Student));
    strcpy(newStudent->name, name);
    newStudent->roll_number = roll_number;
    newStudent->marks = marks;
    newStudent->next = head;
    head = newStudent;
    }
    
    void printStudents() {
    struct Student *current = head;
    while (current != NULL) {
    printf("Name: %s, Roll Number: %d, Marks: %.2f\n", current->name, current->roll_number, current->marks);
    current = current->next;
    }
    }
    
    int main() {
    addStudent("Alice", 101, 85.5);
    addStudent("Bob", 102, 76.2);
    addStudent("Carol", 103, 92.0);
    
        printStudents();
    
        return 0;
    }

### Shopping Cart

Explanation: A shopping cart in an e-commerce application can be implemented using a singly linked list. Each item added to the cart is a node.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct Item {
    char name[100];
    float price;
    struct Item *next;
    };
    
    struct Item *cart = NULL;
    
    void addItem(char name[], float price) {
    struct Item *newItem = (struct Item *)malloc(sizeof(struct Item));
    strcpy(newItem->name, name);
    newItem->price = price;
    newItem->next = cart;
    cart = newItem;
    }
    
    float calculateTotal() {
    float total = 0;
    struct Item *current = cart;
    while (current != NULL) {
    total += current->price;
    current = current->next;
    }
    return total;
    }
    
    int main() {
    addItem("Laptop", 800);
    addItem("Headphones", 50);
    addItem("Mouse", 20);
    
        printf("Total: $%.2f\n", calculateTotal()); // Output: Total: $870.00
    
        return 0;
    }

### Sensor Data Log

Explanation: A log of sensor data readings with timestamps can be implemented using a singly linked list. Each reading is a node with details.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct SensorData {
    char timestamp[50];
    float value;
    struct SensorData *next;
    };
    
    struct SensorData *log = NULL;
    
    void addReading(char timestamp[], float value) {
    struct SensorData *newReading = (struct SensorData *)malloc(sizeof(struct SensorData));
    strcpy(newReading->timestamp, timestamp);
    newReading->value = value;
    newReading->next = log;
    log = newReading;
    }
    
    void printLog() {
    struct SensorData *current = log;
    while (current != NULL) {
    printf("Timestamp: %s, Value: %.2f\n", current->timestamp, current->value);
    current = current->next;
    }
    }
    
    int main() {
    addReading("2023-08-01 10:00:00", 25.5);
    addReading("2023-08-01 11:00:00", 28.2);
    addReading("2023-08-01 12:00:00", 23.8);
    
        printLog();
    
        return 0;
    }

## Doubly Linked List Examples:

### Music Playlist

Explanation: A music playlist can be implemented using a doubly linked list. Each song is a node with details like title, artist, and references to previous and next songs.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct Song {
    char title[100];
    char artist[100];
    struct Song *prev;
    struct Song *next;
    };
    
    struct Song *head = NULL;
    
    void addSong(char title[], char artist[]) {
    struct Song *newSong = (struct Song *)malloc(sizeof(struct Song));
    strcpy(newSong->title, title);
    strcpy(newSong->artist, artist);
    newSong->prev = NULL;
    newSong->next = head;
    
        if (head != NULL) {
            head->prev = newSong;
        }
    
        head = newSong;
    }
    
    void printPlaylist() {
    struct Song *current = head;
    while (current != NULL) {
    printf("Title: %s, Artist: %s\n", current->title, current->artist);
    current = current->next;
    }
    }
    
    int main() {
    addSong("Shape of You", "Ed Sheeran");
    addSong("Believer", "Imagine Dragons");
    addSong("Havana", "Camila Cabello");
    
        printPlaylist();
    
        return 0;
    }


### Undo/Redo History

Explanation: An application's undo/redo history can be implemented using a doubly linked list. Each state change is a node with references to previous and next states.
    
    #include <stdio.h>
    #include <stdlib.h>
    
    struct State {
    int data;
    struct State *prev;
    struct State *next;
    };
    
    struct State *currentState = NULL;
    
    void setState(int data) {
    struct State *newState = (struct State *)malloc(sizeof(struct State));
    newState->data = data;
    newState->prev = currentState;
    newState->next = NULL;
    
        if (currentState != NULL) {
            currentState->next = newState;
        }
    
        currentState = newState;
    }
    
    void undo() {
    if (currentState != NULL && currentState->prev != NULL) {
    currentState = currentState->prev;
    }
    }
    
    void redo() {
    if (currentState != NULL && currentState->next != NULL) {
    currentState = currentState->next;
    }
    }
    
    int main() {
    setState(10); // Initial state
    setState(20);
    setState(30);
    
        undo(); // Back to state with data 20
        redo(); // Forward to state with data 30
    
        return 0;
    }

### Text Editor Buffer

Explanation: A text editor's undo/redo buffer can be implemented using a doubly linked list. Each text change is a node.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct TextChange {
    char text[100];
    struct TextChange *prev;
    struct TextChange *next;
    };
    
    struct TextChange *currentChange = NULL;
    
    void addChange(char text[]) {
    struct TextChange *newChange = (struct TextChange *)malloc(sizeof(struct TextChange));
    strcpy(newChange->text, text);
    newChange->prev = currentChange;
    newChange->next = NULL;
    
        if (currentChange != NULL) {
            currentChange->next = newChange;
        }
    
        currentChange = newChange;
    }
    
    void undo() {
    if (currentChange != NULL && currentChange->prev != NULL) {
    currentChange = currentChange->prev;
    }
    }
    
    void redo() {
    if (currentChange != NULL && currentChange->next != NULL) {
    currentChange = currentChange->next;
    }
    }
    
    int main() {
    addChange("Hello");
    addChange("Hello, world!");
    addChange("Hello, world! How are you?");
    
        undo(); // Back to "Hello, world!"
        redo(); // Forward to "Hello, world! How are you?"
    
        return 0;
    }

### History of Transactions:

Explanation: A history of financial transactions can be implemented using a doubly linked list. Each transaction is a node with details like amount and references to previous and next transactions.
    
    #include <stdio.h>
    #include <stdlib.h>
    
    struct Transaction {
    float amount;
    struct Transaction *prev;
    struct Transaction *next;
    };
    
    struct Transaction *head = NULL;
    
    void addTransaction(float amount) {
    struct Transaction *newTransaction = (struct Transaction *)malloc(sizeof(struct Transaction));
    newTransaction->amount = amount;
    newTransaction->prev = NULL;
    newTransaction->next = head;
    
        if (head != NULL) {
            head->prev = newTransaction;
        }
    
        head = newTransaction;
    }
    
    void printTransactions() {
    struct Transaction *current = head;
    while (current != NULL) {
    printf("Amount: %.2f\n", current->amount);
    current = current->next;
    }
    }
    
    int main() {
    addTransaction(100.0);
    addTransaction(-50.0);
    addTransaction(200.0);
    
        printTransactions();
    
        return 0;
    }

### Undo/Redo Stack:

Explanation: An undo/redo stack in a graphics application can be implemented using a doubly linked list. Each action is a node with references to previous and next actions.
    
    #include <stdio.h>
    #include <stdlib.h>
    
    struct Action {
    char description[100];
    struct Action *prev;
    struct Action *next;
    };
    
    struct Action *currentAction = NULL;
    
    void addAction(char description[]) {
    struct Action *newAction = (struct Action *)malloc(sizeof(struct Action));
    strcpy(newAction->description, description);
    newAction->prev = currentAction;
    newAction->next = NULL;
    
        if (currentAction != NULL) {
            currentAction->next = newAction;
        }
    
        currentAction = newAction;
    }
    
    void undo() {
    if (currentAction != NULL && currentAction->prev != NULL) {
    currentAction = currentAction->prev;
    }
    }
    
    void redo() {
    if (currentAction != NULL && currentAction->next != NULL) {
    currentAction = currentAction->next;
    }
    }
    
    int main() {
    addAction("Draw circle");
    addAction("Move rectangle");
    addAction("Resize triangle");
    
        undo(); // Undo "Resize triangle"
        redo(); // Redo "Resize triangle"
    
        return 0;
    }


## Circular Linked List

### Round-Robin Scheduling
Explanation: In computer science, round-robin scheduling is a technique where tasks are assigned to processors in a circular manner. Each task gets a fixed time slice for execution before moving to the next task.

    #include <stdio.h>
    #include <stdlib.h>
    
    struct Process {
    int id;
    struct Process *next;
    };
    
    struct Process *addToCircularList(struct Process *current, int processID) {
    struct Process *newProcess = (struct Process *)malloc(sizeof(struct Process));
    newProcess->id = processID;
    
        if (current == NULL) {
            newProcess->next = newProcess; // Only one process in the list
            return newProcess;
        }
        
        newProcess->next = current->next;
        current->next = newProcess;
        
        return newProcess;
    }
    
    struct Process *removeFromCircularList(struct Process *current) {
    if (current == NULL) {
    return NULL;
    }
    
        struct Process *removedProcess = current->next;
        
        if (current->next == current) {
            free(current);
            return NULL; // Last process in the list
        }
        
        current->next = current->next->next;
        free(removedProcess);
        
        return current->next;
    }
    
    int main() {
    struct Process *currentProcess = NULL;
    
        currentProcess = addToCircularList(currentProcess, 1);
        currentProcess = addToCircularList(currentProcess, 2);
        currentProcess = addToCircularList(currentProcess, 3);
        
        for (int i = 0; i < 6; i++) {
            printf("Executing process: %d\n", currentProcess->id);
            currentProcess = currentProcess->next;
        }
        
        return 0;
    }

### Music Playlist

Explanation: Circular linked lists can be used to create circular music playlists. Each song node points to the next song, and the last song points back to the first song.

    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct Song {
    char title[100];
    struct Song *next;
    };
    
    struct Song *addToPlaylist(struct Song *current, const char title[]) {
    struct Song *newSong = (struct Song *)malloc(sizeof(struct Song));
    strcpy(newSong->title, title);
    
        if (current == NULL) {
            newSong->next = newSong; // Only one song in the playlist
            return newSong;
        }
        
        newSong->next = current->next;
        current->next = newSong;
        
        return newSong;
    }
    
    void playPlaylist(struct Song *currentSong, int numSongs) {
    for (int i = 0; i < numSongs; i++) {
    printf("Now playing: %s\n", currentSong->title);
    currentSong = currentSong->next;
    }
    }
    
    int main() {
    struct Song *currentSong = NULL;
    
        currentSong = addToPlaylist(currentSong, "Song 1");
        currentSong = addToPlaylist(currentSong, "Song 2");
        currentSong = addToPlaylist(currentSong, "Song 3");
        
        playPlaylist(currentSong, 5);
        
        return 0;
    }

### Circular Queue

Explanation: A circular queue is a queue data structure where the front and rear of the queue are connected, creating a circular structure. It's often used for managing a limited buffer.

    #include <stdio.h>
    #include <stdbool.h>
    
    #define MAX_QUEUE_SIZE 5
    
    struct CircularQueue {
    int items[MAX_QUEUE_SIZE];
    int front;
    int rear;
    };
    
    void initializeCircularQueue(struct CircularQueue *queue) {
    queue->front = -1;
    queue->rear = -1;
    }
    
    bool isCircularQueueEmpty(struct CircularQueue *queue) {
    return queue->front == -1;
    }
    
    bool isCircularQueueFull(struct CircularQueue *queue) {
    return (queue->rear + 1) % MAX_QUEUE_SIZE == queue->front;
    }
    
    void enqueue(struct CircularQueue *queue, int value) {
    if (isCircularQueueFull(queue)) {
    printf("Circular queue is full. Cannot enqueue.\n");
    return;
    }
    if (isCircularQueueEmpty(queue)) {
    queue->front = 0;
    }
    queue->rear = (queue->rear + 1) % MAX_QUEUE_SIZE;
    queue->items[queue->rear] = value;
    }
    
    int dequeue(struct CircularQueue *queue) {
    if (isCircularQueueEmpty(queue)) {
    printf("Circular queue is empty. Cannot dequeue.\n");
    return -1;
    }
    int value = queue->items[queue->front];
    if (queue->front == queue->rear) {
    queue->front = -1;
    queue->rear = -1;
    } else {
    queue->front = (queue->front + 1) % MAX_QUEUE_SIZE;
    }
    return value;
    }
    
    int main() {
    struct CircularQueue cQueue;
    initializeCircularQueue(&cQueue);
    
        enqueue(&cQueue, 1);
        enqueue(&cQueue, 2);
        enqueue(&cQueue, 3);
        enqueue(&cQueue, 4);
    
        int dequeuedValue = dequeue(&cQueue);
        printf("Dequeued value: %d\n", dequeuedValue);
    
        enqueue(&cQueue, 5);
        enqueue(&cQueue, 6);
    
        return 0;
    }

### Circular Linked List for Memory Allocation

Explanation: Circular linked lists can be used to manage memory allocation and deallocation in embedded systems where memory is limited and fragmentation is a concern.

    #include <stdio.h>
    #include <stdlib.h>
    
    struct MemoryBlock {
    int size;
    struct MemoryBlock *next;
    };
    
    struct MemoryBlock *allocateMemory(struct MemoryBlock *current, int blockSize) {
    struct MemoryBlock *newBlock = (struct MemoryBlock *)malloc(sizeof(struct MemoryBlock));
    newBlock->size = blockSize;
    
        if (current == NULL) {
            newBlock->next = newBlock; // Only one block in the list
            return newBlock;
        }
        
        newBlock->next = current->next;
        current->next = newBlock;
        
        return newBlock;
    }
    
    void deallocateMemory(struct MemoryBlock *current) {
    if (current == NULL) {
    return;
    }
    
        struct MemoryBlock *temp = current->next;
        
        if (current->next == current) {
            free(current);
            return; // Last block in the list
        }
        
        current->next = current->next->next;
        free(temp);
    }
    
    int main() {
    struct MemoryBlock *memoryList = NULL;
    
        memoryList = allocateMemory(memoryList, 100);
        memoryList = allocateMemory(memoryList, 200);
        memoryList = allocateMemory(memoryList, 150);
        
        deallocateMemory(memoryList);
        deallocateMemory(memoryList->next);
        
        return 0;
    }

### Circular Linked List for System Timer Events:
Explanation: In embedded systems, a circular linked list can be used to manage scheduled events, such as system timer tasks, where events repeat after a certain interval.

    #include <stdio.h>
    #include <stdlib.h>
    
    struct TimerEvent {
    int interval;
    void (*callback)(void);
    struct TimerEvent *next;
    };
    
    void eventCallback1() {
    printf("Event 1 occurred\n");
    }
    
    void eventCallback2() {
    printf("Event 2 occurred\n");
    }
    
    struct TimerEvent *scheduleEvent(struct TimerEvent *current, int interval, void (*callback)(void)) {
    struct TimerEvent *newEvent = (struct TimerEvent *)malloc(sizeof(struct TimerEvent));
    newEvent->interval = interval;
    newEvent->callback = callback;
    
        if (current == NULL) {
            newEvent->next = newEvent; // Only one event in the list
            return newEvent;
        }
        
        newEvent->next = current->next;
        current->next = newEvent;
        
        return newEvent;
    }
    
    void processEvents(struct TimerEvent *currentEvent) {
    while (1) {
    currentEvent->callback();
    currentEvent = currentEvent->next;
    // Simulate delay or sleep based on the interval
    printf("Waiting...\n");
    }
    }
    
    int main() {
    struct TimerEvent *eventList = NULL;
    
        eventList = scheduleEvent(eventList, 1000, eventCallback1);
        eventList = scheduleEvent(eventList, 2000, eventCallback2);
        
        processEvents(eventList);
        
        return 0;
    }

# Application of Binary Search Trees

## Stock Price Tracking:
Explanation: A binary search tree can be used to track historical stock prices. Each node represents a date, and the left subtree contains dates before the current node's date, while the right subtree contains dates after.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct StockPrice {
    char date[20];
    double price;
    struct StockPrice *left;
    struct StockPrice *right;
    };
    
    struct StockPrice *createStockPrice(const char *date, double price) {
    struct StockPrice *newPrice = (struct StockPrice *)malloc(sizeof(struct StockPrice));
    strcpy(newPrice->date, date);
    newPrice->price = price;
    newPrice->left = NULL;
    newPrice->right = NULL;
    return newPrice;
    }
    
    struct StockPrice *insertPrice(struct StockPrice *root, const char *date, double price) {
    if (root == NULL) {
    return createStockPrice(date, price);
    }
    int compareResult = strcmp(date, root->date);
    if (compareResult < 0) {
    root->left = insertPrice(root->left, date, price);
    } else if (compareResult > 0) {
    root->right = insertPrice(root->right, date, price);
    }
    return root;
    }
    
    int main() {
    struct StockPrice *priceHistory = NULL;
    
        priceHistory = insertPrice(priceHistory, "2023-08-01", 150.25);
        priceHistory = insertPrice(priceHistory, "2023-08-02", 155.10);
        priceHistory = insertPrice(priceHistory, "2023-08-03", 157.50);
    
        // Tree representation:
        //       2023-08-01
        //             \
        //       2023-08-02
        //             \
        //       2023-08-03
    
        return 0;
    }

## Automated Car Parking System:

Explanation: A parking system can use a BST to efficiently manage parking spots. Each node represents a parking spot, and the left subtree contains available spots, while the right subtree contains occupied spots.
    
    #include <stdio.h>
    #include <stdlib.h>
    
    struct ParkingSpot {
    int spotNumber;
    char status; // 'A' for available, 'O' for occupied
    struct ParkingSpot *left;
    struct ParkingSpot *right;
    };
    
    struct ParkingSpot *createParkingSpot(int spotNumber, char status) {
    struct ParkingSpot *newSpot = (struct ParkingSpot *)malloc(sizeof(struct ParkingSpot));
    newSpot->spotNumber = spotNumber;
    newSpot->status = status;
    newSpot->left = NULL;
    newSpot->right = NULL;
    return newSpot;
    }
    
    struct ParkingSpot *insertSpot(struct ParkingSpot *root, int spotNumber, char status) {
    if (root == NULL) {
    return createParkingSpot(spotNumber, status);
    }
    if (status == 'A') {
    root->left = insertSpot(root->left, spotNumber, status);
    } else if (status == 'O') {
    root->right = insertSpot(root->right, spotNumber, status);
    }
    return root;
    }
    
    int main() {
    struct ParkingSpot *parkingMap = NULL;
    
        parkingMap = insertSpot(parkingMap, 101, 'A');
        parkingMap = insertSpot(parkingMap, 102, 'O');
        parkingMap = insertSpot(parkingMap, 103, 'A');
    
        // Tree representation:
        //          101 (A)
        //            / \
        //      102 (O)  103 (A)
    
        return 0;
    }

## Flight Booking System:

Explanation: A flight booking system can utilize a BST to organize available flight seats. Each node represents a seat, and the left subtree contains available seats, while the right subtree contains booked seats.
    
    #include <stdio.h>
    #include <stdlib.h>
    
    struct FlightSeat {
    int seatNumber;
    char status; // 'A' for available, 'B' for booked
    struct FlightSeat *left;
    struct FlightSeat *right;
    };
    
    struct FlightSeat *createFlightSeat(int seatNumber, char status) {
    struct FlightSeat *newSeat = (struct FlightSeat *)malloc(sizeof(struct FlightSeat));
    newSeat->seatNumber = seatNumber;
    newSeat->status = status;
    newSeat->left = NULL;
    newSeat->right = NULL;
    return newSeat;
    }
    
    struct FlightSeat *insertSeat(struct FlightSeat *root, int seatNumber, char status) {
    if (root == NULL) {
    return createFlightSeat(seatNumber, status);
    }
    if (status == 'A') {
    root->left = insertSeat(root->left, seatNumber, status);
    } else if (status == 'B') {
    root->right = insertSeat(root->right, seatNumber, status);
    }
    return root;
    }
    
    int main() {
    struct FlightSeat *seatMap = NULL;
    
        seatMap = insertSeat(seatMap, 1, 'A');
        seatMap = insertSeat(seatMap, 2, 'B');
        seatMap = insertSeat(seatMap, 3, 'A');
    
        // Tree representation:
        //          1 (A)
        //            / \
        //      2 (B)  3 (A)
    
        return 0;
    }

## Online Course Enrollment:

Explanation: An online learning platform can use a BST to manage course enrollments. Each node represents a course, and the left subtree contains available courses, while the right subtree contains enrolled courses.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct Course {
    char courseCode[10];
    char status; // 'A' for available, 'E' for enrolled
    struct Course *left;
    struct Course *right;
    };
    
    struct Course *createCourse(const char *courseCode, char status) {
    struct Course *newCourse = (struct Course *)malloc(sizeof(struct Course));
    strcpy(newCourse->courseCode, courseCode);
    newCourse->status = status;
    newCourse->left = NULL;
    newCourse->right = NULL;
    return newCourse;
    }
    
    struct Course *insertCourse(struct Course *root, const char *courseCode, char status) {
    if (root == NULL) {
    return createCourse(courseCode, status);
    }
    if (status == 'A') {
    root->left = insertCourse(root->left, courseCode, status);
    } else if (status == 'E') {
    root->right = insertCourse(root->right, courseCode, status);
    }
    return root;
    }
    
    int main() {
    struct Course *courseCatalog = NULL;
    
        courseCatalog = insertCourse(courseCatalog, "CSCI101", 'A');
        courseCatalog = insertCourse(courseCatalog, "MATH202", 'E');
        courseCatalog = insertCourse(courseCatalog, "PHYS301", 'A');
    
        // Tree representation:
        //       CSCI101 (A)
        //            / \
        //    MATH202 (E)  PHYS301 (A)
    
        return 0;
    }

## Medical Records:

Explanation: A medical clinic can use a BST to organize patient medical records. Each node represents a patient's record, and the left subtree contains records of patients with lower medical IDs, while the right subtree contains records of patients with higher IDs.
    
    #include <stdio.h>
    #include <stdlib.h>
    
    struct MedicalRecord {
    int patientID;
    char diagnosis[100];
    struct MedicalRecord *left;
    struct MedicalRecord *right;
    };
    
    struct MedicalRecord *createMedicalRecord(int patientID, const char *diagnosis) {
    struct MedicalRecord *newRecord = (struct MedicalRecord *)malloc(sizeof(struct MedicalRecord));
    newRecord->patientID = patientID;
    strcpy(newRecord->diagnosis, diagnosis);
    newRecord->left = NULL;
    newRecord->right = NULL;
    return newRecord;
    }
    
    struct MedicalRecord *insertRecord(struct MedicalRecord *root, int patientID, const char *diagnosis) {
    if (root == NULL) {
    return createMedicalRecord(patientID, diagnosis);
    }
    if (patientID < root->patientID) {
    root->left = insertRecord(root->left, patientID, diagnosis);
    } else if (patientID > root->patientID) {
    root->right = insertRecord(root->right, patientID, diagnosis);
    }
    return root;
    }
    
    int main() {
    struct MedicalRecord *patientRecords = NULL;
    
        patientRecords = insertRecord(patientRecords, 101, "Fever");
        patientRecords = insertRecord(patientRecords, 102, "Fracture");
        patientRecords = insertRecord(patientRecords, 103, "Cold");
    
        // Tree representation:
        //         101
        //         /   \
        //      102   103
    
        return 0;
    }

# ===============================================

# Applications of Hashing

## Password Storage
Explanation: Hashing is commonly used to securely store passwords. Instead of storing plain passwords, the system stores their hash values. When a user tries to log in, the system hashes the entered password and compares it with the stored hash.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    #include <openssl/sha.h> // You may need to install OpenSSL
    
    void hashPassword(char password[], unsigned char hash[SHA256_DIGEST_LENGTH]) {
    SHA256((unsigned char *)password, strlen(password), hash);
    }
    
    int main() {
    char password[] = "mysecretpassword";
    unsigned char hash[SHA256_DIGEST_LENGTH];
    
        hashPassword(password, hash);
    
        printf("Password: %s\n", password);
        printf("Hash: ");
        for (int i = 0; i < SHA256_DIGEST_LENGTH; i++) {
            printf("%02x", hash[i]);
        }
        printf("\n");
    
        return 0;
    }


## Data Integrity Verification
Explanation: Hashing is used to verify the integrity of data during transmission. The sender computes the hash of the data and sends it along with the data. The receiver computes the hash of the received data and compares it with the received hash.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    #include <openssl/sha.h>
    
    void calculateHash(char data[], unsigned char hash[SHA256_DIGEST_LENGTH]) {
    SHA256((unsigned char *)data, strlen(data), hash);
    }
    
    int main() {
    char originalData[] = "Hello, world!";
    unsigned char originalHash[SHA256_DIGEST_LENGTH];
    unsigned char receivedHash[SHA256_DIGEST_LENGTH];
    
        calculateHash(originalData, originalHash);
    
        // Simulating transmission
        char transmittedData[] = "Hello, world!";
        calculateHash(transmittedData, receivedHash);
    
        int hashMatch = memcmp(originalHash, receivedHash, SHA256_DIGEST_LENGTH) == 0;
    
        if (hashMatch) {
            printf("Data integrity verified.\n");
        } else {
            printf("Data integrity compromised.\n");
        }
    
        return 0;
    }

## File Content Deduplication
Explanation: Hashing can be used to identify duplicate files. The hash value of the file content is computed, and if the same hash value exists in the database, it indicates a duplicate file.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    #include <openssl/sha.h>
    
    struct File {
    char name[50];
    unsigned char hash[SHA256_DIGEST_LENGTH];
    };
    
    void calculateFileHash(char content[], unsigned char hash[SHA256_DIGEST_LENGTH]) {
    SHA256((unsigned char *)content, strlen(content), hash);
    }
    
    int main() {
    struct File files[2];
    
        strcpy(files[0].name, "file1.txt");
        calculateFileHash("Hello, world!", files[0].hash);
    
        strcpy(files[1].name, "file2.txt");
        calculateFileHash("Hello, world!", files[1].hash);
    
        int duplicate = memcmp(files[0].hash, files[1].hash, SHA256_DIGEST_LENGTH) == 0;
    
        if (duplicate) {
            printf("Duplicate files found.\n");
        } else {
            printf("No duplicate files.\n");
        }
    
        return 0;
    }

## Caching

Explanation: Hashing is used in caching to quickly access previously computed values. For instance, in a web server, the URLs and their corresponding responses can be cached using a hash table for faster retrieval.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    #define CACHE_SIZE 100
    
    struct CacheEntry {
    char url[200];
    char response[1024];
    };
    
    struct CacheEntry cache[CACHE_SIZE];
    
    unsigned int hashFunction(char *url) {
    unsigned int hash = 0;
    for (int i = 0; url[i] != '\0'; i++) {
    hash = hash * 31 + url[i];
    }
    return hash % CACHE_SIZE;
    }
    
    void addToCache(char *url, char *response) {
    unsigned int index = hashFunction(url);
    strcpy(cache[index].url, url);
    strcpy(cache[index].response, response);
    }
    
    int main() {
    addToCache("https://example.com/page1", "Page 1 content");
    addToCache("https://example.com/page2", "Page 2 content");
    
        // Retrieving from cache
        char urlToRetrieve[] = "https://example.com/page1";
        unsigned int index = hashFunction(urlToRetrieve);
        
        if (strcmp(cache[index].url, urlToRetrieve) == 0) {
            printf("Cached response: %s\n", cache[index].response);
        } else {
            printf("Data not found in cache.\n");
        }
    
        return 0;
    }

## Distributed Key-Value Store

Explanation: Hashing is used in distributed systems to assign keys to specific nodes. Each node is responsible for a range of keys based on their hash values.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    #define NUM_NODES 5
    
    struct Node {
    char name[20];
    int start_range;
    int end_range;
    };
    
    struct Node nodes[NUM_NODES];
    
    void setupNodes() {
    strcpy(nodes[0].name, "Node A");
    nodes[0].start_range = 0;
    nodes[0].end_range = 199;
    
        // Set up other nodes with appropriate ranges
    }
    
    struct Node findNodeForKey(int key) {
    for (int i = 0; i < NUM_NODES; i++) {
    if (key >= nodes[i].start_range && key <= nodes[i].end_range) {
    return nodes[i];
    }
    }
    // Default fallback node
    return nodes[0];
    }
    
    int main() {
    setupNodes();
    
        int keyToStore = 123;
        struct Node nodeToStore = findNodeForKey(keyToStore);
        printf("Key %d will be stored in %s.\n", keyToStore, nodeToStore.name);
    
        return 0;
    }

# ===============================================
# Application of Graphs

## Social Network

Explanation: A social network can be represented as a graph where users are nodes, and connections between users (friendships) are edges. Each user is connected to their friends.

    #include <stdio.h>
    #include <stdlib.h>
    #include <stdbool.h>
    #include <string.h>
    
    #define MAX_USERS 100
    
    struct User {
    char name[50];
    int friends[MAX_USERS];
    int num_friends;
    };
    
    struct User users[MAX_USERS];
    int num_users = 0;
    
    void addUser(char name[]) {
    strcpy(users[num_users].name, name);
    users[num_users].num_friends = 0;
    num_users++;
    }
    
    void addFriend(int user_index, int friend_index) {
    users[user_index].friends[users[user_index].num_friends] = friend_index;
    users[user_index].num_friends++;
    }
    
    int main() {
    addUser("Alice");
    addUser("Bob");
    addUser("Carol");
    
        addFriend(0, 1);  // Alice and Bob are friends
        addFriend(1, 0);  // Bob and Alice are friends
        addFriend(1, 2);  // Bob and Carol are friends
        addFriend(2, 1);  // Carol and Bob are friends
    
        // Graph representation: Alice <-> Bob <-> Carol
    
        return 0;
    }

## Road Network

Explanation: A road network can be represented as a graph where intersections are nodes, and roads connecting intersections are edges.

    #include <stdio.h>
    #include <stdbool.h>
    
    #define MAX_INTERSECTIONS 100
    
    bool roadMatrix[MAX_INTERSECTIONS][MAX_INTERSECTIONS];
    
    void addRoad(int intersection1, int intersection2) {
    roadMatrix[intersection1][intersection2] = true;
    roadMatrix[intersection2][intersection1] = true;
    }
    
    int main() {
    addRoad(0, 1);  // Intersection 0 and 1 are connected
    addRoad(1, 2);  // Intersection 1 and 2 are connected
    addRoad(2, 3);  // Intersection 2 and 3 are connected
    
        // Graph representation: Intersection 0 -- Intersection 1 -- Intersection 2 -- Intersection 3
    
        return 0;
    }

## Web Page Links

Explanation: A collection of web pages with links between them can be represented as a graph where web pages are nodes, and links between pages are edges.
    
    #include <stdio.h>
    #include <stdbool.h>
    #include <string.h>
    
    #define MAX_PAGES 100
    
    struct WebPage {
    char url[100];
    int linked_pages[MAX_PAGES];
    int num_links;
    };
    
    struct WebPage webPages[MAX_PAGES];
    int num_pages = 0;
    
    void addPage(char url[]) {
    strcpy(webPages[num_pages].url, url);
    webPages[num_pages].num_links = 0;
    num_pages++;
    }
    
    void addLink(int page_index, int linked_page_index) {
    webPages[page_index].linked_pages[webPages[page_index].num_links] = linked_page_index;
    webPages[page_index].num_links++;
    }
    
    int main() {
    addPage("https://example.com/page1");
    addPage("https://example.com/page2");
    addPage("https://example.com/page3");
    
        addLink(0, 1);  // Page 1 links to Page 2
        addLink(1, 0);  // Page 2 links back to Page 1
        addLink(1, 2);  // Page 2 links to Page 3
    
        // Graph representation: Page 1 <-> Page 2 <-> Page 3
    
        return 0;
    }

## Flight Routes

Explanation: Air travel routes can be represented as a graph where airports are nodes, and flight connections between airports are edges.
    
    #include <stdio.h>
    #include <stdbool.h>
    #include <string.h>
    
    #define MAX_AIRPORTS 100
    
    struct Airport {
    char name[50];
    int connected_airports[MAX_AIRPORTS];
    int num_connections;
    };
    
    struct Airport airports[MAX_AIRPORTS];
    int num_airports = 0;
    
    void addAirport(char name[]) {
    strcpy(airports[num_airports].name, name);
    airports[num_airports].num_connections = 0;
    num_airports++;
    }
    
    void addConnection(int airport_index, int connected_airport_index) {
    airports[airport_index].connected_airports[airports[airport_index].num_connections] = connected_airport_index;
    airports[airport_index].num_connections++;
    }
    
    int main() {
    addAirport("Airport A");
    addAirport("Airport B");
    addAirport("Airport C");
    
        addConnection(0, 1);  // Airport A is connected to Airport B
        addConnection(1, 0);  // Airport B is connected to Airport A
        addConnection(1, 2);  // Airport B is connected to Airport C
    
        // Graph representation: Airport A <-> Airport B <-> Airport C
    
        return 0;
    }

## Course Prerequisites

Explanation: University courses and their prerequisites can be represented as a graph where courses are nodes, and prerequisites are edges.
    
    #include <stdio.h>
    #include <stdbool.h>
    #include <string.h>
    
    #define MAX_COURSES 100
    
    struct Course {
    char name[50];
    int prerequisites[MAX_COURSES];
    int num_prerequisites;
    };
    
    struct Course courses[MAX_COURSES];
    int num_courses = 0;
    
    void addCourse(char name[]) {
    strcpy(courses[num_courses].name, name);
    courses[num_courses].num_prerequisites = 0;
    num_courses++;
    }
    
    void addPrerequisite(int course_index, int prerequisite_index) {
    courses[course_index].prerequisites[courses[course_index].num_prerequisites] = prerequisite_index;
    courses[course_index].num_prerequisites++;
    }
    
    int main() {
    addCourse("Course A");
    addCourse("Course B");
    addCourse("Course C");
    
        addPrerequisite(0, 1);  // Course A has a prerequisite of Course B
        addPrerequisite(1, 2);  // Course B has a prerequisite of Course C
    
        // Graph representation: Course A -> Course B -> Course C
    
        return 0;
    }
# ===========================================================

# Applications of AVL

## Databases and Indexing:

Explanation: In databases, AVL trees can be used to maintain indexes for efficient data retrieval. Each node in the AVL tree represents a unique key (e.g., a primary key) and points to the corresponding data. This allows for quick search operations based on the key values.

    #include <stdio.h>
    #include <stdlib.h>
    
    struct AVLNode {
    int key;
    struct AVLNode *left;
    struct AVLNode *right;
    int height;
    };
    
    int max(int a, int b) {
    return (a > b) ? a : b;
    }
    
    int height(struct AVLNode *node) {
    if (node == NULL)
    return -1;
    return node->height;
    }
    
    int getBalance(struct AVLNode *node) {
    if (node == NULL)
    return 0;
    return height(node->left) - height(node->right);
    }
    
    struct AVLNode *rotateRight(struct AVLNode *y) {
    struct AVLNode *x = y->left;
    struct AVLNode *T2 = x->right;
    
        x->right = y;
        y->left = T2;
    
        y->height = 1 + max(height(y->left), height(y->right));
        x->height = 1 + max(height(x->left), height(x->right));
    
        return x;
    }
    
    struct AVLNode *rotateLeft(struct AVLNode *x) {
    struct AVLNode *y = x->right;
    struct AVLNode *T2 = y->left;
    
        y->left = x;
        x->right = T2;
    
        x->height = 1 + max(height(x->left), height(x->right));
        y->height = 1 + max(height(y->left), height(y->right));
    
        return y;
    }
    
    struct AVLNode *insert(struct AVLNode *node, int key) {
    if (node == NULL) {
    struct AVLNode *newNode = (struct AVLNode *)malloc(sizeof(struct AVLNode));
    newNode->key = key;
    newNode->height = 0;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
    }
    
        if (key < node->key)
            node->left = insert(node->left, key);
        else if (key > node->key)
            node->right = insert(node->right, key);
        else
            return node;
    
        node->height = 1 + max(height(node->left), height(node->right));
    
        int balance = getBalance(node);
    
        if (balance > 1 && key < node->left->key)
            return rotateRight(node);
    
        if (balance < -1 && key > node->right->key)
            return rotateLeft(node);
    
        if (balance > 1 && key > node->left->key) {
            node->left = rotateLeft(node->left);
            return rotateRight(node);
        }
    
        if (balance < -1 && key < node->right->key) {
            node->right = rotateRight(node->right);
            return rotateLeft(node);
        }
    
        return node;
    }
    
    void inorderTraversal(struct AVLNode *root) {
    if (root != NULL) {
    inorderTraversal(root->left);
    printf("%d ", root->key);
    inorderTraversal(root->right);
    }
    }
    
    int main() {
    struct AVLNode *root = NULL;
    
        root = insert(root, 10);
        root = insert(root, 20);
        root = insert(root, 30);
    
        inorderTraversal(root);
    
        return 0;
    }

## Auto-Completion and Spell Checkers:

Explanation: In auto-completion and spell checkers, AVL trees can store a dictionary of words. This allows for efficient word lookup, suggestion generation, and correction of misspelled words.

    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct AVLNode {
    char word[50];
    int frequency;
    struct AVLNode *left;
    struct AVLNode *right;
    int height;
    };
    
    int max(int a, int b) {
    return (a > b) ? a : b;
    }
    
    int height(struct AVLNode *node) {
    if (node == NULL)
    return -1;
    return node->height;
    }
    
    int getBalance(struct AVLNode *node) {
    if (node == NULL)
    return 0;
    return height(node->left) - height(node->right);
    }
    
    struct AVLNode *rotateRight(struct AVLNode *y) {
    struct AVLNode *x = y->left;
    struct AVLNode *T2 = x->right;
    
        x->right = y;
        y->left = T2;
    
        y->height = 1 + max(height(y->left), height(y->right));
        x->height = 1 + max(height(x->left), height(x->right));
    
        return x;
    }
    
    struct AVLNode *rotateLeft(struct AVLNode *x) {
    struct AVLNode *y = x->right;
    struct AVLNode *T2 = y->left;
    
        y->left = x;
        x->right = T2;
    
        x->height = 1 + max(height(x->left), height(x->right));
        y->height = 1 + max(height(y->left), height(y->right));
    
        return y;
    }
    
    struct AVLNode *insert(struct AVLNode *node, const char *word) {
    if (node == NULL) {
    struct AVLNode *newNode = (struct AVLNode *)malloc(sizeof(struct AVLNode));
    strcpy(newNode->word, word);
    newNode->frequency = 1;
    newNode->height = 0;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
    }
    
        int cmp = strcmp(word, node->word);
    
        if (cmp < 0)
            node->left = insert(node->left, word);
        else if (cmp > 0)
            node->right = insert(node->right, word);
        else {
            node->frequency++;
            return node;
        }
    
        node->height = 1 + max(height(node->left), height(node->right));
    
        int balance = getBalance(node);
    
        if (balance > 1 && strcmp(word, node->left->word) < 0)
            return rotateRight(node);
    
        if (balance < -1 && strcmp(word, node->right->word) > 0)
            return rotateLeft(node);
    
        if (balance > 1 && strcmp(word, node->left->word) > 0) {
            node->left = rotateLeft(node->left);
            return rotateRight(node);
        }
    
        if (balance < -1 && strcmp(word, node->right->word) < 0) {
            node->right = rotateRight(node->right);
            return rotateLeft(node);
        }
    
        return node;
    }
    
    void inorderTraversal(struct AVLNode *root) {
    if (root != NULL) {
    inorderTraversal(root->left);
    printf("%s (%d)\n", root->word, root->frequency);
    inorderTraversal(root->right);
    }
    }
    
    int main() {
    struct AVLNode *root = NULL;
    
        root = insert(root, "auto");
        root = insert(root, "auto");
        root = insert(root, "completion");
        root = insert(root, "checker");
    
        inorderTraversal(root);
    
        return 0;
    }

## Processing and Syntax Analysis:

Explanation: In language processing and syntax analysis, AVL trees can store grammar rules, keywords, or syntax patterns. This helps in efficient parsing and analyzing of code or text.

    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct AVLNode {
    char syntaxRule[100];
    struct AVLNode *left;
    struct AVLNode *right;
    int height;
    };
    
    int max(int a, int b) {
    return (a > b) ? a : b;
    }
    
    int height(struct AVLNode *node) {
    if (node == NULL)
    return -1;
    return node->height;
    }
    
    int getBalance(struct AVLNode *node) {
    if (node == NULL)
    return 0;
    return height(node->left) - height(node->right);
    }
    
    struct AVLNode *rotateRight(struct AVLNode *y) {
    struct AVLNode *x = y->left;
    struct AVLNode *T2 = x->right;
    
        x->right = y;
        y->left = T2;
    
        y->height = 1 + max(height(y->left), height(y->right));
        x->height = 1 + max(height(x->left), height(x->right));
    
        return x;
    }
    
    struct AVLNode *rotateLeft(struct AVLNode *x) {
    struct AVLNode *y = x->right;
    struct AVLNode *T2 = y->left;
    
        y->left = x;
        x->right = T2;
    
        x->height = 1 + max(height(x->left), height(x->right));
        y->height = 1 + max(height(y->left), height(y->right));
    
        return y;
    }
    
    struct AVLNode *insert(struct AVLNode *node, const char *syntaxRule) {
    if (node == NULL) {
    struct AVLNode *newNode = (struct AVLNode *)malloc(sizeof(struct AVLNode));
    strcpy(newNode->syntaxRule, syntaxRule);
    newNode->height = 0;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
    }
    
        int cmp = strcmp(syntaxRule, node->syntaxRule);
    
        if (cmp < 0)
            node->left = insert(node->left, syntaxRule);
        else if (cmp > 0)
            node->right = insert(node->right, syntaxRule);
        else
            return node;
    
        node->height = 1 + max(height(node->left), height(node->right));
    
        int balance = getBalance(node);
    
        if (balance > 1 && strcmp(syntaxRule, node->left->syntaxRule) < 0)
            return rotateRight(node);
    
        if (balance < -1 && strcmp(syntaxRule, node->right->syntaxRule) > 0)
            return rotateLeft(node);
    
        if (balance > 1 && strcmp(syntaxRule, node->left->syntaxRule) > 0) {
            node->left = rotateLeft(node->left);
            return rotateRight(node);
        }
    
        if (balance < -1 && strcmp(syntaxRule, node->right->syntaxRule) < 0) {
            node->right = rotateRight(node->right);
            return rotateLeft(node);
        }
    
        return node;
    }
    
    void inorderTraversal(struct AVLNode *root) {
    if (root != NULL) {
    inorderTraversal(root->left);
    printf("%s\n", root->syntaxRule);
    inorderTraversal(root->right);
    }
    }
    
    int main() {
    struct AVLNode *root = NULL;
    
        root = insert(root, "variable declaration");
        root = insert(root, "loop statement");
        root = insert(root, "function call");
        root = insert(root, "conditional statement");
    
        inorderTraversal(root);
    
        return 0;
    }

## Financial Software and Market Analysis:

Explanation: In financial software, AVL trees can be used to store financial instruments (e.g., stocks) along with their associated data. This enables efficient data retrieval and analysis for market trends.

    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct AVLNode {
    char stockName[50];
    double price;
    struct AVLNode *left;
    struct AVLNode *right;
    int height;
    };
    
    int max(int a, int b) {
    return (a > b) ? a : b;
    }
    
    int height(struct AVLNode *node) {
    if (node == NULL)
    return -1;
    return node->height;
    }
    
    int getBalance(struct AVLNode *node) {
    if (node == NULL)
    return 0;
    return height(node->left) - height(node->right);
    }
    
    struct AVLNode *rotateRight(struct AVLNode *y) {
    struct AVLNode *x = y->left;
    struct AVLNode *T2 = x->right;
    
        x->right = y;
        y->left = T2;
    
        y->height = 1 + max(height(y->left), height(y->right));
        x->height = 1 + max(height(x->left), height(x->right));
    
        return x;
    }
    
    struct AVLNode *rotateLeft(struct AVLNode *x) {
    struct AVLNode *y = x->right;
    struct AVLNode *T2 = y->left;
    
        y->left = x;
        x->right = T2;
    
        x->height = 1 + max(height(x->left), height(x->right));
        y->height = 1 + max(height(y->left), height(y->right));
    
        return y;
    }
    
    struct AVLNode *insert(struct AVLNode *node, const char *stockName, double price) {
    if (node == NULL) {
    struct AVLNode *newNode = (struct AVLNode *)malloc(sizeof(struct AVLNode));
    strcpy(newNode->stockName, stockName);
    newNode->price = price;
    newNode->height = 0;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
    }
    
        int cmp = strcmp(stockName, node->stockName);
    
        if (cmp < 0)
            node->left = insert(node->left, stockName, price);
        else if (cmp > 0)
            node->right = insert(node->right, stockName, price);
        else
            return node;
    
        node->height = 1 + max(height(node->left), height(node->right));
    
        int balance = getBalance(node);
    
        if (balance > 1 && strcmp(stockName, node->left->stockName) < 0)
            return rotateRight(node);
    
        if (balance < -1 && strcmp(stockName, node->right->stockName) > 0)
            return rotateLeft(node);
    
        if (balance > 1 && strcmp(stockName, node->left->stockName) > 0) {
            node->left = rotateLeft(node->left);
            return rotateRight(node);
        }
    
        if (balance < -1 && strcmp(stockName, node->right->stockName) < 0) {
            node->right = rotateRight(node->right);
            return rotateLeft(node);
        }
    
        return node;
    }
    
    void inorderTraversal(struct AVLNode *root) {
    if (root != NULL) {
    inorderTraversal(root->left);
    printf("%s - %.2f\n", root->stockName, root->price);
    inorderTraversal(root->right);
    }
    }
    
    int main() {
    struct AVLNode *root = NULL;
    
        root = insert(root, "AAPL", 150.50);
        root = insert(root, "GOOGL", 2700.20);
        root = insert(root, "AMZN", 3500.75);
        root = insert(root, "MSFT", 260.90);
    
        inorderTraversal(root);
    
        return 0;
    }

## Online Gaming:

Explanation: In online gaming, AVL trees can be used to maintain leaderboards and player scores. This allows for quick updates and retrieval of high scores.
    
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
    
    struct AVLNode {
    char playerName[50];
    int score;
    struct AVLNode *left;
    struct AVLNode *right;
    int height;
    };
    
    int max(int a, int b) {
    return (a > b) ? a : b;
    }
    
    int height(struct AVLNode *node) {
    if (node == NULL)
    return -1;
    return node->height;
    }
    
    int getBalance(struct AVLNode *node) {
    if (node == NULL)
    return 0;
    return height(node->left) - height(node->right);
    }
    
    struct AVLNode *rotateRight(struct AVLNode *y) {
    struct AVLNode *x = y->left;
    struct AVLNode *T2 = x->right;
    
        x->right = y;
        y->left = T2;
    
        y->height = 1 + max(height(y->left), height(y->right));
        x->height = 1 + max(height(x->left), height(x->right));
    
        return x;
    }
    
    struct AVLNode *rotateLeft(struct AVLNode *x) {
    struct AVLNode *y = x->right;
    struct AVLNode *T2 = y->left;
    
        y->left = x;
        x->right = T2;
    
        x->height = 1 + max(height(x->left), height(x->right));
        y->height = 1 + max(height(y->left), height(y->right));
    
        return y;
    }
    
    struct AVLNode *insert(struct AVLNode *node, const char *playerName, int score) {
    if (node == NULL) {
    struct AVLNode *newNode = (struct AVLNode *)malloc(sizeof(struct AVLNode));
    strcpy(newNode->playerName, playerName);
    newNode->score = score;
    newNode->height = 0;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
    }
    
        int cmp = strcmp(playerName, node->playerName);
    
        if (cmp < 0)
            node->left = insert(node->left, playerName, score);
        else if (cmp > 0)
            node->right = insert(node->right, playerName, score);
        else {
            // Update score if player already exists
            if (score > node->score)
                node->score = score;
            return node;
        }
    
        node->height = 1 + max(height(node->left), height(node->right));
    
        int balance = getBalance(node);
    
        if (balance > 1 && strcmp(playerName, node->left->playerName) < 0)
            return rotateRight(node);
    
        if (balance < -1 && strcmp(playerName, node->right->playerName) > 0)
            return rotateLeft(node);
    
        if (balance > 1 && strcmp(playerName, node->left->playerName) > 0) {
            node->left = rotateLeft(node->left);
            return rotateRight(node);
        }
    
        if (balance < -1 && strcmp(playerName, node->right->playerName) < 0) {
            node->right = rotateRight(node->right);
            return rotateLeft(node);
        }
    
        return node;
    }
    
    void inorderTraversal(struct AVLNode *root) {
    if (root != NULL) {
    inorderTraversal(root->left);
    printf("%s - %d\n", root->playerName, root->score);
    inorderTraversal(root->right);
    }
    }
    
    int main() {
    struct AVLNode *root = NULL;
    
        root = insert(root, "Player1", 1000);
        root = insert(root, "Player2", 850);
        root = insert(root, "Player3", 1200);
        root = insert(root, "Player4", 1100);
    
        inorderTraversal(root);
    
        return 0;
    }
