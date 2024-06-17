#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

// Function to create a new node
struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

// Insert a node at the beginning of the list
void insertAtBeginning(struct Node** head, int data) {
    struct Node* newNode = createNode(data);
    newNode->next = *head;
    *head = newNode;
}

// Insert a node after a given node P
void insertAfter(struct Node* prevNode, int data) {
    if (prevNode == NULL) {
        printf("The given previous node cannot be NULL\n");
        return;
    }
    struct Node* newNode = createNode(data);
    newNode->next = prevNode->next;
    prevNode->next = newNode;
}

// Insert a node at the end of the list
void insertAtEnd(struct Node** head, int data) {
    struct Node* newNode = createNode(data);
    if (*head == NULL) {
        *head = newNode;
        return;
    }
    struct Node* temp = *head;
    while (temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newNode;
}

// Find an element in the list
struct Node* findElement(struct Node* head, int key) {
    struct Node* temp = head;
    while (temp != NULL) {
        if (temp->data == key) {
            return temp;
        }
        temp = temp->next;
    }
    return NULL;
}

// Find the next node of a given node
struct Node* findNext(struct Node* node) {
    if (node == NULL) {
        return NULL;
    }
    return node->next;
}

// Find the previous node of a given node
struct Node* findPrevious(struct Node* head, struct Node* node) {
    if (head == NULL || node == NULL) {
        return NULL;
    }
    struct Node* temp = head;
    while (temp != NULL && temp->next != node) {
        temp = temp->next;
    }
    return temp;
}

// Check if a given node is the last node
int isLast(struct Node* node) {
    if (node == NULL) {
        return 0;
    }
    return node->next == NULL;
}

// Check if the list is empty
int isEmpty(struct Node* head) {
    return head == NULL;
}

// Delete a node at the beginning of the list
void deleteAtBeginning(struct Node** head) {
    if (*head == NULL) {
        printf("The list is already empty\n");
        return;
    }
    struct Node* temp = *head;
    *head = (*head)->next;
    free(temp);
}

// Delete a node after a given node P
void deleteAfter(struct Node* prevNode) {
    if (prevNode == NULL || prevNode->next == NULL) {
        printf("The given node is the last node or it is NULL\n");
        return;
    }
    struct Node* temp = prevNode->next;
    prevNode->next = temp->next;
    free(temp);
}

// Delete a node at the end of the list
void deleteAtEnd(struct Node** head) {
    if (*head == NULL) {
        printf("The list is already empty\n");
        return;
    }
    if ((*head)->next == NULL) {
        free(*head);
        *head = NULL;
        return;
    }
    struct Node* temp = *head;
    while (temp->next->next != NULL) {
        temp = temp->next;
    }
    free(temp->next);
    temp->next = NULL;
}

// Delete the entire list
void deleteList(struct Node** head) {
    struct Node* current = *head;
    struct Node* next;
    while (current != NULL) {
        next = current->next;
        free(current);
        current = next;
    }
    *head = NULL;
}

// Function to print the list
void printList(struct Node* node) {
    while (node != NULL) {
        printf("%d -> ", node->data);
        node = node->next;
    }
    printf("NULL\n");
}

int main() {
    struct Node* head = NULL;
    
    insertAtBeginning(&head, 1);
    insertAtEnd(&head, 3);
    insertAfter(head, 2);
    
    printf("Initial list: ");
    printList(head);
    
    struct Node* found = findElement(head, 2);
    if (found) {
        printf("Element 2 found\n");
    } else {
        printf("Element 2 not found\n");
    }
    
    printf("Next of 2: ");
    struct Node* next = findNext(found);
    if (next) {
        printf("%d\n", next->data);
    } else {
        printf("NULL\n");
    }
    
    printf("Previous of 2: ");
    struct Node* prev = findPrevious(head, found);
    if (prev) {
        printf("%d\n", prev->data);
    } else {
        printf("NULL\n");
    }
    
    printf("Is 3 the last element? %s\n", isLast(next) ? "Yes" : "No");
    printf("Is the list empty? %s\n", isEmpty(head) ? "Yes" : "No");
    
    deleteAtBeginning(&head);
    printf("After deleting at the beginning: ");
    printList(head);
    
    deleteAfter(head);
    printf("After deleting after head: ");
    printList(head);
    
    deleteAtEnd(&head);
    printf("After deleting at the end: ");
    printList(head);
    
    insertAtBeginning(&head, 4);
    insertAtEnd(&head, 5);
    printf("Final list before deleting all: ");
    printList(head);
    
    deleteList(&head);
    printf("After deleting the entire list: ");
    printList(head);

    return 0;
}
