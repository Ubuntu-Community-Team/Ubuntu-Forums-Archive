---
title: "Starting Firestarter at Login"
date: 2008-06-15
forum: Security
---

### Post by capatt on 2008-06-15
Hello
      I've got Firestarter to start when Ubuntu starts, but it always presents a request for admin password, which holds everything else up.  Is there a way to automate this so the process is transparent and no password is requested?
      Would it be better to use another firewall program?

Thanks!

---

### Post by Pjotr123 on 2008-06-15
Try ufw (I like that one best):
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

---

### Post by kevdog on 2008-06-15
Unless you need the Firestarter GUI at startup, why dont you export the IPtables ruleset currently, and then at boot time, restore the ruleset using the iptables-restore command within the rc.local file?  Since the rc.local file runs as root, I believe the ruleset should be loaded without any manual intervention.  If you then need to later change or modify the ruleset you could then reload the GUI, make your changes, but would then need to re-export the ruleset (iptables-save command).  Once you have a working firewall ruleset, usually these do not need to be altered frequently (at least for me!)

---

### Post by kevmitch on 2008-06-15
How did you get it to startup at boot? If you use the "BUM" runlevel editor to add it to runlevels 2-5, it should start automatically on boot. This is far preferred to staring on login, because it is conceivable that your computer will be on when no one is logged in when your computer is just as vulnerable to attack.

---

### Post by capatt on 2008-06-16
Thanks for all the replies.  I'm a n00b so the suggestion for exporting the iptables etc, is a bit over my head.

I got Firestarter to start at boot (or is it login?) by going to "Sessions" under Preferences and simply adding it.

I initially found Firestarter by consulting Ubuntu help and got directed here:

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter).  On the interface tab it recommends to "Tic off Enable tray icon and "Minimize to tray on window close", so that "Your firewall will be active when you boot regardless of if you choose to activate the tray icon or not."
What it doesn't say is that it doesn't become active until you physically enter your password and login.  Seems that should be unnecessary if you want the advertised protection to start immediately.

While writing this I just found a link which explains how to eliminate the password.  I'll give this a try:

[http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html](http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html)

---

### Post by hyper_ch on 2008-06-16
Why do you want to run firestarter anyway all the time?
Are you actually sure you need other default settings in iptables? Most often you probably don't need to configure your firewall.

---

### Post by capatt on 2008-06-16
The simple answer is that I'm a n00b with Ubuntu and (competently) familiar only with the Windows environment where you certainly need a firewall running all the time.  I've been test driving Ubuntu, love it, and am now using it full-time.  If there's an equally secure, lighter, simpler(!) alternative, then I'm all ears.

Thanks!

---

### Post by hyper_ch on 2008-06-16
Yes, on windows you need an active firewall becaue so many things get installed that you have no clue about that try to connect to the outside and transmit data... be this by the default windows installation or installation of 3rd party software or software from dubious sources.

However you don't have this mal/nagware infected software on linux so there's not really a point to operate a firewall per se... there might be good reasons to have one but you first should understand the system and the works of a firewall and not just blindly run it... running something blindly is even worse because you assume a false sense of security.

Typical example: It was adviced to have a password that's 6 characters long (many many years ago). The reason was that with a 6 character long password 20 years ago (or something like that) you couldn't brute-force a machine in a reasonable amount of time. However the dogma of the 6-character long password remained for a long time and computers ahve become way faster. No, nobody would say use a 6-character long password and you're save. Due to internet, networked computers, botnets, rainbow tables etc. it can be hacked quite quickly.

So the point is that security is a process and you have to question the dogmas once in a while. From windows you're used to run a firewall like zonealarm and AV all the time. Question is: why do you need it? And once you know, you can ask yourself does this need apply for other systems also? Are there other reasons to run it?

By a default ubuntu install you don't have anything listening at all. Adding a firewall won't make you secure. When you start installing server software, you might want to setup a firewall. However, if you are behind a router, you may rather want to setup a firewall there and not on your computer... and also the point of a server is to "serve" something to a client... so basically you're making holes again into the firewall (maybe for specific IP addresses only)...

It's all a question what do you do and what do you need. By default I'd say no firewall configuration is needed and most users with most common software and p2p don't need anything either.

---

### Post by capatt on 2008-06-16
Thanks for your time and advice.  Given this, I'll just uninstall Firestarter as I have no intention of running any listening services.

---

### Post by hyper_ch on 2008-06-16
you don't have to uninstall it... it's a question whether it's really needed or not... by running p2p you do run a listening service... as long as you know what you install and what it does you should be fine. More dangers arise if you don't know what you're doing.

---

