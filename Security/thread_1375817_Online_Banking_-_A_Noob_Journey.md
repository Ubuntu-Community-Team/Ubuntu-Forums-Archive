---
title: "Online Banking - A Noob Journey"
date: 2010-01-08
forum: Security
---

### Post by petelx on 2010-01-08
I know this is a revisited topic.  I've skim-read the stickies and done some searches, but I think I'm missing some of the fundamentals.  I'm no geek, but have better than average familiarity with windows systems.  I have no experience with Linux.  I have mainstream understanding about how a hacker can use trojans, keyloggers, malware, etc, but I have no real understanding of how to write code or how a hacker can use code exploits.  

This is going to be a long post.  Please understand that I am sincerely grateful to anyone who can offer intelligent advice.  Even if you are able to answer one or two of my questions in part or in full, that would be appreciated.  I'll apologize right now for missing something available elsewhere.   If you're feeling generous, link me to another thread or offer a keyword for a search.  You can even use an expletive when you do it.  I'm trying to decide between buying a new (cheap) PC or using ubuntu on a live CD with my current system.  Before I dive in and do all my ubuntu homework I want to make sure the concept is feasible.  I'm also considering getting some king of nettop (without harddrive) and using it exclusively with ubuntu running on CD.  Yes, paranoid. 

I have a wife and kids who share my home computer, sometimes using it for online games, browsing, email, etc.  I run the usual security stuff.. firewall, anti-viruses, and exercise good practices.  I have windows xp on a partition which I occasionally will wipe clean and restore an image to.  The image is pretty much a clean install with a few extras.  Non-OS partitions store data and some games and are almost never wiped clean.  The point is, my computer is windows based, used by other family members and is subjected to the usual security risks.  I can't say I've ever been compromised, but occasionally my anti-virus program has caught something trying to install.  

It is on this computer that I want to do my banking, but I want to do this with a Live ubuntu CD.  To be clear, I want to run the OS entirely off the CD with nothing on the hard drive.   Everything should run from read only media and temporary system memory.  Any discussion here forward should assume we are only talking about ubuntu run entirely from CD.  I want to boot, go directly to my website of choice, do my thing, log off and restart the PC back into my regular OS which will be either xp or win7.   I will do this only a few times a year, once a month at the very most.  At most I might be on a couple hours at a time.  It could be any day of the year at any time of day.   I will use ubuntu only for this purpose.  No email.  No plugins.  No other browsing.  (The only exception is that I may need adobe acrobat reader to read documents online.  Or perhaps I could just download the pdf to flash drive and read it later with my regular windows OS.)  At this time I will not be running linux anywhere else on the computer.  I am just a private user, not a business, and there are no concerns about physical manipulation of my PC or the CD itself.  My primary concern would be someone seeing my password or login or security related personal information via some kind of keylogger or trojan or some other method I'm not aware of. 

I have read Bodhi's Security Sticky, but I'm not sure how much of this is an issue considering that I will always be running the OS from the CD and will be using default settings.  But let me get on with my noob paranoid questions...

1) Assuming I have a good copy of ubuntu (verified with MD5SUM) what are the changes that some "open source" programmer has deliberately put a back door or code exploit in place for later hacking?  Has this ever happened?  What does the ubuntu community do to detect or prevent this?

2)   I admit, I know little about linux built OSes.  Ubuntu is the only one I've looked into in any kind of depth.  Is there an alternative to ubuntu that I should be looking at that would better serve my needs?

3) When running ubuntu from the CD does it utilize the hard drive in any way?  In other words, is there something ubuntu leaves on the harddrive that might later be manipulated while I'm running windows and then later effect me during my next ubuntu session? 

4) Say my xp system gets compromised without me knowing it.  Say either the primary or extended partitions get compromised.  When I boot with ubuntu, can a hacker somehow use software on my harddrive to compromise ubuntu while it's running from CD?  Or can I assume ubuntu runs as if the hard drive is disconnected?  

5) If my hardware flash bios gets hacked (if such a thing is possible) can that later compromise my ubuntu OS?  (i.e. my modem, router, mobo bios, printer.)

6)  Firewalls & Anti-Virues software.  From reading other posts, it doesn't sound like I'd need a FW because ubuntu closes all the ports.  I only need a port for the browser to use.  I would never be using plugins or 3rd party software.  As mentioned, the one exception might be adobe acrobat reader which I might want to view documents via the browser.  Also, sometimes I might like to use the printer.  I could save things to flash drive and print later from my regular PC with windows OS.  Private information might be at risk but my login and password would be safe.  Anti-virus software also seems unnecessary for reasons stated in the sticky.  Running ubuntu from CD only seems to reinforce the idea that I don't need the extra software, but I welcome your thoughts on this topic.

7) Security updates for ubuntu.  The only updates that would be relevant to me would be those that patch code exploits in the ubuntu OS or default applications.  I would probably also need to update firefox.  To my understanding, I could not patch the CD so I would have to patch the ISO or just re-download ubuntu entirely.  There would be no other way to alter the OS.  This might be a big drawback in terms of upgrade maintenance.   If hacker knows the exploit he could exploit it in realtime when I'm online using ubuntu.  On the bright side, the same thing that would keep me from patching the read-only CD would prevent the hacker from installing any malware.  Is my understanding correct?  I'm grateful to hear any elaborations on this line of thought...  

8  Devil's Advocate.  By my thinking, if I take the proper measures, then what would it take for a hacker to get at me while I'm running ubuntu?  Say the hacker had my IP (which is supposed to by dynamic but I get the same one from my ISP for weeks or months).  Say I boot up with ubuntu.  He'd have to find a port, right?  Then he'd have to know a code exploit.  Then he'd have to get on during the short window of time when I'd be on.  He couldn't install anything on the CD, so he'd have to run something in system memory in real time, right?  Anything he was running would only live until I restarted the PC.  Am I understanding the factors here?  Help me understand what I'm up against here in terms of what's hypothetically possible.

9) Other security measures.  I've read about "Hardened Kernels" and other ways to alter ubuntu for security purposes, but would these measures still be relevant when running from CD?  I assume I would have to modify the CD image before burning.  I might also like to tweak firefox for the most secure settings and have the configuration info burned into the CD as read-only.  For example, I might block all websites except for the one I want to visit.  With a little homework, I assume these modifications to the CD image are possible....?

10)  My preference would be to have the most stripped down version of ubuntu that would only serve the purposes I need.  Is there cause to strip non-relevant applications off ubuntu?  I'm not worried about processing speed or boot times, I just want to remove applications that would provide codes exploits for hackers.  Is this worth considering?

Thanks.  I know it's a long post.  Your help is truly appreciated. :)

---

### Post by chrisinspace on 2010-01-08
petelx,

You are definitely on track with your thinking.  I actually read an article in the Washington Post recently on the topic.  It was written by a security expert who was advocating just this approach.  You might want to check it out:

[http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html](http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html)

I work for a bank so I can tell you that your concerns are justified.  Windows is a security nightmare, even if you are running all of the necessary anti-spyware, -virus, -malware stuff.  Mac is safer, but I actually knew someone whose Mac was compromised by a keylogger.  I will try to answer as many of your questions as I can:

1. Canonical manages the Ubuntu project.  They are a for-profit company (even though they aren't making a profit yet).  They are trying to break into the corporate market, so if a breach of this magnitude were discovered, it would be catastrophic to them.  While nothing is 100% sure, I would imagine they go to great lengths to prevent this kind of thing.

2. Ubuntu is probably a good place to start.  It is a good mix of features and usability.  The great thing about Linux, though, is that you have numerous choices.  [DistroWatch]("http://distrowatch.com/") is a good site for researching what is out there.

3 and 4. It is my understanding that it bypasses the HDD completely.  I believe you can run a LiveCD without a HDD even installed.  You'll probably want to verify that, though.  Your Linux live cd session should not interact with your installed copy of Windows in any way.

5. I have never heard of a BIOS infection, but I can't answer that question with any authority.

6. I don't think you really need a software firewall or AV package if you are running from a live session.  A hardware firewall is always a good idea though.  Many home routers, including wireless routers, have firewall capabilities that you can turn on and configure.  If you have a compatible wireless router a cool Linux project is a re-write of the firmware that adds more robust features.  I use DD-WRT.
[LIST]
[*][http://www.dd-wrt.com/site/index](http://www.dd-wrt.com/site/index)
[*][http://en.wikipedia.org/wiki/DD-WRT](http://en.wikipedia.org/wiki/DD-WRT)
[/LIST]
7. You can install the available updates, but when you leave the session, the changes will not stick.  You would have to re-compile the cd for that.  You could use RemasterSys for that.  I'll go into that software a little more at the end because I think it will apply to a couple of your questions.

8. Again, a live cd is not re-writable, so nothing can permanently install to the disk.  Also, 99% of such malware is written for Windows, so chances are, if it got into your system, it wouldn't affect it.

9 and 10.  I'm not sure about hardened kernels, but RemasterSys can help you create a custom live cd.  I actually made one for some of our bank's more tech-savvy customers.  I stripped out all of the unnecessary software, cleaned up the interface, and branded it with our logos.  It worked great.  Check it out:
[LIST]
[*][http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
[*][http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html) - tutorial
[/LIST]
There is also more about it in the forums.  Sounds like it might be exactly what you are looking for.

Another option that might interest you is installing Sun VirtualBox in Windows and then using it to create a Linux virtual machine (VM).  You could then keep this VM fully updated and it is isolated in the VirtualBox "sandbox" so that is isolated from Windows threats.  This would be a little less secure since you wouldn't have the advantage a fresh session every time, but it would offer a lot of features not available on a live disk.

---

### Post by sanderd17 on 2010-01-08
As mentionned by chrisinspace, you can't write updates to your ubuntu cd. As an alternative, you can use a flash stick. On a flash stick you can install other programs and updates to your needs. If you don't want to leave traces, I believe removing your complete home directory each time would be sufficient since all session information for apps is stored there.

---

### Post by chrisinspace on 2010-01-08
Good point.  There is now an application installed by default in Ubuntu to help you create a bootable flash memory drive.  A best-of-both-worlds scenario would be to get a flash drive with a write-protect switch (or an SD Card if you have a card reader).  Use it to create a bootable USB device.  Then you could turn off the write-protection when you want to update the OS and then turn it back on so the drive is read-only when you use it to browse the internet. The only thing you have to be sure of is that your computer can boot from a USB drive.  Most modern BIOS accommodate this, but it might not work on an older computer.

Thanks for the inspiration!  I might give that a try myself.

---

### Post by steveneddy on 2010-01-08
Order the CD directly from the Ubuntu site to take the element of a back door root kit out of the equation.

---

### Post by FuturePilot on 2010-01-08
> 1) Assuming I have a good copy of ubuntu (verified with MD5SUM) what are the changes that some "open source" programmer has deliberately put a back door or code exploit in place for later hacking? Has this ever happened? What does the ubuntu community do to detect or prevent this?

Most (all?) of the software on the live CD is from the main repository which has some pretty strict review processes for any incoming software. It has been looked over by many people. The chances of something like that happening are pretty low. As of now I am not aware of anything like that happening before.

> 2) I admit, I know little about linux built OSes. Ubuntu is the only one I've looked into in any kind of depth. Is there an alternative to ubuntu that I should be looking at that would better serve my needs?
Ubuntu is probably the best place to start. IMO it has the best hardware support around. As mentioned, there are other Linux distros around but Ubuntu is probably the best choice in this situation.

> 3) When running ubuntu from the CD does it utilize the hard drive in any way? In other words, is there something ubuntu leaves on the harddrive that might later be manipulated while I'm running windows and then later effect me during my next ubuntu session?

There's only once instance where Ubuntu will touch the hard drive on its own and that is if there is an existing swap partition on the hard drive; it will use it for swap space. And that would only exist if you have Ubuntu or another distro installed on your hard drive. Since you don't this won't be an issue. So no, it will not touch the hard drive unless you tell it to.

> 4) Say my xp system gets compromised without me knowing it. Say either the primary or extended partitions get compromised. When I boot with ubuntu, can a hacker somehow use software on my harddrive to compromise ubuntu while it's running from CD? Or can I assume ubuntu runs as if the hard drive is disconnected?
No, it would not be possible for something to compromise Ubuntu in that way. Yes Ubuntu should be able to run from the CD with no hard drive but your BIOS may think otherwise. I tried doing that in my old laptop but the BIOS wouldn't allow it to boot since there was no hard drive.

> 5) If my hardware flash bios gets hacked (if such a thing is possible) can that later compromise my ubuntu OS? (i.e. my modem, router, mobo bios, printer.)
Not that I know of.

> 6) Firewalls & Anti-Virues software. From reading other posts, it doesn't sound like I'd need a FW because ubuntu closes all the ports. I only need a port for the browser to use. I would never be using plugins or 3rd party software. As mentioned, the one exception might be adobe acrobat reader which I might want to view documents via the browser. Also, sometimes I might like to use the printer. I could save things to flash drive and print later from my regular PC with windows OS. Private information might be at risk but my login and password would be safe. Anti-virus software also seems unnecessary for reasons stated in the sticky. Running ubuntu from CD only seems to reinforce the idea that I don't need the extra software, but I welcome your thoughts on this topic.

You're correct here. The software included on the live CD should be enough. Sometimes though, I've found that some printer drivers are not on the live CD and must be installed from the repos.

> 7) Security updates for ubuntu. The only updates that would be relevant to me would be those that patch code exploits in the ubuntu OS or default applications. I would probably also need to update firefox. To my understanding, I could not patch the CD so I would have to patch the ISO or just re-download ubuntu entirely. There would be no other way to alter the OS. This might be a big drawback in terms of upgrade maintenance. If hacker knows the exploit he could exploit it in realtime when I'm online using ubuntu. On the bright side, the same thing that would keep me from patching the read-only CD would prevent the hacker from installing any malware. Is my understanding correct? I'm grateful to hear any elaborations on this line of thought...

This could be tricky. It's not possible to apply all updates on the live CD, particularly kernel updates or other updates that would require a reboot. Redownloading Ubuntu won't help as the ISO images are not updated. As someone mentioned you could use the USB creator to create a live USB but I'm not sure how it would handle updates since I've never tried installing updates on a live USB install.

> 8 Devil's Advocate. By my thinking, if I take the proper measures, then what would it take for a hacker to get at me while I'm running ubuntu? Say the hacker had my IP (which is supposed to by dynamic but I get the same one from my ISP for weeks or months). Say I boot up with ubuntu. He'd have to find a port, right? Then he'd have to know a code exploit. Then he'd have to get on during the short window of time when I'd be on. He couldn't install anything on the CD, so he'd have to run something in system memory in real time, right? Anything he was running would only live until I restarted the PC. Am I understanding the factors here? Help me understand what I'm up against here in terms of what's hypothetically possible.
It would be very difficult for someone to get at the OS directly in this situation. However someone could get on your LAN and cause all sorts of problems. Anything from sniffing your traffic to redirecting you to phishing sites. Definitely take into consideration making sure your network is well secured, particularly any wireless access.

> 10) My preference would be to have the most stripped down version of ubuntu that would only serve the purposes I need. Is there cause to strip non-relevant applications off ubuntu? I'm not worried about processing speed or boot times, I just want to remove applications that would provide codes exploits for hackers. Is this worth considering?

It may or may not be worth the effort to strip all the extra stuff out depending on how important you would consider this. Generally the less software, the less vectors for exploits. However if it's not running it's not really hurting anything either.

Hope that helps :)

---

### Post by rookcifer on 2010-01-08
> **petelx said:**
> 
1) Assuming I have a good copy of ubuntu (verified with MD5SUM) what are the changes that some "open source" programmer has deliberately put a back door or code exploit in place for later hacking?  Has this ever happened?  What does the ubuntu community do to detect or prevent this?

What stops someone working for M$ or other closed-source companies from doing the same thing?  Nothing.  However, the open-source community has the added advantage of having the "many eyes" approach to security -- the more eyes on the code the better.  Basically, to calm your fears, if this sort of thing happened, it would likely be known about by now because at least one guy out of millions would have already discovered it.  Moreover, the kernel itself is looked over and audited with a high degree of thoroughness.

> 2)   I admit, I know little about linux built OSes.  Ubuntu is the only one I've looked into in any kind of depth.  Is there an alternative to ubuntu that I should be looking at that would better serve my needs?

If you're just going to use a liveCD, then I say stick with Ubuntu, although most other distros would work fine too.

> 3) When running ubuntu from the CD does it utilize the hard drive in any way?  In other words, is there something ubuntu leaves on the harddrive that might later be manipulated while I'm running windows and then later effect me during my next ubuntu session? 


Nope, it doesn't touch the hard drive at all because the hard drives are not mounted to begin with.

> 4) Say my xp system gets compromised without me knowing it.  Say either the primary or extended partitions get compromised.  When I boot with ubuntu, can a hacker somehow use software on my harddrive to compromise ubuntu while it's running from CD?  Or can I assume ubuntu runs as if the hard drive is disconnected?  

Nope, see answer to #3.
> 
5) If my hardware flash bios gets hacked (if such a thing is possible) can that later compromise my ubuntu OS?  (i.e. my modem, router, mobo bios, printer.)

Not likely, especially if no untrusted person has physical access to your machine.

> 6)  Firewalls & Anti-Virues software.  From reading other posts, it doesn't sound like I'd need a FW because ubuntu closes all the ports.  I only need a port for the browser to use.  I would never be using plugins or 3rd party software.  As mentioned, the one exception might be adobe acrobat reader which I might want to view documents via the browser.  Also, sometimes I might like to use the printer.  I could save things to flash drive and print later from my regular PC with windows OS.  Private information might be at risk but my login and password would be safe.  Anti-virus software also seems unnecessary for reasons stated in the sticky.  Running ubuntu from CD only seems to reinforce the idea that I don't need the extra software, but I welcome your thoughts on this topic.

You don't even need AV on an installed Ubuntu partition, and you especially don't need it from a liveCD.

> 7) Security updates for ubuntu.  The only updates that would be relevant to me would be those that patch code exploits in the ubuntu OS or default applications.  I would probably also need to update firefox.  To my understanding, I could not patch the CD so I would have to patch the ISO or just re-download ubuntu entirely.  There would be no other way to alter the OS.  This might be a big drawback in terms of upgrade maintenance.   If hacker knows the exploit he could exploit it in realtime when I'm online using ubuntu.  On the bright side, the same thing that would keep me from patching the read-only CD would prevent the hacker from installing any malware.  Is my understanding correct?  I'm grateful to hear any elaborations on this line of thought...  

You're going into paranoia mode here.  You do not need to upgrade a liveCD OS.  Sure, it might be fine to use the latest liveCD, but updating the liveCD itself with new security updates that are meant to be installed on a physical machine is not feasible nor is it necessary.
> 
8  Devil's Advocate.  By my thinking, if I take the proper measures, then what would it take for a hacker to get at me while I'm running ubuntu?  Say the hacker had my IP (which is supposed to by dynamic but I get the same one from my ISP for weeks or months).  Say I boot up with ubuntu.  He'd have to find a port, right?  Then he'd have to know a code exploit.  Then he'd have to get on during the short window of time when I'd be on.  He couldn't install anything on the CD, so he'd have to run something in system memory in real time, right?  Anything he was running would only live until I restarted the PC.  Am I understanding the factors here?  Help me understand what I'm up against here in terms of what's hypothetically possible.

Yes, what you said is basically correct.  He would have to have a code path into your machine by either tricking you or by finding a listening service (there aren't any by default).  Then he would have to find a way to exploit the service.

> 9) Other security measures.  I've read about "Hardened Kernels" and other ways to alter ubuntu for security purposes, but would these measures still be relevant when running from CD?  I assume I would have to modify the CD image before burning.  I might also like to tweak firefox for the most secure settings and have the configuration info burned into the CD as read-only.  For example, I might block all websites except for the one I want to visit.  With a little homework, I assume these modifications to the CD image are possible....?

You can "roll your own" so to speak (in other words, make a remaster of the original Ubuntu liveCD), but I see no reason to do so.  You don't need a hardened kernel for simple web browsing.  The hardened kernels are really only needed if you run an open server.

> 10)  My preference would be to have the most stripped down version of ubuntu that would only serve the purposes I need.  Is there cause to strip non-relevant applications off ubuntu?  I'm not worried about processing speed or boot times, I just want to remove applications that would provide codes exploits for hackers.  Is this worth considering?

No, because there will be no services listening.  And, since you will be on a liveCD, the chances of you accidentally installing malicious software is next to nill.

---

### Post by running_rabbit07 on 2010-01-08
Using the live CD for that is a great idea. If you don't have a lot of RAM you could even create a small Swap partition.

---

### Post by Bill-Gates on 2010-01-08
Noob response to a noob question and answers



QUESTION #8> 
                    8 devil's advocate. By my thinking, if i take the proper measures, then what would it take for a hacker to get at me while i'm running ubuntu? Say the hacker had my ip (which is supposed to by dynamic but i get the same one from my isp for weeks or months). Say i boot up with ubuntu. He'd have to find a port, right? Then he'd have to know a code exploit. Then he'd have to get on during the short window of time when i'd be on. He couldn't install anything on the cd, so he'd have to run something in system memory in real time, right? Anything he was running would only live until i restarted the pc. Am i understanding the factors here? Help me understand what i'm up against here in terms of what's hypothetically possible.ANSWERS
> It would be very difficult for someone to get at the os directly in this situation. However someone could get on your lan and cause all sorts of problems. Anything from sniffing your traffic to redirecting you to phishing sites. Definitely take into consideration making sure your network is well secured, particularly any wireless access.> Yes, what you said is basically correct. He would have to have a code path into your machine by either tricking you or by finding a listening service (there aren't any by default). Then he would have to find a way to exploit the service.
Could you set up a virtual server with multiple virtual proxies on a junk machine to create another layer of protection for yourself or would this be pointless?

---

### Post by DZ* on 2010-01-09
> **sanderd17 said:**
> As mentionned by chrisinspace, you can't write updates to your ubuntu cd. As an alternative, you can use a flash stick. On a flash stick you can install other programs and updates to your needs. If you don't want to leave traces, I believe removing your complete home directory each time would be sufficient since all session information for apps is stored there.

Why not use the "Encrypted Home" feature with a stick. If the stick gets lost, all the banking data on it would remain protected.

---

### Post by petelx on 2010-01-09
WOW!  What a great response.  I really appreciate the feedback but I need a couple days to absorb it all.  Just wanted to post a quick "thank you" for now and I'll comment further over the weekend.   I really think I'll find a way to make this work.

Pete

---

### Post by DZ* on 2010-01-09
> **petelx said:**
> WOW!  What a great response.  I really appreciate the feedback but I need a couple days to absorb it all.  Just wanted to post a quick "thank you" for now and I'll comment further over the weekend.   I really think I'll find a way to make this work.

Pete

There is a "checkbox" to enable encrypted home during the installation.

However, this works best with an internal drive, because checking this option automatically enables encrypted swap as well. With a USB stick, the swap partition name specified in /etc/crypttab (e.g. /dev/sdb3) may change if you boot from a different computer. Theoretically, there is a way to specify the partition by its ID but this doesn't work in Karmic.

A safer way is to do a regular install on to a stick, (just start installer and choose the stick, see Method 1 in [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)), boot from the stick, and add a user with encrypted home from a terminal:

sudo adduser --encrypt-home BankingDude

Then open /etc/fstab (gksudo gedit /etc/fstab),
disable swap by commenting out the swap line
(the one with ... swap sw ... in it)
and put /tmp into RAM by adding a line
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

You may also want to add noatime to the mount options of the "/" partition, to minimize flash wear.

---

### Post by John Bean on 2010-01-09
> **FuturePilot said:**
> Most (all?) of the software on the live CD is from the main repository which has some pretty strict review processes for any incoming software. It has been looked over by many people. The chances of something like that happening are pretty low. As of now I am not aware of anything like that happening before.

No? Google "Ken Thompson and the Self-Referencing C Compiler" ;-)

Now if Thompson had been one of the baddies and hadn't published his "back door" would anyone have discovered it?

Sure you say, that was Unix not Linux. But Thompson's code - complete with back door - was open to all inside the original Unix project, yet nobody was aware of it.

Incidentally: IMO anyone paranoid enough to worry about Thompson's backdoor strategy in a modern well-maintained OS distribution needs to rethink whether any computer is safe enough to use at all.

---

### Post by running_rabbit07 on 2010-01-09
> **John Bean said:**
> Incidentally: IMO anyone paranoid enough to worry about Thompson's backdoor strategy in a modern well-maintained OS distribution needs to rethink whether any computer is safe enough to use at all.

Word.

---

### Post by FuturePilot on 2010-01-09
> **John Bean said:**
> No? Google "Ken Thompson and the Self-Referencing C Compiler" ;-)

Now if Thompson had been one of the baddies and hadn't published his "back door" would anyone have discovered it?

Sure you say, that was Unix not Linux. But Thompson's code - complete with back door - was open to all inside the original Unix project, yet nobody was aware of it.

Incidentally: IMO anyone paranoid enough to worry about Thompson's backdoor strategy in a modern well-maintained OS distribution needs to rethink whether any computer is safe enough to use at all.

I am no longer not aware of anything like that happening before. ;)

---

### Post by perrabyte on 2010-01-09
A regular or hard drive install on a USB device can be made safe since the target computer need not be the one you install from. If you install the 32-bit version of Ubuntu from a computer you don't normally use (could even have its hard drives removed) on to a USB-device with the boot loader on it you could just move that device to the target computer after the install. This is if you don't install some 3:rd party drivers for graphics.

This means you can ask your local Linux friend to make a hard drive (regular) install with some tweaks on a USB-device with no risk to your computer. 

If you only use it occasionally, flash wear should not be a problem.

---

### Post by running_rabbit07 on 2010-01-10
The down side to that is that older systems don't allow USB booting. I just gave a copy of a LiveCD to a relative in from Canada that is using another relative's system to check his mail and such. Now he can boot her system without worrying about leaving any unwanted info on the host system.

---

### Post by rookcifer on 2010-01-10
> **John Bean said:**
> No? Google "Ken Thompson and the Self-Referencing C Compiler" ;-)

Now if Thompson had been one of the baddies and hadn't published his "back door" would anyone have discovered it?

Sure you say, that was Unix not Linux. But Thompson's code - complete with back door - was open to all inside the original Unix project, yet nobody was aware of it.

Incidentally: IMO anyone paranoid enough to worry about Thompson's backdoor strategy in a modern well-maintained OS distribution needs to rethink whether any computer is safe enough to use at all.


Thompson was also a Turing award winner -- a *bona fide* genius.  Nonetheless, this sort of trick can be used by someone working at M$ or Apple or Adobe.  Just because there is an official logo and company name behind software does not mean it's safer than open-source or that the developers are inherently good.  So while Thompson's backdoor is insidious and almost impossible to detect by the mere reviewing of source code (one would have to review machine code by using an independently written disassembler to catch it), we all have to put a level of trust into software.  And if we don't trust software, we have to trust CPU microcode and firmware.

---

### Post by running_rabbit07 on 2010-01-10
> **rookcifer said:**
> Thompson was also a Turing award winner -- a *bona fide* genius.  Nonetheless, this sort of trick can be used by someone working at M$ or Apple or Adobe.  Just because there is an official logo and company name behind software does not mean it's safer than open-source or that the developers are inherently good.  So while Thompson's backdoor is insidious and almost impossible to detect by the mere reviewing of source code (one would have to review machine code by using an independently written disassembler to catch it), we all have to put a level of trust into software.  And if we don't trust software, we have to trust CPU microcode and firmware.

MS doesn't have to place back doors. Just read the EULA for installing Windows, they have unlimited access to your system.

---

### Post by petelx on 2010-01-10
Well, you guys have given me a lot to look at and consider.  USB might be the only option for getting the security updates.  I'm not sure how I would turn the write protect on and off at will.  If it's too easy to do so, then a hacker could do it too.

I thought about putting extra stuff on the CD before burning it, but not much point considering you can't update read-only media.

With my XP CD, I made an image and was able to apply the updates and service packs and then reburn the image to the CD.  Then, when I did a fresh install, updates were already applied.  I can't remember how I did this exactly.  I think maybe Bart PE was invovled.  Anyway, I guess there's not a way to do this with ubuntu.  

Does ubuntu support a version of Adobe Acrobat reader so that I can read PDFs or will I have to add that in?

Thanks again for taking time to read and answer my questions.   It's very generous of you guys to offer your time and advice.  I'm sure I'll post later once I play around with this some more.

Pete

---

### Post by mkvnmtr on 2010-01-10
You are on the right track. I use Puppy Linux for banking with the firewall engaged because it is lighter than Ubuntu. Mostly from the live disk but I also have a ISO mounted to use in a virtual box. Nothing is written to the disk of the virtual machine unless I wish to save it. The ISO boots just like a CD disk and runs in memory.I am on a Ubuntu system but you can do the same on a windows system with virtual box. While I trust Ubuntu much more than Windows I would never put anything important to me on a computer.

---

### Post by FuturePilot on 2010-01-10
> **petelx said:**
> 
With my XP CD, I made an image and was able to apply the updates and service packs and then reburn the image to the CD.  Then, when I did a fresh install, updates were already applied.  I can't remember how I did this exactly.  I think maybe Bart PE was invovled.  Anyway, I guess there's not a way to do this with ubuntu.
Actually you can do this with Ubuntu with something like [UCK]("http://uck.sourceforge.net/") but it's easiest done from an existing install.

> Does ubuntu support a version of Adobe Acrobat reader so that I can read PDFs or will I have to add that in?


Ubuntu comes with a PDF viewer called Evince. But there is also a Linux version of Adobe Reader as well, installable from the Partner repository.

---

### Post by petelx on 2010-01-11
> **steveneddy said:**
> Order the CD directly from the Ubuntu site to take the element of a back door root kit out of the equation.

If I did this, for how long do you think I would be able to apply updates before having to order another CD?  Couple years?

---

### Post by petelx on 2010-01-11
> **DZ* said:**
> There is a "checkbox" to enable encrypted home during the installation.

However, this works best with an internal drive, because checking this option automatically enables encrypted swap as well. With a USB stick, the swap partition name specified in /etc/crypttab (e.g. /dev/sdb3) may change if you boot from a different computer. Theoretically, there is a way to specify the partition by its ID but this doesn't work in Karmic.

A safer way is to do a regular install on to a stick, (just start installer and choose the stick, see Method 1 in [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)), boot from the stick, and add a user with encrypted home from a terminal:

sudo adduser --encrypt-home BankingDude

Then open /etc/fstab (gksudo gedit /etc/fstab),
disable swap by commenting out the swap line
(the one with ... swap sw ... in it)
and put /tmp into RAM by adding a line
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

You may also want to add noatime to the mount options of the "/" partition, to minimize flash wear.

By my thinking, a read-only media like a CD is safter from hacking, but more vulnerable to exploits from a hacker who is able to get access to my PC while I'm actively using it and using system memory.  The USB should help me to upgrade security loopholes, but then I have writeable media that a hacker and plant something on for further evil doing.  

Hmm... if I want the protection of updated security patches then a LiveCD isn't the best.  I'd like to install to USB with the least amount of 3rd party software.  When I tried to install to USB from the liveCD I didn't see an option for it.  It just asked me about repartitioning my hard drive.  Maybe I can just use my Nero or Driveimage to write the ISO onto the USB.   In terms of speed, how fast does the OS run from USB verses from a Hard Drive?

BTW, I actually have a WIRED router and a wireless router that plugs into the wired router.  Booting up into ubuntu, I could plug directly into the wired router and unplug the wireless so, to my understanding, I would not be using my LAN at all.  ?   If my XP booted PC is compromised and my Lan is compromised, does that mean that a hacker could gain access to my ubuntu liveCD booted OS?  Wouldn't that be inaccessible, especially if I plug in for internet access rather than use the wireless?

---

### Post by petelx on 2010-01-11
> **FuturePilot said:**
> Actually you can do this with Ubuntu with something like [UCK]("http://uck.sourceforge.net/") but it's easiest done from an existing install.


Hmm.. I'll look into it. Thanks.

> 
Ubuntu comes with a PDF viewer called Evince. But there is also a Linux version of Adobe Reader as well, installable from the Partner repository.

Sweet.  I'll try it out.  Hell, I might just run this as my regular OS.   Nice OS!

---

### Post by HermanAB on 2010-01-11
Howdy, 

It has been said that you are not paranoid, if they really are out to get you.  

I do think however that you seem to be too paranoid about the wrong things...

I'd suggest that you install Ubuntu with an encrypted home directory so that your bank data is safe if the machine gets stolen, make regular backups to an encrypted USB disk and then relax and enjoy your nice, secure, safe Ubuntu system.  

Running off a CDROM is commendable, but not necessary and not necessarily any better, since you cannot update it, so long term, a normal HD installed system is likely more secure.

---

### Post by tubbygweilo on 2010-01-11
Running from a live cd is IMHO a far greater chore than running from a fully patched, full disk encrypted machine guarded by a well chosen pass-phrase and a good long user password but YMMV.

---

### Post by running_rabbit07 on 2010-01-11
I think have seen enough threads from people who's decrypting stopped working and they lost their data to keep me from doing that. Just do a regular install and utilize private browsing.

---

### Post by DZ* on 2010-01-11
> **petelx said:**
> When I tried to install to USB from the liveCD I didn't see an option for it.  It just asked me about repartitioning my hard drive ....   In terms of speed, how fast does the OS run from USB verses from a Hard Drive?

I do my installs with the text-based iso aka "alternate CD", but I assume the menu is similar: the entry is called something like "use entirre disk - guided partitioning". From there you will see hard drives as sda, sdb (if there are 2 drives). sdc would be unlisted installation stick; and sdd would be the USB flash memory (it would in fact say that it is USB flash and list the size of the disk as well - so that you'd have an idea that this is the correct drive judging by its size).

The speed of a flash USB with encrypted home is very good. In fact, I found the boot time being slightly faster than that from the hard drive (but do add noatime to mount options in /etc/fstab).  Full-disk encription with flash will be too slow.

---

### Post by DZ* on 2010-01-11
> **running_rabbit07 said:**
> I think have seen enough threads from people who's decrypting stopped working and they lost their data to keep me from doing that. Just do a regular install and utilize private browsing.

It is very convenient to have data on a stick encrypted. If data is regularly backed up, there is no problem, esp. with per-account encryption: just recreate a user if something goes wrong there.

My wife has a full-disk encrypted laptop (overkill, but never failed since I first installed the newly arrived 8.04) and a netbook with encrypted home (ecryptfs).

I use Ubuntu exclusively on external drives: on a 16G stick and on a external 320G "Passport" harddrive. Both have encrypted home accounts (ecryptfs). The Passport drive worked flawlessly since I put Hardy on it, although at that time I used manually luks-encrypted home, swap, and tmp partitions. I got the stick later, but it's been awhile too and it's been serving well.

We haven't experienced problems of any kind with encryption yet. However, I backup data with rsync at least weekly on to two identical encrypted external harddrives.

---

### Post by petelx on 2010-01-11
> **HermanAB said:**
> Howdy, 

It has been said that you are not paranoid, if they really are out to get you.  

I do think however that you seem to be too paranoid about the wrong things...



A fair criticism, but regarding the "right" things are you implying that I have left some out?

---

### Post by petelx on 2010-01-11
Special thanks to you chrisinspace for your detailed response.  

> **chrisinspace said:**
> petelx,

You are definitely on track with your thinking.  I actually read an article in the Washington Post recently on the topic.  It was written by a security expert who was advocating just this approach.  You might want to check it out:

[http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html](http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html)



Good article.  I actually read it before this thread.  It's one of the things that got me thinking about ubuntu.  

> 
[snipped]
7. You can install the available updates, but when you leave the session, the changes will not stick.  You would have to re-compile the cd for that.  You could use RemasterSys for that.  I'll go into that software a little more at the end because I think it will apply to a couple of your questions.

8. Again, a live cd is not re-writable, so nothing can permanently install to the disk.  Also, 99% of such malware is written for Windows, so chances are, if it got into your system, it wouldn't affect it.

9 and 10.  I'm not sure about hardened kernels, but RemasterSys can help you create a custom live cd.  I actually made one for some of our bank's more tech-savvy customers.  I stripped out all of the unnecessary software, cleaned up the interface, and branded it with our logos.  It worked great.  Check it out:
[LIST]
[*][http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
[*][http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html) - tutorial
[/LIST]
There is also more about it in the forums.  Sounds like it might be exactly what you are looking for.



I'm still mulling over the RemasterSys application.  It sounds like what I'm looking for.  It would be nice to add a few tweaks to the basic image before writing it to CD or USB.  Either way I'd make a image of the OS (true image) and keep it on hand.

The other thing I'm trying to do is keep the amount of software to a minmum.  The more 3rd party stuff I use, the more potential for hacked software and the greater the chance of some hacker finding an exploit.

Anyway, thanks for the long post.  I'm still looking into it.

---

### Post by petelx on 2010-01-11
> **perrabyte said:**
> A regular or hard drive install on a USB device can be made safe since the target computer need not be the one you install from. If you install the 32-bit version of Ubuntu from a computer you don't normally use (could even have its hard drives removed) on to a USB-device with the boot loader on it you could just move that device to the target computer after the install. This is if you don't install some 3:rd party drivers for graphics.

This means you can ask your local Linux friend to make a hard drive (regular) install with some tweaks on a USB-device with no risk to your computer. 

If you only use it occasionally, flash wear should not be a problem.

I was reading about that and the "persistent partition".  

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
(under method 1)
**Note:**  *This will use the USB drive for /tmp, which will cause extra wear on the flash memory. If you're booting from a system with enough RAM, it would be more desirable to use a tmpfs in RAM for /tmp, in which case you'd want to copy the ISO CD image to the USB drive and add a persistent partition (see next section). On the other hand, if you're not concerned with your USB drive wearing out (lifetime warranty, wear leveling, etc), continue in this section.*

How much system RAM is enough for a bare bones install of Ubuntu?  Without the persistent partition, what kind of life can I expect out of the flash drive?  Say I use it 15 hours a year.  So, if I understand correctly, the persistent partition method still means everything is contained on the flash drive, but with the PP the hardware system RAM will be used..... as opposed to a swap file created on the USB drive?

---

### Post by petelx on 2010-01-11
> **tubbygweilo said:**
> Running from a live cd is IMHO a far greater chore than running from a fully patched, full disk encrypted machine guarded by a well chosen pass-phrase and a good long user password but YMMV.

So if I put it the OS on a bootable USB (with no HD support) I could encrypt the whole flash drive and password protect it?  Others were talking about encypting the home files, but does ubuntu support encrypting everything?  Would this protect from being hacked while I'm logged on and using the OS to browse the internet?  Or, would this only be useful if someone found or stole the USB flash drive and was trying to break in?  

I could keep a backup of the image on a DVD in case something got corrupted or lost.  Again, because I'd only be using the USB for limited purposes and for a limited time, I wouldn't need much or any customizing beyond security patches so it's not like I'd have to always be making new images and storing them.  At the same time, if something got corrupted, no big deal.  Just get my DVD and reburn to the USB flash drive.

---

### Post by petelx on 2010-01-11
> **DZ* said:**
> I do my installs with the text-based iso aka "alternate CD", but I assume the menu is similar: the entry is called something like "use entirre disk - guided partitioning". From there you will see hard drives as sda, sdb (if there are 2 drives). sdc would be unlisted installation stick; and sdd would be the USB flash memory (it would in fact say that it is USB flash and list the size of the disk as well - so that you'd have an idea that this is the correct drive judging by its size).

The speed of a flash USB with encrypted home is very good. In fact, I found the boot time being slightly faster than that from the hard drive (but do add noatime to mount options in /etc/fstab).  Full-disk encription with flash will be too slow.

Thanks.  I can't believe I missed that option for the USB.  I tried installing it on a 2 gig flash drive, but it told me I didn't have enough room, so I just ordered a 4gig drive oline.  I'm debating the persistent partition.  If encryption only helps me in cases where the USB is stolen, then it's not much use to me.  If I go with USB, I'd only use it for short online sessions and for patches/upgrades.  Other than that it would be physically removed from the comptuer at all times.  I might even download the patches with my regular windows OS then apply them to the flash drive.   I don't really understand the tweaks like noatime, but I'll look into it.  Thanks for the tips.

---

### Post by HermanAB on 2010-01-12
```
rob@rob:~$ telnet localhost 8118
Trying 127.0.0.1...
Connected to rob.
Escape character is '^]'.

Hangs, no response, closed with CTRL-C
```

Good!

The above means that your socks connection works.  The problem is with your Firefox configuration.

---

### Post by petelx on 2010-01-12
Sorry to SPAM post you guys.  ha ha.

One last idea.  Why don't I just create the OS on USB flash drive, tweak it how I want it, and then apply the most recent security updates.  Next, use something like True Image to make an image of the flash drive.  Move the image to a DVD.  Use the USB OS as needed upgrading the security patches from time to time.  Every so often I start over with the DVD image.

The more I think about it there's really no reason to alter the ISO before mounting it.  I can install the OS and tweak it all offline.  I assume I could even patch it offline with patches I downloaded previously.

---

### Post by chrisinspace on 2010-01-12
> **mkvnmtr said:**
> You are on the right track. I use Puppy Linux for banking with the firewall engaged because it is lighter than Ubuntu. Mostly from the live disk but I also have a ISO mounted to use in a virtual box. Nothing is written to the disk of the virtual machine unless I wish to save it. The ISO boots just like a CD disk and runs in memory.I am on a Ubuntu system but you can do the same on a windows system with virtual box. While I trust Ubuntu much more than Windows I would never put anything important to me on a computer.

Man, we are diving headfirst down the security rabbit-hole.  This is a good, multi-layered approach.  If you used this method, you get the security benefits of the live cd combined with virtualization, plus you don't have to reboot every time you want a secure session.  All you do is fire up VirtualBox.

---

### Post by petelx on 2010-01-12
[COLOR=Red]Hey all, I just installed ubuntu on USB to test it out.  Turns out, I can't boot to my hard drive any more.  It keeps trying to load GRUB.  

I used Acronis True Image Home 2009 to restore an old image of my primary partition which it apparently did.

As many of you may have guessed, that didn't effect GRUB  I need to remove linux from the boot sector so can access my hard drive with XP.   It's too bad I had to write over my primary, but the other partitions contain data that I'd be more concerned about losing.

I found a few fixes online, but I'm not sure if my logical drives will be safe if I do anything experimental.  Track record isn't so good right now...

I'm sure this isn't the first time a dumass like me has done this.  Could someone please link me to a solution for removing GRUB from my boot sector so I can use my hard drive again with XP?  I never did install ubuntu on my hard drive, just the USB.

Thanks!
[/COLOR]

---

### Post by petelx on 2010-01-13
> **petelx said:**
> [COLOR=Red]Hey all, I just installed ubuntu on USB to test it out.  Turns out, I can't boot to my hard drive any more.  It keeps trying to load GRUB.  

I used Acronis True Image Home 2009 to restore an old image of my primary partition which it apparently did.

As many of you may have guessed, that didn't effect GRUB  I need to remove linux from the boot sector so can access my hard drive with XP.   It's too bad I had to write over my primary, but the other partitions contain data that I'd be more concerned about losing.

I found a few fixes online, but I'm not sure if my logical drives will be safe if I do anything experimental.  Track record isn't so good right now...

I'm sure this isn't the first time a dumass like me has done this.  Could someone please link me to a solution for removing GRUB from my boot sector so I can use my hard drive again with XP?  I never did install ubuntu on my hard drive, just the USB.

Thanks!
[/COLOR]
Found solution from Irony in a different ubuntu forum.  Hey, I did say [COLOR=Red]**NOOB**[/COLOR] journey.  post back later...

 				 				**Re: How do I delete the grub boot loader from the Master boot record?** 			
 			 			 		   		 		 		Boot from XP installation disc > press any key on prompt to boot from CD > after some time options appear, press R for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc

---

### Post by petelx on 2010-01-13
Well guys, I just tested out the ubuntu on a flash drive.  Right after updates, it took 4 minutes to get to the selection screen and 4 more to reach desktop.  I assume it gets faster after that, but by then I was dealing with the boot sector problem and not being able to boot into my regular XP OS.

Overall, I'm impressed with how slick and full featured ubuntu is.  The community has really done a nice job.  Drivers supported all my hardware except the printer.  It's actually far more than what I need for my purposes which is actually a detriment for my purposes.  

I'd think I'd like it better if I had a stripped down version like chrsinspace was talking about.  I'm actually surprised there isn't a market for this.  Some kind of bare minimum highly secure OS used exclusively for banking or stock trading with applications and features that are only doing the task at hand.  Maybe you could even couple it with some kind of phone-in password confirmation or something that would otherwise require a non-computer/internet transaction to complete the log in.   Make it as tiny as possible with the code as clean and tight as possible so that it could be downloaded quickly and installed to a CD or USB quickly and easily by the greenest users.  Something banks or stock trading companies could put out to their customers directly.  Ah, but what do I know.  

I'm still playing with ubuntu, but as you can see it's been a steeper learning curve than I expected.   Upon first install I had to do 181 download patches.  181!  Now, I don't know how many of these had to do with security.  All I would want is to update firefox and the OS itself.  Even so between that and Grub and everything else I don't fully understand, I'm looking at windows in a new light.  Windows is the Devil I Know.  I don't think I'd feel comfortable using ubuntu unless I get more familiar with it and I'm not sure I have the time to get to know it.  A liveCD would have been one thing, but the plate just keeps getting fuller.

Frankly, it's one big pain in the butt to get the peace of mind I'm looking for just to log on a few times a year to check and bookkeep my accounts.  I might just resign myself to do all my banking offline and off the computer.  

I think I achieved what I wanted to do with this thread, which is get a concept for what I need to do.  I now have to study up on the details.

You guys have really been very helfpul and I will keep playing with ubuntu and weighing my options.  I appreciate your time, advice, and effort to help answer my noob questions. 

Thanks!

---

### Post by petelx on 2010-01-13
> **chrisinspace said:**
> Man, we are diving headfirst down the security rabbit-hole.  This is a good, multi-layered approach.  If you used this method, you get the security benefits of the live cd combined with virtualization, plus you don't have to reboot every time you want a secure session.  All you do is fire up VirtualBox.

I see the value of this, but I'd only be using the OS periodically so I don't mind rebooting.  I've even considered investing in a nettop to use just for banking.  I don't mind if it cumbersome to use or boot, I just want it secure.  If I can throw money at it rather than invest a lot of time learning new software and the pitfalls of same, then money I will throw.

---

