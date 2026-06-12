---
title: "Experiement with Trusty iso/zsync"
date: 2013-10-23
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-10-23
I am now currently dowloading what appears to be a trusty tahr .iso.

What I did was I took an old saucy-desktop-i386.iso and renamed it to 'trusty-desktop-i386.iso' and it is actually updating now.

:rename saucy-desktop-i386.iso to:   trusty-desktop-i386.iso

then:

```


zsync -i ./trusty-desktop-i386.iso http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-i386.iso.zsync


```

Regards..

*note* This is experimental and not for novice .

---

### Post by ventrical on 2013-10-23
so far .. so good.

 I will burn this image to usb and try to load it.

brb..

```


Read trusty-desktop-i386.iso. Target 25.7% complete.      
downloading from http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-i386.iso:
######-------------- 34.0% 9.9 kBps         ETA   
#######------------- 35.6% 9.6 kBps         ETA  
########------------ 41.4% 11.1 kBps         TA  
#############------- 69.9% 261.4 kBps         A  

downloading from http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-i386.iso:
################---- 83.0% 260.7 kBps            

downloading from http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-i386.iso:
#################### 100.0% 260.3 kBps DONE      

verifying download...checksum matches OK
used 241369088 local, fetched 698473702
dale@dale-desktop:~/Desktop/saucy1$ 

```

---

### Post by grahammechanical on 2013-10-23
The most scary thing about that operation is errors due to my miserable typing. Now, installing it and rebooting may be a different matter. Zsync is quite smart. I put ./trusty-desktop-amdb64.iso as the target and zsync corrected it to ./trusty-desktop-amd64.iso and carried on with the download. This with a renamed saucy final.

> graham@Sdb8-Roll-Dev:~/Downloads$ zsync -i ./trusty-desktop-amdb64.iso [http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync)
#################### 100.0% 726.4 kBps DONE      


open: No such file or directory
not using seed file ./trusty-desktop-amdb64.iso
Read ./trusty-desktop-amdb64.iso. Target 0.0% complete.      
reading seed file trusty-desktop-amd64.iso: **********************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read trusty-desktop-amd64.iso. Target 76.8% complete.      
downloading from [http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso:](http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso:)
#################### 100.0% 1215.3 kBps DONE     


verifying download...checksum matches OK
used 712302592 local, fetched 215276775


---

### Post by ventrical on 2013-10-23
Well... if I can get the attatchment uploads to work .. here is what scared the E'll out of me ..

---

### Post by ventrical on 2013-10-23
I can't believe it ... !! It worked.... so this is how to do rolling release in a more efficient manner :)

This is Live "Trusty Tahr" session..

---

### Post by grahammechanical on 2013-10-23
I have the same on the live session. I am now about to install.

---

### Post by ventrical on 2013-10-23
it did not have the udapted Ubuntu.info file  for trusty but it did have this:

```

ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

```

which I *assume* will append that files after a full install .. yet I have not installed it yet .. so documentation still forthcomming... perhaps you will beat me to the punch ! :) lol

---

### Post by ventrical on 2013-10-23
Install went seamless .. with one caveat . I stil had to  edit in this file here:

[http://ubuntuforums.org/showthread.php?t=2181414&page=4&p=12821131#post12821131](http://ubuntuforums.org/showthread.php?t=2181414&page=4&p=12821131#post12821131)

 But the think the changelog prefix will eventually do that as the development progresses, i assume . 

 However, past changeovers have led to problems without that Ubuntu.info file being updated.

Regards.

---

### Post by grahammechanical on 2013-10-23
The install went well over here. At least the Ubuntu One returning user sign on is working. But Ubiquity does not set up a Btree file system (btrfs). I noticed this a month ago.

---

### Post by Redalien0304 on 2013-10-23
i am trying this myself also will post results. only thing  done differently installed zsync copied pasted zsync -i ./trusty-desktop-i386.iso [http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-i386.iso.zsync)

---

### Post by ventrical on 2013-10-23
> **grahammechanical said:**
> The install went well over here. At least the Ubuntu One returning user sign on is working. But Ubiquity does not set up a Btree file system (btrfs). I noticed this a month ago.


@grahammechanical

ahhhhaaa ... lookee here.....


After install and then update this is what I got with Ubuntu.info file:

```

ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu development series
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: devel
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu development series

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: devel-security
ParentSuite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: devel-security
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb
Description: Recommended updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb
Description: Pre-released updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb
Description: Unsupported updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


```

So that original file  that was posted in another post for Ubuntu.info got knocked down a peg. Therefore it may even cause problems if we are using this experimental, yet streamlined method of upgrading to Trusty.

Regards..

---

### Post by grahammechanical on 2013-10-23
@ventrical

Do an update. On my system an update made changes to that ubuntu.info. I now have a full set for devel and trusty

> Suite: devel
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
_Description: Ubuntu development series_
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

> Suite: trusty
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
_Description: Ubuntu 14.04 'Trusty Thar'_
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

And all the other references that should be there. I guess it is 14.04 developement branch that rolls over into 14.10 development branch.

And they spelt the name wrong. I am not the only one who doesn't know who to pronounce it.

Regards.

---

### Post by ventrical on 2013-10-23
Exactly my previous point .... so 

[http://ubuntuforums.org/showthread.php?t=2181414&page=4&p=12821131#post12821131](http://ubuntuforums.org/showthread.php?t=2181414&page=4&p=12821131#post12821131)

 is not needed  while using this current method.

---

### Post by ventrical on 2013-10-23
ok.. :) we posted as the same interval :)

 This method , apparently , is rock solid, so I will make a note of it .

thanks for your  help in documenting this experiement.

Much appreciated .

Regards..

---

### Post by zika on 2013-10-23
> **grahammechanical said:**
> ...On my system an update made changes to that ubuntu.info. I now have a full set for devel and trusty...Just on time and just as it should... Toolchain should come tomorrow...

---

### Post by zika on 2013-10-23
> **ventrical said:**
> Exactly my previous point .... so 

[http://ubuntuforums.org/showthread.php?t=2181414&page=4&p=12821131#post12821131](http://ubuntuforums.org/showthread.php?t=2181414&page=4&p=12821131#post12821131)

 is not needed  while using this current method.Wrong...
It was needed at the moment it was written, now it is not since toolchain is here/coming...
Next April just a simple upgrade will do... ;)

---

### Post by grahammechanical on 2013-10-23
It is still less than 7 days since 13.10 was released and I do not know how this compares with previous after release weeks but I think that the devs are working hard right from the off. I would not be surprised if we did not get 14.10 stuff down the turnpike well before 14.10 is released. I think that they want stuff out here to be tested.

Regards.

---

### Post by PokerLegion on 2013-10-23
Is there something new? Because development of the Trusty just started or i am wrong?

---

### Post by zika on 2013-10-23
> **grahammechanical said:**
> It is still less than 7 days since 13.10 was released and I do not know how this compares with previous after release weeks but I think that the devs are working hard right from the off. I would not be surprised if we did not get 14.10 stuff down the turnpike well before 14.10 is released. I think that they want stuff out here to be tested.

Regards.They are learning from experience...
We are getting real development sooner and sooner...
Difference was noticable at the begining of Saucy and now it is even more obvious...
Cheers to devs... ;)

---

### Post by ventrical on 2013-10-23
> **grahammechanical said:**
> @ventrical

Do an update. On my system an update made changes to that ubuntu.info. I now have a full set for devel and trusty





And all the other references that should be there. I guess it is 14.04 developement branch that rolls over into 14.10 development branch.

And they spelt the name wrong. I am not the only one who doesn't know who to pronounce it.

Regards.

Thar har .. har .... said the crusty old pirate !!  :)lol I think someones just having fun ..:)

---

### Post by ventrical on 2013-10-23
> **zika said:**
> Wrong...
It was needed at the moment it was written, now it is not since toolchain is here/coming...
Next April just a simple upgrade will do... ;)

 It is not needed using this current experimental model .. rename saucy iso to trusty, zsync  and try it yourself as I have described it.

Regards..

---

### Post by ventrical on 2013-10-23
> **PokerLegion said:**
> Is there something new? Because development of the Trusty just started or i am wrong?

 Apparently the saucy-desktop-###.isos can be renamed to: trusty-desktop-### .iso and be zsynced successfully for installation. Once the iso is installed or burned to usb/dvd it can then be updated/upgraded and the Ubuntu.info file will also be upgraded.

 Please note that this started out as an experiement on my part and was authenticated by grahammechanical.

Regards.

---

### Post by zika on 2013-10-23
> **ventrical said:**
> It is not needed using this current experimental model .. rename saucy iso to trusty, zsync  and try it yourself as I have described it.

Regards..Yes, it works **now** but it would not work t the time/moment I wrote my message... No way we could try that, but You could trust me/or_not... 
The moment .iso showed up it is OK, at the moment I wrote it there was no .iso... Zsync would not get You to trusty...iso... Never mind, as ususal... Enjoy...

---

### Post by ventrical on 2013-10-23
> **zika said:**
> Yes, it works **now** but it would not work t the time/moment I wrote my message... No way we could try that, but You could trust me/or_not... 
The moment .iso showed up it is OK, at the moment I wrote it there was no .iso... Zsync would not get You to trusty...iso You do not need to have any .iso to start Zsync-ing... Never mind, as ususal... Enjoy...


As you like it.

---

### Post by zika on 2013-10-23
> **ventrical said:**
> Yes .. I aknowledged that and thanked you for that ... perhaps you do not read my replies...

sigh... I don't know why you **ride** me ..

[http://ubuntuforums.org/showthread.php?t=2181414&page=4&p=12821185#post12821185](http://ubuntuforums.org/showthread.php?t=2181414&page=4&p=12821185#post12821185)Your harsh words, that I do not approve/deserve are what makes me get off from this thread and maybe wider... Sorry, I do not want to talk that way...
By no means I did not want any acknowledgment, to the contrary, that is not mine to protect, I've learned that here from others... I was just trying to keep young newcomers straight on track... Do not project Your way of thinking on my posts...

---

### Post by ventrical on 2013-10-23
> **zika said:**
> I was just trying to keep young newcomers straight on track... Do not project Your way of thinking on my posts...

Granted .. and please extend the likewise when I am attempting an open experiment unless there is something topical to contribute .

Kind regards.

---

### Post by sparker256 on 2013-10-23
I did not rename but used the two commands to get the first daily build of Trusty.

```

cd /home/bill/Trusty_Tahr

```

```

zsync -i ubuntu-13.10-desktop-amd64.iso http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync -o ubuntu-14.04-trusty-desktop-amd64-20131021.iso

```

Bill

---

### Post by ventrical on 2013-10-23
Thanks Bill. Theres another streamlined method. +1

Regards...

---

### Post by sparker256 on 2013-10-23
I had t use a 12.04 Startup Disk Creator because other versions (12.10, 13.04, 13.10) would not complete without crashing. I see Trusty Tahr Startup Disk Creator is also broke.

Bill

---

### Post by ventrical on 2013-10-23
> **sparker256 said:**
> I had t use a 12.04 Startup Disk Creator because other versions (12.10, 13.04, 13.10) would not complete without crashing. I see Trusty Tahr Startup Disk Creator is also broke.

Bill

 I am glad you brought that up. I have been using this isolated version of Maveric Meerkat to use SDC and install all my isos to USB because of the same problems. Lucid works as well but it is really hard to get it working reliably anything past 10.10. There was a big discussion on this, I took part in it.. and it got buried. Maybe I could (should) test this more. And I always have to use  (discard on shutdown) option because persistent is just beyond the pale.

sorry .. off topic;)

---

### Post by sparker256 on 2013-10-23
> **ventrical said:**
> I am glad you brought that up. I have been using this isolated version of Maveric Meerkat to use SDC and install all my isos to USB because of the same problems. Lucid works as well but it is really hard to get it working reliably anything past 10.10. There was a big discussion on this, I took part in it.. and it got buried. Maybe I could (should) test this more. And I always have to use  (discard on shutdown) option because persistent is just beyond the pale.

sorry .. off topic;)
I just installed this one on Trusty and it worked fine as I have found with past versions.

usb-creator-kde

Bill

---

### Post by ventrical on 2013-10-24
Repoted the bug here .. usb-creator-gtk

 [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1244067](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1244067)

---

### Post by grahammechanical on 2013-10-24
I went through most of the raring development cycle using 12.04 to burn ISO images because raring would not recognise the presence of disks in the DVD drive not even to play an audio CD. I do not understand how basic utilites become broken.

At the beginning of the saucy cycle I could install saucy and ubiquity would create a btrfs file system to put it on. At the end of the saucy cycle Ubiquity fails to create the btrfs file system. And yesterday's trusty ISO also failed.

I guess it shows the value of testing by humans. OK, Ventrical, you have convinced me. I will now try to use USB Creator to put trusty on a USB stick. How hard can it be? What could go wrong? :)

Regards.

Update: At the first attempt USB Creator blinked out of existence. At the second attempt I kept my beady eye upon it and I dared it to crash in fromt of my eyes. I also refrained from twirling the dialog around the screen out of boredom. Well, it did not crash this time. Tomorrow I will test out the live session and the install process to see if it really did work.

---

### Post by Mateusz Stachowski on 2013-10-24
> **sparker256 said:**
> I did not rename but used the two commands to get the first daily build of Trusty.

```

cd /home/bill/Trusty_Tahr

```

```

zsync -i ubuntu-13.10-desktop-amd64.iso http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync -o ubuntu-14.04-trusty-desktop-amd64-20131021.iso

```

Bill

The output option at the end of your command isn't even necessary. I just zsynced the final image of Saucy with that of Trusty and this will end in unchanged image of Saucy and new image for Trusty.

```
zsync http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync -i ubuntu-13.10-desktop-amd64.iso
```

Also zsync is smart enough to look for appropriate images by itself so if you use only the address it will synchronize your Trusty image. Of course it needs to be in that directory.

```
zsync http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync
```

---

### Post by philinux on 2013-10-24
Nice one worked a treat. Renamed my last iso to trusty then I used same command as usual only changed to trusty.

```
zsync http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync
#################### 100.0% 587.0 kBps DONE      

reading seed file trusty-desktop-amd64.iso: *************************************************************************************************************************************************************************** .....
Read trusty-desktop-amd64.iso. Target 90.2% complete.      
downloading from http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso:
#################### 100.0% 1529.6 kBps DONE     

verifying download...checksum matches OK
used 835956736 local, fetched 91686738
```

---

### Post by ventrical on 2013-10-24
> **philinux said:**
> Nice one worked a treat. Renamed my last iso to trusty then I used same command as usual only changed to trusty.

```
zsync http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync
#################### 100.0% 587.0 kBps DONE      

reading seed file trusty-desktop-amd64.iso: *************************************************************************************************************************************************************************** .....
Read trusty-desktop-amd64.iso. Target 90.2% complete.      
downloading from http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso:
#################### 100.0% 1529.6 kBps DONE     

verifying download...checksum matches OK
used 835956736 local, fetched 91686738
```


  The thing that gets me is that I thought it would fail but I can see now that by doing this renaming convnetion that the .isos take off right from the last release - so it's like there is no wizard behind the curtain sort of thing :) A continued append I would call it.

---

### Post by philinux on 2013-10-24
> **ventrical said:**
> The thing that gets me is that I thought it would fail but I can see now that by doing this renaming convnetion that the .isos take off right from the last release - so it's like there is no wizard behind the curtain sort of thing :) A continued append I would call it.

I don't thin zsync cares it just looks at the target and the daily live. As long as names match hunky dory.

---

### Post by VMC on 2013-10-24
> **philinux said:**
> Nice one worked a treat. Renamed my last iso to trusty then I used same command as usual only changed to trusty.

```
zsync http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync
#################### 100.0% 587.0 kBps DONE      

reading seed file trusty-desktop-amd64.iso: *************************************************************************************************************************************************************************** .....
Read trusty-desktop-amd64.iso. Target 90.2% complete.      
downloading from http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso:
#################### 100.0% 1529.6 kBps DONE     

verifying download...checksum matches OK
used 835956736 local, fetched 91686738
```

Renaming is not needed. zsync reads any iso your using and uses what is the same on the destination zsync. example:
```
$ zsync -i /media/user/SAVE/ISO/*yourmama.iso*  http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync
#################### 100.0% 116.5 kBps DONE 
 
reading seed file /media/vmc/SAVE/ISO/yourmama.iso: ******************************************
***********************************Read /media/user/SAVE/ISO/yourmama.iso. Target 68.0% complete.      *******************
downloading from http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64

```
"*yourmama.iso" *was gnome. The "-i" option can be any iso file - preferrably ubuntu. I use several to get the closest % possible. gnome as you can see is 68% the same as Trusty. I will use several ubuntu-iso's to find the closest match to the one  iso - xubunty, lubuntu.kubuntu I'm zsyncing.
In this case its Trusty.

---

