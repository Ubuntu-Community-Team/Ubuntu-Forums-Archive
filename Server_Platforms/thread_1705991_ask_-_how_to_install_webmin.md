---
title: "ask - how to install webmin ?"
date: 2011-03-13
forum: Server Platforms
---

### Post by cakka on 2011-03-13
hello,

**[COLOR="Blue"][SIZE="4"]=== This problem have been solved, Thank You ===[/SIZE][/COLOR]**


i want to install webmin on my vps
my vps is using ubuntu as operating system
i have download webmin, but when i install it
it come failed
i got this message :


[I]
root@server1:/home/apps# dpkg --install webmin_1.530_all.deb
Selecting previously deselected package webmin.
(Reading database ... 21634 files and directories currently installed.)
Unpacking webmin (from webmin_1.530_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on apt-show-versions; however:
  Package apt-show-versions is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin
[/I]


so, i do this :
root@server1:/home/apps# apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-

and get this message :
[I]perl apt-show-versions
Reading package lists... Done
Building dependency tree
Reading state information... Done
perl is already the newest version.
Package libnet-ssleay-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libnet-ssleay-perl has no installation candidate[/I]

next, i am getting this instruction on webmin page :
> If you are installing on Ubuntu and the apt-get command reports that some of the packages cannot be found, edit /etc/apt/sources.list and make sure the lines ending with universe are not commented out.

how to edit the file via ssh ?

thanks

---

### Post by Kozley on 2011-03-13
I has same problem with it. I was came with a solution to install webmin: sudo apt-get install -f after you install fail.

---

### Post by cakka on 2011-03-13
@Kozley
thanks for your help
i will try your suggestion

---

### Post by cakka on 2011-03-13
> **Kozley said:**
> I has same problem with it. I was came with a solution to install webmin: sudo apt-get install -f after you install fail.

i have try that, and it give me this :


[I]root@server1:/home/apps# sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  webmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 91.4MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 37898 files and directories currently installed.)
Removing webmin ...[/I]


when i go to XXX.XXX.XXX.XX:10000
it's still :
[I]This webpage is not available.

The webpage at [http://XXX.XXX.XXX.XX:10000/](http://XXX.XXX.XXX.XX:10000/) might be temporarily down or it may have moved permanently to a new web address.[/I]

any other ideas ?
thanks

---

### Post by Kozley on 2011-03-13
> **cakka said:**
> i have try that, and it give me this :


[I]root@server1:/home/apps# sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  webmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 91.4MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 37898 files and directories currently installed.)
Removing webmin ...[/I]


when i go to XXX.XXX.XXX.XX:10000
it's still :
[I]This webpage is not available.

The webpage at [http://XXX.XXX.XXX.XX:10000/](http://XXX.XXX.XXX.XX:10000/) might be temporarily down or it may have moved permanently to a new web address.[/I]

any other ideas ?
thanks

Alright, I see you had installed successfully before it fails.
I can put a link to youtube howto, there was I did followed to installation and it works for me. Give a try again. Here's the link: [http://www.youtube.com/watch?v=yrraRReECRg](http://www.youtube.com/watch?v=yrraRReECRg)

Remember always put your localhost on browser after install successfully: [https://localhost:10000](https://localhost:10000)

---

### Post by kevinthecomputerguy on 2011-03-13
You can read page 1 of my website, it will tell you how
 
[http://woodel.com](http://woodel.com)
 
But basically all it is saying is you are missing packages, so type
 
sudo apt-get install those-packages-it-says-you-are-missing-....
 
example in your case that would be this
 
sudo apt-get install *libnet-ssleay-perl libauthen-pam-perl libio-pty-perl apt-show-versions*

---

### Post by jerome1232 on 2011-03-13
I had to attempt to install webmin, then those individual packages, then apt-get install -f figured it all out.


I wonder why dpkg won't just grab those dependencies on it's own?

---

### Post by cakka on 2011-03-15
> **Kozley said:**
> Alright, I see you had installed successfully before it fails.
I can put a link to youtube howto, there was I did followed to installation and it works for me. Give a try again. Here's the link: [http://www.youtube.com/watch?v=yrraRReECRg](http://www.youtube.com/watch?v=yrraRReECRg)

Remember always put your localhost on browser after install successfully: [https://localhost:10000](https://localhost:10000)

ok, i will check this video
i will say to you if something still wrong

> **kevinthecomputerguy said:**
> You can read page 1 of my website, it will tell you how
 
[http://woodel.com](http://woodel.com)
 
But basically all it is saying is you are missing packages, so type
 
sudo apt-get install those-packages-it-says-you-are-missing-....
 
example in your case that would be this
 
sudo apt-get install *libnet-ssleay-perl libauthen-pam-perl libio-pty-perl apt-show-versions*

thanks for your help, i will try it too if the video didn't give me the solution

> **jerome1232 said:**
> I had to attempt to install webmin, then those individual packages, then apt-get install -f figured it all out.


I wonder why dpkg won't just grab those dependencies on it's own?

i have to do that, but it just remove the webmin
is i make a mistake ?

thanks

---

### Post by kevinthecomputerguy on 2011-03-15
:- )

---

### Post by cakka on 2011-03-15
> **Kozley said:**
> Alright, I see you had installed successfully before it fails.
I can put a link to youtube howto, there was I did followed to installation and it works for me. Give a try again. Here's the link: [http://www.youtube.com/watch?v=yrraRReECRg](http://www.youtube.com/watch?v=yrraRReECRg)

Remember always put your localhost on browser after install successfully: [https://localhost:10000](https://localhost:10000)

i have tried the method on youtube but there is any different, check out this

[I]root@server1:/home/apps# sudo dpkg -i webmin_1.530_all.deb
Selecting previously deselected package webmin.
(Reading database ... 21634 files and directories currently installed.)
Unpacking webmin (from webmin_1.530_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on apt-show-versions; however:
  Package apt-show-versions is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin

root@server1:/home/apps# sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
[B][COLOR="Red"]The following packages will be REMOVED:
  webmin
[/COLOR][/B]0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
[B][COLOR="red"]1 not fully installed or removed.
After this operation, 91.4MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 37898 files and directories currently installed.)
Removing webmin ...[/COLOR][/B]
[/I]

it is not install the needed package but remove the webmin
i am using ubuntu-10.04-x86 for my vps

thanks

---

### Post by cakka on 2011-03-15
> **kevinthecomputerguy said:**
> Can't believe i am being compared to some video on a webmin question...
 
nobody knows who i am :- (

sorry for that, i just try to clearing this problem step by step ;)
thanks for your help friend :popcorn:

---

### Post by jerome1232 on 2011-03-15
did you try installing those packages you are missing?

```
sudo apt-get install libnet-ssleay-perl libauthen-pam-perl libauthen-pam-perl libio-pty-perl apt-show-versions
```

---

### Post by cakka on 2011-03-15
> **kevinthecomputerguy said:**
> You can read page 1 of my website, it will tell you how
 
[http://woodel.com](http://woodel.com)
 
But basically all it is saying is you are missing packages, so type
 
sudo apt-get install those-packages-it-says-you-are-missing-....
 
example in your case that would be this
 
sudo apt-get install *libnet-ssleay-perl libauthen-pam-perl libio-pty-perl apt-show-versions*

after install webmin, i have try this 
*apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl apt-show-versions*

but it make some application downgraded & crash
any ideas ?

on webmin site, i am getting this tutorial :

***If you are installing on Ubuntu and the apt-get command reports that some of the packages cannot be found, edit /etc/apt/sources.list and make sure the lines ending with universe are not commented out.***

but how to do that ?

thanks

---

### Post by cakka on 2011-03-15
> **jerome1232 said:**
> did you try installing those packages you are missing?

```
sudo apt-get install libnet-ssleay-perl libauthen-pam-perl libauthen-pam-perl libio-pty-perl apt-show-versions
```

yes, i did. check on #13

thanks

---

### Post by cakka on 2011-03-15
i have tried the step that i got from webmin site, but i am confuse to edit the ***/etc/apt/sources.list*** file

please tell me the way
thanks

---

### Post by jerome1232 on 2011-03-15
Be careful editing this file!!!!

sudo nano /etc/apt/sources.list

or if you have a gui installed (assuming gnome)

gksu gedit /etc/apt/sources.list

kde

kdesu kate /etc/apt/sources.list

---

### Post by kevinthecomputerguy on 2011-03-15
Page 1 of my website walks you through the steps
 
or this command
 
sudo apt-get install vim 
 
sudo vim /etc/apt/sources.list
 
good luck
 
Edit * run sudo before every command

---

### Post by jerome1232 on 2011-03-15
You said an application was going to be downgraded? What was the exact output from that attempt to install?

---

### Post by cakka on 2011-03-15
> **jerome1232 said:**
> You said an application was going to be downgraded? What was the exact output from that attempt to install?


sorry, i am wrong
after i do :
*apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl apt-show-versions*

i tried to download and install libnet-ssleay-prel
now i am trying to edit the /etc/apt/sources.list

thanks

---

### Post by cakka on 2011-03-15
this problem have solved
thanks friends, for your help :)

---

### Post by Kozley on 2011-03-15
> **cakka said:**
> this problem have solved
thanks friends, for your help :)

Glad to you have solved your problem to install webmin :)
Please mark this thread as solved. You can find it on drop down "Thread Tools".

---

### Post by cakka on 2011-04-28
> **Kozley said:**
> Glad to you have solved your problem to install webmin :)
Please mark this thread as solved. You can find it on drop down "Thread Tools".

ok, thank you

---

