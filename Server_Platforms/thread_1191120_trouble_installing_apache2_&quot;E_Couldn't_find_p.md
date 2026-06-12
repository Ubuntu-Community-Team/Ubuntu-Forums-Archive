---
title: "trouble installing apache2 &quot;E: Couldn't find package apache2&quot;"
date: 2009-06-18
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-06-18
i typed the code
 sudo apt-get install apache2

put it says:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2

what do i do?

---

### Post by cdenley on 2009-06-18
Do you have an internet connection. Did you run "sudo apt-get update" first? What is this output?
```

cat /etc/lsb-release
grep ^[^#] /etc/apt/sources.list

```

---

### Post by rhythmiccycle on 2009-06-18
sudo apt-get update

did the trick

thanks

---

### Post by aanca on 2009-07-10
hi. i am totally new to ubuntu, tried to install apache2 and failed with the same error message. read replies on this forum, used command
 sudo apt-get update
 before installing apache and it worked for me also. after that  i also read the explanation somewhere. 

so, thanks.

---

### Post by Ray1 on 2011-09-11
hello, I am getting the same error, it only seems to be checking my cd-drive

after I run the above cmd, it gave me this:  deb cdrom:[ubuntu 7.0 _gutsy gibbon_ -release i386 (20071016)]/ gutsy main restricted

thank you for any help

Ray

---

### Post by rhythmiccycle on 2011-09-11
> **Ray1 said:**
> hello, I am getting the same error, it only seems to be checking my cd-drive

after I run the above cmd, it gave me this:  deb cdrom:[ubuntu 7.0 _gutsy gibbon_ -release i386 (20071016)]/ gutsy main restricted

thank you for any helphoww

Ray

What Camden are you running exactly?

---

### Post by Ray1 on 2011-09-11
sorry, new to linux here, what does "Camden" mean?

---

### Post by rhythmiccycle on 2011-09-11
> **Ray1 said:**
> sorry, new to linux here, what does "Camden" mean?

Sorry, I ment to say "cmd" but the autospell on my phone changed it.

What command are you trying to run?

---

### Post by Ray1 on 2011-09-11
sudo apt-get install apache2

Which got me this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2

I then found this forum, and tried :

sudo apt-get update

which got me this:

deb cdrom:[ubuntu 7.0 _gutsy gibbon_ -release i386 (20071016)]/ gutsy main restricted

Thats where i am as of right now.

---

### Post by rhythmiccycle on 2011-09-12
what does:

```

lsb_release -a

```

return?

---

### Post by Ray1 on 2011-09-13
Distributor ID: Ubuntu
Description:     Ubuntu 7.10
Release            7.10
Codename:       gutsy

---

### Post by Ray1 on 2011-09-13
my problem is solved, thanks for the help.

---

### Post by mörgæs on 2011-09-13
I just noticed that you are running 7.10.

This release ran out of support more than two years ago, meaning that security holes have not been patched. I would recommend that you do a fresh install of a supported release.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

