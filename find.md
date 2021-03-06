﻿
# 查找：
### 在线性表中顺序查找的基本思想：       
将要查找的值与表中的每一个值进行比较。     
如果相等，则查找成功，并返回该数据位置。    
如果直到最后都没有直到匹配的数据，则查找失败。    

### 查找表与查找
##### 查找表的概念：       
查找表是由同一类型的数据元素构成的集合。表中的每个数据元素均由若干个数据项组成，每个数据项的值称为该数据元素的关键字，其中可以唯一标识一个数据元素的关键字称为主关键字；否则称为次关键字；     

举例：       
全体学生组成一个集合，各学生为一个数据元素，学号为主关键字，姓名为次关键字；    

### 查找：      
查找，顾名思义也就是，搜索；     
是指，在查找表中寻找满足给定条件的数据元素；    
查找要求返回该数据元素在查找表中的位置。    
如果找到相应的数据元素，则称为查找成功。         

数据结构分为线性结构和非线性结构，其中有线性表和树的概念，因此针对查找表不同的存储结构，查找可以分为线性表查找、树结构查找等。      
```
线性查找
树结构查找
```
#### 线性表的查找：
线性表的查找就是对线性存储结构的数据元素集合中查找某个元素的操作；    
#####线性表查找的算法：
```
顺序查找
折半查找
```
##### 顺序查找
顺序查找的基本思想：    
比较目标值与表中的每一个元素的值。     
如果某个元素的值与目标值相等，则查找成功，并返回该数据元素的位置。     
如果直到表尾仍没有找到与目标值匹配的元素，则查找失败。     

示例：      
要求从一组数据 `16 42 23 7 45` 中查找数据7     
初始数据     `16 42 23 7 45`     
```
第一步   7与第一个元素匹配
第二步   7与第二个元素匹配
第三步   7与第三个元素匹配
第四步   7与第四个元素匹配，匹配成功，返回数据元素7的位置。
```
##### 顺序查找代码：
```java
int[] data = {16,42,23,7,45};
int len = data.length;
for(int i=0;i<len;i++) {
  if(data[i] == findData) {
   System.out.print("查找成功！");
    break;
  }
if(i==len-1)
   System.out.print("查找失败！");
}
```

##### 折半查找算法
折半查找的基本思想：
折半查找的基本思想就是，用指定的关键字与查找表中间位置数据元素的关键字比较。如果二者相等，则查找成功；否则以中间元素为界，将查找表分为前、后两部分。如果中间元素关键字大于给定关键字，则在前一子表进行折半查找；否则在后一子表进行折半查找。重复上述过程，直到出现匹配的数据元素，则查找成功。反之，如果直到子表为空时仍未找到，则查找失败。      

我们要想使用折半查找线性表，有一个前提条件，这个线性表必须是已经排序号的，也就是说，这个线性表是一个有序序列；        

举例：      
```
待查找元素  45
有序序列    7 16 23 42 45
根据折半查找的基本思路，待查找元素45分别与有序序列中的元素23，元素42，元素45进行比较，最后查找成功，返回元素45的位置。
```
##### 折半查找代码：
```java
public static void main(String[] args) {
 int[] data={7,16,23,42,45};
 int len = data.length;
 int low = 0;  //定义最低位
 int high = len-1;  //定义最高位
 while(low<=high) {
   int middle = (low+high)/2;    //计算平分位置
   if(findData == data[middle])
   {
     System.out.println("查找成功，位于data["+middle+"]");
      return;
   }
  //确定下一步要平分的子序列的位置
  else if(findData <data[middle])
     high = middle-1;
  else
     low = middle+1;
  }
  System.out.println("查找失败");
}
```

在代码中，首先要确定有序序列的最低位和最高位的位置，然后计算出平分位置；平分位置的计算方法就是，最低位+最高位除以2，并且取整；        
那么计算出平分位置之后，我们再通过待查找元素与该平分位置的关键字进行比较，那么如果相等，则说明查找成功，通过return关键字结束；而如果不相等，则需要确定下一步要平分的子序列的为，那么以此类推，直到最后；        
那么如果直到最后都没有查找成功的话，则说明整个查找是失败的。    

### 二叉查找树
二叉查找树也叫二叉排序树；
#### 二叉树：
二叉树是个有序树，并且每个节点最多有两个子节点；    
##### 二叉查找树的概念：
- 若它的左子树非空，则左子树上所有节点的值均小于根节点的值；    
- 若它的右子树非空，则右子树上所有节点的值均大于根节点的值；    
- 左右子树本身又是一棵二叉查找树。   

二叉查找树的这些特点确保了二叉查找树中不存在两个节点具有相同的关键字的值；因为左子树中的关键字值必须严格地比根节点的关键字小，而右子树中的关键字的值必须严格地比根节点的关键字大。

##### 中序遍历二叉树的步骤：
```
中序访问左子树
访问根节点
中序访问右子树
```
##### 二叉查找树的性质：
按中序遍历二叉查找树，所得到的中序遍历序列是一个递增有序序列。

##### 构造二叉查找树之插入算法
- 确定插入位置的方法：   
比较新节点关键字与个子树根节点的大小关系。如果新节点关键字小，则递归进入相应根节点的左子树，直到找到左子树为空的位置；否则，递归进入相应根节点的右子树，直到找到右子树为空的位置。
此时，便确定了新节点的插入位置。

代码：     
```java
class Node {
  int data;
  Node left;
  Node right;
 public Node(int data,Node left,Node right) {
    this.data = data;
    this.left = left;
    this.right = right;
  }
}
```
在代码中，首先定义了节点类：Node类，类中含有data left right等属性；分别表示当前节点的数据、左节点和右节点。      
```java
private void addTree(Node rootNode,int data) {
  //添加到左边
 if(rootNode.data >data) {
    if(rootNode.left == null)
      rootNode.left = new Node(data,null,null);
    else
      addTree(rootNode.left,data);
 else{
   //添加到右边
     if(rootNode.right == null)
       rootNode.right = new Node(data,null,null);
     else
       addTree(rootNode.right,data);
   }
}
```


- addTree方法，即，插入节点的方法；   
在方法中，第一个if判断表示：当前插入节点小于树中的节点时，则将继续递归进入这个节点的左子树，直到找到左子树为空的位置。     
相反，当插入节点大于树中的节点时，则将继续递归进入这个节点的右子树，直到找到右子树为空的位置。    
```java
private void showTree(Node node) {
 if(node.left != null) {
    showTree(node.left);
}
System.out.println(node.data+" ");
if(node.right != null) {
  showTree(node.right);
  }
}
```


- showTree方法；
这个方法用于中序遍历树中的节点，并打印输出节点的值。      
第一个if条件判断，遍历左子树；      
第二个if条件判断，遍历右子树；         

示例：
```
将一组数据5,3,7,2,4,8依次插入到一棵树当中，并构造成二叉查找树。
5作为根节点，依次进行下去；
```
对于同一组数据，我们采用不同的顺序，可以生成不一样的二叉查找树；


##### 构造二叉查找树之删除算法
一般来说，根据删除节点是否含有子节点，将二叉查找树的删除操作分为三种情况：
- 第一种情况：    
如果删除的节点没有子节点，在删除的时候直接将其父节点的相应位置的引用设置为空即可。     
- 第二种情况：        
如果当前删除节点，只有一个子节点，只要让这个要删除的节点的子节点代替的位置即可。     
换句话说，如果要删除的节点是父节点的左节点，那么就让它的子节点成为其父节点的左节点；而如果要删除的节点是父节点的右节点，就让它的子节点成为其父节点的右节点即可。      
- 第三种情况：    
如果当前删除的节点有两个子节点。    
用最接近于删除节点的中序后继节点来代替它。       
所以，我们首先需要找出最接近于待删除节点的中序后继节点是哪一个。    

##### 程序实现删除操作
第一种情况      
```java
if(cur.left==null&&cur.right==null) {
 if(cur !=root)
   if(cur.parent.right == cur)
     cur.parent.right = null;
   else
    cur.parent =null;
 else
  root = null;
}
```

第二种情况：当前删除的节点含有一个左节点     
```java
if(cur.left !=null) {
 if(cur != root) {
   if(cur.parent.right == cur)
      cur.parent.right = cur.left;
   else
      cur.parent.left = cur.left;
   cur.left.parent = cur.parent;
 }else{
  root = cur.left;
  cur.left.parent = null;
  }
}
```

第二种情况：当前删除的节点含有一个右节点     
```java
if(cur.right !=null) {
 if(cur != root) {
   if(cur.parent.right == cur)
      cur.parent.right = cur.right;
   else
      cur.parent.left = cur.right;
   cur.right.parent = cur.parent;
 }else{
  root = cur.right;
  cur.right.parent = null;
  }
}
```

##### 二叉查找树的查找
二叉查找树的基本查找方法：    
如果二叉查找树为空，则查找失败；否则：     
 从根节点开始，如果给定值等于根节点关键字，则查找成功；     
 如果给定值小于根节点的关键字，则继续在左子树上递归查找    
 如果给定值大于根节点的关键字，则继续在右子树上递归查找     
 如果直到最后也没有查找到给定值，则整个查找是失败的。    

查找代码     
```java
public Node searchNode(int id) {
 Node n=null;
 Node cur = root;
 while (true) {
    if(cur == null)  
 	break;
    if(id == cur.data) {
	n = cur;
	break;
    }
    if(id >cur.data)
        cur = cur.right;
    else
        cur = cur.left;
    }
    return n;
}
```

根据二叉查找树的基本查找方法：如果二叉查找树为空，则查找失败；    
```java
if(cur == null)  
 	break;
```

通过break语句跳出while循环，不再继续查找；    
也就是说，如果二叉查找树为空，则直接跳出循环，不再继续查找了，并且说明这个查找是失败的；
如果二叉查找树不为空，首先，从根节点开始，如果给定值等于根节点关键字，
则查找成功，即：      
```java
if(id == cur.data) {
	n = cur;
	break;
}
```
查找成功以后，同样通过break跳出while循环，不再继续查找。   
如果给定值不等于根节点关键字，继续查找，即：    
```java
if(id >cur.data)
        cur = cur.right;
    else
        cur = cur.left;
```
如果给定值大于根节点的关键字，则继续在右子树上递归查找；   
如果给定值小于根节点的关键字，则继续在左子树上递归查找；  

最后，通过return语句，返回查找到的节点。    


##### 平衡二叉树一般具有下列性质：
二叉树中任意节点的左右子树的高度之差的绝对值不大于1.    
树的高度：     
就是指树的根节点到树中叶节点的最长路径的长度，也称作深度。        

在平衡二叉树中，一个节点的左右子树的高度之差称为该节点的平衡因子。    
所以，平衡二叉树上各节点的平衡因子只可能是 -1 、 0 、1 。       
因为左右子树的高度之差的绝对值不大于1。         

##### 平衡二叉树的优点：
美观。        
可以提高查找效率。    
所以，一般尽量将二叉查找树构造成平衡二叉树，这样各方面的性能会得到很大的提高。      

##### 平衡二叉树的调整方法：
前面我们讲解过二叉查找树的插入、删除等操作，同样对于平衡二叉树，它也支持节点的增加或删除等操作。       
而在经过节点的插入或删除操作以后，往往会造成树中的某些节点的高度和平衡因子发生变化，从而平衡二叉树失去了平衡。以至于不再满足平衡二叉树的条件。此时，我们需要重新调整二叉树的结构，使之重新平衡。     
