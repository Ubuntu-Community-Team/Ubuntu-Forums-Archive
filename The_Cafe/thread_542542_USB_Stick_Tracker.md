---
title: "USB Stick Tracker"
date: 2007-09-04
forum: The Cafe
---

### Post by segphault_ on 2007-09-04
Hey everyone,
School is just around the corner for me, and I was wondering if anyone could be of help. I have a USB memory stick (who doesn't) that I intend to put school work on, but it also contains important information and a basic backup of my home directory with settings and documents. I don't intend to lose it, but I want to have a bit of security just in case. I have put a "If found please read.txt" file inside the root directory of my USB stick, but I also wanted to add a autorun script for Windows computers that would ping some server and the server would take note of the IP. This way I would have a vague idea of where it went if it got lost/stolen. I was wondering if there is anything like this that I can put onto the stick, something that uses a special service to download a certain link that the user obtained from the server, one that is unique to them. 
I'm sorry if you don't understand, I do a pretty crappy job at explaining things.
Thanks to anyone who can help me with this.

---

### Post by scooper on 2007-09-04
I don't know about autorun from a USB stick.  If you could run a program that transmits something to a server wouldn't that likely be trapped by firewall software?  I think there's some amount of firewalling on by default in Windows.  Not positive though.

What I do is to encrypt the important stuff in a TrueCrypt partition on the stick.  Basically you could take a 1 GB stick and have TrueCrypt make a 500 MB partition that can't be accessed or read without a secure pass phrase.  Reading it directly won't help because it's written encrypted.  This seems like a better solution, making it near impossible for your important info to be read.

TrueCrypt is easy to install (via apt-get) and use.  It has a Windows version, allowing you to read your data anywhere, except Mac.

---

