---
title: "bash history"
date: 2011-07-22
forum: Security
---

### Post by themanfromdelmonte on 2011-07-22
I checked my user accounts bash history and found the commands below.
 

 The lastb, whowatch, and grub customizer are my commands. I recently had the mouse pointer move around the desktop when not in use and music starting randomly. I assume that the intruder got the user password. Someone has entered the commands and I have the only physical contact.
 

 Sam is the name of the sudo account.
 

 What do you think the intruder was planning(hello world)??  Should I wipe the disk and start again?
 

 

 sudo w 
 lastb 
 ifup 
 ifup -h 
 ifup -a 
 sudo ifuo -a 
 sudo ifuo -ap 
 sudo w 
 sam 
 user sam 
 root 
 sudoroot 
 kuser 
 fuser 
 fuser -v 
 last 
 lastb 
 ac 
 whowatch 
 which bash 
 #!/bin/bash 
 # declare STRING variable 
 STRING="Hello World" 
 #print variable on a screen 
 echo $STRING 
 top 
 1susb 
 lsusb 
 lspci 
 ip DDR 
 ip addr 
 iwconfig 
 sudo last ; w 
 lasat 
 last 
 grep last ; lastb 
 sudo add-apt-repository ppa:danielrichter2007/grub-customizer 
 ac 
 apt-get stop sendmail 
 firefox 
 end

---

### Post by sanderd17 on 2011-07-22
> **themanfromdelmonte said:**
>  I recently had the mouse pointer move around the desktop when not in use and music starting randomly.

I've seen this a lot of times, in ubuntu, a music file starts playing when you hover over it with your mouse. So if you have some music files on your desktop you probably heard them.
>  I assume that the intruder got the user password. Someone has entered the commands and I have the only physical contact.

If you did not install any servers (like an SSH server), than nobody can get into your computer from the outside, even not with a password.
> 
 

 Sam is the name of the sudo account.
 

 What do you think the intruder was planning(hello world)??  Should I wipe the disk and start again?
 

 

 sudo w 
 lastb 
 ifup 
 ifup -h 
 ifup -a 
 sudo ifuo -a 
 sudo ifuo -ap 
 sudo w 
 sam 
 user sam 
 root 
 sudoroot 
 kuser 
 fuser 
 fuser -v 
 last 
 lastb 
 ac 
 whowatch 
 which bash 
 #!/bin/bash 
 # declare STRING variable 
 STRING="Hello World" 
 #print variable on a screen 
 echo $STRING 
 top 
 1susb 
 lsusb 
 lspci 
 ip DDR 
 ip addr 
 iwconfig 
 sudo last ; w 
 lasat 
 last 
 grep last ; lastb 
 sudo add-apt-repository ppa:danielrichter2007/grub-customizer 
 ac 
 apt-get stop sendmail 
 firefox 
 end

There are indeed some weird commands in this history, but nothing dangerous. Maybe your brother went on your computer?

---

### Post by themanfromdelmonte on 2011-07-22
The music was not the 30s clip you get when the mouse passes over a sound file. It was a random track that just started playing. No apps were open. I found it to be rhythmbox when I checked in system monitor. 

Nobody uses the computer apart from me and my wife and my wife finds it hard to open firefox. No way would she even think about opening up a terminal. When the strange thing were happening I notice the ram usage was up a third compared to normal.

I have no services running at all apart from cups. I have a router firewall and a configured firewall on the computer.

Either those commands were sent over the Internet or by breaking into my house which seems a bit extreme.

---

### Post by Irihapeti on 2011-07-22
Have you had remote desktop enabled? I see this quite often: someone opens remote desktop, enables it by clicking on the box and forgets about it. OR a few folk have thought that they had enabled remote desktop for the LAN only, but uPNP automatically forwarded the port to the internet.

It's an easy way for someone to get in, especially if no password or a weak password is used - and I think that the password is restricted to something rather short.

---

### Post by doas777 on 2011-07-22
> **Irihapeti said:**
> Have you had remote desktop enabled? I see this quite often: someone opens remote desktop, enables it by clicking on the box and forgets about it. OR a few folk have thought that they had enabled remote desktop for the LAN only, but uPNP automatically forwarded the port to the internet.

It's an easy way for someone to get in, especially if no password or a weak password is used - and I think that the password is restricted to something rather short.
+1.
I'd almost guarantee that remote desktop was the culprit.

---

### Post by uRock on 2011-07-22
I recommend backing up data that needs to be saved and reinstalling. Especially if the cracker installed the PPA shown in the history output.

---

### Post by unspawn on 2011-07-23
> **uRock said:**
> I recommend backing up data that needs to be saved and reinstalling.
Hold on a second. You *recommend* it? Based on what? Do you perchance possess something we haven't seen like process, open files or network listings? Or maybe last, lastlog, lastb, debsums, rsyslog, other users shell history, MAC times or other evidence so you can make an informed decision? 


> **uRock said:**
> Especially if the cracker installed the PPA shown in the history output.
And why "especially"? AFAIK the SW is just a GRUB configuration GUI? So unless that repo was subverted to have a package payload containing Something Completely Different (MPFC), should you not verify things before making such claims? Please realize I'm not here to chide you in any way but what does making claims without verifying evidence cause except fear, uncertainty and doubt?

---

### Post by themanfromdelmonte on 2011-07-23
I deleted the remote access app as I was never going to use it along with every other server that I was never going to use. Time to reinstall

---

### Post by SoFl W on 2011-07-23
The music files starting...
Places-> Home Folder-> Edit-> Preferences-> Preview tab, under Sound Files change the entry to "Never"
(This is in Gnome 2)

Had a friend who got real nervous when his mouse started to move across the screen.  After some investigation he figured out it was because of his cell phone and wireless mouse.  He moved the cell phone away, it would stop.  He put the phone back down the mouse cursor would start moving again.

---

### Post by uRock on 2011-07-23
> **unspawn said:**
> Hold on a second. You *recommend* it? Based on what? Do you perchance possess something we haven't seen like process, open files or network listings? Or maybe last, lastlog, lastb, debsums, rsyslog, other users shell history, MAC times or other evidence so you can make an informed decision? 



And why "especially"? AFAIK the SW is just a GRUB configuration GUI? So unless that repo was subverted to have a package payload containing Something Completely Different (MPFC), should you not verify things before making such claims? Please realize I'm not here to chide you in any way but what does making claims without verifying evidence cause except fear, uncertainty and doubt?

You are saying that you'd just keep going with a system which had been accessed and software installed? Reinstalling only takes 30-45 minutes on my end and I would do it in a heart beat if I felt my system had been compromised.

---

### Post by bodhi.zazen on 2011-07-23
> **uRock said:**
> You are saying that you'd just keep going with a system which had been accessed and software installed? Reinstalling only takes 30-45 minutes on my end and I would do it in a heart beat if I felt my system had been compromised.

It depends on the skill of the intruder vs the skill of the sys admin.

If the sys admin has to ask on these forums I think it is safe to assume they are on the short end of the stick.

Now if unspawn or anyone else wants to walk someone through the clean up process, fine, but it can be hard.

If you find and clean the root kit you can know it is clean. Finding nothing is a long long ways from proving a clean system.

If you want to learn to clean systems , expect a bit of reading, I like these two articles as an overview:

[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1)

[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2)

---

### Post by unspawn on 2011-07-23
> **bodhi.zazen said:**
> Now if unspawn or anyone else wants to walk someone through the clean up process, fine, but it can be hard.
I'd be happy to take the OP on a fact-finding mission but if a root compromise is found there will be no talk of any "cleaning up". (BTW you realize those Symantec docs are seven years old, right? ;-p) 
Anyway, the OP should signal readiness as he already wrote:
> **themanfromdelmonte said:**
> Time to reinstall
and I don't want to waste time if he's in the process of doing that.

---

### Post by bodhi.zazen on 2011-07-23
> **unspawn said:**
> I'd be happy to take the OP on a fact-finding mission but if a root compromise is found there will be no talk of any "cleaning up".

Thought so =)

> (BTW you realize those Symantec docs are seven years old, right? ;-p)

Aye, but they give a good overview of what is involved in forensics. Do you know a better 1 or 2 page summary to give users some idea of what is actually involved when performing forensics on a linux box ? Post 'me here.

---

### Post by bcschmerker on 2011-07-23
> **SoFl W said:**
> ...Had a friend who got real nervous when his mouse started to move across the screen.  After some investigation he figured out it was because of his cell phone and wireless mouse.  He moved the cell phone away, it would stop.  He put the phone back down the mouse cursor would start moving again.The uncommanded pointer movement sounds like a radio-interference issue.  A lot of radioelectronic conveniences, e.g., Bluetooth® Audio Sink, Logitech® Unifying mouse/keyboard technology, &c., use the 2.4 GHz band nowadays.  I prefer to keep a minimum of radioelectronics transceivers and/or transponders on any and all systems at my computer station for that reason.

Concerning the primary question here, in Ubuntu®, many X application backends use /bin/bash for essential functionality; I often call up bash via GNOME Terminal to access console and NCurses apps that have no GUI's in X.org, for instance.  I disable Remote Desktop and Remote Assistance on all my 'puters due to the inherent security issues therein---I've heard horror stories of remote Roots in Microsoft Windows® going back to 1995.

---

### Post by Irihapeti on 2011-07-24
I have a kitchen table with an English oak top, which has a marked woodgrain pattern. If I put my wired mouse directly on it, the pointer starts creeping across the screen. Using a plain mouse mat solves that problem.

---

### Post by bodhi.zazen on 2011-07-24
> **bcschmerker said:**
> The uncommanded pointer movement sounds like a radio-interference issue.  A lot of radioelectronic conveniences, e.g., Bluetooth® Audio Sink, Logitech® Unifying mouse/keyboard technology, &c., use the 2.4 GHz band nowadays.  I prefer to keep a minimum of radioelectronics transceivers and/or transponders on any and all systems at my computer station for that reason.

This is a very good point, thank you for posting that information.

---

### Post by unspawn on 2011-07-24
> **bodhi.zazen said:**
> Post 'me here.
While I'm still partial to the old CERT Intruder Detection Checklist: [http://web.archive.org/web/20080109214340/http://www.cert.org/tech_tips/intruder_detection_checklist.html](http://web.archive.org/web/20080109214340/http://www.cert.org/tech_tips/intruder_detection_checklist.html) I'll settle for two Chuvakin / Zeltser cheat sheets: [http://zeltser.com/network-os-security/security-incident-survey-cheat-sheet.html](http://zeltser.com/network-os-security/security-incident-survey-cheat-sheet.html) and [http://zeltser.com/log-management/security-incident-log-review-checklist.html](http://zeltser.com/log-management/security-incident-log-review-checklist.html). Concise and available as PDF as well.

---

### Post by uRock on 2011-07-24
Some more good reading material, thanx. :KS

---

### Post by sanderd17 on 2011-07-24
> **bcschmerker said:**
> The uncommanded pointer movement sounds like a radio-interference issue.  A lot of radioelectronic conveniences, e.g., Bluetooth® Audio Sink, Logitech® Unifying mouse/keyboard technology, &c., use the 2.4 GHz band nowadays.  I prefer to keep a minimum of radioelectronics transceivers and/or transponders on any and all systems at my computer station for that reason.



I've also seen my mouse go mad once because of interference with the power net. When I plugged in the net power of my laptop, my mouse went crazy, when I worked only on battery, the mouse was reacting normal.

The TV was also disturbed, so we called the power net maintainers. They renewed all the contacts from the power line to our house and I haven't had any issues since.

That was over a year ago, and the man who did the work was surprised what effect disturbed power could have.

---

