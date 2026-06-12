---
title: "I can not login after root password changed"
date: 2012-08-06
forum: Security
---

### Post by hoboy on 2012-08-06
Yesterday I have changed my root password this morning when I started the the machine I can not login to ubuntu desktop.
I stop at where to input the password, I had disable this so I could login wihtout inputing the password.
when I wrote the password I can not login in.
I was installing MySql then I changed root password.
I can login using recovery then I can login into the Terminal.
I am desperated.

---

### Post by spynappels on 2012-08-06
Your MySQL root password does not have anything to do with your Ubuntu password, normally, there is no password set for root in Ubuntu and all maintenance is done using sudo rather than the root account directly.

Did you have the Login Automatically feature enabled? Are you trying to login to the desktop using your MySQL password? Can you remember what your original Ubuntu password for your user was?

If you can't, you can use the Recovery console to reset your password.

---

### Post by hoboy on 2012-08-06
> **spynappels said:**
> Your MySQL root password does not have anything to do with your Ubuntu password, normally, there is no password set for root in Ubuntu and all maintenance is done using sudo rather than the root account directly.

Did you have the Login Automatically feature enabled? Are you trying to login to the desktop using your MySQL password? Can you remember what your original Ubuntu password for your user was?

If you can't, you can use the Recovery console to reset your password.

>Did you have the Login Automatically feature enabled?
Yes I did
>Are you trying to login to the desktop using your MySQL password? 
yes, it is the same password as root password.

>you can use the Recovery console to reset your password.
How do i dod that ?
It seemed like thet the user I am trying to login with has a different privilidge or has a new password

tks

---

### Post by hoboy on 2012-08-06
I have reset the password but that has not helped:
I have have the Login Automatically feature enabled? 
I can not pass it, can not login

---

### Post by steeldriver on 2012-08-06
1. what EXACTLY happens when you try to log in (does it tell you the password is incorrect? or some other message? or no message?)

2. can you log in at a virtual terminal e.g. Ctrl-Alt-F1?

---

### Post by hoboy on 2012-08-06
> **steeldriver said:**
> 1. what EXACTLY happens when you try to log in (does it tell you the password is incorrect? or some other message? or no message?)

2. can you log in at a virtual terminal e.g. Ctrl-Alt-F1?

>can you log in at a virtual terminal e.g. Ctrl-Alt-F1?
Nop
> what EXACTLY happens when you try to log in ?
When I enter the password then enter
it treid to login I can se that by the background of the screen 
I can se somthing written on the terminal but goes away again very fast
then back to the login of the locked screen, and no message

---

### Post by ottosykora on 2012-08-06
in such case I think it is not the password problem, but rather something is crashing while loading your profile.

In this case, you better go to the command line console and try to correct things you have done before this happened, or remove software or configuration of what ever you have done before the problem came up.

---

### Post by hoboy on 2012-08-06
Unfortunately I maybe have to make make a new installation.
I was only trying to install dupral, then I uninstalled and installed mysql.

---

### Post by spynappels on 2012-08-06
Just as an aside, when you change the MySQL root password, this does NOT change any other passwords on the system, including any user passwords.

---

### Post by hoboy on 2012-08-06
> **spynappels said:**
> Just as an aside, when you change the MySQL root password, this does NOT change any other passwords on the system, including any user passwords.

I think I did something like this.
[http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/](http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/)
then run chown mysql:mysql .-R

---

### Post by ottosykora on 2012-08-07
then go and uninstall all you have installed and then you should be able to boot again.

As said, the system is crashing on something you did and not refusing password.

I had the same, simply made some syntax mistake in some config file which is loaded on start up and I had exactly same result as you.

So I tried to remember what I did before as last and from the rescue prompt I went to remove the problematic entries. and magic, the system started again.

---

