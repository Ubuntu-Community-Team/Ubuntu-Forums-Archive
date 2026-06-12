---
title: "Host Screen saver Locks-up"
date: 2017-08-30
forum: Virtualisation
---

### Post by diyhouse on 2017-08-30
I am running basic Ubuntu 16.04 install ( plus latest VirtualBox with guest editions installed) as a host OS for several other guests,. including other ubuntus, (mint, Xbuntu) and another Windows 10 guest.
The host and guest can run fine for several days,.. without issue. Then without warning, I can wake the m/c up with a mouse wiggle.. to get the following screensaver login.

Basically my name ( which I have blanked out ),.. and an empty prompt box.. and as far as I can discover no way to enter a passwd,.. esc, ctrl-c do nothing,.. or just entering the passwd all do nothing.
I can switch to a tty input,.. login in without issue,.. I have tried restarting the screen service,.. but this of course ( as i discovered ) kills the guests,.. 

Can I kill the screen saver process...?
Or does anyone have ideas on how I can resolve/ or fix this problem.
many thanks

---

### Post by sp40140 on 2017-08-30
What are your hardware specs?
Do you have guest OS running at the same time?
Have you tired disabling the screen saver?
Have you checked the logs (/var/log)?

---

### Post by diyhouse on 2017-08-30
Intel nuc i7,.. with 16gig RAM...
Guest OS's I have running, would be Win10 Pro,.. mythbuntu, and maybe a win10Home... and maybe a mint
Although guests running does not seem to be a factor... but I don't know for sure

all essentially running in RAM,.. swap not used...

I will check log file next time it fails,...  current up time is nearly 2days..
Not tried disabling screen saver,.. as that sort defeats the object.. doesn't it?

Tx

---

### Post by sp40140 on 2017-08-31
I meant to say vm guests running at the same time.
Also, have you tried to not run any vm and see if the issue exists?
Which software you use for VM? (VMWare, VBox, KVM)?
As to the screen saving.. 
It's logical to assume that you don't access all theses os from the same single screen. Therefore, little need for monitor. Also, as I typically turn off my monitor at home. Just a different way of doing things.
Keep an eye on resources as well. Specially any spikes.

---

### Post by diyhouse on 2017-09-02
Ahh,.. yes,... I am using VBox,...
trying to run system with running guest m/c or VBox is not really practical,... as it is, m/c has been running for 4.5 days so far,.. and has not died,... so hence only happens very infrequently,.. the biggest pain is it takes out the guest m/cs without gracefully saving and closing....

I run two screens currently,... and as you say,.. they do time out,.. and I do certainly switch the one off most nights,..

For now I will wait for the next event,.. and see if the syslog shows anything...

---

### Post by diyhouse on 2017-09-04
well after just over 5 days,.. it failed,..
I checked the logs in /var/logs.. and a trawled all recent log files,.. and nothing,.. the only thing in syslog was the tty login I had just done.
Any other log have no recent updates of any activity,.. 

So back to the drawing board,... Thoughts at the moment go as follows,.. not sure but cpu usage 'seems' to go up,.. ( but might be me dreamimg ),.. and failure seems to occur after 5'ish days of running...

Is their a process to kill for the screen saver,.. or is that just part of the window manager...

Maybe I could use 'Another' screen saver... humm lets go for another week and see..

---

### Post by diyhouse on 2017-09-06
Failed again,.. this time it only took 3 days,.
Have now removed passwds from the screenlock to see if that does anything... and cpu usage did not seem to go up,.. ( well at least for now)
Hummm

---

