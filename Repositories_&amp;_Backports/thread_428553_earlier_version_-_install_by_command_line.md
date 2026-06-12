---
title: "earlier version - install by command line"
date: 2007-04-30
forum: Repositories &amp; Backports
---

### Post by ebeaty on 2007-04-30
Hello.  I'm running Feisty, but I need to install the sun-java5-jdk package from an earlier repository (version 1.5.0-06-1 from dapper).  Is there an easy way to do this by the command line using apt-get, dpkg, or some other utility?  

Thanks for your help,
Ed

---

### Post by jfinkels on 2007-04-30
> **ebeaty said:**
> Hello.  I'm running Feisty, but I need to install the sun-java5-jdk package from an earlier repository (version 1.5.0-06-1 from dapper).  Is there an easy way to do this by the command line using apt-get, dpkg, or some other utility?  

Thanks for your help,
Ed

I have never tried this buuut...

You will have to enable the dapper repositories in your /etc/apt/sources.list file. 
First backup your sources.list file by typing the following in the terminal: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```
Then type the following command to open the text editor "nano":
```
sudo nano /etc/apt/sources.list
```
Edit each line so that every time "feisty" appears, change it to "dapper". (Actually, you should probably change it so that only the restricted repository is dapper, because you only really need the sun-java5-jdk package) Then save and exit by pressing <Ctrl>+<O> and <Ctrl>+<X>. Now you will have access to dapper repos after you run ```
sudo aptitude update
```

---

### Post by ebeaty on 2007-04-30
Thanks!  That worked great!

---

### Post by jfinkels on 2007-04-30
> **ebeaty said:**
> Thanks!  That worked great!

Great! Just remember and be aware that you won't be getting any updates from Feisty's restricted repositories anymore; it'll be Dapper.

---

