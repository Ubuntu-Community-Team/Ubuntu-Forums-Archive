---
title: "Newb question about Kubuntu/security/sudo/root"
date: 2005-07-04
forum: Server Platforms
---

### Post by knewbix on 2005-07-04
Hi folks. Quite new to Linux and very new to Kubuntu. The first thing I noticed about Kubuntu (after the usual problems n00bs face) was that I couldn't type "su" and "password" and be root in a konsole window until I close it, like most other distros I've tried. I found the cure for this eventually, but I read up on it a little and it seems to be for security reasons so I don't do it, but I'm having problems getting my head around the whole idea.

Is the problem basically that people open a root konsole window and leave it open after they've done what they wanted to do as root, thus allowing someone who has hacked normal user access to your box to do root stuff? Hope this question makes sense. Obviously I don't know much about security but I'm trying to understand.

That's the only real reason I can think of for why I can't just 'login' to a konsole window and do all my root stuff without typing the password over and over for each sudo command. (Like I said, I did find out how to actually cure this, but I'm curious about the reasoning behind it.) Thanks guys.

---

### Post by Lord Illidan on 2005-07-04
It is better to use sudo and type a password before you do an action which can potentially harm your system. At least, when the system asks you for the password, you have a second or two in which you say "Wait a bit, what am I going to do?". If you stay using root, chances are greater that you harm your system without even knowing it...

Hope this helped!! I am a n00b too..

---

### Post by knewbix on 2005-07-04
Thanks Lord :) It just strikes me as strange that I have to enter my password every single time I want to do something as root. If I open a root konsole window, then I know it's there and I can do root stuff any ol' time. I wold not have opened a konsole and logged in as root on it if I didn't want to do root stuff, you know what I'm saying? It's all remeniscent of Window's "are you sure you want to do that" popups. *Yeah, I want to do that!*  :)

---

### Post by LordHunter317 on 2005-07-04
[QUOTE=knewbix]Is the problem basically that people open a root konsole window and leave it open after they've done what they wanted to do as root, thus allowing someone who has hacked normal user access to your box to do root stuff?[/quote]No, it isn't.  The core issue comes from the fact that having two accounts isn't inherently more secure than one, and having an account that's privileged all the time is bad.

With sudo, you're only privileged when you run a command with sudo.  Everything else is unprivleged.  That's the gain.  It saves you from the headache of having two accounts.

As for being more secure, it's not inherently more secure.  Most of the security gain is dependent on social setting and situation.

[quote=Lord Illidan]It is better to use sudo and type a password before you do an action which can potentially harm your system. At least, when the system asks you for the password, you have a second or two in which you say "Wait a bit, what am I going to do?".[/quote]This isn't worth writing home about, because if you're not generally cautious, sudo isn't going to make you more cautious.

And sudo doesn't prompt everytime anyway, and you can get a root shell from sudo, making this even less of a gain.

---

### Post by Lord Illidan on 2005-07-04
Thanks for the clarification, LordHunter!!

---

### Post by crashtest on 2005-07-04
[QUOTE=knewbix]Thanks Lord :) It just strikes me as strange that I have to enter my password every single time I want to do something as root. If I open a root konsole window, then I know it's there and I can do root stuff any ol' time. I wold not have opened a konsole and logged in as root on it if I didn't want to do root stuff, you know what I'm saying? It's all remeniscent of Window's "are you sure you want to do that" popups. *Yeah, I want to do that!*  :)[/QUOTE]

You don't have to enter your passwd at all if you'd rather not.  Edit the admin line in /etc/sudoers so that it reads: %admin  ALL=(ALL) NOPASSWD:ALL

The safe way to edit the sudoers file is to do 'sudo visudo' which will open an editor that checks for syntax errors in the sudoers file, preventing you from doing something crazy.

---

### Post by knewbix on 2005-07-05
Thanks for clearing this up for me, folks.

---

### Post by pes on 2005-07-05
You can always write "sudo su -" and you will become root for that console window. Do not think that opened root console is some security problem. And do not think that you are safe from hackers when disabling normal root access. This Ubuntu way (disabling root access) was selected only because other distributions users normally use root account for every day tasks after instalation. When they cannot log in as root in Ubuntu, it forces them to use normal account and use sudo for system administration tasks. There is no other security reason. Disabled root access only protects users from theirs bad habits, there is no other reason, no "improved security". If there weren't stupid users, using root access for their everyday Internet browsing, there will be no reason to disable root account  ;-) .

---

### Post by LordHunter317 on 2005-07-05
[QUOTE=pes]You can always write "sudo su -" and you will become root for that console window.[/quote]sudo -s is better.

>  Do not think that opened root console is some security problem.It can be, depending on physical security.

> This Ubuntu way (disabling root access) was selected only because other distributions users normally use root account for every day tasks after instalation. I doubt the other distributions had anything to do with it.

> Disabled root access only protects users from theirs bad habits, there is no other reason, no "improved security". If there weren't stupid users, using root access for their everyday Internet browsing, there will be no reason to disable root account  ;-) .None of this is true.  There are several security-related reasons for not having an interactive root account.

---

### Post by pes on 2005-07-05
[QUOTE=LordHunter317]sudo -s is better.[/QUOTE]
advantages/disadvantages? 
[QUOTE=LordHunter317]It can be, depending on physical security.[/QUOTE]
If you leave your computer physically, you should lock access or log our. Otherwise you are at risk, dosn't matter if you are logged as root or not.
[QUOTE=LordHunter317]There are several security-related reasons for not having an interactive root account.[/QUOTE]
Please tell me the reasons (yes, I read [https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo)). I replied to newbie question only to make sure he don't think that he is 100 % safe from hackers with disabled root access. I saw lots of Ubuntu beginners and they were always sure they are invulnerable, just because root account is 'not there'. I have to say again that if there were no newbies, there is no real reason to disable interactive root account. You don't become 100 % safe with it. 

And you can't say it's not true. It's my opinion, you have different opinion. It's not 'true'/'not true'.

---

### Post by LordHunter317 on 2005-07-05
[QUOTE=pes]If you leave your computer physically, you should lock access or log our. Otherwise you are at risk, dosn't matter if you are logged as root or not.[/quote]And such situations exist, and can make root consoles a security problem.

I'll admit to them not being common though, but I've worked in a few places where securing terminals was really difficult, if not impossible.

> Please tell me the reasons Having a root account requires two passwords, which can be a negative.  Root accounts run with privelege all the time,   meaning that all programs are a potential security risk.  To be fair, Ubuntu's sudo policy doesn't mitigate this point any, nor does it really need to, I think.  But in the enterprise, limiting what can be done interactively with privilege is a good thing.  It reduces your attack surface.

> I have to say again that if there were no newbies, there is no real reason to disable interactive root account. You don't become 100 % safe with it.That's just simply not the case.

> And you can't say it's not true. It's my opinion, you have different opinion. It's not 'true'/'not true'.Computers don't believe in nor operate under moral relativism, so I don't see why I should either.

This isn't a very subjective matter, really.  Some point of it are subjective, but the idea that, "if there weren't newbies, root interactive access could be left enabled and you'd still be as secure," just isn't true.  There's no basis in fact for that.  Proper sudo policy reduces your attack surface over a fully privileged account.

---

