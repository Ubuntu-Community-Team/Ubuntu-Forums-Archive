---
title: "My enormously fun day with Cryptolocker"
date: 2013-11-21
forum: The Cafe
---

### Post by estamets on 2013-11-21
Oh it was a hot damn blast.. A day at six flags doesn't even compare to this much fun.

It all started when someone decided to open a email attachment claiming that they have a voicemail on their phone and if they click the link, they can hear it. That was about 11:45 am on Tuesday. 

I get back to my desk at noon to eat lunch and listen to my voicemail-- On the actual phone, not through email. With a statement like, "This thing says I have 100 hours to pay 300 dollars in bitcoins? Then my files will be usable again? It changed my wallpaper, I like it and want it back.

Yes.. All that stated and they are worried about their wallpaper.

Then I saw what I've been fearing since I caught wind of it. That's when I encountered a virus that I (to date) was actually afraid of.

In the 15 minutes between the attachment executing and when I got my voicemail.. This bad boy had made most of our server side excel and word docs unreadable due to file encryption. Not only those but PDF's and god knows what else.. But, our CNC programs and accounting software was still functional because they're on a different server AND they don't have file extensions. They're just "files".

I begin searching this thing out on Bleeping Computer, US-CERT and whatever else.. Yeah, they all say the same thing. Even to this day they say it. I'll summarize for those who don't know, either risk it and pay the fine and assume criminals aren't lying to you OR restore from backup.

We sucked it up and restored from a backup tape and basically lost a day electronically. That and our file server is running Ubuntu 12.04 server and our other two servers - wait - We did have only two, now 2 servers are running Server 2008 R2 and 1 on Ubuntu.

That was roughly 36 hours ago, this is my first night home. After restoring from tape.. Installing 12.04 on our "useless" old MS Server 2004 with ONLY 16Gig of Ram, preserving what I could with regard to file structure everyone would be used too (Folder names etc..), creating a script that'll map the drives on log in and making sure our 2008 servers will see the new file server. I'm done.

Vent over.

---

### Post by Jonor on 2013-11-21
This Cryptolocker thing did stir me into resuming USB thumbdrive backups which have otherwise been gathering dust, in case a Linux version appears, it wasn't that long ago since the failed Hand Of Thief trojan.

---

### Post by estamets on 2013-11-21
Certainly worth a shot.. Anything that prompts someone to backup is good. However, as stated in the sequence of events, the issue didn't ultimately rest with the computer... It was with the user.

I will say though that how it was crafted and the fact that it appeared to be from our own domain, didn't help with the whole "user error" argument. No fault specifically, I mean, I know how it looked to the user.. We do have Kylin now, who knows.. Might be a backdoor already.

---

### Post by Erik1984 on 2013-11-22
Creepy stuff. It does make you think about samba shares in the network. I plan to use a Raspberry Pi as backup server on the local network. However if I let Windows PCs write to the Samba shares (they have to to be able to make backups) the files inside the share can easily be cryptolocked by malware on any one of the Windows PC. So maybe I should make a separate directory on the backup drive (not shared with the network) to occasionally mirror all files in the samba shares to. Also if you have your Dropbox synced with Windows PCs this can be dangerous. One infected Windows PC could cryptolock the dropbox folder and if you don't see it in time all paired devices will soon have the cryptolocked versions of files in their local Dropbox folders too. And the same applies to all cloud sync services that work like Dropbox (Ubuntu One for example).

---

### Post by mips on 2013-11-23
> **estamets said:**
> 
It all started when someone decided to open a email attachment claiming that they have a voicemail on their phone and if they click the link, they can hear it. That was about 11:45 am on Tuesday. 

In most companies I know of that will result in disciplinary action. People by know should know better than to click on arb attachments.

---

### Post by andyfied on 2013-12-03
I have had an unreasonable number of calls from various companies asking me to decrypt their files. (If anyone is wondering, it's probably not possible to do without a supercomputer and could still take centuries to decrypt.)

Well done for having a suitable back up system, even if it was horrible to get everything back the way is was. Still better than having nothing and folding the company (as I assume most of the people calling me did!)

---

### Post by estamets on 2013-12-03
Thanks Andy. Believe it or not, my "if it ain't broke" attitude may have helped.. We have a good old fashioned tape backup that unmounts itself when the backup is done to protect against power surges, that may have been the saving grace. The software is actually dos based and menu driven.. Think Midnight Commander.

Usually, Malwarebytes and various assortments of AV scanners fix most issues. Not this. I have noticed with the computers I clean outside of work.. Most people have EVERTHING in My Documents and normally a 20 dollar flash drive would back up most of it. The trick is, with cryptolocker, you can't have the drive plugged in at all at the time of infection. It's scary how many people don't have any sort of backup at all. Basically, back up, unplug, put in drawer.

This is only the beginning. The virus was executed with Admin privileges locally but on the domain side, it encrypted user shares that have read/write capablility via shared drives. So, I'm wondering now if my new file server with 12.04 would have prevented this at all. Was it able to infect our server side shares BECAUSE it's Server 2008 OR was it just because it had .xls and .doc extensions on a file system the user had read/write access to?

I may set up my own honeypot-ish mock up to see what happens because I'm not sure if I've read anything about that aspect.

---

### Post by Erik1984 on 2013-12-04
> **estamets said:**
> Thanks Andy. Believe it or not, my "if it ain't broke" attitude may have helped.. We have a good old fashioned tape backup that unmounts itself when the backup is done to protect against power surges, that may have been the saving grace. The software is actually dos based and menu driven.. Think Midnight Commander.

Usually, Malwarebytes and various assortments of AV scanners fix most issues. Not this. I have noticed with the computers I clean outside of work.. Most people have EVERTHING in My Documents and normally a 20 dollar flash drive would back up most of it. The trick is, with cryptolocker, you can't have the drive plugged in at all at the time of infection. It's scary how many people don't have any sort of backup at all. Basically, back up, unplug, put in drawer.

This is only the beginning. The virus was executed with Admin privileges locally but on the domain side, it encrypted user shares that have read/write capablility via shared drives. So, I'm wondering now if my new file server with 12.04 would have prevented this at all. Was it able to infect our server side shares BECAUSE it's Server 2008 OR was it just because it had .xls and .doc extensions on a file system the user had read/write access to?

I may set up my own honeypot-ish mock up to see what happens because I'm not sure if I've read anything about that aspect.

I don't think the OS matters there. If you offer a writable network share then it's just that and any client with the right credentials (if the network folder is protected) can write to it (and mess it up by cryptolocking all files). I just can't see how Windows or Ubuntu as a server would make a difference here. Maybe the underlying filesystem on the server side could make a difference for recovery and 'undoing' the changes made by cryptolocker.

---

### Post by andyfied on 2013-12-04
I agree with everything Euroman says there. Also, rather than take the risk of playing with it you can check out this forum discussion:
[http://www.kernelmode.info/forum/viewtopic.php?f=16&t=2945](http://www.kernelmode.info/forum/viewtopic.php?f=16&t=2945)
And there is an interesting video of it in action here:
[http://blogs.sophos.com/2013/10/10/information-regarding-the-CryptoLocker-ransomware-trojan-making-the-rounds/](http://blogs.sophos.com/2013/10/10/information-regarding-the-CryptoLocker-ransomware-trojan-making-the-rounds/)

I read somewhere (sadly can't find the source) that one professional watched it waltz straight through Office 365's malware detection and start wandering the network. Any network storage or anything attached physically is at risk. Unmounted tape drives are perfectly fine of course :)

But then the best solution is not clicking on suspect email attachments... ;)

---

### Post by estamets on 2013-12-05
Thank you for the links everyone.. Watching the video IS a safer alternative. I don't know why I didn't find those myself.

---

### Post by Jonor on 2014-01-08
A [LiveLeak news item]("http://www.liveleak.com/view?i=dd6_1389171933") suggesting Cryptolocker is to be tweaked and remarketed as DIY ransomware called Powerlocker.

---

### Post by SCBrisbane on 2014-01-08
Does anyone know if Ubuntu client + wine is vulnerable to cryptolocker?

---

### Post by Erik1984 on 2014-01-08
> **SCBrisbane said:**
> Does anyone know if Ubuntu client + wine is vulnerable to cryptolocker?

In theory yes. **If** Wine has write access to certain files and Wine is able to run cryptolocker it could change (lock) those files.

---

### Post by cptrohn on 2014-01-08
I feel your pain,

We have had 3 seperate bouts of cryptolocker on our network.   Even after giving users extensive training on malware and what not to click on, AND even telling the users if you have ANY questions at all forward us the email so we can check it out.  really was a scary one, luckyicly we keep good backups as well.

---

### Post by corbin.loftis on 2014-01-19
I got scared about random people hacking my accounts and whatnot, and now every password I have (I went through and changed EVERYTHING) is at LEAST 256-bit encrypted. Emails and Facebook are 400-bit. My computer even uses a 256-bit password (that I have to remember), and has an encrypted home folder, with secure storage inside that for my financial records and stuff using Truecrypt. I'm not leaving anything to chance. Oh, and all my important stuff is backed up to contiguous RAID drives, because I've been the one to lose everything and have to start from scratch before... NEVER AGAIN.

---

### Post by Jonor on 2014-08-06
[Relief for Cryptolocker victims arrives.]("http://www.bbc.co.uk/news/technology-28661463")

---

