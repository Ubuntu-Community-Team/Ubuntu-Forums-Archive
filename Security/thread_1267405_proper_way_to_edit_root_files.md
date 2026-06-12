---
title: "proper way to edit root files"
date: 2009-09-15
forum: Security
---

### Post by marcvs on 2009-09-15
Hi All,

I have Kubuntu sharing a machine with Vista. I mostly work on Vista, so I am not completely familiar with how certain things work on Kubuntu. A major annoyance for me is denied permissions to edit files owned by root. For example, I need to quickly change a couple of lines in httpd.conf to test something. I make a copy of the file and open the original in Kate, only to find at the end that I am unable to save. So I launch Kate again, this time from the command line using sudo. This is annoying to say the least. I find myself needing to edit this type of files quite often, so I end up having to go through the cmd line launch procedure everytime (I think you also have to keep the console window used to launch the process open until you're done). 

I realise this is a security feature, but what how am I expected to login if I plan to make a lot of changes to files owned by root? Logging in as root is also discouraged. I had managed to make changes to allow this (login as user 'root'), but these have been reverted during my last update which including upgrading Kubuntu (to v9 I believe), so it looks like something I shouldn't do.

Is it possible to create a user with root privileges (like a user who is part of the Administrators group under Windows)? I am not highly concerned with security - this is my home machine. It is behind a router with most ports blocked and I am willing to risk having a root user I can logon with. 

Speaking of security, what are the main reasons for discouraging root login? The way I see it:

 * limit damage from malicious software by restricting access to files (it will still have access to my data anyway, which is all I care about).

 * limit damage from user/bot who gets access/takes over your system remotely. as above, my data is still unsecured. and secondly, isn't a router enough protection against this (except browser exploits, of course)?

I find some features to be detrimental to the usability of the system since no one can live in the home folder alone. This reminds me of the UAC feature introduced by Vista. It was the first thing I disabled and I was already prepared to  go back to XP if disabling it was not possible. 

*In short* what I would like to setup here is a normal user when I plan to work only with my data, and a root user with which I can logon to Kubuntu (root is there but using it to logon is not allowed, right?). I was able to do this on other systems with KDE (FreeBSD if my memory serves me right).

(apologies for wall-of-text:))

cheers

---

### Post by aesis05401 on 2009-09-15
Heya,

You should remember to use the kdesu and gksu for launching gui apps as root on kde and gnome respectively.  If you use plain old sudo it will work usually, but can have subtle problems (or not so subtle problems in the case of firefox).

Secondly, I don't know much about the Linux gui systems, but I just tested the root launcher concept on gnome... create a launcher, add 'gksu <text-editor-name>' to the 'command' field of the launcher properties, drop any text files you want to edit as root onto the new desktop launcher icon... and enter your password.

Would this be more convenient than what you were going through?  Have you tried using nano from CLI?  That is my preferred method.

---

### Post by lloyd_b on 2009-09-15
The simplest solution is to set up a new menu entry (let's call it "root edit"), with the command being "kdesu -c kate", which would invoke "kate" with full root access.  

You can, if you choose, enable the root account, so you can log into it and work from there.  Forum rules explicitly forbid anyone here telling you how to do it, but a quick Google search will provide you with the info.

I believe the main reason for disabling the root account was to limit the amount of damage a beginner could do, since *nix beginners have the habit of doing everything as root.  A second reason is that it means you don't have to remember the root password for every machine (if it's something you use every day, that's no problem, but if you only need root access every once in a while it's easy to forget the root password to a machine, especially if you regularly deal with multiple machines).

I've also seen a joking comment that it was disabled because that's one less question to ask during the install process. :)

Lloyd B.

---

### Post by Agent ME on 2009-09-15
> **aesis05401 said:**
> You should remember to use the kdesu and gksu for launching gui apps as root on kde and gnome respectively.  If you use plain old sudo it will work usually, but can have subtle problems (or not so subtle problems in the case of firefox).
If you're on a terminal, it doesn't make a difference between using sudo or gksudo. The only difference between them is that sudo asks for your password on the terminal, and gksudo asks for your password in a dialog box. (Gksudo would be needed if you make a shortcut, because no terminal would be open for that.)

---

### Post by aesis05401 on 2009-09-15
> **Agent ME said:**
> If you're on a terminal, it doesn't make a difference between using sudo or gksudo. The only difference between them is that sudo asks for your password on the terminal, and gksudo asks for your password in a dialog box. (Gksudo would be needed if you make a shortcut, because no terminal would be open for that.)

So root permissions no longer overwrite your user permissions in certain cases?  FF add-ons load according to the proper profile?  Do you have a link?

Edit: Just to clarify, my understanding was that these issues were never going to be patched, because the desktop managers were each implementing dedicated sudo front-ends.  So long as you don't use sudo for graphical applications you won't hit the corner cases, but they were definitely out there as of last time I checked.

---

### Post by cariboo on 2009-09-16
Just a note, there really isn't a need to enable the root account, I haven't found anything that I couldn't do using sudo -i

---

### Post by aysiu on 2009-09-16
> **Agent ME said:**
> If you're on a terminal, it doesn't make a difference between using sudo or gksudo. The only difference between them is that sudo asks for your password on the terminal, and gksudo asks for your password in a dialog box. (Gksudo would be needed if you make a shortcut, because no terminal would be open for that.) No, it actually makes a difference:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by The Cog on 2009-09-16
Please don't log in as root. It invites doing it by habit, which increases the risk of horrible mistake or OS compromise by a trojan. And it really isn't necessary.

For command-line root work, just use **sudo -i** in a normal command prompt first. For graphical root work, **gksu nautilus** gives you a root file manager. No need for repeated password entry.

It reminds me of the time that wearing seatbelts was made compulsory here in the UK. It felt awkward at first, but I have to say that now, I feel very unsafe when not wearing one. And it **has** saved lives, although on the down side it has led to a worsening organ donor shortage. The idea of being able to edit system files any time feels just as unsafe - shudder.

And normal users are well capable of working entirely within their own home directory. Only the administrator needs to edit files outside, and only when he is working as administrator. Most of the time even a sysadmin will be using the machine in the rôle of a normal user. They are two distict rôles.

---

### Post by ApEkV2 on 2009-09-16
> **marcvs said:**
> 

....so I end up having to go through the cmd line launch procedure everytime....



What I do is sudo nautilus and while running nautilus as root I could dbl
click txt files and edit them with gedit (can change to kate if you want).

If I closed nautilus and needed it again, all I would do is type " ctrl + p enter " (shortcut for last command used), and would save having to type it again.
I think you would need to install nautilus on kubuntu though (don't remember if it comes installed).

---

### Post by aysiu on 2009-09-16
> **ApEkV2 said:**
> What I do is sudo nautilus and while running nautilus as root I could dbl
click txt files and edit them with gedit (can change to kate if you want). Should be ```
gksudo nautilus
``` ```
gksudo gedit
``` and ```
kdesu kate
``` Save *sudo* for terminal applications.

Graphical apps should use *gksudo* or *kdesu*

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by __p1n__ on 2009-09-16
I treat most of my o/s environments as disposable so I'm a little laissez-faire with them.  The exceptions are my banking image and general work image which are both persistant so I follow standard unix security practices when I run them up and log into them.

Yesterday I did a quick pentest on another forum member's server.  During that session I used a flash-boot ubuntu image that ran wholly in memory.  Stayed as root the entire time and when I finished and shut down the instance it was all flushed.

If your o/s instance is persistant at all then I support the general advice to not run root.  Not all o/s instances need be treated with such care though.

---

### Post by The Cog on 2009-09-17
Oops. Since you're on KDE, instead of **gksu nautilus**, you probably want to use **kdesu dolphin**. 

Same principle, different desktop.

---

### Post by marcvs on 2009-12-09
hi Lloyd

thanks everyone for your tips. 

i had forgotten about this thread...:redface:  i'm still reading through this but i get the impression these are "hack" methods. being root can have bad consequences but let the user deal with that i say. i still prefer the root login method (i'm being hard-headed, i know).

[COLOR="DarkRed"]OK, computer, i'm aware of the risks involved in being root but i repeat - 
I am the president! now let me fire those nukes!![/COLOR]

>>Forum rules explicitly forbid anyone here telling you how to do it
?! this is unbelievable:) are users causing that much damage to themselves?

>>A second reason is that it means you don't have to remember the root password for every machine
you will also learn really well your own password since you have to key it in every 5 minutes;)

>>main reason for disabling the root account was to limit the amount of damage a beginner could do
this makes me laugh and rage at the same time. the system protects you from yourself? imho the system should make it clear to the user that they are taking full control and that it gives you the power to cause total destruction. i think the Ubuntu team should realise many of it's users are responsible enough and shouldn't be treated this way - honestly this is the only nag I have with this wonderful distro.

---

### Post by cariboo on 2009-12-09
The forum rule is there for a reason, many new users don't realize the power root has, you can easily trash the whole system with a couple of commands. 

There is documentation available at the Ubuntu help wiki that explains the [Rootsudo]("https://help.ubuntu.com/community/RootSudo") policy.

---

### Post by aysiu on 2009-12-09
> **marcvs said:**
> i think the Ubuntu team should realise many of it's users are responsible enough and shouldn't be treated this way - honestly this is the only nag I have with this wonderful distro. The users who are responsible enough already know how to log in as root.

If you have to ask, you don't know enough yet to be doing it responsibly.

---

### Post by bodhi.zazen on 2009-12-10
> **marcvs said:**
> i think the Ubuntu team should realise many of it's users are responsible enough and shouldn't be treated this way - honestly this is the only nag I have with this wonderful distro.

You dredged up a 3 month old thread to insult the staff ???

May I take that as an offer for you to personally support all Ubuntu users who set a root password and then have a problem with their systems ? Are you willing to assist with data recovery and restoration of system files via chmod 777 /* ?

There are times when it is necessary to set a root password, and in those instances it is supported (I just did this in another thread in fact).

For the most part, it is completely unnecessary and causes problems which either the staff or other community members have to clean up, and can involve data loss, with is tragic.

So while you are free to use the root account as you see fit, please do not make others clean up after your mess when you instruct a new user to set a root password.

---

