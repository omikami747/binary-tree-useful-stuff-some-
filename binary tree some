#include<bits/stdc++.h>
using namespace std;
class node{
    public:
    int data;
    node* left;
    node* right;
    node(int val)  {
        data = val;
        left = NULL;
        right = NULL;
    }
};
int height(node* root){
    if(root == NULL){
        return 0;
    }
    return max(height(root -> left),height(root -> right)) + 1;
}
bool isbalanced(node* root){
    if(root == NULL){
        return true;
    }
    if(isbalanced(root -> left) && isbalanced(root -> right) && abs(height(root->left) - height(root -> right)) < 2){
        return true;
    }else{
        return false;
    }
}
void printlevelorder(node* root){
    queue <node*> q;
    if(root == NULL){
        return;
    }
    
    q.push(root);
    q.push(NULL);
    while(!q.empty()){
        node* node1 = q.front();
        q.pop();
        if(node1 != NULL){
            cout<<node1->data<<"->";
            if(node1->left){
                q.push(node1->left);
            }
            if(node1->right){
                q.push(node1->right);
            }
        }
        else{
            if(!q.empty()){
                cout<<endl;
                q.push(NULL);
            }
        }
    }
}
int search(vector <int> inorder , int curr , int start  , int end){
    int size = inorder.size();
    for(int i = 0;i < inorder.size();i++){
        if(curr == inorder[i]){
            return i;
        }
    }
    return -1;
}
node* buildtreepostorder(vector <int> inorder , vector <int> postorder , int start , int end){
    if(start > end) return NULL;
    static int idex = inorder.size() - 1;
    int curr = postorder[idex];
    node* node1 = new node(curr);
    idex--;
    if(start == end)return node1;
    int pos = search(inorder , curr , start , end);
    node1->right = buildtreepostorder(inorder , postorder , pos + 1 , end);
    node1->left = buildtreepostorder(inorder , postorder , start , pos - 1);
    return node1;
}
node* buildtreepreorder(vector <int> preorder , vector <int> inorder , int start , int end ){   
    if(start > end){
        return NULL;
    }
    static int idx = 0;
    int curr = preorder[idx];
    idx++;
    node* node1 = new node(curr);
    if(start  == end){   
        return node1;
    }  
    int pos = search(inorder , curr , start , end);    
    node1->left = buildtreepreorder(preorder , inorder , start , pos - 1);
    node1->right = buildtreepreorder(preorder , inorder , pos + 1 , end);
    return node1;
}
int better_diameter(node* root , int* height){
    if(root){
        return 0;
    }
    int lh = 0,rh = 0; 
    int left_diameter = better_diameter(root->left ,&lh );
    int right_diameter = better_diameter(root->right , &rh);
    int curr_diameter = lh + rh + 1;
    return (max(curr_diameter ,max(left_diameter , right_diameter)));
}
void sumReplace(node* root){
    if(root == NULL){
        return;
    }
    sumReplace(root->left);
    sumReplace(root->right);
    if(root->left){
        root->data += (root->left->data);
    }
    if(root->right){
        root->data += (root->right->data);
    }
    
}

void inorderprint(node* root){
    if(root == NULL){
        return;
    }
    inorderprint(root->left);
    cout<<root->data<<"->";
    inorderprint(root->right);     
}
int count1 = 0;
void countnodes(node* root){
    if(root == NULL){
        return;
    }
    queue <node*> q;
    q.push(root);
    while(!q.empty()){
        node* node1 = q.front();
        q.pop();
        count1 += 1;
        if(node1 -> left)q.push(node1->left);
        if(node1 -> right)q.push(node1->right);
    }
}
int sumofnodes(node* root){
    if(root == NULL ){
        return 0;
    }
    return sumofnodes(root -> left) + sumofnodes(root -> right) + root->data;
}
int heightcalc(node* root){
    if(root == NULL){
        return 0;
    }
    int lh = heightcalc(root->left);
    int rh = heightcalc(root->right);
    return max(lh,rh)+1;
}
int main(){
    vector <int> preorder = {1,2,4,5,3,6,7};
    vector <int> inorder = {4,2,5,1,6,3,7};
    vector <int> postorder = {4,2,5,3,1};
    node* root = buildtreepreorder(preorder , inorder , 0 , preorder.size() - 1);
    inorderprint(root);
    cout<<endl;
    node* root1 = buildtreepostorder(inorder , postorder , 0 , postorder.size() - 1);
    inorderprint(root1);
    cout<<endl;
    printlevelorder(root);
    countnodes(root);
    cout<<count1<<endl;
    cout<<sumofnodes(root)<<endl;
    cout<<heightcalc(root)<<endl;
}
