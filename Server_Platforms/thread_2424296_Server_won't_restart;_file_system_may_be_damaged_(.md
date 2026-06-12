---
title: "Server won't restart; file system may be damaged (16.04)"
date: 2019-08-06
forum: Server Platforms
---

### Post by ceriana on 2019-08-06
Good morning,

this morning, our MySQL server crashed out of nowhere. After just restarting the MySQL server didn't work, the guys at the hosters hotline told me to restart the whole server (running on 16.04), which I did via their cloud control center.
This led to some dubious error messages:

[IMG]https://i.imgur.com/gIbobod.png[/IMG]

Phoning the hotline again, the support staff told me that the file system might be corrupted, and I have to mount Knoppix to repair it. Ok, fine.

To be honest: from this point on, I have no idea what to do without breaking the whole system. I'm inside the mounted Knoppix, but how do I repair the given errors?

If you need more information, feel free to ask.

Thank you.

---

### Post by TheFu on 2019-08-06
You don't **need** to use knoppix.  That was just someone's suggestion.  I don't know if knoppix has LVM tools or not, but there is mention of an LVM LV not being available.  This may or may not be important.  If the boot device isn't found, looking for LVM LVs might just be the next step. IDK.

If it were me, I'd delete the VM and start fresh with a new one, then restore from my backups.  The box would be back up and running again in about 45 min, at the most.

How bad is it if all the data is lost?

If you are paying that company for support, then they should run the fsck and disk checking tools for you. Inside a VM, as this machine appears to be, that will be of limited use, since it is unlikely the VM has direct access to the disk controller or disk hardware. 

Please post text. We can't copy/paste images like we can with text. Too start, 
```
sudo fdisk -l
lsblk
```
with code tags so everything lines up correctly.  If it doesn't look the same posted here as it does in the terminal, please fix it.

---

### Post by SeijiSensei on 2019-08-06
I use Linode for cloud hosting and pay a few extra bucks each month for them to take snapshot backups of the whole system each night.  If disaster strikes, I can use the snapshot to spin up a new VM.  Haven't used this often, but when I've needed it, it was worth every penny.

Of course, I also back up all the important files on the VM to a disk in my home office.  That's easier when you just need to restore a few files.

I also use the mysqldump and pg_dump utilities to create plain-text backups of my MySQL and PostgreSQL servers each night.  Those files get shipped to my home office as well.

---

### Post by CharlesA on 2019-08-06
I've had this stuff happen to me before and it isn't fun to try to recover from it. If you are able to mount a liveCD, you can try the steps listed here to determine if you can mount the lvm and fsck the file system.
[https://askubuntu.com/questions/26886/fixing-unbootable-installation-on-lvm-root-from-desktop-livecd](https://askubuntu.com/questions/26886/fixing-unbootable-installation-on-lvm-root-from-desktop-livecd)

---

### Post by LHammonds on 2019-08-07
> **ceriana said:**
> this morning, our MySQL server crashed out of nowhere.

Although you might be able to get the server to boot up eventually, I am not sure you want your database server to continue forward with potentially corrupted data.

If it were me, I would create a new VM and restore my database backups (mysqldump .sql files) and re-cycle the old IP address and move on from there.

But you have not said if you have backups.  Please tell me you have multiple backups of your database.

LHammonds

---

