---
title: "Can someone help me love ubuntu? (die sudo)"
date: 2008-05-26
forum: Security
---

### Post by fr0g12 on 2008-05-26
Look here is the deal, I have used Linux for fun (along side windows) for several years now and i thought i would give Ubuntu a try because it has such a following.  I like Ubuntu, i really do but this **sudo crap** is about to piss me off enough to load something else. In any other Linux distro i can use a root account (su + pw) in the terminal, with all the privileges i should be allowed to have as an adult. I don't like being treated like a child or a 93 year old woman on my own computer, if you know what i mean. If i break it ill reload it (big deal), but at this point i know enough not to break my own computer. And to be honest the lack of real/normal root functions is about to make me go back to my previous distro. Anytime i try and do anything i am used to, such as compile/configure/make/install etc a program or any other root function i have come to expect in Linux it declines me over root access. I don't care about how "dangerous" something is (as if lives are at stake), this is not a pentagon computer and I am not an idiot.  Will someone, please, help me set up my computer so it runs like a normal Linux box, so i don't abandon Ubuntu for good? From other posts i have a root account but it is effectively impotent and i still get messages saying i don't have root privileges...I want a root account that is capable of completely destroying the OS if i choose (or accidentally screw something up), its my computer right??? sooo yeah, can anyone help me love ubuntu?

---

### Post by ad_267 on 2008-05-26
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Using "sudo -i" gives you a root login.

---

### Post by twright on 2008-05-26
edit:
comment removed due to policy

sudo su or sudo -i work just as well

---

### Post by hyper_ch on 2008-05-26
Have a look at this:  [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by fr0g12 on 2008-05-26
Ok this is a good for instance.. I am trying to install this emulator and when i try and install i get 

[: 37: ==: unexpected operator
Must be logged on as root.

even tho i have done all of what you have suggested already..

I just don't understand how i can be either logged on as root or use any other commands i have heard mentioned but still i am not the root.

---

### Post by fr0g12 on 2008-05-26
Ok well if its too hot of a topic.. apparently lol.. someone can feel free to email me [email]fr0g12@hotmail.com[/email] or whatever.

---

### Post by ad_267 on 2008-05-26
If you've used sudo in front of the command or logged in as root using "sudo -i" then you shouldn't be getting that error. Another way of getting a root login is restarting and selecting recovery mode. I would guess that it might be a bug with the software you're trying to install.

---

### Post by twright on 2008-05-26
to enable su via terminal only (not via gdm) all you need to do is sudo passwd root and enter the desired passoword but i'm not sure that is the issue

---

### Post by fr0g12 on 2008-05-26
alright well thanks for trying to help, but its more than one app and i have had them on multiple distros before. Time to search the underground i suppose. And ill try the recovery mode next and if that fails ill just reload something else. Like i said Linux is a hobby and curiosity to me, its not terribly important that any particular distro works. I just wanted ubuntu to work.. Anyway thanks again

---

### Post by Jose Catre-Vandis on 2008-05-26
There is a way, but forum policy does not encourage running as root:

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by mbaker824 on 2008-05-26
> **fr0g12 said:**
> alright well thanks for trying to help, but its more than one app and i have had them on multiple distros before. Time to search the underground i suppose. And ill try the recovery mode next and if that fails ill just reload something else. Like i said Linux is a hobby and curiosity to me, its not terribly important that any particular distro works. I just wanted ubuntu to work.. Anyway thanks again

If you really want to use 'su' exactly like you would in, say, Fedora, it's easy enough to do - simply change the root password to a known value.  You can do that from a terminal:

> sudo passwd root

or using the Users and Groups applet under System->Administration.  In either case, once you know what the root password is, you can use the 'su' command just as you would in any other distro.

Ubuntu obviously believes in the 'sudo' concept, but there are those who believe it to be a bad idea.  In general, the argument goes that now you have two or more passwords (root and any sudoers) that have to be hard to guess, rather than just one.  There is some logic to this argument, but I'm not sure it really makes that much difference one way or the other.  Still, if all you're interested in is typing 2 characters for a root terminal rather than 7, just change the root password and you're there.  

If you're concerned about security, after changing the root password and making absolutely sure 'su' works, you can remove your regular user accounts from the admin group, and no more sudo!

Mark

---

