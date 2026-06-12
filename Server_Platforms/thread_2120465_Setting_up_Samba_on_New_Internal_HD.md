---
title: "Setting up Samba on New Internal HD"
date: 2013-02-26
forum: Server Platforms
---

### Post by artemenko on 2013-02-26
Hi all --
 
So I can get samba working for a folder on my main hard drive with a single user I call "dru" and a password.
 
I recently added a new 1TB Western Digital Blue hard drive and it is making me pull my hair out.
 
I used Gparted to format/partition the new drive.  At some point I think I mounted it.  I was able to setup sharing, but that was only when I used "sudo nautiulus" and right-clicked a new folder on the new hard drive and setup sharing.
 
I am totally confused about sharing inside ubunut and sharing with Samba.
 
At the end of the day, all I was is one folder in the main drive and one folder in the new drive that I can put movies into.  Using the same user "dru" to access both is ideal.
 
I'm afraid I've completely tangled up the Samba settings and am contemplating a fresh install.
 
Help?

---

### Post by darkod on 2013-02-26
First of all, did you make an entry in fstab so it can mount the disk on boot? Clicking it in nautilus only mounts it temporary. Also, it mounts it in /media which is not the best solution.

Create a mount point for example /data2, to mark that it's the second disk:
sudo mkdir /data2

After that you can make an entry for the ext4 partition on the disk in /etc/fstab, like:
```
UUID=<string>   /data2   ext4   defaults   0   2
```

You can get the UUID strings for all partitions with:
sudo blkid

That line in fstab will mount it each time on boot, and always at /data2.

After that you only need to define a samba share from /data2 and that's it. I see you use the GUI in nautilus and right-click, you can also do it in terminal in /etc/samba/smb.conf.

In any case it should work. Try working more in terminal, like creating the /data2 folder, etc. It's easier and cleaner. Other things that you want to do in the GUI, like actually sharing the /data2, you can.

---

### Post by artemenko on 2013-02-26
Thx DarkoD -- love that movie btw!
 
>  
First of all, did you make an entry in fstab so it can mount the disk on boot? Clicking it in nautilus only mounts it temporary. Also, it mounts it in /media which is not the best solution.

 
OK that explains why it worked temporarily! And yes it dumped it in media. I do not know how to use fstab.
 
How does Ubunto know that ```
sudo mkdir /data2
``` is for the second drive? That always confused me when setting up mountpoints. Also Gparted seemed to mount automatically too? After I format the drive, the "mount" option is grayed out. Also, I noticed if I don't input a lable, the hard drive gets a crazy long name of letters and numbers like Bae884 ad20931 etc.
 
Also -- I had trouble when trying to follow a guide [here]("http://askubuntu.com/questions/125257/how-do-i-add-an-additional-hard-drive") (link should go to ask ubuntu dotcom question #125257)
 
It says 
**> 2.1 Create a mount point**> 
 
sudo mkdir /hddBut I get a message that it already exists?
 
Hence I went the nautilus route and created a temporary fix.
 
Thanks for all your help man!

---

### Post by darkod on 2013-02-26
/data2 is just a folder you will create, you tell it to mount the second hdd there with the fstab entry line. If you use the UUID of the partition that is on the second disk, that will get mounted at /data2.

If you once created /hdd it will exist even if nothing is mounted there. So, you will not be able to create the same folder again.

To edit fstab you can do it with gedit with sudo permisions, in terminal type:
```
gksu gedit /etc/fstab
```

That will open it for editing. Add the line using the correct string for the correct partition, and it will mount that partition at /data2 all the time.

PS. Just be careful when editing fstab, don't change any of the other lines, just add the line for your new mount. If you are unsure which UUID to use, post the output of:
sudo blkid

and we can help.

---

### Post by artemenko on 2013-03-06
> [COLOR=#000000]Add the line using the correct string for the correct partition, and it will mount that partition at /data2 all the time[/COLOR]

This worked!  Problem solved.  Thanks man!

---

