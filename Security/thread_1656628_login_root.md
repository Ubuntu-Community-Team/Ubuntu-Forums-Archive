---
title: "login root"
date: 2010-12-31
forum: Security
---

### Post by owiknowi on 2010-12-31
installed kubuntu 10.04.1 in expertmode from alternate cd.
when asked to set up users was asked: "allow root login?"
answered "yes" and gave a password for root, then set up a normal user.

in ubuntu 10.04.1 this works just fine and i'm able to login as root.
in kubuntu 10.04.1 this doesn't seem to work?

anyone any idea why?

thanks up front for your help!

p.s. please no discussions on why i should not login as root. ;)

---

### Post by CharlesA on 2010-12-31
It's easier to just disable root login, and use ***sudo -i*** or ***su*** to get a root shell.

---

### Post by cariboo on 2010-12-31
I'd like to know what you mean by saying it doesn't work. If you have the root account disable, you should be able to su to root in a terminal.

---

### Post by owiknowi on 2010-12-31
thank's for the replies!

in ubuntu i can log in - at the graphical log in screen that is - as root user.
this way i can mess things up or adjust them the way i think is best.

a root terminal works fine when root password is set (root terminal).

so why does it work on a fresh ubuntu installation and not likewise in kubuntu?

---

### Post by CharlesA on 2010-12-31
Probably a security measure, as you shouldn't be logging into a GUI as root.

I don't really know, as I've never actually logged in as root to a GUI. I always use gksudo or kdesudo to run applications with root permissions.

---

### Post by owiknowi on 2010-12-31
> **CharlesA said:**
> Probably a security measure, as you shouldn't be logging into a GUI as root.

I don't really know, as I've never actually logged in as root to a GUI. I always use gksudo or kdesudo to run applications with root permissions.

i specifically asked not to go this way. just needed a pretty simple answer.
so i'll leave it at this and close the thread.

---

### Post by lisati on 2010-12-31
> **owiknowi said:**
> i specifically asked not to go this way. just needed a pretty simple answer.
so i'll leave it at this and close the thread.

We don't normally discus "log in as root" here, so maybe closing the thread is a good idea.

For those who are interested, some further information can be found at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

