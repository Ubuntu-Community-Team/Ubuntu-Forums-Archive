---
title: "Correct working with branches on remote server"
date: 2019-01-08
forum: Server Platforms
---

### Post by ivancsvetkov on 2019-01-08
Hello,
Working with php project and using git(on bitbucket) I had to switch to other branch, work with it, upload it, 
but after return to master and work with it and upload merged branches like similar scheme:
1) On local server
```
git stash
git checkout -b NewsWithdiffForHumansFormat

```
# work with files which are inside of NewsWithdiffForHumansFormat branch
```
git add .
git commit -m "NewsWithdiffForHumansFormat commit 1"
git push origin NewsWithdiffForHumansFormat

```and new branch was created on bitbucket with my changes.

2) On remote SERVER :
```
cd  project_dir
git stash
git fetch origin NewsWithdiffForHumansFormat:NewsWithdiffForHumansFormat
git checkout NewsWithdiffForHumansFormat

```After steps above my changes in NewsWithdiffForHumansFormat are applied to my remote server and NewsWithdiffForHumansFormat branch
is current on my remote server.
It works for me ok(I have a few files only), but reading docs I found that command
```
git pull --rebase
```
must be applied here, otherwise that could raise problems and I missed why?
I read in docs :
> [COLOR=#4d4d4d]A [/COLOR]--rebase[COLOR=#4d4d4d]option can be passed to [/COLOR]git pull[COLOR=#4d4d4d]to use a rebase merging strategy instead of a merge commit. [/COLOR]


3) On local server return to master branch
```
git checkout master
git stash pop 

```# work with files which are inside of master branch
git add .
```
git commit -m "mergin master with NewsWithdiffForHumansFormat"
git merge NewsWithdiffForHumansFormat

```After merging I have all my changes on master branch


4) On remote SERVER pull data :
```
cd  project_dir
git checkout master
git pull origin master 

```Now all my modifications in master branch.

5) Please, look, if that flow is correct and pay attention at my question ap point 2)?

6) Also after that I have 1 more branch NewsWithdiffForHumansFormat on my local and remote servers and on bitbucket. 
As I do not need it I can delete it with command :
```
git branch -d NewsWithdiffForHumansFormat

```Both on my local and remote servers

but how to delete it on bitbucket properly and safe ?

Thanks in advance!

---

### Post by ajgreeny on 2019-01-08
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

