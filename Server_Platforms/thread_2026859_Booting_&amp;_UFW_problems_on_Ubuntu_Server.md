---
title: "Booting &amp; UFW problems on Ubuntu Server"
date: 2012-07-15
forum: Server Platforms
---

### Post by CocoMonGo on 2012-07-15
Hi all, this is my first post on ubuntuforums, so if I have posted this in the wrong place, apologies. I just (<6months) worth of ubuntu/linux knowledge so be gentle too.

Firstly my setup; I have a HP Proliant Microserver N40L connected through ethernet with Ubuntu Server 12.04 installed and a xubuntu desktop as GUI (via apt-get install xubuntu-desktop). The server is set to boot to CLI , where I have a choice of booting to xubuntu desktop later (startx). I am trying to run a headless server, and already have UFW/GUFW, SAMBA, Transmission, OpenSSH and XBMC installed (among others) and they run mostly without problems. 

Issue 1: With UFW set to "enable" on startup, I find all my connections blocked. I had to reconnect my monitor,etc to "disable" and "enable" it again and all my connections are fine again. I would understand that if I have set the firewall rules wrongly, but they work once I have re-enabled UFW, which to me rules out a wrong setting in the rules. Any pointers to this area?

Issue 2: I have not tried this many times yet, but in the two times when I tried to boot the system without the monitor connected the system does not actually complete the bootup sequence. It just hangs half way through the process, just prior to the login screen. Any pointers?

I am a little lost with these issues as I find these issues a little perplexing, especially with my limited knowledge in Ubuntu as a whole. Any help is much appreciated.

---

### Post by darkod on 2012-07-16
Don't discard a rule with wrong syntax in UFW that easily. In many cases, wrong syntax can cause it to stop loading the script, but a disable/enable can make it continue.

How did you set up your rules, using before.rules or after.rules files, or directly with the ufw commands like:
sudo ufw allow 22 etc

---

### Post by CocoMonGo on 2012-07-16
> **darkod said:**
> Don't discard a rule with wrong syntax in UFW that easily. In many cases, wrong syntax can cause it to stop loading the script, but a disable/enable can make it continue.

How did you set up your rules, using before.rules or after.rules files, or directly with the ufw commands like:
sudo ufw allow 22 etc


Solved. I took your advise and decided to remove all the rules and spent a couple of hours learning to setup UFW through CLI. I previously did this through GUFW in X. So far so good with Samba, SSH and XBMC remote working. 

Some how the issue about the system not booting on reboot is no longer present too. Many thanks.

---

