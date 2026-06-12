---
title: "Ubuntu Server on a Buffalo Linkstation?"
date: 2006-08-08
forum: Server Platforms
---

### Post by S29K on 2006-08-08
I bought a Buffalo Linkstation HD-HDG250LAN to act as a media server/backup drive so I wouldn't have to leave my computer on all day and am struggling with the best way to set it up.

I managed to flash the firmware with Openlink to allows me telnet access to the device and can fiddle with it to my hearts content but am frankly a little over my head trying to set up what I want via telnet and the terminal.  I'm spoiled by Gnome and its fancy GUI tools and haven't the knowledge to comfortably configure it from the command line without a step by step howto.

I successfully got the TwonkyVision MediaServer trial to work but only because it is fairly well-documented.  I would like to use gmediaserver and have tried to get it running but to no avail.

Is it possible to install Ubuntu to my network storage device in either server or PowerPC version and go from there?  I think with a more familiar environment I'd have half a chance of getting this to work.

---

### Post by S29K on 2006-11-16
I'm still beating my head against the wall trying to make this work. ](*,) 

There is an option to install a debian version of the firmware that will work with instructions from [www.linkstationwiki.net](www.linkstationwiki.net) but I would prefer to have Ubuntu instead.

Is it possible to install the default debian firmware and make a few changes to repositories etc. to make it an Ubuntu server? :-k

---

### Post by dataw0lf on 2006-11-16
> **S29K said:**
> 
Is it possible to install the default debian firmware and make a few changes to repositories etc. to make it an Ubuntu server? :-k

It's a long shot, but worthy of an attempt. I doubt it will work without serious hackery, however.

---

### Post by BrandonG777 on 2008-05-03
Try Freelink with Webmin. Make sure you pull your drive out and resize the partitions otherwise you'll run into space problem later down the road when you try to add some extra features. It's not Ubuntu but it's Debian which is still nice. With Webmin you can configure you're little box through a web interface. I'm sure you could install all the X11 libraries but I don't think that box has enough memory to really do much. I've been using it on mine for almost a year and love it. With NFS shares to my iMac I get about 12mb/s a sec, which for that box that's about as good as it gets. I also have Twonky, Samba, FTP, and DAPP servers running so I can serve my media up to my Ubuntu laptop (via NFS), Frontrow on my Mac Mini hooked up to a flatscreen in the bedroom (via NFS), PS3 & Xbox 360 in the living room (via Twonky), or any Windoze machine that finds it's way into my home (via Samba). I also use a perl package called pytvshows that automatically pulls in my TV shows from tvrss.net. It's possible to run this and a torrent client from the Linkstation but I choose not too because it quickly becomes overwhelmed with it's 400mhz processor. So I run thos processes on my Mac Mini and just have Transmission move the files to the Linkstation after they've completed downloading.

---

### Post by S29K on 2008-05-07
I ended up using Freelink as you recommended and had it working fairly well.  Unfortunately the little guy wasn't up to the task of streaming my MP3 collection to a UPnP media server attached to my stereo and crapped out frequently. In it's defense, 14,000 MP3s are a lot to randomize and serve up.

---

### Post by BrandonG777 on 2008-05-08
> **S29K said:**
> I ended up using Freelink as you recommended and had it working fairly well.  Unfortunately the little guy wasn't up to the task of streaming my MP3 collection to a UPnP media server attached to my stereo and crapped out frequently. In it's defense, 14,000 MP3s are a lot to randomize and serve up.

Yeah, something isn't setup right. I'm running Twonky on mine serving up video to my PS3 and XBox 360, as well as running NFS shares to my Mac Mini and iMac and I play video on both. I also had my iTunes Library on it at one time but apparently iTunes Libaries aren't designed to be shared and had a bit of corruption but that was due to two machines accessing the same library at once. What kind of file system are your shares? I'm using XFS (which is great filesystem for sharing large files over a network) and achieving 12mb/s over NFSv4. Which isn't great I know but it's close to the best results I've seen posted in the forums for the LinkStation Live. I didn't even think about you using a lesser model until now. I know some of them have slower processors, mine has a 400mhz ARM9 based processor with a gigabit adapter (yeah why did they even bother with a 400mhz processor) but I'm not running Jumbo Frames or anything.

---

### Post by S29K on 2008-05-08
Mine only has a 266Mhz PPC processor with 128 Mb of Ram to work with. :(

---

### Post by BrandonG777 on 2008-05-10
> **S29K said:**
> Mine only has a 266Mhz PPC processor with 128 Mb of Ram to work with. :(

That sucks, but I think you should still be able to at least stream MP3s, I mean if I can stream HD video on mine you should be able to do that, unless there is some other factor I'm not aware of. Are you using XFS for your base filesystem?

---

### Post by far2gud on 2008-05-10
I installed twonky on mine using the Kurobox pro installer from the twonky website. Apparently the kurobox pro had the same chipset/controller as the ls live.

Does anyone think it would be worth while trying this?

[http://buffalo.nas-central.org/index.php/Ubuntu_installation_guide](http://buffalo.nas-central.org/index.php/Ubuntu_installation_guide)

Thanks,

---

### Post by BrandonG777 on 2008-05-10
Yeah, I dunno about all that. I would probably switch to Ubuntu LTS if I had the option but I've been very happy with Debian. I don't have all the latest options but I do have a rock solid NAS that has never failed on me (knock on wood.) I would make sure you're using the XFS filesystem for your shares to start with. Ubuntu isn't going to offer any better performance.

---

### Post by S29K on 2008-05-12
I don't remember exactly what I did (as it was 2 years ago) but I probably used Ext3 because it was familiar.  I've started playing with the LS since you reopened my thread and will likely try out a few things and see if I can put it back into service again.

---

### Post by BrandonG777 on 2008-05-13
> **S29K said:**
> I don't remember exactly what I did (as it was 2 years ago) but I probably used Ext3 because it was familiar.  I've started playing with the LS since you reopened my thread and will likely try out a few things and see if I can put it back into service again.

I've really gotten my money's worth out of mine. Nothing else would have been this versatile but I haven't been completely happy with the speed but similar devices don't perform much better. I think my next purchase will probably one of the HP Linux based file servers or building my own in some kind of RAID 5 configuration. The problem I have now is that I've become so reliant on it if something happens to that drive I will be in a world of hurt. If you need any help with yours just let  me know. If you don't have anything on the drive I would STRONGLY recommend you pull the drive out and hook it to a desktop or a USB adapter and repartition so that you have more storage on the system drive. I actually had enough room to install everything I wanted but ran out of space applying updates and then I had to unload everything to a server at work, repartition and copy everything back. A real pain. I've had pretty good luck tweaking mine but I've been a bit on the cautious side because I'm not sure how to reload or restore if something where to happen to my system partition. I'm sure I could figure it out if I got to that point but I've just tried to keep that from happening.

---

