---
title: "Kubuntu 11.10 needs some work IMHO"
date: 2012-02-02
forum: Testimonials &amp; Experiences
---

### Post by paradigm2 on 2012-02-02
Hello I've been a linux user for a long time and recently decided to try Kubuntu again after many years.  Unfortunately it isn't quite up to the standard in my opinion.  Here are some things which happened to me in the install and the first hour:

1. The installer presents as a default option the resizing of my forth disk.  No other drives are listed under the first option.  Option two allows me to "use the whole disk" and I am able to select other drives.  Thinking this will be sufficient I chose this one.  To my surprise it neglected to install a swap partition on my system with 2 GB of ram. :o  Should it really be this way?

[s]2. For some reason there is a delay of 15 - 20 seconds between the POST and when Grub2 appears with the menu.  It is a black screen otherwise with a cursor at the top.  It does not do this on other distributions, at least more than 5 seconds.  At first I thought it was completely hanging.  Note that these other systems seem to use Legacy Grub.[/s] update: Happens on OpenSUSE also, after all.

3. The general performance of Kubuntu 11.10 compared to the instal of OpenSUSE 12.1 which I just performed is horrible.  I'm not sure what the problem is but things noticeably lagged under Kubuntu where they are not currently under OpenSUSE.

4. For some reason after initiating the initial update when I started the rekonq browser it began opening gwenview for each and every image.  It spawned over three dozen windows. (!)

5. During the same initial update (of around 150 packages) for some reason it froze exactly at 50% progress.  I believe on libmsn-something-or-other.  I waited several minutes and nothing happened.  I noticed the muon updater was no longer generating network activity.  So I then tried to quit out and abort gracefully.  Muon would not allow this.  It did nothing.  Finally I had to go to a terminal and force a reboot because in trying to logout from within the KDE environment it seemed muon was intercepting the request.


6. Upon rebooting I discovered that I no longer had any package management functions as each time I attempted to use them I was told that another instance was already running and that I had to exit that one first.  No such instance was running.  I rebooted once more and the same thing occurred again.  

7. Somehow I was able to open an instance of the other muon packager I believe (I am a very experienced Linux user but am not familiar with all these new package managers having used them now for an hour only) and it gave me the same error but somehow I also generated an error telling me to use 'dpkg -a (etc)' which I did by coping and pasting.

8. Upon rebooting I now started receiving a segmentation fault each time I tried to run the muon software manager.  See [http://ubuntuforums.org/showthread.php?t=1909185](http://ubuntuforums.org/showthread.php?t=1909185)

Note that the installation itself generated no known errors and my CD passed the integrity test as did my memory test.  Plus I am writing this now on OpenSUSE KDE which is working flawless.

All of this having happened in the first hour or two of use I hope you can understand why I switched to OpenSUSE and why I am writing this message.  Perhaps one day I will give Kubuntu a try once again.  I hope the developers can fix the issues and I thank them for their work regardless of my switching away from Kubuntu.

Thank you for reading.

---

### Post by mastablasta on 2012-02-03
> **paradigm2 said:**
>  
1. The installer presents as a default option the resizing of my forth disk. No other drives are listed under the first option. Option two allows me to "use the whole disk" and I am able to select other drives. Thinking this will be sufficient I chose this one. To my surprise it neglected to install a swap partition on my system with 2 GB of ram. :o Should it really be this way?
.
 
no. something is wrong.
>  
3. The general performance of Kubuntu 11.10 compared to the instal of OpenSUSE 12.1 which I just performed is horrible. I'm not sure what the problem is but things noticeably lagged under Kubuntu where they are not currently under OpenSUSE.
.
Not sure what the issue is or how installation went. i only tested it live and didn't find it to be any slower or faster than OpenSUSE.
> 
4. For some reason after initiating the initial update when I started the rekonq browser it began opening gwenview for each and every image. It spawned over three dozen windows. (!)
Something definatelly seems to have gone wrong on install.
 > 
5. During the same initial update (of around 150 packages) for some reason it froze exactly at 50% progress. I believe on libmsn-something-or-other. I waited several minutes and nothing happened. I noticed the muon updater was no longer generating network activity. So I then tried to quit out and abort gracefully. Muon would not allow this. It did nothing. Finally I had to go to a terminal and force a reboot because in trying to logout from within the KDE environment it seemed muon was intercepting the request.
 
Muon (htough it should be faster than packagekit seems to be causing a lot of problems. for some it is even not working at all. it should have made into this edition, but i suspect the "forced it in" so more people would test it for the LTS version comming out in April.
 
> 
6. Upon rebooting I discovered that I no longer had any package management functions as each time I attempted to use them I was told that another instance was already running and that I had to exit that one first. No such instance was running. I rebooted once more and the same thing occurred again. 
 
7. Somehow I was able to open an instance of the other muon packager I believe (I am a very experienced Linux user but am not familiar with all these new package managers having used them now for an hour only) and it gave me the same error but somehow I also generated an error telling me to use 'dpkg -a (etc)' which I did by coping and pasting.
 
8. Upon rebooting I now started receiving a segmentation fault each time I tried to run the muon software manager. See [http://ubuntuforums.org/showthread.php?t=1909185](http://ubuntuforums.org/showthread.php?t=1909185)
 

Muon again eh? try synaptic instead/for now.
 
> 
Note that the installation itself generated no known errors and my CD passed the integrity test as did my memory test. Plus I am writing this now on OpenSUSE KDE which is working flawless.

 
If by "integrity test" you mean the Md5Sum check of the downloaded ISO, then i guess either something went wrong with install. Also Muon is "beta" really. again i am not sure why they threw it in this addition if it's so buggy, but it's probably so more people would give it a go and report the bugs back to be fixed for the LTS edition.
i am still on 10.10 waiting for the LTS and doing osme testing in between to see if some things got fixed or not.
 
.> 
All of this having happened in the first hour or two of use I hope you can understand why I switched to OpenSUSE and why I am writing this message. Perhaps one day I will give Kubuntu a try once again. I hope the developers can fix the issues and I thank them for their work regardless of my switching away from Kubuntu.
 
Thank you for reading.
 
that's great! use what works best.

---

### Post by paradigm2 on 2012-02-03
> **mastablasta said:**
> no. something is wrong.

Not sure what the issue is or how installation went. i only tested it live and didn't find it to be any slower or faster than OpenSUSE.

Something definatelly seems to have gone wrong on install.
 
Muon (htough it should be faster than packagekit seems to be causing a lot of problems. for some it is even not working at all. it should have made into this edition, but i suspect the "forced it in" so more people would test it for the LTS version comming out in April.
 

Muon again eh? try synaptic instead/for now.
 

 
If by "integrity test" you mean the Md5Sum check of the downloaded ISO, then i guess either something went wrong with install. Also Muon is "beta" really. again i am not sure why they threw it in this addition if it's so buggy, but it's probably so more people would give it a go and report the bugs back to be fixed for the LTS edition.
i am still on 10.10 waiting for the LTS and doing osme testing in between to see if some things got fixed or not.
 
.
 
that's great! use what works best.

I suspect that something went wrong with the install also now.  Yes I mean the integrity test built into the installation CD. 

Regarding the swap issue I actually did a few installs on different disks.  Due to the 30 second delay I had mistakenly thought that there were issues with grub2 and bios disk order so I simply installed to another disk first.  It definitely showed no swap being activated in 'top', but I wonder if the Kubuntu installer gets confused in some way when there are many disks and/or additional installs?

---

### Post by paradigm2 on 2012-02-03
> **paradigm2 said:**
> 

4. For some reason after initiating the initial update when I started the rekonq browser it began opening gwenview for each and every image.  It spawned over three dozen windows. (!)

For QA or anyone interested I notice another user had this problem and reported it here as well:
> 
rekonq loads the main page, but no images appear, instead of appearing on the website, the images all open individually in Gwenview (spamming my desktop) 


[http://ubuntuforums.org/showthread.php?t=1915584&highlight=Muon](http://ubuntuforums.org/showthread.php?t=1915584&highlight=Muon)

Also he had the same problem with muon segfaulting.  He goes on to ask if 11.10 is in Beta and whether he should install another version. :/

I was half afraid to report the Gwenview issue for fear that people would think I was nuts. :P

---

### Post by ventrical on 2012-02-03
I am just taking a little break here and had some time to  do some more testing with Kubuntu 10.10 and 11.10.  It is just awesome - the way Kubuntu can detect monitors and run 3D graphics where other releases of Ubuntu seems to struggle.  I have been experimenting with an older system that will run CCSM (cube) and other 3D effects with Kubuntu Ocelot where  Ubuntu Ocelot would not.! Goes the same with the older intel chips. What the problem is? .. I have no idea but I know that  the obsoleted Ubuntu PCs will work just fine under the KDE DE.

  11.10 sort of acts like Windows 8 is proposed to work. It is a very fun and bouncy  DE . And CCSM  is more or less built in to  Desktop effects and so it appears that a lot of the animation glitches  (like minor ripping and tearing) are not prevalent .

  I'll be off beta testing 12.04 but I just thought I would drop in with some of my views on Kubuntu 11.10. A great piece of work.!

regards,
Ventrical

---

### Post by mastablasta on 2012-02-05
it would be best to report the strange behaviour on launchpad. reporting it on forums won't improve it if it's a bug. could it be that only a certain mirror image has the bug?

CD integrity check only disk, not if the download was done propperly.  here is how to check the download: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by paradigm2 on 2012-02-05
> **mastablasta said:**
> it would be best to report the strange behaviour on launchpad. reporting it on forums won't improve it if it's a bug. could it be that only a certain mirror image has the bug?

CD integrity check only disk, not if the download was done propperly.  here is how to check the download: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I'm not sure if it would make sense for me to open a bug now since I no longer use it or have it installed.  I probably won't be much help then unfortunately.  I suppose I might try again on another disk and see.  If I do this and it occurs again I will definitely file a bug.

Please explain why you think I should have also ran a separate MD5 check.  I had thought that the CD integrity check basically fulfilled this function.  I don't think I understand.

---

### Post by marl30 on 2012-02-05
The only bug I can identify with from this thread is the Muon package manager. It's still functions like it's in Alpha stage. My solution to this after every fresh install of Kubuntu is to add the Muon development ppa, and problem solved. Aside from that, Kubuntu 11.10 has been completely awesome.

---

### Post by mastablasta on 2012-02-06
> **paradigm2 said:**
>  
Please explain why you think I should have also ran a separate MD5 check. I had thought that the CD integrity check basically fulfilled this function. I don't think I understand.
 
CD integrity check only checks if the CD burned correctly. [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
 
Md5sum checks the downloaded ISO on your computer to make sure it matches the ISO on the server.
 
in other words if you downloaded a bad ISO, burned it and ran CD integrity, it can check it out as OK. however the bad iso on your computer will be the same bad ISO only on CD. it will not check for example if there is a file missing or similar compared to the official version on server. it will only check the burned CD. 
 
however the md5sum check shouldn't be necessary if you downloaded it via torrent as torrent is checking it it while downloading. still sometimes it's good to do it anyway.

---

### Post by paradigm2 on 2012-02-06
> **marl30 said:**
> The only bug I can identify with from this thread is the Muon package manager. It's still functions like it's in Alpha stage. My solution to this after every fresh install of Kubuntu is to add the Muon development ppa, and problem solved. Aside from that, Kubuntu 11.10 has been completely awesome.

Glad it worked for you. :)

---

### Post by paradigm2 on 2012-02-06
> **mastablasta said:**
> CD integrity check only checks if the CD burned correctly. [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
 
Md5sum checks the downloaded ISO on your computer to make sure it matches the ISO on the server.
 
in other words if you downloaded a bad ISO, burned it and ran CD integrity, it can check it out as OK. however the bad iso on your computer will be the same bad ISO only on CD. it will not check for example if there is a file missing or similar compared to the official version on server. it will only check the burned CD. 
 
however the md5sum check shouldn't be necessary if you downloaded it via torrent as torrent is checking it it while downloading. still sometimes it's good to do it anyway.

Intriguing.  I would have thought that if you downloaded a corrupt iso the CD integrity check would likely also detect that since presumably the hash would not match the hash which is expected.  I guess I don't know how it works under the hood so you may be right about that.  I guess I will make it a point to check that also.

---

### Post by slickvguy on 2012-02-09
> **paradigm2 said:**
> 

5. During the same initial update (of around 150 packages) for some reason it froze exactly at 50% progress.  I believe on libmsn-something-or-other.  I waited several minutes and nothing happened.  I noticed the muon updater was no longer generating network activity.  So I then tried to quit out and abort gracefully.  Muon would not allow this.  It did nothing.  Finally I had to go to a terminal and force a reboot because in trying to logout from within the KDE environment it seemed muon was intercepting the request.


6. Upon rebooting I discovered that I no longer had any package management functions as each time I attempted to use them I was told that another instance was already running and that I had to exit that one first.  No such instance was running.  I rebooted once more and the same thing occurred again.  



I just did a Kubuntu 11.10 install and had the exact same thing happen to me. The actual installation went perfectly, but when I went to do the updates after the initial restart, the package manager froze at about 50%. I waited for about 15 minutes, but clearly it wasn't going to continue. I tried to restart, but was told that Muon wouldn't allow it (gee, that's a first). Did a h/w reset (hate doing that!) and then couldn't run Muon (got that same "another instance preventing" message). Obviously something was still out of whack. Since it had stalled while doing something with dpkg, I opened a terminal and ran "sudo dpkg -C", and was able to continue after following the suggestions that dpkg offered. 

I'll play with Kubuntu for a few days to make a decision if I'm going to use it. Aside from this installation/update issue, I notice a few other buggy behaviors from various apps. (e.g. I tried importing bookmarks into rekonq, and some strange behaviour resulted in it deleting original bookmarks for no apparent reason (before the import was executed), also the bookmark editor crashed on me a previous time. So I can see already that Kubuntu isn't quite as stable as Ubuntu (well, 10.10 at least, since I haven't tested Ubuntu 11.10 enough except for unity, gnome shell, etc.), for example. Little bugs won't be a dealbreaker, but is is something to consider. 

Anyway...just wanted to confirm that OP wasn't the only one who had that specific problem, and to post what worked for me to get out of it. Thanks for the PPA advice for Muon. Good suggestion.

---

### Post by nothingspecial on 2012-02-10
Thank you all for your contributions.

> In keeping with a vote by the forum membership which followed a discussion about the management of this section of the forum, threads will now be closed one week after the time of the original post. This is to allow limited discussion.

---

