---
title: "Reinstall without destroying /home Raid"
date: 2011-10-02
forum: Server Platforms
---

### Post by kleverbear on 2011-10-02
Hi all, i need some advice/help on a goof up.

I have headless Ubuntu 10.04 LAMP/Samba server running on a Intel Atom 270 with 2g Ram and here's were i did the mistake. My / is on a 2g CF card and the /opt is on a 40g partition of a 80g HDD, the /home is on a 2.7tb Raid 5. 

The / was supposed to be on the first partition of 40g and the /var on the second 40g partition of the same hdd, the swap was to be on the 2g CF and /home on the raid. In my drunk stupor i did not realize my mistake till I installed Webmin and noticed the system info showed as 2g drive. Confirmed this via fdisk :(

So how can i fix this without destroying /home i've loaded almost half of it already.  Any suggestions are welcomed, except those to not drink and install. :)


Thanks in advance, Chris

---

### Post by kleverbear on 2011-10-03
Anyone??

---

### Post by Vegan on 2011-10-03
make a backup first before anything drastic

---

### Post by kleverbear on 2011-10-03
Yeah I got that part done but i didn't back up my home folder its to big. So even then I'm in trouble. I did 
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude= /home /

to grab all my confs in one snap shot. But i recall correctly i still have to remake all my /mnt /sys/lost+found /proc /home .

---

### Post by kleverbear on 2011-10-03
Bump...

---

### Post by HermanAB on 2011-10-04
Simple really.  You can re-install and just don't format /home - leave it be.

---

### Post by Jonathan L on 2011-10-04
> **kleverbear said:**
> Hi all, i need some advice/help on a goof up.

I have headless Ubuntu 10.04 LAMP/Samba server running on a Intel Atom 270 with 2g Ram and here's were i did the mistake. My / is on a 2g CF card and the /opt is on a 40g partition of a 80g HDD, the /home is on a 2.7tb Raid 5. 

The / was supposed to be on the first partition of 40g and the /var on the second 40g partition of the same hdd, the swap was to be on the 2g CF and /home on the raid. In my drunk stupor i did not realize my mistake till I installed Webmin and noticed the system info showed as 2g drive. Confirmed this via fdisk :(

So how can i fix this without destroying /home i've loaded almost half of it already.  Any suggestions are welcomed, except those to not drink and install. :)


Thanks in advance, Chris

Hi Chris

As Herman says, when you do your install, choose "Manual" for the installation process.  Don't reformat your disk.  But I'd definitely try to tar up /home onto /var then ftp that somewhere just in case.  _Really do it: if you make a single mistake in the reinstallation it will be gone._

Making backups when you've run out of space can be tricky, but here's some ideas.  If the free space of /var is enough to fit a tar of /home, then do that and copy the big tarfile off your computer by ftp.  If you need to split it into pieces for copying purposes, use tar -M -L 5000000 of tar to make 5Mbyte pieces; then you can for example store them on (perhaps a few) free google accounts temporarily).  (Good examples here [http://paulbradley.tv/44/](http://paulbradley.tv/44/))  Or of course if you can borrow a friend's computer you could mount it over a LAN and tar directly; best way if there's not enough space in /var.  Or if you have access to Amazon Web Services you could just make a disk for a few hours and use that.  I do recommend tar for this kind of thing as opposed to anything else, but have also had good results from rsync and similar if you're copying to a similar filesystem type.

And just in passing, are you sure your want to use a CF card for swap?  They can be slow for writing and have limits on the number of writes.  CF for / and hard disk for everything else sounds quite good to me!

Just some thoughts.

Regards
Jonathan.

---

### Post by a2j on 2011-10-04
I'd get 3TB external drive and back it up to it.
what is gonna happen to your data when your raid5 goes down? without regular backups...

---

### Post by kleverbear on 2011-10-04
> **Jonathan L said:**
> Hi Chris


Or of course if you can borrow a friend's computer you could mount it over a LAN and tar directly; best way if there's not enough space in /var.

I was not familiar with this process. I'll look this up. This would would be better to create a back up on to my local. 
Im thinking to unmount /home then backup. Re-install and mount /home after, also Ill be upgrading that 2gb cf to a 16gb and installing on to it and using the 80gb hdd for /var.  How does that sound?


@HermanAB thanks i just was not sure if it would work. 
@a2j I do have offsite back up 3main folders in my raid, primarily my pictures folder since i collect all of our extended family fotos. I let them upload to it so i can keep them in storage and backup. Been using mozy back up. Works well.

---

