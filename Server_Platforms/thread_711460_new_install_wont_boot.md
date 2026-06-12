---
title: "new install wont boot"
date: 2008-02-29
forum: Server Platforms
---

### Post by bbarrons on 2008-02-29
I bought 2 servers off of ebay and starte to work on them the last few days. I was able to get the first one installed with kubuntu over the network. The second one will go thru the complete in stall but will not boot. The systems were virtually identical except the second one has drives that are hot swapable. They have the same drives, mobos, nics, memory, processors,..... Any ideas where to look? 
I have no cdrom so it all has to be done over the net unless I use a usb drive......

---

### Post by Sam Lars on 2008-02-29
Where does it get to on boot?

---

### Post by bbarrons on 2008-03-01
In an effort to not make the post too long I guess I could have given a little more info......After install finishes it restarts and then goes to boot failure... no boot device found. I had installed this many times with different options to see what option gave me the best results. I setup a tftpserver, pxelinux,  and used apache2 for my distro. I was able to install on the first try the first server using 7.10...... I then hooked up my second server to install and that one would not setup. First, it would start to read from web server then it would fail on the first few files and ask for a different mirror. The only way it would install would be from the us.archive mirror..... I then would get thru the install and try to create a raid ... and it did but would not install grub to it at the end. SO I gave up that idea.......and moved on. After trying all the options for 7.10 I setup a folder for my 6.06 server disk and the server installed on the first try.... from my mirror...... SO, I went back to my 7.10 setup and then it installed the first time without a hitch....... SO, in a moment of desperation I was hoping there was a mind reader out there that specialized in pxelinux setups and new a network install  thru and thru..... and could read between the lines and tell that I was frsutrated and starting to babble.........
 SO, all in all, it works, I still have to figure out how to setup raid.
I have 4 37gb scsi drives to play with in these servers and I would like to be able to have it all running quite well before I go to far.......
! server is going to be for zimbra email and the other is going to be setup with squid and dansgaurdian.......
 If anyone gets to the end of the post and still wants to offer some suggestions I would apprecaite it.....:lolflag:

---

### Post by Sam Lars on 2008-03-01
Here's what looks to be a nice guide to setting up RAID...
[http://ubuntuforums.org/showpost.php?p=4391983&postcount=2](http://ubuntuforums.org/showpost.php?p=4391983&postcount=2)

---

### Post by bbarrons on 2008-03-02
Thanks Sam, I hadnt thought of doing it that way. I was going to try the install over just to see how it reacts to raid but I think I will move all data to the first drive that has the OS on it and then build a raid 1 from the other 3 drives. I would like to have the zimbra mailboxes on a raid. If I lose the OS drive it can always be replaced and reinstalled but the data for mail should be kept a little more secure.

---

