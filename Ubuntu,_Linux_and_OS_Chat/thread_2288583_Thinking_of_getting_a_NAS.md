---
title: "Thinking of getting a NAS"
date: 2015-07-28
forum: Ubuntu, Linux and OS Chat
---

### Post by GrouchyGaijin on 2015-07-28
Hi Folks,

I am running Ubuntu 14.04 on two laptops and Xbuntu 14.04 on a third laptop.
I am seriously considering buying a NAS box. Has anyone used the Western Digital My Cloud?
If so, what was your experience?  How easy is it to save files from an Ubuntu machine and then access those files remotely over the Internet?
I found this review which does not mention Linux:
[http://www.pcworld.com/article/2051347/wd-my-cloud-review-a-better-more-secure-alternative-to-cloud-storage.html](http://www.pcworld.com/article/2051347/wd-my-cloud-review-a-better-more-secure-alternative-to-cloud-storage.html)

I did find a couple of posts online that say "The shares can be mounted in Linux either via CIFS (SMB) or NFS.", but I really am not sure what this means.

---

### Post by pfeiffep on 2015-07-28
[COLOR=#ff0000]**"Has anyone used the Western Digital My Cloud?"**[/COLOR]
Earlier this year I purchased a 3 TB Western Digital My Cloud along with a 4 TB Western Digital My Book Studio. I was apprehensive about using commercial cloud services to back up my computers and decided to take it all inside my home. I use the 4TB unit to create safepoints of the data on My Cloud. I used an internet browser to connect to My Cloud's dashboard from an Ubuntu 14.04 installation (WD's software is NOT required).
I have successfully backed up:
     2 Ubuntu installs
     2 Windows 7 installs
     1 Mac Book Pro
I intentionally disabled Internet access from outside my home.

---

### Post by GrouchyGaijin on 2015-07-28
Sounds great - how did you mount the My Cloud from the Ubuntu machine?  Did Ubuntu see it on the network automatically and could you transfer files via the file manager or did you need to use FTP?

---

### Post by Dave_Rove on 2015-07-28
I've just got the 3TB version, and I'm really pleased with it. It's small and very power frugal, barely getting warm despite having no fan, and consumes about 4W when the disk spins down when it's not being used. I'm using a CIFS share (a.k.a SMB, the most common NAS share method) which is easy to mount permanently in Ubuntu (Google: Ubuntu CIFS mount), but no doubt you can browse to it via the file-manager's built-in network explorer as a test. (It also has NFS, but I've not bothered with that because I prefer a lack of uid/gid file ownership for NAS files which makes it easy to access from different accounts.)

It runs a full Debian Linux as its OS, so Linux users will want to enable SSH to access it via the command line too.

Edit: It also has a "Cloud Storage" remote access feature where it will backup stuff to a WD server somewhere on the Internet, and you can access that from anywhere apparently, although I've not enabled that. I understand that its downside is that the upload of very large files takes so long that the disk rarely spins down, so I prefer to back it up to a USB3 drive every few weeks. In principle, you could access your NAS from the Internet by setting up port-forwarding in your Internet router but be careful of the security (so use a high-numbered port and Google: port forwarding security risks).

---

### Post by Bucky Ball on 2015-07-28
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by GrouchyGaijin on 2015-07-28
Thanks Guys,

I think I'm going to buy one.  I'm sure you will hear back from me if I have problems.

---

### Post by howefield on 2015-07-28
I bought the 2TB version to replace its predecessor, an 8 year old My Book Live. Both are great drives and are cool and quiet. 

As Dave_Rove mentioned above, accessing files is easy enough via the (U)buntu file manager or mount permanently in fstab and the web interface to administer the drives settings doesn't care what operating system you are on. :)

---

### Post by GrouchyGaijin on 2015-07-28
That is definitely good news.  Have you guys been able to share files with people not on the same wi-fi network?
Basically, I live in Sweden and want to share stuff with family in the US.  I've been using Dropbox, but would like to ween myself off of services like that.

---

### Post by Lars Noodén on 2015-07-28
If you can forward an outside port to your NAS and it supports SSH (and thus SFTP) then you can access it from anywhere in the world.  There are dedicated graphical clients like CyberDuck, WinSCP, and FileZilla, but the regular run of the mill file managers like Nautilus support SFTP, too.  You might just want to have a dynamic DNS hostname so that you can find the machine regularly, if your ISP does not give you a static IP.

---

### Post by andrew.robbins.fli on 2015-08-03
I have been using the WD My cloud device and it works really well. The webclient is used to setup shares and sharers as they call directories and users, and the PC app is used to view/edit/save/download your files. FTP is fast and works well, and filezilla works like a charm with WD mycloud.

---

### Post by GrouchyGaijin on 2015-08-03
Hey Guys,

Thank you for all of the replies.  I have just a couple of follow up questions.  I was almost ready to pull the trigger and order one when I noticed some reviews on the website where I was going to purchase the NAS.  A couple of users complained about terrible transfer speeds.  I then looked for additional reviews and came across a recurring theme at Amazon.  It seems that, at least among people who bought from Amazon, that the drives would die after several months to a couple of years, in any case not a long time.

So my questions to you guys are:

How is the connection speed from your PC to your NAS over your wifi network? (I realize that each person's experience will be different and that the problem could be the network and have nothing to do with the NAS.)  How are the drives holding up for you?  Have you had any issues?  Finally, based on your experience, would you purchase another WD My Cloud?

Thanks again, I truly appreciate the advice.

---

### Post by pfeiffep on 2015-08-04
> **GrouchyGaijin said:**
> Hey Guys,
<snip>
Thanks again, I truly appreciate the advice.
[COLOR=#ff0000]How is the connection speed from your PC to your NAS over your wifi network?[/COLOR] I have setup MC for a backup solution for my home devices as well as a shared data store (Ubuntu, Windows 7, and Mac). I don't use it for streaming media. I set auto safepoint creation for 1am when we're all asleep. When accessing the shared data I find the initial access in a day response somewhat slow, subsequent access is exactly what I expect. I have 3 devices connected via wifi and 2 devices hard wired to my router. I notice a delay even on the wired devices when first accessing which indicates to me that the device might have been asleep. The device is entirely workable for my situation.

[COLOR=#ff0000]How are the drives holding up for you?[/COLOR] I'm quite happy with WD, I purchased from them recertified drives in March of this year and have had absolutely no problems wrt hardware.

[COLOR=#ff0000]Have you had any issues?[/COLOR] The software running on the MC is a bit slow responding sometimes, probably because it is in a sleep mode. When I manually create a safepoint the software is slow to indicate success. The time reported for completion on auto safepoint creation indicates a time discrepancy within the MC (once identified it's not an issue). The error code reporting is not documented very well, and engineering could not or would not address my questions - customer support then extended my 90 day warranty (recertified devices on have 90 days) to 1 year. The error codes were all related to safepoint creation and failures - this has not been a major problem and has since not been a problem for the last 2 months.

[COLOR=#ff0000]Finally, based on your experience, would you purchase another WD My Cloud?[/COLOR] yes

---

### Post by howefield on 2015-08-05
> **GrouchyGaijin said:**
> How is the connection speed from your PC to your NAS over your wifi network? (I realize that each person's experience will be different and that the problem could be the network and have nothing to do with the NAS.)  How are the drives holding up for you?  Have you had any issues?  Finally, based on your experience, would you purchase another WD My Cloud?

Both wired and wireless speeds are awful, but adequate enough for my workload. That's not to say they are significantly worse than comparable products but no point in giving you examples, as you say - each network is different and comparative speeds are easily enough found elsewhere.

No issues except for being peeved that there is no remote access app for linux (there is for windows and mac). That isn't a problem as there are other ways of course, but given the extensive use of linux in the product, seem to me that linux should be a first class citizen in every regard.

I did buy another, got 8 years out of my My Book Live edition and probably shortened the life of it at the end after a period of power outages and finally a lightening strike, if I get as long out of this one, I'll be happy. Looks good, works well and the price was right.

---

