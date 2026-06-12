---
title: "Remote Backup question"
date: 2011-09-14
forum: The Cafe
---

### Post by hyperAura on 2011-09-14
Hi guys,

I have a server used for my business and I would like to save my data some place outside my business premises.
e.g. synchronizing the server files with my desktop pc at home during the night..

What is the best way to do that?

Is this possible? If yes, is it secure?

Thanks 

Hyper

---

### Post by CharlesA on 2011-09-14
rsync over ssh if your connection can handle it is pure win.

Otherwise look into cloud storage.

---

### Post by haqking on 2011-09-14
> **CharlesA said:**
> rsync over ssh if your connection can handle it is pure win.

Otherwise look into cloud storage.

+1

Secure rsync is a godsend.

Cloud....no comment ;-)

---

### Post by CharlesA on 2011-09-14
> **haqking said:**
> 
Cloud....no comment ;-)

Dropbox gets a +1 from me. ;)

---

### Post by hyperAura on 2011-09-14
Sorry for not posting this **SMALL **detail but the server is a Windows machine.

On desktop PC I have both Linux and Windows.

---

### Post by CharlesA on 2011-09-14
I wonder is Cygwin works with the windows file system. Hmm...

If that works, go the rsync route, otherwise you can sync to dropbox or whatever.

---

### Post by agillator on 2011-09-14
Is it possible? Absolutely. The are a number of ways to do it. I find I prefer rsnapshot. The config file can be a little tricky - tabs are required in places - but once you get that down it works well.

I suspect the problem you will face regardless of how you do it is the fact that you are going off site. This will mean you are limited in speed by your provider(s). A typical home DSL account is 1500 mbs download/384 mbs upload. I don't know what you have - cable, DSL, whatever, and I don't know what your business has, but the upload speed may be 384. If you are backing up gigabytes at a slow speed you may never get done. You might consider backing up on site to another media (NAS for example) and periodically copying to DVD and taking the DVD off site. Or, if you are backing less than a DVD will hold, backup directly to a DVD at night and every night take the previous night's DVD home/off site.

Edit: While I was writing you apparently posted that you are using Windows. rsnapshot may run on CygWin, I don't know - might be worth checking out.

---

### Post by haqking on 2011-09-14
> **CharlesA said:**
> I wonder is Cygwin works with the windows file system. Hmm...

If that works, go the rsync route, otherwise you can sync to dropbox or whatever.


there are SSH servers for windows.

Is it a corporate server ? and under your admin control ?

windows live mesh, dropbox, sftp are all options also

---

### Post by CharlesA on 2011-09-14
How does rsnapshot differ from rsync?

---

### Post by haqking on 2011-09-14
> **CharlesA said:**
> How does rsnapshot differ from rsync?


it is based on rysnc and uses rsync doesnt it ?

---

### Post by agillator on 2011-09-14
I see some are suggesting DropBox or whatever. My two cents worth, if it is worth that much: I am old fashioned. If I am backing up data I want secured I would NOT put it in someone else's control even though they insist it is encrypted, etc., etc. THEY screw up once and you are screwed and have no control over it. Too many hacking incidents, etc. I would absolutely keep everything in the backup chain under my personal control. But then that is just paranoid me.

---

### Post by Paqman on 2011-09-14
> **CharlesA said:**
> 
Otherwise look into cloud storage.

I've looked at this. Seriously expensive if you're talking about any real quantity of data. It could be worth it if it's critical data for your business, but I was looking at it for personal use. Ouch.

---

### Post by hyperAura on 2011-09-14
what is a corporate server? 

I am using an HP ML ProLiant tower server (small business)..

The amount of data so far is around 60GBs..

and the connection speed is DSL 2Mbps on both ends..

---

### Post by agillator on 2011-09-14
CharlesA: rsnapshot uses rsync and an ssh tunnel. 

hyperAura: With those speeds going directly off site might not be a problem. My comment about control still applies, though. I'm not sure what is available for Windows, but I THINK rsynch will work through CygWin on Windows. If so you can do it yourself if rsnapshot can't do it for you.

---

### Post by haqking on 2011-09-14
> **hyperAura said:**
> what is a corporate server? 

I am using an HP ML ProLiant tower server (small business)..

The amount of data so far is around 60GBs..

and the connection speed is DSL 2Mbps on both ends..


I just meant one used in a business (corporate ) environment.  I see from your OP it is, but im assuming small scale.

I was asking incase there was a sys admin and IT dept to deal with and not just yourself that was all.

You want to sycn 60GB daily remotely to your home machine ?

**why dont you stick in a USB HDD and have a copy of the data on there and take it home everynight ? under your control and no bandwidth issues or syncing problems**

---

### Post by CharlesA on 2011-09-14
> **agillator said:**
> I see some are suggesting DropBox or whatever. My two cents worth, if it is worth that much: I am old fashioned. If I am backing up data I want secured I would NOT put it in someone else's control even though they insist it is encrypted, etc., etc. THEY screw up once and you are screwed and have no control over it. Too many hacking incidents, etc. I would absolutely keep everything in the backup chain under my personal control. But then that is just paranoid me.

I'd prefer doing a "hard backup" with physical media stored in an offsite location but convenience vs security is a compromise.

> **Paqman said:**
> I've looked at this. Seriously expensive if you're talking about any real quantity of data. It could be worth it if it's critical data for your business, but I was looking at it for personal use. Ouch.

Indeed. They can get insanely expensive.

Also +1 to external drive.

---

### Post by hyperAura on 2011-09-14
ok let's say I use rsync through cygwin..

how can I connect one end to another? I assume that I have to go to my ISP and tell him that I need a static IP for the server connection in order for my desktop PC to be able to locate the server machine..

---

### Post by hyperAura on 2011-09-14
@haqking Ive read that rsync has the capability to send only files that have changed so the big amount of work will need to be done only the first time the files are backed up..

Changed files every day are less than 500Mb so I assume that it would not take so long..

---

### Post by CharlesA on 2011-09-14
> **hyperAura said:**
> ok let's say I use rsync through cygwin..

how can I connect one end to another? I assume that I have to go to my ISP and tell him that I need a static IP for the server connection in order for my desktop PC to be able to locate the server machine..

Setup dyndns and open the port on your router for ssh (and secure the ssh server, since that's the #1 way of having a box cracked).

> **hyperAura said:**
> @haqking Ive read that rsync has the capability to send only files that have changed so the big amount of work will need to be done only the first time the files are backed up..

Changed files every day are less than 500Mb so I assume that it would not take so long..

That is correct - it only sends changed files.

---

### Post by haqking on 2011-09-14
> **hyperAura said:**
> @haqking Ive read that rsync has the capability to send only files that have changed so the big amount of work will need to be done only the first time the files are backed up..

Changed files every day are less than 500Mb so I assume that it would not take so long..


in short yes.  But i would still have a USB HDD as not only a extra backup source, but the convenience to carry home with you, and not worry about remote syncing or in addition as an extra level

---

### Post by CharlesA on 2011-09-14
> **haqking said:**
> in short yes.  But i would still have a USB HDD as not only a extra backup source, but the convenience to carry home with you, and not worry about remote syncing or in addition as an extra level

+1. Would be easier to set up.

As for syncing to the external - check out robocopy.

---

### Post by hyperAura on 2011-09-14
Thanks CharlesA.

I will open the ssh port on the router on both ends? or just on the server router? 

I thought ssh was secure.. Do you mean physical access security or logical access security of the server machine?

---

### Post by CharlesA on 2011-09-14
SSH is secure, but you need to lock it down - use complex passwords or keys at the very least.

You'd have to open the port on the receiving router (the one at home).

---

### Post by hyperAura on 2011-09-14
@haqking I used to backup my data on an external Seagate USB HDD but for some reason it failed in less than 3 months..

I know that this is just an unlucky incident but Ive decided on a remote backup, if possible, since it would save me time as I will not have to wait the backup to be done every day before leaving work, in order to take the HDD with me..

Thanks

---

### Post by CharlesA on 2011-09-14
> **hyperAura said:**
> @haqking I used to backup my data on an external Seagate USB HDD but for some reason it failed in less than 3 months..

Do you recall which model? I've had quite a few Seagate external drives and none of them have failed with normal use. There was that one time when one of them fell from about 3 feet (bumped off desk) and needless to say that one was toasted. They RMA'd it without any problems tho.

---

### Post by Porcini M. on 2011-09-14
For USB HDDs, I'd recommend simply buying USB HDD enclosures, where you supply the internal drive for it (so it's just the case + the USB interface + the power supply). Then you can swap out drives as needed, without buying whole entire USB HDD units.

---

### Post by Old_Grey_Wolf on 2011-09-14
> **hyperAura said:**
> ...
Is this possible? If yes, [COLOR="Red"]is it secure[/COLOR]?
...

This struck me as significant. 

Depending on the size of the company and your need for securing your data, you have to evaluate your tolerance for security risks.

Anytime you allow access to your server over the WAN you are assuming some risk. Once a port or protocol is opened, you need to be cognizant of the risk and protect the server accordingly. 

Depending on the application you choose to use, you need to read about the recommended security best practices for that application. This is not a backup solution; however, it provides an example of security best practices for an application, this is a link to Apache's security best practices [http://click.apache.org/docs/user-guide/html/ch06.html](http://click.apache.org/docs/user-guide/html/ch06.html). Some applications don't provide security guidelines; so, you are left to figuring it out for yourself. The guidelines usually mitigate the risk as much as possible; however, they don't make the system 100% secure. You opened a port or protocol; therefore, you assume some level of risk. You also need to look into detecting security relevant events through examining system and application logs, etc. One place to begin learning about detecting security relevant events is in the Ubuntu Security Forum @ [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338), the sticky threads may be helpful.

---

### Post by hyperAura on 2011-09-15
Hey guys thanks for your replies..

@CharlesA - This is the model of the HDD I was using (320GB) 
[http://www.seagate.com/www/en-us/products/external/freeagent/freeagent_go/](http://www.seagate.com/www/en-us/products/external/freeagent/freeagent_go/)

---

### Post by CharlesA on 2011-09-15
> **hyperAura said:**
> 
@CharlesA - This is the model of the HDD I was using (320GB) 
[http://www.seagate.com/www/en-us/products/external/freeagent/freeagent_go/](http://www.seagate.com/www/en-us/products/external/freeagent/freeagent_go/)

Ah ok. One of the ones I've not used. I only use the "desk" version since I don't intend to have to access them on the go. ;)

Good luck with getting everything setup - if you've got any questions, I'm sure there are people who can help.

---

### Post by haqking on 2011-09-15
> **CharlesA said:**
> Ah ok. One of the ones I've not used. I only use the "desk" version since I don't intend to have to access them on the go. ;)

Good luck with getting everything setup - if you've got any questions, I'm sure there are people who can help.


it is approaching nearly 30 years since i started with computers and in that time i have never had a single HDD failure with my own equipment.  I have had them on brand new Servers in a corporate environment and the like but never had one personally fail.

I still actually have a commodore 9060  5MB hard drive in the attic, which i used to use with a commodore pet that i got from my brother in the 80's after he had got me interested in computers from a zx80.

The pet still fires up as does the hard drive.

they dont make em like they used to...LOL

---

### Post by hyperAura on 2011-09-15
Thanks for all your replies.. 

I will agree with you haqking.. Everything has an expiration date these days..

---

