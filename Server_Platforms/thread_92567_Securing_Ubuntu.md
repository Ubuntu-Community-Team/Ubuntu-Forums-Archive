---
title: "Securing Ubuntu"
date: 2005-11-19
forum: Server Platforms
---

### Post by UbunuAndrew on 2005-11-19
Hello, 

The other day I gave SSH access to a co-worker (It's a close knit environment so there's nothing 'major' to worry about.) along with the root / user passwords of my system. Again it wasn't anything big as he was helping me out.

I want to make sure that I keep him from doing 'other' things to my system, as he already played a nice little crack on my earlier this evening. 

I've changed my root, and user passwords and have completely removed SSH. How else can I keep him from doing other such things if any? If the root pass was changed along with the 'user' pass - is there anything else that can he can do to get in if he doesn't know that pass?

---

### Post by kruz on 2005-11-19
open your

/etc/hosts.deny
or /etc/host.deny

cant remember if there is an 's or not
ne wayz find it
and put his IP in there

:)

that will slow him down until he changes his IP
or uses an ip spoofer

but u can also stop the rsync daemon?
or other remote desktop daemons or progs running

---

### Post by soulestream on 2005-11-19
if he's logging in via internet just change your IP address

soule

---

### Post by unixfudotnet on 2005-11-22
i'd start by not giving accounts to people that i do not trust.

hard to secure a machine when you give root access to everyone that asks for it.

---

### Post by ubuntu_demon on 2005-11-22
I moved this thread to our security section.

He can't do anything very easily anymore now that he can't login. Unless he has installed a rootkit or some other way of getting in.

You can remove his useraccount :

$ sudo deluser username

to make sure he hasn't tampered with the sudo settings you can check here :

$ sudo visudo

you can purge and reinstall ssh. To make sure he hasn't tampered with it :

$sudo apt-get remove ssh --purge
$sudo apt-get install ssh

You can install and run chkrootkit (does give false warnings sometimes so report the result here if you get any) :

$sudo apt-get install chkrootkit
$sudo chkrootkit

You can install firestarter for a bit more safety.
$sudo apt-get install firestarter

You can never be entirely sure unless you reinstall. 

Regarding the future : you can read in this forum section what kind of security tools are available for:
- detecting attacks 
- detecting altered filesystem

(I have played a bit with snort and aide for example)

---

### Post by HJThis on 2005-11-22
Hi,To all

Yes as was said i would get both rkhunter & chkrootkit

but i will add you don't need anyone on you PC
that likes to play games on you.

BOL ;)

---

