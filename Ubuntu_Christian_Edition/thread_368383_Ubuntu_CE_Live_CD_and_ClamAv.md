---
title: "Ubuntu CE Live CD and ClamAv"
date: 2007-02-23
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2007-02-23
I recently have had a run in with some virus problems and was trying to find a Live CD with virus software that I can scan from the Live CD.  I was unable to make one, so I started thinking about  making one, (big learning curve), then I realized, I'm about 90% sure that Ubuntu CE comes with ClamAv by defualt, is this correct?  All I would need to do is boot into Ubuntu CE and run freshclam in the terminal (to update the virus database) and then scan with that.  Essentially it is an anti-virus Live CD.  Will this work?  Does Ubuntu CE come with ClamAv installed?  If not how hard, or what modifications would need to be made?

This could be yet another marketing tool for Ubuntu CE, not marketing as in selling, but getting it out there!

Shane

---

### Post by mysticrider92 on 2007-02-23
I don't know if ClamAV is installed in Ubuntu CE by default or not. I assume these are Windows viruses? There are a few live cd distros out there that are meant to be used to get rid of viruses. Is something like [this]("http://www.bitdefender.com/bd/site/presscenter.php?menu_id=25&n_id=58") what you are looking for? [Here]("http://www.livecdlist.com/?pick=All&showonly=Windows+Antivirus&sort=&sm=1") are a couple others, the avast! on looks almost exectly like what you need. You could probably make a CE cd specifically for this, but the Ubuntu live cd's make it harder to access the host computer's hard drive(s).

---

### Post by shane2peru on 2007-02-23
Thanks for the info.  I think I have used BitDefender before, but was unable to find it again.  I think the last time I used it, I couldn't figure out how to mount a NTFS partition either.  But in Ubuntu I know how to do that.  Also, I don't remember if it automatically found the internet connection.  I was hoping that Ubuntu CE came with ClamAv installed.  I will have to give it a try later and see.  Thanks for the link though.

Shane

---

### Post by mhancoc7 on 2007-02-23
> **shane2peru said:**
> I recently have had a run in with some virus problems and was trying to find a Live CD with virus software that I can scan from the Live CD.  I was unable to make one, so I started thinking about  making one, (big learning curve), then I realized, I'm about 90% sure that Ubuntu CE comes with ClamAv by defualt, is this correct?  All I would need to do is boot into Ubuntu CE and run freshclam in the terminal (to update the virus database) and then scan with that.  Essentially it is an anti-virus Live CD.  Will this work?  Does Ubuntu CE come with ClamAv installed?  If not how hard, or what modifications would need to be made?

This could be yet another marketing tool for Ubuntu CE, not marketing as in selling, but getting it out there!

Shane

Yes, ClamAV is installed by default in Ubuntu CE. It is needed for the web content filtering. I am not sure how well the LiveCD will work for scanning for viruses. I have never even thought about it before. Let me know if it works.

Jereme

---

### Post by shane2peru on 2007-02-23
Wow the resolution on this thing is horrible!!!  I booted into the Live CD mounted the ntfs partition, updated ClamAv and am scanning as we speak.  It was super easy, and workes great.  The resolution is something like 640x480 with no other options I think this thing has ATI video card or something.  Despite the blown up display this is a great Live CD virus scanner!!  I'm going to let it run for the night.  I will post back if I run into any snags.  New marketing road (as in plug, or plus) for Ubuntu CE!!!

Shane

---

### Post by mhancoc7 on 2007-02-24
> **shane2peru said:**
> Wow the resolution on this thing is horrible!!!  I booted into the Live CD mounted the ntfs partition, updated ClamAv and am scanning as we speak.  It was super easy, and workes great.  The resolution is something like 640x480 with no other options I think this thing has ATI video card or something.  Despite the blown up display this is a great Live CD virus scanner!!  I'm going to let it run for the night.  I will post back if I run into any snags.  New marketing road (as in plug, or plus) for Ubuntu CE!!!

Shane

Sounds great! Once you get done please let me know how it goes and the steps you took.

I tried to run freshclam on my system and got an error so I would love to hear what you did.

Jereme

---

### Post by shane2peru on 2007-02-24
Jereme,

Ok, here is what I did to scan my Windows PC with a Ubuntu CE Live CD. I wrote it out in a way that you can take it and include it in directions or something like that if you would like.  Modify it if you see anything that needs changing.  Really nice benefit to Ubuntu CE.

1.  Boot into Ubuntu CE (I used dapper because that is the disk I had handy, I'm about 90% sure Edgy would be the same, and a little better because the ClamAv Engine will be more up-to-date)

2.  Open Terminal type paste ```
sudo fdisk -l
```  This will let you know what partitions are there.
**Note:** If you have more than one partition you want to scan then you are going to need to make 2 or three directories, depending on what you want to scan. 

3.  Now in the terminal ```
sudo mkdir /media/[COLOR="Red"]sda2[/COLOR]
```  You can really use whatever you want for the sda2 part.  I always like to use the hard drive name.  Anything red from here on out you may need to adjust.

4.  Next in the good old terminal```
sudo mount /dev/[COLOR="Red"]sda2[/COLOR] /media/[COLOR="Red"]sda2[/COLOR]
```  this is all I did and it mounted my NTFS partition.  **Note:** Also if you have more than one, you will need to mount them all.
**Note:** If the Live CD didn't automatically detect and setup your Network connection, you will need to make sure it works before updating ClamAv.  It set mine up for DHCP, which my network doesn't like, so I went and placed the IP address in to make it work better.

5.  Now we need to update ClamAv with the latest virus info.  Again in the terminal```
sudo freshclam -v
```  the -v is the verbose mode, I like to know what is going on.  

6.  Now we are going to scan the drive or drives.  I don't trust ClamAv to just go ripping files out of where they belong, so we are just going to log all the info, and you will need to go back and manually remove anything that doesn't belong.  Again in the good old terminal```
sudo clamscan -rvi --no-mail -l /home/ubuntu/Desktop/clamav.log  /media/[COLOR="Red"]sda1[/COLOR] 
```  Some of the options you can adjust as you prefer.  If in doubt type ```
man clamscan
``` and check out the options.   Here are the ones that I use:
r - Recursive
v - Verbose (again because I like to know what it is doing)
i - only log the infected files
--no-mail - should keep you out of the mail boxes to avoid messing up your mail client
-l - is the log file and tells it where to log it to, ours logs it on the Desktop for easy retreival

7.  Ok, I let mine run all night long, and was still going, so save ample amount of time to run this (of course it depends on the speed of the machine, and the size of the partition being scanned.)  Now open the log file and you can see what was labeled as a virus, or problematic file.  If you see anything that you think is a real virus you can go and delete it in the terminal using the ```
sudo rm /path/to/the/virus/VirusName
```  Use this at your own risk, it is not reversible be very careful removing files. Mine turned up three false positives two were large zip files that were too large to be scanned, and one is an old Win 98 program that I'm sure is not problematic.  It didn't call them viruses, but did give some warning about them.  If you have an over abundance of viruses you probably need to completely re-format your computer and your MBR to overwrite any viruses.  Backup any data that is not virus infected and re-install your OS.


Shane

---

### Post by mhancoc7 on 2007-02-24
Awesome!! Thank you.

Jereme

---

