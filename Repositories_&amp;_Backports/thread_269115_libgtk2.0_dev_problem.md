---
title: "libgtk2.0 dev problem"
date: 2006-10-01
forum: Repositories &amp; Backports
---

### Post by bayger on 2006-10-01
Does anybody know how to resolve the following problem (apt-get install libgtk2.0-dev)?

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.17-1ubuntu5) but 2.8.20-0ubuntu1 is to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
E: Broken packages

Is there a dependency error in the repo?

---

### Post by bayger on 2006-10-01
If somebody has the same problem. Maybe this is the solution for you. [Follow this link]("http://ubuntuforums.org/showthread.php?p=1567243").

---

### Post by ryan723 on 2006-10-04
I had the same exact error.
EasyUbuntu created a backup sources.list (/etc/apt/sources.list-eu-2006-9-27-11-57-35 in my case).  
i backed up my current sources.list and them copied the pre-EasyUbuntu file to sources.list, updated, and installed libgtk2.0-dev without errors.


detailed steps:
'cd /etc/apt/'
'sudo cp sources.list sources.list.backup.10042006'
'sudo cp sources.list-eu-2006-9-27-11-57-35 sources.list'
'sudo apt-get update'
'sudo apt-get install libgtk2.0-dev' 
...hope this helps someone.

---

### Post by gr8whitesavage on 2006-10-19
Helped me thanks!

---

### Post by dizm on 2006-12-06
Helped me too!  Thanks!

---

### Post by gilad g on 2006-12-25
helped me as well.
thanks! :)

---

### Post by goldaryn on 2007-01-12
i had the same problem.. (xubuntu feisty herd 2).. was using

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse

and when I did 
```
sudo apt-get install libgtk2.0-dev
```
I got:

The following packages have unmet dependencies.
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.10.6-0ubuntu4) but 2.10.7-0ubuntu1 is to be installed
                 Depends: libglib2.0-dev (>= 2.12.0) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.12) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.9) but it is not going to be installed
E: Broken packages

But when I use

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse

(i.e. main servers as opposed to local).. it works

Hope this helps someone..

g.

---

