# Task-package com.demo;

import java.util.Stack;

public class Tree {}
class leaf extends Tree{}
class Branch extends Tree{


    public Tree(Tree left, Tree right) {
        this.left = left;
        this.right = right;
    }
    public Tree left;
    public Tree right;
}

public String treeToParens(Tree tree) {
    if (tree instanceof Leaf) {
        return "()";
    } else if (tree instanceof Branch) {
        Branch branch = (Branch)tree;
        return "(" + treeToParens(branch.left) + treeToParens(branch.right) + ")";
    } else {
        throw new IllegalArgumentException("Invalid tree type");
    }
}

public Tree parensToTree(String parens) {
    Stack<Tree> stack = new Stack<>();
    for (int i = 0; i < parens.length(); i++) {
        char c = parens.charAt(i);
        if (c == '(') {
            stack.push(null);
        } else if (c == ')') {
            Tree right = stack.pop();
            Tree left = stack.pop();
            stack.pop(); // Pop the null placeholder
            stack.push(left);
        } else {
            throw new IllegalArgumentException("Invalid character: " + c);
        }
    }
    if (stack.size() != 1) {
        throw new IllegalArgumentException("Invalid parens string");
    }
    return stack.pop();
   
}



}









