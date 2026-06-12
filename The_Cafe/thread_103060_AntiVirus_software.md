---
title: "AntiVirus software"
date: 2005-12-13
forum: The Cafe
---

### Post by WebDrake on 2005-12-13
Hello all,

As anyone who has followed my posts will know (most of them being pleas for help...) I've only recently switched to using Linux as an OS on my main computer.

On Windows I make use of NOD32 antivirus software, which of all the available alternatives seems to be a really quite exceptional choice.  I've set up ClamAV and Firestarter with Ubuntu, but I was wondering whether in the case of the former it might be worth using NOD32 (for Linux file server) instead.

I wonder if anyone has any experience of both products under Linux and could advise?

Many thanks,

         -- Joe

---

### Post by linbetwin on 2005-12-13
Do you use your Ubuntu computer as a server?

---

### Post by earobinson on 2005-12-13
unless the computer is a server you will not need an AV

---

### Post by WebDrake on 2005-12-13
[QUOTE=earobinson]unless the computer is a server you will not need an AV[/QUOTE]
I don't really buy that, although I'm happy to listen to arguments.

There are two reasons I want AV protection under Linux.  One is that my machine is dual boot with XP, which I need to use occasionally, and I want to be sure the shared parts are virus-free.  (The shared parts include email!)

The second is that Linux' present status of being a virus-free zone is not going to last if we have any success in making our OS mainstream.  I'm not going to take chances. ;-)

---

### Post by earobinson on 2005-12-13
Read this [http://www.ubuntuforums.org/showthread.php?t=102582&highlight=av](http://www.ubuntuforums.org/showthread.php?t=102582&highlight=av)

As for the shared part linux will not infect it nor get infected by windows viruses, So as long as windows dose its part to keep it clean you will be fine.

> The second is that Linux' present status of being a virus-free zone is not going to last if we have any success in making our OS mainstream. I'm not going to take chances.
This is a very good point. I do not know of any linux AV's that search for linux viruses I only know of linux AV's that search for windows viruses for servers. There are however linux firewalls (see link above)

Security in linux IMO is very diferent to that of windows. Also updates come a lot faster.

If linux is ever mainstream maybe we will ned AV's I hope however that linux just continues to fix security bugs instead so that a viruse can not hurt your computer instead of removing them (thats all a AV really dose)

NOTE: feal free to start/find a debate on linux AV's in the community chat howver the teck support pages are not the place for this.

EDIT: If a mod wants to copy these pages and start the debat that would be great

---

### Post by linbetwin on 2005-12-13
I happen to know a certain user who would be very active in a thread like this one.

---

### Post by Donnut on 2005-12-13
The very base of linux, logging in as a user instead of admin prevents this.  I sure there are hackers who can get around it, but what's the point?  People who use Linux are willing to learn about computers in general anyway.

---

### Post by Chayak on 2005-12-13
*click click click spark and raises a lit torch* just kidding

Well I don't really have AV on my workstation to protect it but I do send quite a few files around to friends who have not yet converted.  I just consider it a courtesy to them.

---

### Post by WebDrake on 2005-12-14
[QUOTE=Donnut]The very base of linux, logging in as a user instead of admin prevents this.[/QUOTE]
Again, I don't buy this.  Early viruses were written for Unix, which has the same security model.  You don't need to get root access to still do some nasty stuff.

---

### Post by earobinson on 2005-12-14
[QUOTE=WebDrake]Again, I don't buy this.  Early viruses were written for Unix, which has the same security model.  You don't need to get root access to still do some nasty stuff.[/QUOTE]
WebDrake, what can you do without root access, you could deleat all that users files yes but that will not break the computer and some how that program still needs to be run.

Also Im pretty sure the viruses you are refereing to where back before people even used passwords and security had not been thought of. Security is a big part of programing now.

I would let anyone run rapent with a guest account on my ubuntu box (guest account would not have read or write access to my files and so all they could do is make there own files maybe fill up my hardrive) And unless you can come up with something to back it up you cant make this claim ". You don't need to get root access to still do some nasty stuff."

Could some one find a loophole with linux and write a viruse? YES! Could some one find a loophole with windows and write a viruse? YES! but the fast development of cycle of linux will patch the whole to this virus faster than windows. Its also important to point out that a lot more people have looked at the code to linux and checked it than windows, peer review Is one of the best ways to make sure you have good product.

Hope this answers your question, feal free to call me a fool and come up with a counter example.

---

### Post by LinuxSwede on 2005-12-14
[QUOTE=earobinson]WebDrake, what can you do without root access, you could deleat all that users files yes but that will not break the computer and some how that program still needs to be run.

Also Im pretty sure the viruses you are refereing to where back before people even used passwords and security had not been thought of. Security is a big part of programing now.

I would let anyone run rapent with a guest account on my ubuntu box (guest account would not have read or write access to my files and so all they could do is make there own files maybe fill up my hardrive) And unless you can come up with something to back it up you cant make this claim ". You don't need to get root access to still do some nasty stuff."

Could some one find a loophole with linux and write a viruse? YES! Could some one find a loophole with windows and write a viruse? YES! but the fast development of cycle of linux will patch the whole to this virus faster than windows. Its also important to point out that a lot more people have looked at the code to linux and checked it than windows, peer review Is one of the best ways to make sure you have good product.

Hope this answers your question, feal free to call me a fool and come up with a counter example.[/QUOTE]

I'll call you a fool for it, most people love to access their own data so they have permissions for it, simple early virus... poof, all gone.

there is a reason why ClamAV exists and is widely used.

IOW, don't run unneccessary services or servers, use ClamAV and keep an eye on the log files and you'll be fine.

---

### Post by earobinson on 2005-12-14
> Clam AntiVirus is a GPL anti-virus toolkit for UNIX. The main purpose of this software is the integration with mail servers (attachment scanning). The package provides a flexible and scalable multi-threaded daemon, a command line scanner, and a tool for automatic updating via Internet. The programs are based on a shared library distributed with the Clam AntiVirus package, which you can use with your own software. Most importantly, the virus database is kept up to date .
[http://www.clamav.net/abstract.html#pagestart](http://www.clamav.net/abstract.html#pagestart)

Have you ever found a viruse with clamAV that was a linux virus? Im not even sure if this program finds linux viruses it may just find windows viruses in  your mail server.

Maybe AV's will become important but as it is now I have never had the need for one, nor should any normal user.

EDIT: More info on the topic [http://www.ubuntuforums.org/showthread.php?t=98912](http://www.ubuntuforums.org/showthread.php?t=98912)

---

### Post by earobinson on 2005-12-14
double post :(

---

