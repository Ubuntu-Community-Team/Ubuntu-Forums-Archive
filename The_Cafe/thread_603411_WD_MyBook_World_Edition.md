---
title: "WD MyBook World Edition"
date: 2007-11-05
forum: The Cafe
---

### Post by Shimmy on 2007-11-05
I recently bought a WD MyBook World Edition 500gb, and i would like to share my experiences with this drive and Ubuntu.

My kids has a Windows computer, so i used it to configure the MyBook-Drive, using the shipped CD.
After the configuration i was able to find the drive in Ubuntu under System->network.

But i wanted to get more out of the MyBook, so i read some tutorials about it, and found out that there is actually a Linux-OS in MyBook, so by taking out the harddrive from the mybook, and mount it in a Ubuntu-box, it's possible to access the Linux-System files. Now, why do you want to do this? Well, because it's very easy to change in the inet.d config-file to make it start an SSH-Daemon. I did this, and then putting the harddrive back in the MyBook, and started it. Now i was able to connect to MyBook using SSH. Or even FTP.
Right now i'm compiling rtorrent client, this will be great, now i can manage my downloads from anywhere in the world :)

I'm very happy with my MyBook so far, and i really recommend it.

---

### Post by Iceni on 2007-11-05
I'm sorry, it's very early for me. Can you actually run programs (rtorrent) on your MyBook or am I missing the point here?

If you can that would be super cool!

---

### Post by Shimmy on 2007-11-05
> **Iceni said:**
> I'm sorry, it's very early for me. Can you actually run programs (rtorrent) on your MyBook or am I missing the point here?

If you can that would be super cool!

Yes, that is exactly what i can :)
This is the "World Edition" i don't think it's possible on the simpler versions that only has USB.

---

### Post by mozetti on 2007-11-05
Could you please post a link to your product? I think I have a similar hard drive, but I don't recognize the "World Edition" part of the name. I'd like to compare your product to mine.

Also, could you write up a tutorial when you have time? This would be an awesome feature set to add to the drive.

Thanks!

---

### Post by Shimmy on 2007-11-05
> **mozetti said:**
> Could you please post a link to your product? I think I have a similar hard drive, but I don't recognize the "World Edition" part of the name. I'd like to compare your product to mine.

Also, could you write up a tutorial when you have time? This would be an awesome feature set to add to the drive.

Thanks!

This is the one i have:
[http://www.wdc.com/en/products/products.asp?driveid=278](http://www.wdc.com/en/products/products.asp?driveid=278)
And there are some tutorials out there on how to open the case, but none of them was for my version, some have hidden screws, mine did not, i just removed the rubber-band that wraps around the case, and then bend it open.

The inside however looks the same as many of the tutorials, there are some screws to remove, and don't try to figure out it yourself, it's hard :)

Anyways, here are some links i found useful:
Open the case:
[http://discussions.virtualdr.com/showthread.php?t=215504](http://discussions.virtualdr.com/showthread.php?t=215504)
[http://www.hardwareanalysis.com/content/topic/65604/](http://www.hardwareanalysis.com/content/topic/65604/)
Hacks:
[http://martin.hinner.info/mybook/](http://martin.hinner.info/mybook/)
[http://mybookworld.wikidot.com/](http://mybookworld.wikidot.com/)

It's really easy.

---

### Post by morgengenuss on 2008-04-09
man, that sounds awesome! i'm strongly considering buying the exact same thing at the moment and was going through the forums only to stumble upon this great thread.

i guess now there's not much to check out before i buy it, only one last question remains open: what about the noise level? i couldn't find anything on wd's website about it... (i would have to have it in my living room)

---

### Post by morgengenuss on 2008-04-09
one more thing that i'd like to know: what experiences have you made with speed?

it seems that there is a difference between the 500gb version and the mybook world ii (with one or two tb). also in terms of noise. any experiences?

---

### Post by freejam on 2008-04-27
> **Shimmy said:**
> I recently bought a WD MyBook World Edition 500gb, and i would like to share my experiences with this drive and Ubuntu.

My kids has a Windows computer, so i used it to configure the MyBook-Drive, using the shipped CD.
After the configuration i was able to find the drive in Ubuntu under System->network.



Hi everyone new to Ubuntu and agree with Shimmy's praise - I just bought the **Western Digital 1 TeraBit MyBook World Edition** with a single hard disk - this has an ethernet connection and USB port for a daisy chain additional drive, the unit was supplied with an ethernet cable but no USB cable.  There is no need for any configuration in Windows or Ubuntu - just plug into your router and power up. You only need to run the Windows configuration if you want to change the default user name **admin** and password **123456** - even this is possible (I suspect) via Firefox in Ubuntu. Unless you need remote access don't bother to load WD Anywhere.

The WD MyBook starts automatically when the power lead is inserted - as said above it's available by clicking through Ubuntu Places, Network, Windows Network, workgroup, MYBOOKWORLD and identified as **/PUBLIC**, but in Vista or XP it will be assigned a drive letter.

Mine's being accessed by two Vista laptops, an XP PC and a Ubuntu box - simultaneously, and storing a bit torrent download.   Running good as gold, there's no fan so no noise and it's effective passive cooling makes it slightly warm to the touch. Make sure your MyBook is powered up when you boot Ubuntu - I'm running Gutsy.  This is a nice piece of kit that plugs and plays straight off with Ubuntu.

**UPDATE** Well it worked ok for about 3 days and then started dropping out - lost its connection after about an hour or less of running.  It's gone back - I swapped it for a Freecom Network Drive, no more WD for me.

---

### Post by freejam on 2008-04-27
> **morgengenuss said:**
> one more thing that i'd like to know: what experiences have you made with speed?

it seems that there is a difference between the 500gb version and the mybook world ii (with one or two tb). also in terms of noise. any experiences?

Morgengenuss - Update - Sorryo but don't buy it its now been returned.

---

### Post by morgengenuss on 2008-04-28
wow, that sounds really amazing!
i guess i gotta go for one of them :)

thanks a lot for your experience sharing!

---

### Post by SuperSon!c on 2008-04-28
that's an excellent trick. too bad it seems to be just for that version, but i'll hold out for a real good price on the 1TB.

---

### Post by lobner on 2008-06-29
> **Shimmy said:**
> It's very easy to change in the inet.d config-file to make it start an SSH-Daemon. I did this, and then putting the harddrive back in the MyBook, and started it. Now i was able to connect to MyBook using SSH. Or even FTP.
Right now i'm compiling rtorrent client, this will be great, now i can manage my downloads from anywhere in the world :)


EXCELLENT - just bought it, cant wait to get that sshd up and running... :guitar:

---

### Post by jethro10 on 2008-06-29
Hi,
Dont forget products like the Qnap newtork drives, these have package management systems also linux based and you can install all sorts.

By default it has www and ftp servers backup progs, Mysql server, Joomla CMS web site etc.

---

### Post by lobner on 2008-06-29
Hi jethro10, as far as I can tell, there are no actual drive included in the package when you buy an Qnap unit. This adds an aditional expence. More than I am willing to give... the My Book suits me :)

---

### Post by hanzomon4 on 2008-06-29
This sounds like something I could use. I have a lot of video files stored on my Ubuntu desktop and I use NFS to access the files on my macbook pro. It works pretty good but I want something with more capacity that won't get tampered with by family when I leave again for school. 

Would I be able to access something like this from miles away? It would be so cool to backup large files that I want to move off my laptop to remote storage in another state.

---

### Post by jethro10 on 2008-06-30
> **hanzomon4 said:**
> This sounds like something I could use. I have a lot of video files stored on my Ubuntu desktop and I use NFS to access the files on my macbook pro. It works pretty good but I want something with more capacity that won't get tampered with by family when I leave again for school. 

Would I be able to access something like this from miles away? It would be so cool to backup large files that I want to move off my laptop to remote storage in another state.

I don't know about the WD in particular, but the Qnap I mentioned above and no doubt most others offer web based file managers and often SSH access so you can access your device anywhere.

---

### Post by rickh57 on 2008-06-30
I have a 1TB WD MyWbook World Edition. [Hacking WD MyBook World Ed]("http://mybookworld.wikidot.com/") has tutorials about adding SSH and many other tools to it, along with trouble-shooting and recovery documentation. Mine had the issue of disappearing after a few hours, but following some instructions on that site, I reformatted a couple of the partitions and it is now working fine. Since I have a couple of other Linux (Ubuntu, of course) machines, I haven't bothered to put MySQL, etc., on the WD, but it has the ability.

---

### Post by antieshay on 2008-07-05
> **Shimmy said:**
>  because it's very easy to change in the inet.d config-file to make it start an SSH-Daemon. I did this, and then putting the harddrive back in the MyBook, and started it. Now i was able to connect to MyBook using SSH. Or even FTP.


Can I learn how to make the change for the FTP use? Thx

---

### Post by mips on 2008-07-06
> **antieshay said:**
> Can I learn how to make the change for the FTP use? Thx

If you follow the links in the first post you would learn all about it.

---

