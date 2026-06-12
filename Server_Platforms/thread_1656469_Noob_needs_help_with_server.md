---
title: "Noob needs help with server"
date: 2010-12-30
forum: Server Platforms
---

### Post by hosinfefer on 2010-12-30
Hi,

Sorry for the long post..but dont want to leave anything out.


I have built a dual cpu amd server with 32gb of ram and 16 cores. I have 1 vertex 2 64gb for boot drive and a 9.5TB raid 5 for storage (adaptec raid). I am having a large amount of trouble getting the system to boot off the ssd. I have ubuntu 10.10 server loaded right now and I walked through the installer with no probelms. It asks me to eject the disk and reboot into the system. When the reboot is complete I just get a black screen with a blink "_" in the top left corner. No error msg or anything. I want to use this as a file server and a VM host. 

Can someone help plz?

---

### Post by kevinthecomputerguy on 2010-12-31
Its probably trying to boot off the raid card. Disable all raid in your bios, and reboot. If all else fails, remove the raid card, walk through the install again, and then when all is well, re-introduce the raid card.

---

### Post by hosinfefer on 2010-12-31
I have done this and it does not work. I have gone into bios and set the first boot device to CD ROM and second boot device to OCZ Vertex. It see the name of the ssd right in bios. I have everything else turned off in bios for boot. I have also done like you said and removed everything and still not working. I have also loaded 2 different ssd (ocz and intel) and both failed. any other thoughts?

---

### Post by CharlesA on 2010-12-31
Could it be possible that it's not loading grub onto the ssd? I'm not quite sure if they have an MBR in the same way as a HDD does.

---

### Post by hosinfefer on 2010-12-31
thats what a friend was saying. Is it possible to manually load grub on the ssd. If I load grub on the 9.5tb raid will it decrease the performace of the ubuntu os runnning on the ssd? I am not sure how to get this working.

---

### Post by CharlesA on 2010-12-31
Are you able to boot off a livecd and try to install grub on the ssd manually?

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

As far as I know, an SSD should work the same as a HDD, but as I don't have one, I can't be 100% sure.

---

### Post by hosinfefer on 2010-12-31
not sure how to do that. If I boot from live cd then go to terminal where do I go from there? Do I need the computer hooked up to internet?

---

### Post by CharlesA on 2010-12-31
> **hosinfefer said:**
> not sure how to do that. If I boot from live cd then go to terminal where do I go from there? Do I need the computer hooked up to internet?
Did you read [this]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD") part of the above link?

---

### Post by hosinfefer on 2011-01-01
ok so on step 4 i treid doing the command

sudo mount /dev/sdb /mnt

I get back "mount: /dev/sdb already mounted or /mnt busy

---

### Post by kevinthecomputerguy on 2011-01-01
Add a "1" to sdb and make a new folder in /mnt 
Example ext3 mount =
Sudo mount -t ext3 /dev/sdb1 /mnt/newfolder

---

### Post by kevinthecomputerguy on 2011-01-01
Add a "1" to sdb and make a new folder in /mnt 
Example ext3 mount =
Sudo mount -t ext3 /dev/sdb1 /mnt/newfolder

---

### Post by hosinfefer on 2011-01-01
wow fast reply..didnt think I would hear back for a bit.

Now it looks like the drive was already mounted. didnt know how\where. I did a mount -l and I seen the sdb 60gb which is my ssd mounted uner /media/2XXXXXXXXXXXXXXXXXXXXXxXXX (really long sting). I then did the sudo grub -install --root-directory=/media/2XXXXXXXXXXXXXXXXXXXX/ /dev/sdb. It did some things and asked to reboot. Now when i reboot without the CD I get a grub>...when I type sudo grub-update i get error 27. Think I am getting there but stuck again

---

### Post by hosinfefer on 2011-01-02
nvm got it. thanks everyone

---

