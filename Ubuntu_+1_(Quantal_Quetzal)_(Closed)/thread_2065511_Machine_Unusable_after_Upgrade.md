---
title: "Machine Unusable after Upgrade"
date: 2012-10-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mmasroorali on 2012-10-02
Dear All,
This morning I ran distribution upgrades to Quantal Quetzal in both my home and office machines. The previous version was 12.04.

For my office machine it went fine leaving aside to Beta version problems which I like to face twice every year. However, due to some local problems, the house machine had to be hard rebooted at midpoint of upgrade (software downloads finished, installation in progress). After this, the graphical window environment was unavailable but the terminals were available (Ctrl-Alt-F1). 

I ran 
```
sudo apt-get upgrade 
```
which also exited with some dpkg error at some point.

Now, the machine boots fine, I get the graphical login window, and then the machine locks. No keyboard, no mouse and hence no terminal.

I guess my options are,
[LIST=1]
[*]Somehow coax the machine not to start a graphical environment and then run update plus upgrade from terminal. I do not know how to ask the machine not to start the graphical environment during reboot.
[*]Boot the machine with an old version (I have 11.10 in hand) CD (that is how I am making this post) and then run update plus upgrade. I do not know how run upgrade for the OS in hard disk when the machine is running from an Ubuntu CD.
[*]Install an old version from CD, then run dist upgrade. I know how to do this, but this is lossy, lengthy and painfull.
[/LIST]

Any suggestion will be appreciated. I prefer to go for the first one, if possible. But definitely you may want to show me other options.


**_Update after an hour_**
[http://askubuntu.com/questions/92276/how-do-i-boot-into-true-text-mode](http://askubuntu.com/questions/92276/how-do-i-boot-into-true-text-mode) tells me how to boot Ubuntu in text mode. However, when I try to run
```
sudo update-grub
```
after editing my original grub file, this does not work, as it should not, the grub file is not on the default location. Rather it is in a mounted disk and the command does not work.

---

### Post by rbrick49 on 2012-10-02
did you update from precise to quantal. if you did this i would suggest you download a dailly build of quantal then reinstall as sometimes as I have found you will get some small problem where your distro wont install new kernels
only a suggestion

---

### Post by grahammechanical on 2012-10-02
Do you get the Grub menu? You can do a couple of things.

a) At the Grub menu select the kernel that you wish to boot and press the letter 'e' That will let you edit the Grub script for loading that kernel. Look for a line that has "ro quiet splash" towards the end of the line and replace "quite splash" with "nomodeset." (without the quotation marks)

That should get you to a login screen and from there to a desktop. You may need to install video drivers.

b) At the grub menu select Recovery mode. I find that selecting Resume sometimes gets me to a working desktop.

Or, select Root - Drop to root shell prompt. That will get you to a command-line but the file system will be read-only, which is no good. My method is to first select Resume because that makes the File System Read and Write, then back out of Resume and go to Root - Drop to a root shell prompt. Then you will be able to run updates and upgrades, etc.

By the way. 12.10 now has Grub 2.0 and not Grub 1.99 as does 12.04. What does the Grub menu look like? Is it so different to the 12.04 Grub menu? 

By installing Grub 12.10 you have become a tester of the 12.04 + Grub 1.99 upgrade to 12.10 + Grub 2.0 and I would like to know what your experience is like.

Regards

---

### Post by mmasroorali on 2012-10-02
> **grahammechanical said:**
> Do you get the Grub menu? You can do a couple of things.

a) At the Grub menu select the kernel that you wish to boot and press the letter 'e' That will let you edit the Grub script for loading that kernel. Look for a line that has "ro quiet splash" towards the end of the line and replace "quite splash" with "nomodeset." (without the quotation marks)

That should get you to a login screen and from there to a desktop. You may need to install video drivers.


I did the above and the machine booted fine. But just like my original problematic state in the first post, the login screen appears and then the keyboard and mouse get locked.



> **grahammechanical said:**
> 
b) At the grub menu select Recovery mode. I find that selecting Resume sometimes gets me to a working desktop.

Or, select Root - Drop to root shell prompt. That will get you to a command-line but the file system will be read-only, which is no good. My method is to first select Resume because that makes the File System Read and Write, then back out of Resume and go to Root - Drop to a root shell prompt. Then you will be able to run updates and upgrades, etc.


I want to try other modes like text in grub. But grub does not appear any more. It takes me directly to login screen and locks. 

So, the current problem boils down to, how to edit the grub options after the changes made above.

> **grahammechanical said:**
> 
By the way. 12.10 now has Grub 2.0 and not Grub 1.99 as does 12.04. What does the Grub menu look like? Is it so different to the 12.04 Grub menu? 

By installing Grub 12.10 you have become a tester of the 12.04 + Grub 1.99 upgrade to 12.10 + Grub 2.0 and I would like to know what your experience is like.

Regards

It is too early to comment. Perhaps I can make my comments after I have solved my problems.

Actually, I make it a point to start using every beta version of Ubuntu just to keep my moderate and limited expertise in practice. Life has become pretty smooth (dull?) after switching to Ubuntu. For me it was, 1991-97: Sun Sparc, 1997-2005: Fedora, 2005-today: Ubuntu. So, I have gradually moved to less challenging domains.

Regards.

---

### Post by dino99 on 2012-10-02
Quickly said:

- grub2.0 (12.10) is a huge rewrite and acts very differently than 1.99 (12.04). By the fact, its installation also use different pathes.

- Thats means : they both conflict.

So you should purge actual installed grub, then logout/in, and install only grub2.0 from 12.10 . 

That is the hard way i've learnt on a multi hdds and distros pc. Now i only have grub2.0 installed on all the hdd, the menu is clean and booting is as expected.

---

### Post by mmasroorali on 2012-10-02
> **dino99 said:**
> Quickly said:

- grub2.0 (12.10) is a huge rewrite and acts very differently than 1.99 (12.04). By the fact, its installation also use different pathes.

- Thats means : they both conflict.

So you should purge actual installed grub, then logout/in, and install only grub2.0 from 12.10 . 

That is the hard way i've learnt on a multi hdds and distros pc. Now i only have grub2.0 installed on all the hdd, the menu is clean and booting is as expected.

I could update if I could login. I can not, the machine locks.

I have tried both text and graphical mode for login. I made grub to appear by holding the shift key, and tried both the splash and text options. Every time the machine locks after boot. 

Am I running out of options?

---

### Post by ventrical on 2012-10-03
> **mmasroorali said:**
> I could update if I could login. I can not, the machine locks.

I have tried both text and graphical mode for login. I made grub to appear by holding the shift key, and tried both the splash and text options. Every time the machine locks after boot. 

Am I running out of options?


You can try to download the beta 2 .iso and then try to install it in =nomodeset.

 And I think also , while it is booting, you can hit <ctrl + t> repeatedly and that may bring you to terminal.

---

