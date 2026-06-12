---
title: "Weird stuff happening between ubuntu and windows network"
date: 2008-10-09
forum: Server Platforms
---

### Post by effec on 2008-10-09
I have my ubuntu machine setup on my network. Yesterday, all was great, i got a shared file up (files) and was set. Today however, I was no longer able to access my ubuntu server from windows. 

When i went to take a look at the server i noticed that the desktop folder i created (files) was gone! I was pissed, but got over it quick and just created a new one named (crater). I checked the network settings and everything looked ok. Now for the weird stuff. From windows, I can still see and open the old files from inside the 1st folder i created. I get prompted (files may be corrupt blah blah). Now , i go back to the ubuntu server looking for the file folder.....and its no where. Also, for some reason, ubuntu setup its own workgroup. My workgroup is named thegalaxy and ubuntu is in "workgroup"

Whats going on?

---

### Post by lykwydchykyn on 2008-10-09
How reliable is the hardware?  Is it possible there is a disk or memory failure?

can you post your smb.conf file?

---

### Post by agray on 2008-10-10
Not sure why your folder keeps disappearing, but as far as the two computers having different workgroups, well samba comes with the default workgroup as "WORKGROUP" just like a windows computer does.  You have to go into your samba config file and just edit the line that says "workgroup = " to whatever your workgroup name is, the restart the samba service and then they should be on the same workgroup.  This is how it worked for me anyways, good luck.

---

### Post by cdenley on 2008-10-10
I've only seen files disappear when the hard drive is dead. I've seen computers run from memory for days with a dead hard drive, writing any disk changes to the disk cache in memory, never successfully writing it to disk.

---

### Post by effec on 2008-10-10
> **lykwydchykyn said:**
> How reliable is the hardware?  Is it possible there is a disk or memory failure?

can you post your smb.conf file?

I dont think it is a hard drive issue, because the drives were running fine under windows xp for about 2 years. But I guess it is still possible. Just to be sure, does Ubuntu have any kind of software to test harddrives for failure?

Also, how do you access the smb.conf file?

---

### Post by lykwydchykyn on 2008-10-10
smb.conf is at /etc/samba/smb.conf

You can test the HDD with the "badblocks" and "fsck" commands.  It's best if you run these from a liveCD while the filesystem in question isn't mounted (in fact, for fsck it's required).  You'd run them like this:
```

badblocks -v /dev/sda
fsck /dev/sda1

```

You can also run memtest from the liveCD's boot menu to test the RAM.  Just FYI, even if all these tests pass, it's possible that there are physical problems, I've seen devices pass these tests that turned out to be bad.

---

### Post by effec on 2008-10-10
Thanks for all the help. I was able to get my server off the other workgroup and still have access to "crater", my shared folder. 

However, I can still see "files on mars" from my windows client. This folder was the first shared folder I created on my ubuntu server - the one that dissapeared from my ubuntu desktop. I still cannot located it on the ubuntu server. How can I find it and delete it?

---

### Post by lykwydchykyn on 2008-10-10
In /etc/samba/smb.conf, you should see an entry something like this:
```

[files on mars]
path = /path/to/filesOnMars
something = blah
something else = blablah

```

That should tell you the path to the folder being shared.

---

### Post by effec on 2008-10-11
Looks like its on /root/desktop

Is there a way to safely delete this?

What i dont get about ubuntu is how can i create desktop file in root if I cant even log in as root.

Geeze, this is confusin.

Also the folders that are inside my shared folder are locked for some reason? Why are the folders and files locked now?

---

### Post by cariboo on 2008-10-11
There two ways I can think of right off of the top of my head if you type in a terminal:

```
sudo -i
```

You drop to root's directory right away and if you use:

```
gksu nautilus
```

You also start in root's directory

Jim

---

