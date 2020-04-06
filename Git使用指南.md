## Git使用指南

> [廖雪峰教程](https://www.liaoxuefeng.com/) 

#### 1. 创建repository

``git init``

#### 2. 在对应文件夹下增删查改

#### 3. 添加文件repository

``git add readme.txt``

#### 4. 提交

``git commit -m "wrote a readme file"``

#### 5. 查看状态

``git status``

#### 6.查看具体修改的内容

``git diff readme.txt``

#### 7.查看提交日志

``git log``

如果嫌输出信息太多，看得眼花缭乱的，可以试试加上`--pretty=oneline`参数： 

#### 8.准备把`readme.txt`回退到上一个版本 

在Git中，用`HEAD`表示当前版本，也就是最新的提交`1094adb...`（注意我的提交ID和你的肯定不一样），上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个`^`比较容易数不过来，所以写成`HEAD~100`。 

使用命令	``git reset --hard HEAD^``

查看   ``cat readme.txt``

当你用`$ git reset --hard HEAD^`回退到旧版本时，再想恢复新的版本，就必须找到新版本的commit id。Git提供了一个命令`git reflog`用来记录你的每一次命令：

```
$ git reflog
e475afc HEAD@{1}: reset: moving to HEAD^
1094adb (HEAD -> master) HEAD@{2}: commit: append GPL
e475afc HEAD@{3}: commit: add distributed
eaadf4e HEAD@{4}: commit (initial): wrote a readme file
```

终于舒了口气，从输出可知，新版本的commit id是`1094adb`

#### ==变向说明在提交时写说明的重要性==

#### 9.关联github

+ 设置ssh
+ Creat a new repo
+ ``git remote add origin git@github.com:账户名/仓库名.git``
+ 推送到远程仓库  ``git push -u origin master``
  + 由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。
+ 从现在起，只要本地作了提交，就可以通过命令： ``git push origin master``
+ 