---
title: "Samba - missing /etc/init.d/samba + testparm -s doesnt work"
date: 2010-06-19
forum: Server Platforms
---

### Post by neosn4ke on 2010-06-19
Installed Ubuntu Server 10.04

Installed Samba via:
```
sudo apt-get install samba
```

Problem 1:
/etc/init.d/samba is missing.
Is it placed somewhere else in Ubuntu?

Problem 2:
```
sudo testparm -s smb.conf.master > smb.conf
```
returns:
```
-bash: smb.conf: Permission denied
```
Why is that?


PS
I am a n00b to linux, so Im probably just doing something wrong...

---

### Post by Ryan Dwyer on 2010-06-19
It's /etc/init.d/smbd.

Try:
sudo bash
testparm -s smb.conf.master > smb.conf
exit # to exit the privileged bash prompt

---

### Post by neosn4ke on 2010-06-19
1
So to restart samba I basically use
```
sudo restart smbd
```
right?
And do I need also to do 
```
sudo restart nmbd
```
?


2
That worked, thanks!
So this
```
sudo bash
```
is kind of a "root-mode"?

---

### Post by Ryan Dwyer on 2010-06-19
Yes, sudo restart smbd. nmbd is to do with resolving hostnames, so you might not need to restart that one. It depends what you're doing.

sudo bash basically runs a new instance of your terminal session as root. So yeah, it's sort of like "root-mode". Typing exit ends that bash session and returns you to the previous non-privileged session.

---

### Post by Morbius1 on 2010-06-19
I believe the technically correct way to reproduce the the restarting of the old "samba" service is to restart nmbd first:

```
 sudo restart nmbd
```Then,
```
 sudo restart smbd
```There is one more complication to all this. Back in the good old days if the samba service wasn't running you could issue a **sudo service samba restart** and it would start it. But not anymore.

If smbd is running then a **sudo restart** will restart it.  If smbd is not running then you have to start it:
```
sudo start smbd
```If you issue a sudo restart and smbd is not running you will get this error message:
> restart: Unknown instance: 


---

### Post by neosn4ke on 2010-06-19
Ok, thank you very much, that was very helpful.

Dont know how to change the tag to [SOLVED] though...

---

### Post by kanolsen on 2010-06-22
To post as solved check the Thread tools on the top of the page.

Kanolsen

---

### Post by TFroehlich3 on 2012-02-20
> **Morbius1 said:**
> I believe the technically correct way to reproduce the the restarting of the old "samba" service is to restart nmbd first:

```
 sudo restart nmbd
```Then,
```
 sudo restart smbd
```There is one more complication to all this. Back in the good old days if the samba service wasn't running you could issue a **sudo service samba restart** and it would start it. But not anymore.

If smbd is running then a **sudo restart** will restart it.  If smbd is not running then you have to start it:
```
sudo start smbd
```If you issue a sudo restart and smbd is not running you will get this error message:

my nmbd is giving me this error. How can I fix this?

---

