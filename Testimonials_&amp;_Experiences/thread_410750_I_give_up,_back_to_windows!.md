---
title: "I give up, back to windows!"
date: 2007-04-16
forum: Testimonials &amp; Experiences
---

### Post by johnbradbury on 2007-04-16
Okay,
a few weeks ago I make the decision to put aside Windows and give Linux a chance. This took me from my comfort zone and gave me a large dose of what it must feel like to be an average computer user when something goes wrong.

At first I wanted to take a look at Linux because of all the industry buzz and due to some frustration over the price of Windows Vista and the hardware upgrades I would need in order to run the OS and the many VMWare sessions I have open.

I took my time to learn a little about Linux and the Open Source community, and if I'm honest what I read really struck a cord. I'd long dismissed the Free Software Movement as meaning free of charge and ultimately low quality. I hadn't really thought about the freedom to adapt and change software to meet my needs, or do avoid being locked into a specific vendor or product.

The more I read the better it all sounded. It made sense that as a business I wouldn't want to be held to ransom by a single software provider, forced to upgrade when they released a new OS and generally restricted in what I could do with the software I'd paid good money for. In theory I was a Linux convert!

Sadly the theory was all I managed. Installing Linux has proven a near impossible task and after hours and hours of failed installations I'm just about ready to give up.

I've tried to install:

Ubuntu 6.06
Ubuntu 6.10
Ubuntu 6.10 [Alternative Text Install]
Ubuntu 7.04 Beta
OpenSuse
Fedora 6
Knoppix 5.1
Xandros 4

and not one of them actually gave me a working system. The installation seems to complete fine but upon reboot the screen just goes blank after a while. Just before it goes blank I get something along these lines:

last mount point was in the future - FIXED
the system then starts to scan the drive (I assume this is the equivalent of chkdsk in windows) and fails at varying points freezing the screen. I’ve posted support requests and nothing seems to have worked that was suggested.

I installed Windows back onto the laptop and attempted to setup Linux in a VMWare session, and guess what the whole thing loaded fine. At this point I'm guessing it's a driver issue with either the Display Adapter or the Hard Drive given that these are the only differences when loading an OS into VMWare?

I truly wanted to get involved with the Linux community and learn more about this OS but every attempt I've made has failed and at the end of the day I need a system to just work when I need it.

---

### Post by Tsen on 2007-04-16
Yeah, some sort of hardware compatibility issue.
What's the computer's specs?

Anyway, sad to see somebody resorting back to Windows.  If you ever get the chance on a different computer, you might want to give it another try.  Or hell, just keep using it in VMWare.  Just get a feel for it, it's a pretty good OS.

---

### Post by Jouke74 on 2007-04-16
I know what you mean. With some hardware it is very difficult to get and KEEP everything running and requires a lot of forum reading and getting around in the terminal. An update can potentially break your system. Stability? Once it's running and you don't do anything yes, before that, well.... 

To give you some small examples:
- I could speed up my Ubuntu quite a lot by adding my host name in the internet hosts file?? :) 
- I was only able to start network manager, after i had rebuild the highcolor iconcache??? :D  

Maybe a dual boot first if you have one computer. That you can get your work done in windows and get to know linux. Check your hardware, memory and disks for hardware errors.  Also list your more specific hardware. 

Are the live cds running, (Knoppix should be going)? 
Upon boot do you get any graphics screen at all? 
Are you getting to a login screen?
What did you try already?

This way it is difficult to give specific help (assuming you still want it).

Wish you all the best with any system, JJ.

---

### Post by bwhite82 on 2007-04-16
Linux thrives from its users. I can't really say, "give back by helping developers" as Linux hasn't really given you anything yet. But, issues can only get fixed if developers are aware of them. Once you do isolate the problem, please let the developers of the relative content know what the issue is so that they may fix it. Good luck on whichever route you choose.

---

### Post by mac.ryan on 2007-04-16
Too bad.

I understand your frustration and I respect your choice. I don't know if there is a solution to your problems, sure when posting request for help it might have helped to give more information on your system.

Concrete example: in your thread "Installation Woes" nor the title or the text provide essential information such your hardware configuration, or - more noticeably - the fact you were trying to install ubuntu on a Tablet PC.

I can't guarantee if you had formulated your help requests differently you would have got help. I can guarantee - though - that a forum title like "Troubles installing on Tablet PC - HP tx1000" would have attracted the attention of people with that kind of expertise more effectively.

Anyhow... I wish all the best to you whether you will get back to windows or will finally find a solution to your troubles with GNU/Linux. :)

PS: Here [a classic]("http://www.catb.org/%7Eesr/faqs/smart-questions.html") on how to maximise the effect of help requests (ubuntu has a much less harsh approach to noobs than that described in there, though!)

---

### Post by Spr0k3t on 2007-04-16
I always hate to lose another user.  The thing I really don't understand is how you were able to install the various distributions without a problem until reboot.  Perhaps an issue with the computers drive.  I know some systems will not work at all due to lack of support on the SATA bus with non-standard communication specs.

I tried to go back through your postings on here to see if I might be able to offer up some assistance, but I couldn't get any hardware specs.  The offer is still good if you are interested.

---

### Post by johnbradbury on 2007-04-16
I've posted a more details description of the error and the process leading upto it here:
[http://ubuntuforums.org/showthread.php?p=2461977#post2461977](http://ubuntuforums.org/showthread.php?p=2461977#post2461977)

Hopefully someone will know how to fix.

---

### Post by drillchart on 2007-04-16
I know for me that I had a lot of problems getting Ubuntu to work on a laptop got it running had some more problems so I too gave up.  I decided to come back and tried it on an older desktop that was given to me, install was ten times easier, everything worked after the install though not all drivers were what I thought to be correct, but everything was working.  Good luck I hope all works out.

---

### Post by aysiu on 2007-04-16
I've moved this thread to a more appropriate subforum.

If you want to help out johnbradbury, the link to the support thread is there for you.

---

### Post by Geekkit on 2007-04-16
> **johnbradbury said:**
> I truly wanted to get involved with the Linux community and learn more about this OS but every attempt I've made has failed and at the end of the day I need a system to just work when I need it.

This is basically where I'm at as well. The USB support is shaky, especially with my Nokia phone. A bug report has been made at:

[INDENT][https://bugs.launchpad.net/ubuntu/+bug/102965](https://bugs.launchpad.net/ubuntu/+bug/102965)[/INDENT]

A reference to it is at:

[INDENT][http://www.linuxquestions.org/questions/showthread.php?t=526755](http://www.linuxquestions.org/questions/showthread.php?t=526755)[/INDENT]

And boot failing (without setting the BIOS to defaults due to turning of SATA drive support):

[INDENT][https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/33269](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/33269)[/INDENT]

And DVD mounting also locks up the system (found several references to what may be the problem but not sure which one was particularly **the **show stopper).

Essentially these are show stoppers and make the jump to Linux unobtainable (at least for me) since I need a system that doesn't crash/hang/lock/freeze. It's clear that these are bugs and that they've been filed but not sure when they will be updated. I suggest you do the same thing I'm doing which is wait a year and then try again. :)

---

### Post by beniwtv on 2007-04-17
> **johnbradbury said:**
> I've posted a more details description of the error and the process leading upto it here:
[http://ubuntuforums.org/showthread.php?p=2461977#post2461977](http://ubuntuforums.org/showthread.php?p=2461977#post2461977)

Hopefully someone will know how to fix.

I *think* I have the solution for this. I posted in your thread mentioned above.

I also own a HP (not the same model though), and it will lock up in console mode. In GUI all works fine, though. 

This is why it locks up, the fschk is in console mode, and it's completely random when it locks up.

---

