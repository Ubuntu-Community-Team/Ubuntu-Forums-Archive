---
title: "Linux Server for a small accountant."
date: 2008-05-21
forum: Server Platforms
---

### Post by Compucore on 2008-05-21
I was wondering about something here and I need some input back about this. My accountant wants some kind of back up for his files that he has for his small business that he has and for his wife. I was thinking of proposing a small Linux server with a large enough hard drive tha they could simply dump their data on it into separate accounts on that and back it up from there onto tape in some way. I had initially propose maybe an external usb hard drive but the problem with that is that if they both want to back up onto the same drive they would have to move it from one machine to another. And mayb sharing one file between the two computers on a share spot on the server itself instead of leaving both computers running and putting it to share on one computer while the other has to retrieve it on the other computer while the is gone. A share folder I guess you would call it. 

They already have a small network one is wired in and is running on a wireless onto a small router from US Robotics. My thoughts would have been using a regular desktop that is using a PIII or a PIV between 1-2.6GHZ CPU and about 512 megs of ram. And either a 160gig-1terabyte of hard drive space. Then just expand the hard drive space via usb when needed if/when the drive bays are full. And a simple external tape drive a 12/24 SCSI tape for over night back up. So it can do a incremental back ups on files. Would this be the best way for them. I know I can get the parts for a computer recycling center that are all use and are from the office computers and not the typical home computers that you buy at the boxed stores like best buy for example. 

And even though I do have windows servers OS's I am not going to give those out due to licensing reasons. I was thinking of using Ubuntu just for that and set it up on a system. What do you gus think of this? Any inputs on this it is basically for under 5 computers. And can be easily telnet to the machine when it is connected to their small network. 

Compucore

---

### Post by original_jamingrit on 2008-05-21
Were you thinking of mounting it as a network drive or a samba server?

I found this little tutorial that may be of interest, it seems to be what you described. [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

EDIT: Actually, that might be a little insecure set up, but that won't be a huge problem if you have a NAT router and don't let it to be accessible from outside the LAN.

---

### Post by Compucore on 2008-05-22
As far as I know it is suppose to be secure. When I was last there for his computer I was doing an emergency restoration of her computer. We were lucky enough to retrieve all of his data off of the computer.And I needed to check something up ion his router for the name of the group. But did not have the password for it. Since he had someone else do it or him. And never game him the username or password to log back into it. 

I remember seeing from Ubuntu here some documentation for certain features that will be enabled for secured features that I am already use to in seeing it at a regular office like home drives on the server itself so they can save their data on there instead of on their own computer. The only thing that I needed to fine out with samba. What worries me a little bit is with samba and making it secure. I know that with Active directory you can make adjustments on certain features under windows server. Where as the comand line there ight not be a menu typse of application for it where you can choose like 1 make a change for something or 2 for something else. The command line doesn't really bother me. But when you want to make things easier instead of typing in a lot of commands for it. just having a simple menu directly there for it. The setting the limitations for each account or making a shared directory.  I'll take a look into that even for refernece which never hurts to have.

Compucore

---

### Post by mdr on 2008-05-22
Personally I backup about 500GB each day and I do not bother with a tape drive.

I use duplicate disks in server and rysnc.  Do a differential daily backup to external disks plus a weekly offsite.

---

### Post by rickyjones on 2008-05-22
I actually have a customer where I implemented this, and will actually be redoing their server this summer (updated OS, new disks, etc...).

Install Ubuntu Server and configure however you want the disks. I personally recommend a RAID1 setup for redundancy with an additional external USB hard drive for back up purposes. Overkill? Depends on who you ask.

Then use SAMBA to actually setup the users. As long as the server is secure from the internet I wouldn't go overboard with security, just use the same usernames/passwords as they do on their Windows computers. This way there is seamless integration.

Windows Offline Files can come in handy here or you can use your own file sync program. I recommend Always Sync.

As I noted, I'll be redoing the server for a customer this summer. Probably a new server chassis with a faster processor/more memory as well. I'm thinking 4 hard drives - a single drive for the OS installation and then 3 drives in a RAID5 array for the actual data. I'd like to do a RAID1 for the OS but I'm still not sure on the best and most cost effective way to configure that with Ubuntu.

Anyhow, those are my thoughts, take them as you see fit.

Thanks,
Richard

---

### Post by hyper_ch on 2008-05-22
What is the price range he's willing to invest?

---

### Post by Compucore on 2008-05-22
I will be talking with him soon about this. Maybe this afternoon since I want to find out on which way to go with this. I will give him the options of either going with an external usb for both or go with a server with similar set up. Personally I would rather go with a server on site that way if one of the machines should go belly up we would not be panicking on the data itself. Where as two external USB drives one for each machine they may fool around with the application and make it worst if they interrupt the application running while backing their data. I'll update this when I get the input from them. 

Compucore
 
> **hyper_ch said:**
> What is the price range he's willing to invest?

---

### Post by hyper_ch on 2008-05-22
well, if it's just for backup you don't need a high-end solution and you might find a NAS suitable... an NSLU2 ([http://en.wikipedia.org/wiki/NSLU2](http://en.wikipedia.org/wiki/NSLU2)) running a debian might be what you need. That would be quite cheap...

---

### Post by Compucore on 2008-05-22
True I could go with Nas but they will need expandability as well Right now they have two computers to work with possible that they might expand as well since they have two youn children as well so at a later date for back ups of the kids homework on the computer would be a good thing too. So The room on their router that they have is very small on it. Loking at maybe four connections on it. And the only way of expanding that would to use a cross over to a larger switch or hub. I willbe seeing him soo to see which way they decide on it. Right now the onl thing that has been mentioned was using a usb external hard drive. 

I will discuss on the situation with him to see which way he wants to go with it. To make sure that the options are there and that it is the right for their needs. If it was just one computer it would an easy answer. But when your involving two andmaybe more in the future for the kids you have to look at it. I know the kids were not mentioned in the beginning so not to fret about it. right no it is just the two computers. 

COmpucore

---

### Post by Girya on 2008-05-22
I've been running backuppc for my home network. It runs on a ubuntu server using lvm so I can just hang another hard disk when this one fills up. Its a P4 I salvaged from the dump (no kidding) with 1gb of mem. its completly automated and does a daily incremental and a weekly full backup. it takes about 90 min to backup 50gb. It pools data so it only makes one copy of identical files that are from different hosts. A server running backuppc using lvm and raid with hot swap disks for off site storage would be pretty good.

kevin

---

### Post by Compucore on 2008-05-22
Hey Girya,

Just out of curiousity of the raid are you running Raid 1,3,4/5 on your server at home? I was thinking if they do go for a server I could go with just a regular computer with maybe and just get a raid card that could fit an external raid array and a usb 500 gig externall drive to back it up. It's interesting to fit out on some peoples servers to see what they have. My netserver LPR is very limited on internal hard drive space for it. I would need to gt a set of external ones to extend it out onto that.  

:D

> **Girya said:**
> I've been running backuppc for my home network. It runs on a ubuntu server using lvm so I can just hang another hard disk when this one fills up. Its a P4 I salvaged from the dump (no kidding) with 1gb of mem. its completly automated and does a daily incremental and a weekly full backup. it takes about 90 min to backup 50gb. It pools data so it only makes one copy of identical files that are from different hosts. A server running backuppc using lvm and raid with hot swap disks for off site storage would be pretty good.

kevin

---

### Post by hyper_ch on 2008-05-23
well, NAS can also easily extended by attaching more NAS or by using larger drives... for a pure fileserver/backup server I tend to think that NAS (in non-professional environments) are best price/effect soltuions.

---

### Post by jonabyte on 2008-05-23
I wouldn't recommend using tape drives anymore, since hd's are soo cheap and faster to restore data.

---

### Post by NateMan on 2008-05-23
I would have to recommend using a hardware ide raid5 card. Then there will be redundancy and ide raid 5 cards are getting cheaper and cheaper. I got a 12 port for 80 the other day, full hardware enterprise raid. I run a raid5 setup for all of my data and a separate raid1 setup for my os. This seems to be fairly bullet proof as well. Another good idea would be to have a usb drive they bring in to update files every so often that is stored at another location, such as the accountants house. This would be much more cost effective than tape, and should be reliable. A pentium 3 would be great for the processor esp with a hardware raid card. As for setup, the perfect server guide works quite well, just disable the webpage stuff and don't install ispconfig. Should be fine behind a firewall. If your really worried about your data, redundancy and off site backups are key. I was able to make a similar sort of setup with 1.5TB (using 4 500gig drives) for less than $600.

---

### Post by Compucore on 2008-05-23
My same thoughts exactly as well with raid 5. Whether  they are running on SCSI or on IDE. Usually When I have purchased used servers from the computer recycling center up over here they already have SCSI built into them. But this will be the exception to the case and more likely be using ide instead of SCSI. Well It depends on th tap being use as well. I would stick with a usb external drive for that. But since they are really smal and its not really worth the investment of having it for them anyways. Or even an automate tape back up from where I work not too long ago. I have one myself that is a 12 gig uncompressed 24 gig compressed. I still use it from time to time over here. But I'll be revamping some of my own machines and put a couple of them together as a small server group

They are behind a firewall on their router. But I don't knwo when the last time the router was check for any new firmware on it. I'm usually diligent on mine at home I check at leas one a month at the main web site for any firmware updates. The server itself will not be used for any emails or web server so that will be already taken out. 

Compucore

> **NateMan said:**
> I would have to recommend using a hardware ide raid5 card. Then there will be redundancy and ide raid 5 cards are getting cheaper and cheaper. I got a 12 port for 80 the other day, full hardware enterprise raid. I run a raid5 setup for all of my data and a separate raid1 setup for my os. This seems to be fairly bullet proof as well. Another good idea would be to have a usb drive they bring in to update files every so often that is stored at another location, such as the accountants house. This would be much more cost effective than tape, and should be reliable. A pentium 3 would be great for the processor esp with a hardware raid card. As for setup, the perfect server guide works quite well, just disable the webpage stuff and don't install ispconfig. Should be fine behind a firewall. If your really worried about your data, redundancy and off site backups are key. I was able to make a similar sort of setup with 1.5TB (using 4 500gig drives) for less than $600.

---

