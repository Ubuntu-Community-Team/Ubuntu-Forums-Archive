---
title: "Locked myself out of sudo"
date: 2010-06-17
forum: Server Platforms
---

### Post by max-power2717 on 2010-06-17
Whoops, I'm really worried now.

I wanted to add myself to the group of a user that I created so that I could easily manipulate the files owned by that user without having to use sudo. 

I used the usermod command to do this (something like the following):

> sudo usermod -G anh max*

*regarding the command, it is possible that I absent-mindedly used -g insted of -G - I can't be sure of that. 

I am the admin of the system (username max) and sudo has always worked just fine for me. 

The changes hadn't taken effect after executing that command, but I confirmed that my name had been added to the anh group in the /etc/group file. Ended my shell session, and logged back in (through ssh) and found that I couldn't execute sudo commands any more. I get the message: "max is not in the sudoers file.  This incident will be reported."

Can anyone recommend the best way to re-establish myself as someone privilaged to use sudo on my system? Preferably without needing a complete reinstallation...

Thanks in advance.
Max.

---

### Post by wojox on 2010-06-17
Sure Max, try this [Fix Broken Sudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by max-power2717 on 2010-06-17
Thank you for such a quick and helpful reply.

This guide worked for me, the solution for case 1 in the guide worked.

I had to restart a few times to get into the grub boot menu because I have a single boot system, but in the end holding down shift while booting up brought up the boot menu and I could choose the recovery console boot option. 

Thanks once again Wojox.

---

### Post by wojox on 2010-06-17
Your Welcome :p

---

### Post by sisco311 on 2010-06-17
> **max-power2717 said:**
> 
> sudo usermod -G anh max


```
usermod -G group1[,group2...] user
```
adds the user to the list of groups and removes the user from any other group (expect the user's initial login group). You have to use the -a flag to add the user to the supplementary groups:
```
usermod -aG group1,[group2...] user
```

On a Debian based system you could use the adduser perl script to add a user to a supplementary group:
```
adduser user group
```

I prefer the gpasswd command which should work on most Linux systems:
```
gpasswd -a user group
```

Or if you understand the syntax of the /etc/group file, you can use:
```
vipw -g
```
to edit it manually.

---

### Post by max-power2717 on 2010-06-17
Thank you Sisco, you actually answered just what I was wondering about the -G command. Somehow, I didn't get that vital bit of information from the man pages before I issued the command. 

When the problem arose, I figured it'd be because of something like that. 

Thanks for the tips on different ways to achieve the same goal without wiping out my sudo privileges.

---

