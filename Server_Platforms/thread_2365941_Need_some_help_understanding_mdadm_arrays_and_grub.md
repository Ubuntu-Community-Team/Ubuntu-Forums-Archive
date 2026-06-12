---
title: "Need some help understanding mdadm arrays and grub config"
date: 2017-07-12
forum: Server Platforms
---

### Post by david_silvester on 2017-07-12
I need some help to understand the config of my linux system, specifically the mdadm arrays and the boot config.

Background to this problem is that I have just upgraded my ubuntu installation from 14.04.5 LTS to 16.04.2 LTS using the command do-release-upgrade
Everything seemed to go well, except for right at the end when I get this warning - 

the array /dev/md/server-name:3 with UUID c9403cc0:269c850c:834a7d9a:02fe77e4 is currently active, but it is not listed in mdadm.conf.
if it is needed for boot, then YOUR SYSTEM IS NOW UNBOOTABLE!

Obviously thats worrying me! However, I checked and this array is just a data array, not the boot drive.

It is not listed in mdadm.conf but my other 3 arrays (Including boot partition) are listed. I dont know if this is a problem, should all arrays be listed in mdadm.conf?

When I set up this array, I added it to /etc/fstab and I understood that should be enough to have it mounted at boot time. Is that right?
And rather than listing it by its uuid i have just listed it as follows - 

/dev/md127 /backups2 auto defaults 0 0

Is that ok?

Now from this I have found something else that I don't understand - 

I see a list of my arrays in these two places - 

/etc/fstab
mdadm.conf

But in both places they have different uuids. Is that normal? Or are those two locations referencing different things?

Sorry guys for the bad terminology, I dont fully understand this stuff - still learning :-)

---

### Post by darkod on 2017-07-12
You got that message because only the arrays that are defined with ARRAY definition in mdadm.conf will get assembled on boot.

First get the array UUID using this command:
```
sudo blkid
```

Note that the array members (for each array) have a common UUID identifier, but have different unique UUID_SUB. That common UUID is the array UUID. Copy it and create a definition for your array in mdadm.conf, for example:
```
ARRAY /dev/md3 UUID=40a73183:f7e7e999:93c0acc5:7ff5d0d1
```

On the other hand, the UUID you put in fstab is the UUID of the filesystem that is on the md device. You will also see it in the blkid results. You use this UUID to create the line in fstab to automount the array on boot. And that will be a different UUID from the one you used in mdadm.conf.

---

### Post by david_silvester on 2017-07-13
Thanks for confirming that. I am starting to understand.

I found the UUID for the array that is not listed in mdadm.conf, it is - c9403cc0-269c-850c-834a-7d9a02fe77e4

Currently in mdadm.conf the existing 3 arrays are listed in this format - 

ARRAY /dev/md/0 metadata=1.2 UUID=346b09ac:57ef85eb:afb6a56d:f4e77077 name=server:0
ARRAY /dev/md/1 metadata=1.2 UUID=bb696ba1:296ef2d7:65054677:0853eb8d name=server:1
ARRAY /dev/md/2 metadata=1.2 UUID=9e7bfde0:2b611c75:08dd114b:2ba28332 name=server:2



As per results from the sudo blkid command the missing array is /dev/md127

So in mdadm.conf should I be listing it as follows - 

ARRAY /dev/md/127 metadata=1.2 UUID=c9403cc0-269c-850c-834a-7d9a02fe77e4 name=server:3

?

---

### Post by darkod on 2017-07-13
Actually you can put it /dev/md3 and it will have that name on each boot/assemble. The 127 is used sometimes by the system but you are not obligated to use it.

Also the metadata version is not necessary but you can leave it, or not, as you wish...

Be careful if you change its name to /dev/md3 and if you are using /dev/md127 in fstab. But you already said you use UUID in fstab so changing the device name would not matter.

---

### Post by david_silvester on 2017-07-13
OK thanks. Although the first 3 arrays are referenced using their UUIDs in fstab, the 4th array is referenced via /dev/md127 (I think the first 3 were added automatically because i created them during setup but 4th one was added by me at a later date). So as such I have stuck with [COLOR=#000000]ARRAY /dev/md/127 ... in mdadm.conf.

I am going on site tomorrow so I will reboot and I will let you know if it all boots back up again :-) Thanks a lot for your help.[/COLOR]

---

