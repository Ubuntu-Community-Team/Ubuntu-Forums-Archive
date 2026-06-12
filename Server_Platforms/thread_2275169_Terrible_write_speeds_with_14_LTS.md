---
title: "Terrible write speeds with 14 LTS"
date: 2015-04-24
forum: Server Platforms
---

### Post by Uranium-235 on 2015-04-24
I had 10 server on my poweredge 1800 (dual xeon 3ghz, 2GB ram). Linux raided (mdadm) raid 1, and two 1TB WD black drives. Eventually, after 3 years, webmin stopped working, but the smb shares were still working. About a year or so later I tried to upgrade it with the in-house upgrade command, and it stopped connecting to my network (upgrade didn't finish, had errors). I knew it was time to upgrade to a the latest LTS

I tried 14 server, got it on, I took one drive out and wiped the other drive and set it for raid 1 (missing disk in array, to be corrected after I copied all the data from the other disk)

after getting webmin on and some finagling, I managed to zero the superblock and mount the other disk to copy data, but writing to the large share partition was SO SLOW. if I did it in webmin, if I use cp -r, or samba itself. As a test I went ahead and set up samba to share the folder, and tried to upload something, over my gigabit network, it was uploading at ~2MB/sec. This was at one time 10 server I would usually be able to write at about ~60MB/s and read at 90MB/s. Another thing I do, is enabled data compression, not sure if its an issue with that or not, didn't effect my old 10 server. On my 10 server I used ext3 (even though I think 4 was available). On the new install I used 4 cause i'd figure it's come along in the past several years. I tried to use webmin to change ide parameters and whatnot, make sure DMA was enabled. 

When I copied directly with sudo cp it would get about 64MB in  half an hour. 

I had no speed issues installing, everything was fast. Any idea? It it related to ext4?

any help would be great. I don't want to have to buy the extra ram and CF card to get FREENAS on there

thanks

---

### Post by TheFu on 2015-04-24
What is "10 server" and "14 server"?
What do the log files show?

I would simplify and test.
Then I would re-simplify and test again after determining if the network or the disks or the controller or something else was at fault.
Then I would watch the log files for issues.

---

### Post by Uranium-235 on 2015-04-24
10 server and 14 server I mean version of ubuntu

how can it be network related, I logged in with SSH and used the cp command

where would those log files be pertaining to the disks?

---

### Post by TheFu on 2015-04-24
You mentioned smb/samba - that's network, right?

System logs /var/log/* go in here. Always. Use **grep** to find the interesting places. Look for cable issues, warnings, errors ... usb resets.  I've seen USB issues stop a server from processing anything for 20-30 sec, then clear up completely and the server works fine for a month, even if the USB storage was just mounted, but not being used.

There were multiple releases in 2010 and 2014. The exact release may matter to someone. They are commonly denoted by "yy.mm".

If the file systems are nearly full, performance can suck.

**cat /proc/mdadm** could be helpful to see the options as might some diags from **hdparm**. 
[http://www.linux-magazine.com/Online/Features/Tune-Your-Hard-Disk-with-hdparm](http://www.linux-magazine.com/Online/Features/Tune-Your-Hard-Disk-with-hdparm)
[http://www.robthomson.me.uk/2011/03/30/tuning-kvm-guests-you-need-to-do-it/](http://www.robthomson.me.uk/2011/03/30/tuning-kvm-guests-you-need-to-do-it/) - the storage part might help

There are disk performance testing tools. Can't recall the names now, sorry. Would be good to create a benchmark script for yourself (or allow some monitoring software to run for a few hrs) before attempting to change things. 

FreeNAS will not be faster. FreeNAS is for ZFS RAIDz2 protection, not for higher performance on a server like this, IMHO.

---

### Post by Uranium-235 on 2015-04-25
well I re-installed, this time made two partitions this time (/ and swap) instead of a dedicated partition for the files
I did notice that it asked me to save changes to my swap part when the partitioner started up before I set everything back up

Still going slow but not as slow as before, using cp -r -v

I'm using compression and sync after writing. 

the light on my receiving HDD is pretty much 100% lit, while the reading drive is barely blinking (though constantly blinking)

---

### Post by darkod on 2015-04-25
One question: Did you wait for the array to be created fully before starting to copy? I know you can use mdadm array right after you create it but note that depending on disk (array) size the initial creating will take some time and if you start copying data it might affect speed because there is lots of load on the disk.

Also, try to stop using webmin. It will only get you into trouble along the line. Use ssh and intend to learn things, if that's your goal. Webmin in many cases treats the config files diffrently and can create instability. That's why it's not officially recommended as admin tool. I understand many people are tempted to use GUI like tool, but you also need to take into account the complications it can make for you.

---

### Post by lisati on 2015-04-25
> **Uranium-235 said:**
> 10 server and 14 server I mean version of ubuntu

Just as an aside, "10" can refer to TWO different versions, 10.04 and 10.10. Likewise with 14.....

---

### Post by Uranium-235 on 2015-04-25
I was generalizing the versions cause my current trouble is no longer with them (10.x), they are gone. True I didn't specify 14. its 14.04.2 LTS

it can't be initialized cause its only one disk. Its a clean volume that is missing a drive. Once I copy the data from the other drive, i'll create the matching partitions and initialize it then. I'm wondering if that might be the reason, not sure if Raid 1 is freaking out cause of the missing member

I use a combination of webmin and console/ssh. Webmin has come a long way and I use it for basic stuff, but yeah, I did have some problems with it, like it not restarting samba from the samba interface, had to use the startup/shutdown interface to reboot samba successfully

---

### Post by darkod on 2015-04-25
It is true that I have never created raid1 with missing member so I can't confirm 100%, but I think even in this case the disk present is divided into chunks, like any raid disk. The fact that it hasn't got a second disk to sync to, is not relevant. The present disk has to be divided in chunks because that can't be done later when you already have data on it and add the second disk, right? This action will take a lot of disk activity which might make the disk slower until the initiliazation is finished.

And I assume you create the array with the 'missing' place holder, otherwise it wouldn't create a raid1 mirror. Something like:
```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 missing
```

(I think I didn't forget any parameter, anyway the important part is to use the 'missing')

---

### Post by Uranium-235 on 2015-04-25
another note, webmin reports my CPU usage is 23% I/O? Is this a raid thing or is DMA disabled

---

### Post by Uranium-235 on 2015-04-27
wow, ok, well I was using putty on my laptop for the cp command and in the webmin file manager it showed the file size increasing at about 1M a second. I had to leave my laptop set to keep on when shut the past 3 days to copy that data from the old drive to the new. I did it this time at the console itself and noticed a huge difference of about 100M/sec

then I noticed compression was not turned on, on the newly created folder. Turned it on, went back down. so I guess we now know what the problem is (technically isn't a problem or bug, but a fact). I don't remember having this issue with EXT3, but I'm not sure I paid that much attention to the write speed back when I had less data

---

