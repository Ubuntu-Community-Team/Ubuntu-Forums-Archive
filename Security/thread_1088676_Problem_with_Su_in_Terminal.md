---
title: "Problem with Su in Terminal"
date: 2009-03-06
forum: Security
---

### Post by kerileigh on 2009-03-06
Hi i am running ubuntu 8.10, but cannot seem to be able to use the su command in terminal....... i get

keri@ubuntu:~$ su
Password: 
su: Authentication failure
keri@ubuntu:~$ 

My user account is the only account on ubuntu and i cannot work out why my password is not working?

Can anyone help me? :KS

---

### Post by sisco311 on 2009-03-06
it's because, by default, the root account password is locked in ubuntu.

you can use sudo/gksu to run applications as root.


to start a root shell, type:
```
sudo -i
```.

read more here: [uhelp]community/RootSudo[/uhelp]

---

### Post by kerileigh on 2009-03-06
Im sorry i don't quite understand and have had a read through the link you gave me. :(

Ill tell you what im trying to do, im trying to update my Java following the instructions on Java's site to see if i can get You Tube to work. As at the moment it just keeps crashing fire fox it locks up and goes Grey as soon as you try and play a video.

Im following these instruction 
[http://java.com/en/download/help/5000010500.xml#rpm](http://java.com/en/download/help/5000010500.xml#rpm)

---

### Post by lloyd_b on 2009-03-06
```
sudo su
```will give you a root shell (assuming that you actually need a root shell, that is).  If you just want to run a single command as root,```
sudo <command>
```will do the trick.

Looking at that link, the "sudo su" is the best approximation of their instructions.  However, is there a reason that you just don't install JRE from the repos? ```
sudo apt-get install sun-java6-jre
```

Lloyd B.

---

### Post by kerileigh on 2009-03-06
Just because it seems to recommend i install java 6 update 12 and i have java 6 update 10 im guessing, and it always seems to put that version on here. To be honest i don't think it will solve my you tube problem anyway but i thought it would be worth ago.

Sorry to be a pain im new to all this :D

---

### Post by bodhi.zazen on 2009-03-06
> **kerileigh said:**
> Sorry to be a pain im new to all this :D

It is no problem at all, that is what we are here for. 

It is hard to know how much or little you may know about Linux  or Ubutnu, so if you read something you do not understand, just ask.

The simple answer is that, unlike many distros, Ubuntu does not use su (the root accoutn is disabled / locked).

Instead you use sudo.

To run a single command, use sudo <command> and enter your log in password.

If you wish to run multiple commands, as is likely with the how to you are following, obtain a root shell with :

sudo -i

You then have become root, or the ultimate administrator, and you enter commands without using sudo.

HTH.

---

### Post by kerileigh on 2009-03-06
Thank you i think i understand now.... I got it to install but it has made no difference to my problem, so for now i have downloaded opera and will use that to play videos on YouTube and so on. See this thread [http://ubuntuforums.org/showthread.php?t=1088786](http://ubuntuforums.org/showthread.php?t=1088786)

Thank you for all your replys :)

---

