---
title: "What do I need for my server?"
date: 2006-12-06
forum: Server Platforms
---

### Post by OttifantSir on 2006-12-06
At the moment, I have a seven-year old laptop (that works OK enough) and a five year old server with the specs 
P3 1.26 Ghz 
1.5 GB RAM 
HP NC3163 
4 RAID-drives (2x36.7 GB, 2x67.8 GB) 
CD-ROM 
floppy 
2xUSB1.1
2xUSB2.0(PCI-card)
SCSI somewhere in there 
(Don't know it all)

My intention is to revert this server back to a server. Mainly just a storage. I know I will get a laptop for my birthday the end of February (hopefully one with no OS or Ubuntu, but probably Windows) So I wish to be able to connect to the server and store files on it, and access those files from the laptop. It won't do much else but sit there and have the files ready for access. 

I read about Logical Volume Management, and the impression I got, was that, after having created root and swap, the rest of the remaining space on all drives could be made to look like one drive. If so, is there something that tells you, from my info, that it's going to be impossible?

I have heard about LAMP and a few other things for a server, but what do I need for what I want? A simple FTP-service? Or maybe an HTTP-server? 

Please, I don't know anything at all on servers, but if you would be so kind as to tell me what you think I need for this, I will read up on it and make a judgement later on.

Sidequestion: Is it possible to keep the files already on this machine when moving to LVM (If I am right in my assumption of this, off course)

PS: Will Install Ubuntu on the laptop the moment I get it if it's Windows.

---

### Post by adamkane on 2006-12-06
You don't really need anything special. You just need to decide if you want GNOME or not. I prefer having GNOME on my file server, since it makes administration easier. The server CD without GNOME is really for businesses and production servers.

I have NFS, SAMBA, and LAMP on my server (with GNOME), and all is ok.

If you want LVM, all you need to do is create an LVM partition during installation.

---

### Post by andyjenkins on 2006-12-06
LVM should work great for you.  I have an Ubuntu server that is used for storage as well, with 2x200GB EIDE disks.  Are you considering RAID1?  Since you have the 2 pairs of matched disks, you're in a good situation for RAID.  You'll end up with about 100GB of network storage if you use RAID1, 200GB if you don't.  However, if you don't, then you could lose everything if even one disk fails.  RAID1 mirrors the data, so every time you write to a file, it stores two copies: one on the first disk, one on the second, it's slower to write, marginally faster to read, but the network connection will be the limiting factor anyways.  If one disk fails, no problem - at your convenience, you can replace it with another of the same (or larger) size, and you won't lose any of your files.

So, in your situation, you could take your two 36.7GB disks and make them into one RAID1 disk of 36.7GB, with a command like:

sudo mdadm --create --level=1 --raid-devices=2 /dev/hda /dev/hdb

(assuming hda and hdb are your 36.7 GB disks; don't try this command on a computer with important data on it).  You'll get a device called /dev/md0 that is your RAID1 mirror, this will look just like a single 36.7GB hard disk.  You can do the same with your 67.8 GB disks to get /dev/md1.  Then, you can use LVM to combine /dev/md0 and /dev/md1 into one (100GB) logical volume, and make partitions out of that.

On my server, at least one hard drive dies about every year-and-a-half or so, but I don't have to worry about it with RAID1.  RAID+LVM can be complicated, but since you have this empty server to play around with, now might be a good time to learn.

The guide I always use for LVM is here:

[http://www.tldp.org/HOWTO/LVM-HOWTO/index.html](http://www.tldp.org/HOWTO/LVM-HOWTO/index.html)

But it doesn't really talk about RAID.  When creating your physical volumes, you would use /dev/md0 and /dev/md1 instead of /dev/hda and /dev/hdb and so on, if you want to use RAID.  If you don't, you can just use it as-is.

I also think having GNOME on a server doesn't make it "not a server" and I always use the desktop CD for installing.  Along with a web server, you'll probably want an SSH server, and Samba for serving files to windows machines on your network.

---

### Post by houstonbofh on 2006-12-06
What kind of RAID?  First, RAID on a RAID card will be much faster than software RAID.  But some RAID cards have poor support...  So, a little info on branding will help here.

---

### Post by Brazen on 2006-12-06
BTW: ask for a laptop from here: [http://system76.com](http://system76.com) and help support Ubuntu from an OEM.

---

### Post by OttifantSir on 2006-12-06
1- Well, the server isn't empty.

2- I do not intend to use Windows.

3- When I got it, it was set up as RAID 1, but I wanted more storage, less fail-safe.

4- I have asked for a laptop from System76, but I live in Norway. They don't ship to me.

5- The server is a Compaq (I know, discontinued) ML 370/G2.

6- It's got (according to Units in Windows' System) two Compaq 64bits/66Mhz Dual Channel Wide Ultra3 SCSI-cards.

7- RAID controller is at the top of the list saying it isn't installed. If it's software or not, I don't know.

I just wish to store files on it, and access these files from a laptop. Eventually, I will be using nothing but Linux.

---

### Post by elst on 2006-12-06
All that you really need is SSH - this securely handles both command-line access and file transfer. Both GNOME and KDE provide you with graphical access to files over SSH in the same way as with other protocols.

A slightly more elaborate solution is Subversion - this provides remote access to the files that it manages over SSH and HTTP/WebDAV, and means that you have access to every version of your files.

Given the age of the server I'd strongly recommend thinking about off-line backups. If a fan or the power supply fails then all of your data is trapped on a computer that won't be quick or cost-effective to repair (because of the parts involved).

---

### Post by OttifantSir on 2006-12-06
Ok, so what would be my choice in the 6.10 Server Installation menu?

Would/could this be handled with Remote Desktop?

It would be OK to be able to send print jobs to this, as it would be in a fixed space, and laser printers are quite cumbersome to lug around.

Do I need more then?

Still have found no answer to whether all my files will be deleted if I want to use Logical Volume Management. (I assume this is the case)

---

### Post by elst on 2006-12-06
For SSH, install the server without selecting any tasks, and then:

sudo aptitude update
sudo aptitude upgrade
sudo aptitude install openssh-server

Remote desktop stuff just provides graphical displays, not file transfer.

The standard printing service (CUPS) may be configured to accept jobs from remote clients.

Switching to LVM basically involves reformatting the drives, so yes, you need to do this before you put data on the system.

---

### Post by OttifantSir on 2006-12-06
OK, I won't be using Remote Desktop to access and store files on the server, but will it be up to the task of managing it?

I had forgotten about CUPS. Thanks for reminding me.

---

### Post by andyjenkins on 2006-12-06
Using LVM without RAID is fine.  Beware that the failure time of your LVM logical volume (the four disks combined) is now the minimum of the failure time of each of the disks (i.e. the first disk to fail will bring down the whole logical volume), which makes this less reliable than one equally-reliable 200GB disk (not fear-mongering, just FYI).  You may be able to recover some data if only 1 disk goes down, but you may not (I've never successfully recovered data from LVM when 1 pv dies, others may have better advice).

You may be able to create this whole setup without having to make other backups of your data, assuming you don't already have 200GB of data.  For instance, assuming you have 100GB of data right now (on 1 67GB and 1 36GB), you can make pv's (physical volumes) on the other two disks, create a vg (volume group) containing these new pvs.   Then create a lv (logical volume) on these (empty) disks of size 100GB, copy your data from the used 67 and 36 to this new lv, verify that it's all copied over OK.  You'd have:

newvg(100GB): newlv  100GB (with new copy of data)
hdc    67GB  (with 2/3 of original data)
hdd    36GB  (with 1/3 of original data)

Then, (after verifying everything is on newlv OK), you can wipe hdc and hdd, make new pvs on them, and then use 'vgextend' to add them to the vg for newlv.  So now, you'd have:

newvg(200GB): newlv  100GB (with data), +100GB of empty space

Then, you resize newlv to be 200GB (ext3 is easy to resize, most others are resizeable too).  There's a guide here: [https://fcp.surfsite.org/modules/smartfaq/faq.php?faqid=279](https://fcp.surfsite.org/modules/smartfaq/faq.php?faqid=279) for doing this on Fedora (concepts and most commands would be the same).  I'm sure myself and others can modify this to be the Ubuntu way if you're interested.  It may be easier for you to just back up the data and start clean, if this seems confusing or you don't want to risk it (backups never hurt).  I have done this vgextend thing when I upgraded from 67GB disks to 200GB disks and my power supply didn't like having 4 hard drives at once.  You could also try this concept out with a 'fake' LVM setup on one disk beforehand (using smaller partitions), since it's unwise to play with LVM the first time on real data.  Sounds like either way, you'll have a pretty cool setup.

---

### Post by OttifantSir on 2006-12-07
Yeah, nothing wrong with backups, it's just time-consuming to write it out to discs, and I'm not good at making plans for backing up my data. At some point I lose control of what's been backed up and what's not. This resulting in having four CDs with My Documents and each containing almost the same.

Thanks for the offer to port the manual to Ubuntu. I will have a look at it before I take you up on the offer, or see if I will try do to a backup. At the moment, I have apx 100 GB total, but spread over four hard-drives. Windows and programs on one (36.7), documents on one (36.7), and videos on both the 67.2-disks. All in all, excluding the programs I won't be using, it's about 100 GB. So, I hope I can get it done without too much fuss.

I hope to end up (when I get the new laptop) with this: This outdated laptop is still usable enough to be a worthy replacement of my stereo (bad stereo, better speakers on the server that can be mounted to this laptop), the server doing what it's supposed to: Store files and give access to them on both this laptop and the new, and the new laptop will be the true day-to-day computer.

Too bad the Dell XPS M2010 is so expensive. Unless I get a flat-screen for Christmas, I have to save up for it. That computer has so much built-in that if I could have that, I could, with the previous plan, also get rid of my DVD-burner (for TV only), my stereo and TV, the huge CRT-screen now located with my server, and use the wireless keyboard and mouse I have on it to sit comfortably without an oven in my lap and do whatever I wanted to do digitally. However, that's the dream. Reality won't be far behind, but not quite as perfect.

---

### Post by houstonbofh on 2006-12-07
> **OttifantSir said:**
> 3- When I got it, it was set up as RAID 1, but I wanted more storage, less fail-safe.

5- The server is a Compaq (I know, discontinued) ML 370/G2.

6- It's got (according to Units in Windows' System) two Compaq 64bits/66Mhz Dual Channel Wide Ultra3 SCSI-cards.

7- RAID controller is at the top of the list saying it isn't installed. If it's software or not, I don't know.


This could be a major nightmare.  I have a lot of experience with these old Compaqs...  Some of it good...

To start, go to the HP website (or where ever you can) and get a "Smart Start" CD.  **Find out what RAID card you have!**  One Compaq RAID card worked out of the box.  One required major work loading it into the boot image.  One only worked under Debian Sarge.  However, if you do have a RAID card, you can configure your like drives as two different sized RAID 1 mirrors.  Then LVM the resulting two drives safely.

Now on to video.  The onboard card is crap, and will take work to work in X.  You will need to remove the 16+ bit options, or it will try for a resolution you don't have the video memory for and drop to VGA.  Just set it for 8-bit and all is good.  Ugly, but it's a server...

If you are using the built in Compaq Ethernet card, it may be a Thunder-Lan nightmare.  They can auto-negotiate wrong.  Bouncing the interface will fix it. (Or a new card)

All that said, once you get it running, you won't have to ever touch it again.  Solid boxes.

---

### Post by OttifantSir on 2006-12-09
I got a box I got from the guy who gave me this server, with 5 CDs and a floppy in it. From Compaq. I had it to a local computer shop to help me get the RAID working as I would like, as I hadn't even heard of it prior to obtaining the server, and didn't know how to work it. That earned me another box with two CDs (from HP).
I have looked at these CDs, but I can't figure them out. I can't find anything useful on them.
That is mostly because of my inexperience with servers I guess.
I have visited the HP website, but I can't find information on my server. If you, or anyone, have any documentation on it, I will be glad for the help. It seems HP doesn't provide this. I used about two weeks, every day, looking for help from HP's site, and nothing useful came of it.

As for the built-in Ethernet card, it was another card in the box when I got it. It seemed almost like a second motherboard, it tried to do so much: Video, Ethernet, sound. I took the card out of the box and took it to the same local computer store I employed for my RAID-settings, and they took a look at it and said that it was something they hadn't ever seen. They could see what it was supposed to do, but that it would probably be more expensive hunting down info, drivers and know-how to use it, then actually buying a second Ethernet-card, chep (yet better than built-in) graphics card and sound card (I got mine from a Norwegian web-market for apx $8.50). What is Thunder-LAN?

The on-board graphics seem to be really good. I have the option of a refresh-rate of upto 100 Mhz, 1600x1200, Millions of colours, 24-bit setting. And off course, anything lower.

Well, to find out which RAID-card I have, what do I do? Apart from loading the Smart Start CD? Where do I find the info?

---

### Post by houstonbofh on 2006-12-10
You boot from the Smart Start CD.  It will have lots of wonderfull tools, like a system erase utility (HD, BIOS, and RAID config) diagnostics, and a RAID configuration utility.  Also, at boot time, it will show on the screen.  Something like "Smart 2/P" or "Smart 2/DH" will flash before it spins up the drives.

And Thunder-LAN was a nasty chipset for ethernet.  I used to work for Compaq, and I still have nightmares about that card.

Now as to your specs... [http://h18000.www1.hp.com/products/servers/ProLiantml370/description.html](http://h18000.www1.hp.com/products/servers/ProLiantml370/description.html)

Not sure where you are, but the US version specs.
[http://h18000.www1.hp.com/products/quickspecs/10901_na/10901_na.html](http://h18000.www1.hp.com/products/quickspecs/10901_na/10901_na.html)
Q & A
[http://h18000.www1.hp.com/products/servers/proliantml370/questionsanswers-G2.html](http://h18000.www1.hp.com/products/servers/proliantml370/questionsanswers-G2.html)

Note the **slight** difference in links.  (ProLiant vs proliant)  Both link to similar, but slightly different versions of the same material.

---

### Post by chrisfay on 2006-12-10
[sarcasm]Good luck with the Compaq! [/sarcasm]

I was given the task to build an internal website for my corporation and the server they gave me to use was an old depricated Compaq Proliant DL360. I had a nightmare getting the stock RAID controller to work with the Ubuntu installation due to a known bug i found after a couple hours of diggin.

If you have a problem with the installation, it may be due to Ubuntu's failure to recognize the cpqarray module on bootup. You have to use your install cd to manually add the module into etc/initframsfs-tools/modules and recompile the kernal iso. After that all is well....

Here's a link to a post here related to it:
[http://ubuntuforums.org/showthread.php?t=255335&page=2&highlight=compaq+proliant](http://ubuntuforums.org/showthread.php?t=255335&page=2&highlight=compaq+proliant)

Just a heads up if you have the same problem...:-D

---

### Post by houstonbofh on 2006-12-10
For the record, you do not have to re-compile the kernel.  You just have to have the driver in the boot image.  This is not just limited to Compaq.  I had to go through the same thing with a DAC960 array controller.  What really ticks me off is that Debian Sarge lodes them fine!!! :evil: Anyway, that is why I was trying to get him to tell me what controller he has.  I have been done that road more than once!  But once you know the way it is not that bad.

---

### Post by chrisfay on 2006-12-10
> For the record, you do not have to re-compile the kernel.

Yeah, thats right...thanks for clearing that up.

---

### Post by PanzerMKZ on 2006-12-11
btw if that nic you took out has vid on it also more then likely a remote access card.  As for file sharing you might want to look into a few different things.  Such as Samba or ftp server.  Currently I run both on a home network.  linux can mount a smb drive really easy.  for the ftp server I am currently running vsftpd.  Just apt-get and set conf like you want.  Have not yet tried to share printers.  but other then that you should be all set.  Will ssh is a must.  Then just make sure your bios is setup not to error on anything.  A deadhead box is alot easier since you don't have to worry with connecting anything up to it.  Other then network and power.  Thanks folks for the raid links.   I got to check on that cause I got a dac960 that boots correctly but when I start transfering to it via ftp it just slows to a crawl(this is dev server).  Main server runs sweet. dual 500 cel with 256 ram. 2x18gig scsi and one 320gig IDE.


Panzer

---

