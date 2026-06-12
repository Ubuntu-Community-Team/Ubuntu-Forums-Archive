---
title: "Why enable the root account?"
date: 2006-01-13
forum: The Cafe
---

### Post by ardchoille on 2006-01-13
I see a lot of posts telling people to enable the root account. There is absolutely no reason to enable the root account. You should never log into the root desktop. You can perform any admin task from the user desktop using sudo or su. 

Can someone name one admin task which cannot be performed using sudo or su? Why do people keep telling others to enable the root account? I don't get it.

---

### Post by aysiu on 2006-01-13
I agree that people are too hasty to entertain those asking to log in as root.

On the other hand, having a root account exist is handy in case something happens to your sudo user account so that you can't log into it (and I don't mean an X login, just a login in general).

For me, it's not so much a security concern as a convenience issue--I'd rather ```
gksudo nautilus
``` than log out, log in as root, make changes, log out of root, and log back in again as user. It's faster and less trouble.

---

### Post by amohanty on 2006-01-13
I agree that having root is a great covinience. However i have disabled root xdm login, so that I only use a terminal to su and do whatever I want _and_ am automatically logged out when I am done.

AM

---

### Post by DaMasta on 2006-01-13
I was under the impression that the root user exists, just with no password. I guess I'm mistaken? :confused:

---

### Post by ardchoille on 2006-01-13
The root account exists, but it is disabled by default. There is no way to log into the root account and that is the way it should be. Which means that if a cracker got into your user account, they can't crack into or brute force the root account because it's disabled - thus, they can't do any damage to the system. The last time I actually logged into the root account was back in 2000, I believe, when I didn't realise how dangerous it was. I have used sudo or su ever since then and I can do anything from the user account that needs to be done.

---

### Post by Thirsteh on 2006-01-13
If need be you can always do 'sudo bash' which is pretty much equivalent to 'su -'.. But no, I don't see why anyone would want to enable the root user. You have to make a minor workaround to make webmin work on an Ubuntu computer because it logs in as root by default, and, there is a workaround so.. That's the only thing I can think of.

---

### Post by Zwack on 2006-01-13
Sudo doesn't set the environment properly... as a result I have come across some programs that will not work under sudo...

In fact if you try to run them as anything other than real root then your shell goes away...

So there are sometimes valid reasons for running as root...

Most of the time sudo -s works just fine 

Z.

---

### Post by cotcot on 2006-01-13
I guess that some want to have a graphical interface as root because they are used to that in MS windows as administrator. If you are new with sudo it might be hard to understand the concept without having read about it, so then falling back to what you know is quite normal. In my first linux setups I had the same reflex but as a became more confortable with the command line in terminal I do not feel the need anymore. I now have no root account.

---

### Post by ardchoille on 2006-01-13
[QUOTE=cotcot]I guess that some want to have a graphical interface as root because they are used to that in MS windows as administrator. If you are new with sudo it might be hard to understand the concept without having read about it, so then falling back to what you know is quite normal. In my first linux setups I had the same reflex but as a became more confortable with the command line in terminal I do not feel the need anymore. I now have no root account.[/QUOTE]
That is a very good point. So, maybe we should be encouraging newbies to learn how to use the command line rather than telling them to enable the root account.

I'm sorry, it just makes my blood boil every time I see someone saying "just enable the root account".

---

### Post by aysiu on 2006-01-13
[QUOTE=ardchoille]That is a very good point. So, maybe we should be encouraging newbies to learn how to use the command line rather than telling them to enable the root account.

I'm sorry, it just makes my blood boil every time I see someone saying "just enable the root account".[/QUOTE] I just tell them to ```
gksudo nautilus
``` if they need point-and-click and to otherwise use the command-line... or to read the third link of my signature.

---

### Post by kenweill on 2006-01-13
[QUOTE=ardchoille]The root account exists, but it is disabled by default. There is no way to log into the root account and that is the way it should be. Which means that if a cracker got into your user account, they can't crack into or brute force the root account because it's disabled - thus, they can't do any damage to the system. The last time I actually logged into the root account was back in 2000, I believe, when I didn't realise how dangerous it was. I have used sudo or su ever since then and I can do anything from the user account that needs to be done.[/QUOTE]

Well, if they can crack in your user account, then I guess they can do the same damage as well running "sudo".

---

### Post by aysiu on 2006-01-13
[QUOTE=kenweill]Well, if they can crack in your user account, then I guess they can do the same damage as well running "sudo".[/QUOTE] Except it's a lot easier to guess the root account's username (which is... *root*) than it is to guess the user account's username (which could be anything, really).

---

### Post by asimon on 2006-01-13
KDE needed some patching before it worked with su. I suppose there is still software in universe which is not yet patched to work without an enabled root account. Webmin does fall in this category, does it?

---

### Post by Iandefor on 2006-01-13
[quote=aysiu]I agree that people are too hasty to entertain those asking to log in as root.

On the other hand, having a root account exist is handy in case something happens to your sudo user account so that you can't log into it (and I don't mean an X login, just a login in general).[/quote] Exactly. A while ago, I did a little editing to /etc/sudoers and messed it up (turns out I accidentally deleted a hashmark) and sudo died. My only recourse had been to use the root account. But I agree with ardchoille, enabling root is a security risk.

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-01-13
[QUOTE=Iandefor]Exactly. A while ago, I did a little editing to /etc/sudoers and messed it up (turns out I accidentally deleted a hashmark) and sudo died. [/QUOTE]

That's why you should always use visudo to edit the sudoers file. It checks if the file is messed up before saving.

---

### Post by AlexandreP on 2006-01-13
[QUOTE=aysiu]On the other hand, having a root account exist is handy in case something happens to your sudo user account so that you can't log into it (and I don't mean an X login, just a login in general).[/QUOTE]
What about just rebooting Ubuntu in recovery mode?  It logs you as root.  I don't know why root should be enabled, then...

---

### Post by nocturn on 2006-01-13
[QUOTE=AlexandreP]What about just rebooting Ubuntu in recovery mode?  It logs you as root.  I don't know why root should be enabled, then...[/QUOTE]

While you are at it, it is a good security measure to secure grub (set a password, lock recovery mode, etc).

---

### Post by asimon on 2006-01-13
[QUOTE=aysiu]Except it's a lot easier to guess the root account's username (which is... *root*) than it is to guess the user account's username (which could be anything, really).[/QUOTE]
Yes, many attacks fail because the attacker doesn´t know the name of a user account.

---

### Post by ardchoille on 2006-01-13
[QUOTE=kenweill]Well, if they can crack in your user account, then I guess they can do the same damage as well running "sudo".[/QUOTE]
And how do they get the sudo password?

---

### Post by drizek on 2006-01-13
IIRC, a while ago it was not possible to use "kdesu" in kde to run programs as root unless the root account was enabled. i think that has been fixed now to work with sudo.

---

### Post by Iandefor on 2006-01-14
[quote=SuperDiscoMachine V.5.7-3]That's why you should always use visudo to edit the sudoers file. It checks if the file is messed up before saving.[/quote] Yeah... vi on it's own doesn't have error-checking, as I found out the hard way.

---

### Post by briancurtin on 2006-01-14
[QUOTE=ardchoille]And how do they get the sudo password?[/QUOTE]
if they cracked your account, they have your sudo password. they are one in the same.

---

### Post by ssam on 2006-01-14
[QUOTE=briancurtin]if they cracked your account, they have your sudo password. they are one in the same.[/QUOTE]

thats if they crack your account by guessing user/passwords and loggin in. this can only happen if you have sshd running, accessable to where every the cracker is, and with passwords allowed.

i think the biggest security worry in the linux desktop is probably firefox. its a big complex bit of code and deals with untrusted data. if someone finds a buffer overflow that allows artbitary code execution, and gets an expoit out then they can effectively run any code/command as the user you run firefox as. they will have no trouble working out your user name, but wont know your password.

in this case it makes little difference where you use root or sudo. what would make you a bit safer would be if you did not browse the internet from your admin account (but we all do anyway)

---

