# Trees
code not running properly
// Tree.cpp : This file contains the 'main' function. Program execution begins and ends there.
//

#include <iostream>
using namespace std;
class Node
{
public:
    int data;
    Node* Lchild;
    Node* Rchild;

};
Node* root = new Node();
class Queue
{
public:
    int front;
    int rear;
    int size;
    Node** Q;
};
Queue* create(int x)
{
    Queue* q = new  Queue();

    q->front = -1;
    q->rear = -1;
    q->Q = new Node*[x];
    return q;
}
void Cenqueue(Queue* q, Node *x)
{
    if ((q->rear + 1) % q->size == q->front)
        cout << "Queue is full:" << endl;
    else
    {
        q->rear = (q->rear + 1) % q->size;
        q->Q[q->rear] = x;

    }
}
Node* Cdequeue(Queue* q)
{
    Node *x=NULL;
    if (q->front == q->rear)
    {
        cout << "Queue is empty" << endl;

    }
    else
    {
        q->front = (q->front + 1) % q->size;
        x = q->Q[q->front];

    }
    return x;
}
int isEmpty(Queue* q)
{
    if (q->front == q->rear)
        return 1;
    else
        return 0;
}
void Tcreate()
{
    Node* p, * t;
    int x;
    Queue* q;
    q = create(100);
    cout << "Enter the root value" << endl;
    
    cin >> root->data;
    root->Lchild = root->Rchild = NULL;
    Cenqueue(q, root);
    
    while (!isEmpty(q))
    {
        
        p = Cdequeue(q);
        cout << "Enter left child of" <<p->data<< endl;
        cin >> x;
        if (x != -1)
        {
            t = new Node();
            t->data = x;
            t->Lchild = t->Rchild = NULL;
            p->Lchild = t;
            Cenqueue(q, t);
        }
        cout << "Enter right child:" <<p->data<< endl;
        cin >> x;
        if (x != -1)
        {
            t = new Node();
            t->data = x;
            t->Lchild = t->Rchild = NULL;
            p->Rchild = t;
            Cenqueue(q, t);
        }
    }
       



    }
void preorder(Node* t)
{
    if (t != NULL)
    {
        cout << t->data << endl;
        preorder(t->Lchild);
        preorder(t->Rchild);
    }
}

int main()
{
    Tcreate();
    preorder(root);
}

// Run program: Ctrl + F5 or Debug > Start Without Debugging menu
// Debug program: F5 or Debug > Start Debugging menu

// Tips for Getting Started: 
//   1. Use the Solution Explorer window to add/manage files
//   2. Use the Team Explorer window to connect to source control
//   3. Use the Output window to see build output and other messages
//   4. Use the Error List window to view errors
//   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
//   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
