#include <iostream>
using namespace std;

typedef struct _Node
{
    int val = 0;
    _Node *prev = NULL;
    _Node *next = NULL;
} Node;

void node_reverse(Node **np)
{
    Node *tmp;
    tmp = (*np)->prev;
    (*np)->prev = (*np)->next;
    (*np)->next = tmp;
}

int main()
{
    int M;
    int N, K;
    int val;

    cin >> M;
    while (M--)
    {
        Node *head = new Node();
        Node *tmp = head;
        Node *cur = head;
        cin >> N >> K;
        if (N == 0)
        {
            cout << endl;
            continue;
        }
        for (int i = 0; i < N; i++)
        {
            cin >> val;
            if (i == 0)
            {
                head->val = val;
                head->prev = NULL;
                head->next = NULL;
            }
            else
            {
                Node *newNode = new Node();
                newNode->val = val;
                cur->next = newNode;
                newNode->prev = cur;
                cur = cur->next;
            }
            cur->next = head;
            head->prev = cur;
        }

        Node *dummytail = new Node();
        dummytail->prev = cur;
        dummytail->next = NULL;
        cur->next = dummytail;
        Node *dummyhead = new Node();
        dummyhead->next = head;
        dummyhead->prev = NULL;
        head->prev = dummyhead;

        int times = N / K;
        Node **last_gp_tail;
        Node **cur_gp_new_tail;
        Node *cur1;
        Node *next;
        last_gp_tail = &dummyhead;
        next = dummyhead->next;
        while (times--)
        {

            for (int i = 0; i < K; i++)
            {

                cur1 = next;
                next = cur1->next;

                if (i == 0)
                {
                    cur_gp_new_tail = &cur1;
                }

                node_reverse(&cur1);

                if (i == (K - 1))
                {
                    cur1->prev = *last_gp_tail;
                    (*last_gp_tail)->next = cur1;
                    last_gp_tail = cur_gp_new_tail;
                }
            }
            (*last_gp_tail)->next = next;
            next->prev = *last_gp_tail;
        }

        Node *print = dummyhead->next;

        while (print != NULL)
        {
            cout << print->val << ' ';
            print = print->next;
        }
        cout << endl;
    }
}
