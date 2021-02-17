# Learn Git

## 创建版本库

创建一个空目录

```
mkdir 版本库
cd 版本库
pwd
```

把这个目录变成Git可以管理的仓库

``` 
git init
```

添加文件到版本库

```
git add 文件名
git commit -m "标注"
```

## 时光机穿梭

当修改文件后，可用以下命令查看结果

```
git status
```

查看具体修改了什么内容

```
git diff 文件名
```

#### 版本回退

告诉我们历史修改记录

```
git log
```

回退到上一个版本

```
git reset --hard HEAD^
```

回退到某个版本

```
git reset --hard 前几位版本号
```

记录每一次命令

```
git reflog
```

#### 管理修改

如何提交第二次修改

```
1.继续git add -> git commit
2.先不提交第一次修改，git add 第二次修改后，再git commit
3.第一次修改 -> git add -> 第二次修改 -> git add -> git commit
```

#### 撤销修改

丢弃工作区的修改

```
git checkout -- 文件名
```

丢弃暂存区的修改

```
git reset HEAD 文件名
```

此时回到前述丢弃工作区修改的场景

#### 删除文件

工作区删除文件

```
rm 文件名
```

版本库删除文件

```
git rm 文件名
git commit -m "注释"
```

误删需要找回

```
git checkout -- 文件名
```

## 远程仓库

#### 添加远程库

首先在GitHub中点击"Create a new repo"按钮，创建一个新的仓库，例如learngit

根据GitHub的提示，在本地learngit库下运行命令

```
git remote add origin git@github.com:prince687028/learngit.git
```

添加后，生成名为origin的远程库

把本地内容推送到远程

```
git push -u origin master
```

#### 从远程库克隆

远程库准备好之后，克隆一个本地库

```
git clone git@github.com:prince687028/gitskills.git
```

## 分支管理

#### 创建与合并分支

创建分支

```
git checkout -b 分支名
```

![git-br-create](https://www.liaoxuefeng.com/files/attachments/919022363210080/l)

-b表示创建并切换，相当于以下两条命令

```
git branch dev
git checkout dev
```

列出所有的分支

```
git branch
```

切换分支

```
git checkout 分支名
```

合并指定分支到当前分支，即使当前分支指向与指定分支相同的内容

```
git merge 分支名
```

![git-br-ff-merge](https://www.liaoxuefeng.com/files/attachments/919022412005504/0)

删除分支

```
git branch -d 分支名
```

也可以使用switch来进行分支的切换

创建并切换到新的分支

```
git switch -c 分支名
```

切换到已有的分支

```
git switch 分支名
```

#### 解决冲突

例如master和feature两个分支都进行了修改，此时会出现合并不成功的情况，需要通过手动解决冲突

分支合并图

```
git log --graph
```

#### 分支管理策略

合并分支时，使用普通模式合并

```
git merge --no--ff -m "注释" 分支名
```

此时的分支合并示意图如下

![git-no-ff-mode](https://www.liaoxuefeng.com/files/attachments/919023225142304/0)



#### Bug分支



## 标签管理

#### 创建标签

打上一个新标签

```
git tag 标签名
```

查看所有标签

```
git tag
```

对于指定版本号的文件打标签

```
git tag 标签名 版本号
```

查看标签所对应的内容

```
git show 标签名
```

#### 操作标签

标签打错了，删除标签

```
git tag -d 标签名
```

将标签名推送到远程

```
git push origin 标签名
```

一次性推送所有未推送到远程的标签

```
git push origin --tags
```

删除远程标签，需要先完成本地删除，然后使用

```
git push origin :refs/tags/标签名
```

