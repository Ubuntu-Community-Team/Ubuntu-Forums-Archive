---
title: "Do I really have a virus in Ubuntu?"
date: 2009-02-07
forum: Security
---

### Post by thenewgirl on 2009-02-07
I'm using Ubuntu 8.04. Surfing reddit using Firefox. Got a bunch of pop ups saying I had viruses on my computer. And then this Windows screen pops up and says Trojan Detected in flashing red under all the drives. Anyway, to me it looks completely ridiculous, but I do have to restart my computer to get rid of it. So far has only happened following links from reddit.

Really don't know much about this stuff, so any help is appreciated. Sorry if it's a stupid question!

Thanks.

---

### Post by andrewc6l on 2009-02-07
Odds that you have a virus are pretty low. You shouldn't have to reboot - at the very least, just kill firefox. From a command line:

$ ps ax | grep firefox

This will show you something like:
27807 ?        Ssl    2:37 /usr/lib/firefox-3.0.5/firefox

Then:
$ kill 27807

You might be able to do the same thing with File -> Quit.

[edit] I just checked, you should be able to do the same thing without going to the command line with:
System -> System Monitor
Click on "Processes" tab
Find "firefox" and select it
End Process (or maybe Edit -> Kill Process)

By default, Ubuntu doesn't have a virus scanner enabled, so any warnings you see are scams provided by advertisers.

---

### Post by R.Bucky on 2009-02-07
i read an article a couple of weeks ago about some IT guy running viruses on Wine to see if they would infect the linux machines. Apparently, one out of the 6 viruses corrupted the Wine install without harm to the Ubuntu box. Something to think about.

do not be too cocky about the linux virus protection. although the distro is hardened against these traditional trojans and others, be aware that only a small portion of the world uses Linux. As more users are gathered in the world, hackers will find methods of forcing their way to linux systems. Microsoft dominates the internet with something like 90% of all OS's on the planet - plenty of people to find security holes...

---

### Post by Tim Sharitt on 2009-02-07
You most likely don't have a virus. Attack sites use the pop-ups to make people think they have a virus and tell them to download a so-called anti-virus program which itself is usually some type of malware.

Edit: If you use Firefox, the no-script plug-in can help keeps those types of pop-ups to a minimum.

---

### Post by beyboo on 2009-02-07
Can you post a screenshot of all that you  see-  viruses, trojans under drives and whatever else you see...

---

### Post by thenewgirl on 2009-02-07
> **andrewc6l said:**
> Odds that you have a virus are pretty low. You shouldn't have to reboot - at the very least, just kill firefox. From a command line:

$ ps ax | grep firefox

This will show you something like:
27807 ?        Ssl    2:37 /usr/lib/firefox-3.0.5/firefox

Then:
$ kill 27807

You might be able to do the same thing with File -> Quit.

[edit] I just checked, you should be able to do the same thing without going to the command line with:
System -> System Monitor
Click on "Processes" tab
Find "firefox" and select it
End Process (or maybe Edit -> Kill Process)

By default, Ubuntu doesn't have a virus scanner enabled, so any warnings you see are scams provided by advertisers.

That's what I was thinking, that it was the ad that was saying I had a virus, especially with all the Windows stuff. But, I'd recently installed Wine and thought "oh, no. First thing having to do with Windows and I get a virus!" 

Thanks for the methods for closing Firefox. That was a problem...didn't know how to kill it without rebooting.

---

### Post by thenewgirl on 2009-02-07
> **R.Bucky said:**
> i read an article a couple of weeks ago about some IT guy running viruses on Wine to see if they would infect the linux machines. Apparently, one out of the 6 viruses corrupted the Wine install without harm to the Ubuntu box. Something to think about.

do not be too cocky about the linux virus protection. although the distro is hardened against these traditional trojans and others, be aware that only a small portion of the world uses Linux. As more users are gathered in the world, hackers will find methods of forcing their way to linux systems. Microsoft dominates the internet with something like 90% of all OS's on the planet - plenty of people to find security holes...

This is exactly what I was thinking. I've heard of more and more people using Linux and figured maybe the proliferation had given the hackers time to catch up. I almost didn't ask the question thinking "nah, of course I'm safe" but then I thought twice...just in case!

I actually uninstalled Wine since everything on the screen was Windows related. I don't know whether it made a difference, but I haven't had the problem again and have been using the internet. Wasn't really using Wine anyway...

Thanks for the response. I appreciate it.

---

### Post by thenewgirl on 2009-02-07
> **Tim Sharitt said:**
> You most likely don't have a virus. Attack sites use the pop-ups to make people think they have a virus and tell them to download a so-called anti-virus program which itself is usually some type of malware.

I was hoping it was something like that. Thank you as well.

> **Tim Sharitt said:**
> Edit: If you use Firefox, the no-script plug-in can help keeps those types of pop-ups to a minimum.

Perfect! Thank you, I'll use that.

---

### Post by thenewgirl on 2009-02-07
> **beyboo said:**
> Can you post a screenshot of all that you  see-  viruses, trojans under drives and whatever else you see...

Oh, man, I didn't even think to get a screen-shot! If it happens again I'll post back in case it'll help someone else.

Good thing to remember. Thank you.

---

### Post by Chayak on 2009-02-07
No you don't have any viruses.  It's just popups designed to scare users into downloading and installing a variant of the zlob trojan (fake antivirus).  Your computer is fine.  I'm a malware researcher by trade so I see a lot of this stuff.  There's a good reason why trust and use linux as a base system and run virtual machines for everything else.

---

### Post by cariboo on 2009-02-07
I got a call from a former client last night, they ran into something similar, except the popup was for Antivirus 360. It told them thier computer was infected and to click on the button to repair the problem. The people had been looking at Norton 360 earlier and thought this was a bit fishy. The big tip off was the poor English in the popup.

Jim

---

### Post by thenewgirl on 2009-02-07
> **Chayak said:**
> No you don't have any viruses.  It's just popups designed to scare users into downloading and installing a variant of the zlob trojan (fake antivirus).  Your computer is fine.  I'm a malware researcher by trade so I see a lot of this stuff.  There's a good reason why trust and use linux as a base system and run virtual machines for everything else.

Cool. Thanks!

---

### Post by thenewgirl on 2009-02-07
> **cariboo907 said:**
> I got a call from a former client last night, they ran into something similar, except the popup was for Antivirus 360. It told them thier computer was infected and to click on the button to repair the problem. The people had been looking at Norton 360 earlier and thought this was a bit fishy. The big tip off was the poor English in the popup.

Jim

Thanks, Jim. Actually that's exactly what this one was for! It did look rather amateur come to think of it.

If I'd actually been running Windows I'd probably be frantic right now.

---

### Post by zerofool2005 on 2009-02-09
There are still buffer overflows for nix based software. Just hackers dont like to write the code to run on nix. Its too much effort for such a small %% of the world. When they could have 10k of unpatched XP machienes

---

### Post by dburnett77 on 2009-02-09
Well, it's like this:  "Shields Up, Sulu!".
Takes care of everyting.

---

### Post by gtdaqua on 2009-02-10
> **R.Bucky said:**
> 
....although the distro is hardened against these traditional trojans and others, be aware that only a small portion of the world uses Linux. As more users are gathered in the world, hackers will find methods of forcing their way to linux systems. ...

It does not mean that because Linux has a low market share, the hackers are not targeting as much as they do in Windows. The architecture of both the OS are very different. When a user runs a program in windows, he runs it as administrator. Linux does not. So if you want to really harm the linux system, the user will have to do it explicitly. 

You get automatically infected in Windows. Because the virus can automatically download, install itself and execute. This can't be done in a Linux box. That's why Linux is a safe-bet. Only thing you do need to worry about would be the vulnerabilities in packages or kernel and they have to remotely exploitable to worry too much about it.

---

