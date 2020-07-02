Linked List is a linear data structure. Unlike arrays, linked list elements are not stored at a contiguous location; the elements are linked using pointers.

/* Advantages of Linked_List   */

1.The size of the arrays is fixed: So we must know the upper limit on the number of elements in advance. Also, generally, the allocated memory is equal to the upper limit irrespective of the usage.
2.Inserting a new element in an array of elements is expensive because the room has to be created for the new elements and to create room existing elements have to be shifted.

Advantages over arrays
1) Dynamic size
2) Ease of insertion/deletion

Drawbacks
1) Random access is not allowed. We have to access elements sequentially starting from the first node. So we cannot do binary search with linked lists efficiently with its default implementation. Read about it here.
2) Extra memory space for a pointer is required with each element of the list.
3) Not cache friendly. Since array elements are contiguous locations, there is locality of reference which is not there in case of linked lists.


// A simple C# program to introduce a linked list 
using System; 
  
public class LinkedList { 
    Node head; // head of list 
  
    /* Linked list Node. This inner class is made static so that  
    main() can access it */
    public class Node { 
        public int data; 
        public Node next; 
        public Node(int d) 
        { 
            data = d; 
            next = null; 
        } // Constructor 
    } 
    
    
    /* This function prints contents of  
    linked list starting from head */
    public void printList() 
    { 
        Node n = head; 
        while (n != null) { 
            Console.Write(n.data + " "); 
            n = n.next; 
        } 
    }
    
    /* method to create a simple linked list with 3 nodes*/
    public static void Main(String[] args) 
    { 
        /* Start with the empty list. */
        LinkedList llist = new LinkedList(); 
  
        llist.head = new Node(1); 
        Node second = new Node(2); 
        Node third = new Node(3); 
        
        llist.printList();
  
        /* Three nodes have been allocated dynamically.  
        We have references to these three blocks as head,  
        second and third  
  
        llist.head     second             third  
            |             |                 |  
            |             |                 |  
        +----+------+     +----+------+     +----+------+  
        | 1 | null |     | 2 | null |     | 3 | null |  
        +----+------+     +----+------+     +----+------+ */
  
        llist.head.next = second; // Link first node with the second node 
  
        /* Now next of first Node refers to second. So they  
            both are linked.  
  
        llist.head     second             third  
            |             |                 |  
            |             |                 |  
        +----+------+     +----+------+     +----+------+  
        | 1 | o-------->| 2 | null |     | 3 | null |  
        +----+------+     +----+------+     +----+------+ */
  
        second.next = third; // Link second node with the third node 
  
        /* Now next of the second Node refers to third. So all three  
            nodes are linked.  
  
        llist.head     second             third  
            |             |                 |  
            |             |                 |  
        +----+------+     +----+------+     +----+------+  
        | 1 | o-------->| 2 | o-------->| 3 | null |  
        +----+------+     +----+------+     +----+------+ */
    } 
} 
