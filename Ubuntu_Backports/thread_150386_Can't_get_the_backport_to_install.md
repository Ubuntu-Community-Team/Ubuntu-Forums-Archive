---
title: "Can't get the backport to install"
date: 2006-03-25
forum: Ubuntu Backports
---

### Post by kpgalligan on 2006-03-25
I hate posting this because I'm sure it's going to seem like a real nub issue.  However, I can't seem to force a backport to install.

I'm trying to install postgresql on a server install.  In the backports packages list, it looks like 8.0.6 and 8.1.? is available.  Ideally I'd probably shoot for the 8.0.6.  I guess the first question is if this is a really bad idea?

After that, how do I get it to work?  I ran just...

```
apt-get install postgresql
```

before adding the backports source.  It installed 7.4.  I ran remove on that, which hopefully worked (but ran very quick).  That's when I moved on to the backports.

I've read the "getting started"...

[http://ubuntuforums.org/showthread.php?t=40291]("http://ubuntuforums.org/showthread.php?t=40291")

I added the following to my sources file...

```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

Then I've tried...

```
apt-get -s install postgresql
```

It says it'll install 7.4.

I tried...

```
apt-get -s -t breezy-backports install postgresql
```

and it said the same.  Any thoughts?

Thanks in advance.

---

### Post by Sutekh on 2006-03-26
[QUOTE=kpgalligan]
...

I added the following to my sources file...

```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

Then I've tried...

```
apt-get -s install postgresql
```

It says it'll install 7.4.

...
[/QUOTE]

Did you use
```
sudo apt-get update
```In between these steps, to refresh the package lists, now that you have added the backports repository?

---

### Post by kpgalligan on 2006-03-26
[QUOTE=Sutekh]Did you use
```
sudo apt-get update
```In between these steps, to refresh the package lists, now that you have added the backports repository?[/QUOTE]

Yeah.  I ran the update.

Should I need to specify the '-t breezy-backports', or should it find the newer version?

---

### Post by Sutekh on 2006-03-26
It should find the newer version and try to install it.   I'm not sure why its not working.   When you run apt-get update are the repository lists refreshed without errors?


You could go the long way and download the .deb from the Ubuntu repositories

[Ubuntu Packages - postgresql-8.1](http://packages.ubuntu.com/breezy-backports/misc/postgresql-8.1)

and install the dependencies yourself, then install postgresql-8.1 with
```
sudo dpkg -i postgresql-8.1_8.1.2-1~breezy1_i386.deb
```

---

