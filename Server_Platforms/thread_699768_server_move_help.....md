---
title: "server move help...."
date: 2008-02-17
forum: Server Platforms
---

### Post by hockey97 on 2008-02-17
Hi I have  ubuntu 7.10 and windows xp on my main computer that I use for personal stuff ect. I setup a ubuntu server on it and have a dual boot.

I am soon going to finish making my website and found out a problem.
I use this main computer with windows xp mostly to make the art of my websites ect and play games the whole time. I already have ubuntu all setup and have mysql and apache2 on it already and I would hate to redo all that again. I plan to move the server to my new computer but I don't want to have to go through all the setup and config on that new computer.

Is their a way I can copy everything on my main computer that has the ubuntu os  and  put it on my new computer so when I boot up the new computer I would have everything the same as what it was on my main computer??

I want to copy ubuntu files ect and everything that is already on my main computer and put it on my new computer so the new computer would the the server and the main computer would be the backup server.

So I want to copy all ubuntu files from the main computer and put it on the new computer to be able to boot with the new computer to the same exact ubuntu that was on my main computer.

---

### Post by cdenley on 2008-02-18
So basically, you want to copy your hard drive? This would work assuming you have a 32-bit install, or they are both 64-bit systems.

-install the new hard drive in the old system (temporarily)
-boot to the livecd
-partition the new hard drive with gparted
-mount the new root filesystem
-copy files from old root filesystem to new root filesystem
-run this command with /dev/sdb being the path to the new hard drive, and /media/newdisk being where the new root filesytem is mounted
```

sudo grub-install --root-directory=/media/newdisk /dev/sdb

```

If the new system has different drive assignments, or the partitioning on the drives are different, you will have to change your grub configuration. If you are using a GUI, you may have to change your video driver.

I believe you can also use partimage. I never tried it.

---

### Post by hockey97 on 2008-02-18
Thanks.  I  will give that a try.  The reason I need to to this was that I installed ubuntu on my personal computer and was planning to make it a server how ever I notice that I have games in windows xp and 3d modeling software and gimp on windows xp so I notice I can't have both running  so I decided to use my new computer as the server and my personal computer as backup.

I is possible for me when running windows xp be able to emulate ubuntu or have it running??

I am only using ubuntu as a server and I use windows xp for most things like graphics and webpage developing.

I would really love to be able to run ubuntu while in windows xp.

Well before I try messing with the files I am going to look more into it so I don't mess anything up.  I hate config the web servers and dns server ect it's a pain.

---

