---
title: "So I'm either hacked or paranoid...."
date: 2013-03-14
forum: Security
---

### Post by AsianSquirrel on 2013-03-14
[HR][/HR]To make a lo(n)g story...well, long:   [awful joke]

Today, the logs in the /var/log/cups directory were basically taking up more than half of the 100GB I use for Ubuntu  (I dual boot with Windows) and the first thing I did was try to delete  the .gz archive files (made sense to me!) but of course I didn't have  access privileges. So, being a newbie and not knowing exactly what to do but reluctant to Google anything, I tried adding myself to the "adm" group that the Nautilus (yes, I use Nautilus!) said it belonged to. Even after doing that I couldn't do anything. I tried using the wubi-resize script thingy but of course, there wasn't even enough space to create a .temp or whatever for it to resize. So I decided to attempt a reboot and lo and behold, it decided to try to boot in failsafe graphics mode (what is that good for, anyway?!) and then froze (or is that just a Windows term?). Frantically Googling on my tablet, I found this post on some forum by a guy who had the cups log file (what exactly is cups supposed to be for?) problem too. The thing that scared me to death and back was the fact that he said he'd been...hacked?! That really got me Googling. Then I rebooted (shut the thing down by holding down the power button on my computer --last-ditch method, but it works) in recovery mode, was still confused and added myself to the adm and root groups (and added root to the root group, just for the sake of it) via the root terminal thingy, and then rebooted *again*....and opened the normal (what is it, Gnome Terminal or something?) terminal with CTRL-ALT-T (in Linuxspeak, CTRL-META-T?) and my ultra-cool translucent orange Squirrel terminal profile had been deleted and apparently replaced with some kind of unnamed profile that looked a whole lot like the default. I'm not really that worried about the fact that I'll have to redo the trivial color config, just the fact that it happened. I probably sound really amateur, but I am definitely an amateur so I guess that's okay?          Thanks!

---

### Post by Moose on 2013-03-14
1. Oh my god that joke actually made me laugh incredibly hard for some reason.

2. Are you sure it just isn't Wubi reserving space?

---

### Post by prodigy_ on 2013-03-14
> **AsianSquirrel said:**
> I tried adding myself to the "adm" group
This is unnecessary. You should use sudo command for administrative tasks instead:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In your case (from Terminal): ```
sudo find /var/log/cups -type f -exec rm '{}'  \;
``` or ```
gksudo nautilus
``` if your really prefer the GUI way.

> **AsianSquirrel said:**
> hacked?!
Change your password and use [rkhunter](https://help.ubuntu.com/community/RKhunter) to check if there's any real evidence to support your fears.

---

### Post by Stonecold1995 on 2013-03-16
> **prodigy_ said:**
> Change your password and use [rkhunter]("https://help.ubuntu.com/community/RKhunter") to check if there's any real evidence to support your fears.

If an attacker has got root privilages, changing your password won't do much, because it's very easy to do things to circumvent that (backdoors, etc).  Also, rkhunter is notoriously bad at ignoring false positivies, it flips out at even the smallest things (e.g. a hidden file somewhere aside from /home).  If you HAVE been hacked, reinstalling is the only thing you can do.  Of course, I highly doubt you've been hacked anyways.  Linux is very secure, and it's not like you're running a web server.

---

### Post by claracc on 2013-03-16
Cups is the unix printer system used by ubuntu, if logs take more than 50 GB, obviously there is a problem with printer system . [https://help.ubuntu.com/11.10/serverguide/cups.html](https://help.ubuntu.com/11.10/serverguide/cups.html)

As it has been said previously you are in adm group, so it is unneccesary to add you to this group. You are not allowed to delete the file logs in cups because you haven't used sudo to remove the files: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

At last, I don't know if you have installed ubuntu (which one?) inside windows trough wubi or you have a dual boot windows/ubuntu. It would be good to clarify in order to solve the problem

As a newbie, I recommend you to learn about ubuntu [https://help.ubuntu.com/](https://help.ubuntu.com/) prior to run commands which can damage your system. Also, I provide a link in order to investigate why your cups logs are so big: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670).

---

### Post by unspawn on 2013-03-16
> If an attacker has got root privilages, changing your password won't do much, because it's very easy to do things to circumvent that (backdoors, etc).  
If an attacker gains root privileges changing *anything* is a bad reflex, think "disturbing the crime scene". Common errors new and seasoned users alike make are installing software and deleting "evidence". Most of that can be attributed to a lack of awareness, knowledge and preparation.


> Also, rkhunter is notoriously bad at ignoring false positivies,   
That's one way to view it and it holds true especially for the ninety nine point ninety nine per cent of uninformed users who just install that SW based on the advice of others w/o realizing 0) the order of things (post-OS installation securing and hardening first, etc, etc), 1) what they run (passive post-incident vs active "early warning" tools like fail2ban, Samhain, etc, etc), 2) let alone read the documentation to know what tests actually do and become aware of configuration modifications of white listing.


> If you HAVE been hacked, reinstalling is the only thing you can do.  
If a machine is compromised then the incident should be investigated for various reasons: in the worst case nothing happened and then re-installing becomes a waste of time. Or something did happen and then re-installing may just expose the same loophole again. Or posted information may cause different views in which case analysis is helped by many eyeballs (or so one would hope). The problems here are that members don't care, don't realize the effect of their "advice" or don't know basic incident handling procedure and therefore lack the practical experience to interpret signs in the first place. Then it sadly becomes a thoughtless reflex to just to advise the victim to re-install. 


> Of course, I highly doubt you've been hacked anyways. Linux is very secure, and it's not like you're running a web server.
If something can't be analyzed due to lack of information then the OP should be asked to provide it. Supposition, speculation, assuming are all nice entertainment-wise but *facts trump fiction.* 

*Do note removal of the quoted users handle signals these must be taken as general comments.

---

