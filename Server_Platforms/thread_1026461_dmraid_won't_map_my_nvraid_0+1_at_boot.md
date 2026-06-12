---
title: "dmraid won't map my nvraid 0+1 at boot"
date: 2008-12-31
forum: Server Platforms
---

### Post by fronglegoose on 2008-12-31
Hi, I hope someone can help me with this cause I've spent a lot of time on it already.

I'm trying to get a server up and running with ubuntu 8.10 server x64 on an athlon 64 x2 4200 system. It will mainly run vmware server, and VMs will live on this volume. 

I have a nvidia raid set up to do raid 0+1; that's two striped raids mirrored. It's fast in reads, writes and latency and doesn't have to be rebuilt like a raid 5 (which i used to have). This raid worked nicely under windows, but windows itself didn't work nicely, so I'm switching it to linux. 

I can mount this no problem once linux is booted with dmraid -ay. Devices come up under /dev/mapper as eg:
nvidia-bgaffeeff
nvidia-bgaffeeff-0
nvidia-bgaffeeff-1
nvidia-bgaffeeff1
nvidia-bgaffeeff2

the -0 and -1 are the underlying raid 0's and the one without numbers is the mirrored raid 1, so the one you can use parted on. The other two are the two partitions on the volume. 

So I know the configuration works. The only problem is that I am unable to have it brought up on boot so I can put it in fstab. 

As far as I am aware ubuntu has been able to work in this way since 6.06. dmraid is automatically added to the initrd on install. But maybe it doesn't work for more complicated setups like mine? Maybe only simple RAID 0 and 1?

It might be important to note that I also tried installing to this raid, and dmraid brought it up fine, but in the installer it had a red error and said it wasn't able to find the volume or something such; essentially, no matter what I tried it wouldn't work. I even used the alternate x64 disc. 

Have tried:
mkinitramfs -u all -k (and -u `uname -r`) many times and ways
tried generic kernel 2.6.27-9-generic instead of server, and mkinitramfs again
aptitude purge and reinstall dmraid
tried booting desktop live cd but it didn't fully boot?? think that might be a video problem though. 
thoroughly checked ram with bit fade test 2 times and default tests 10 times using memory tester on desktop cd

I'll add more detail if I can think of anything. this is kind of a brain dump.

Thanks very much, and happy new year!

---

### Post by fronglegoose on 2008-12-31
actually that's update-initramfs not mkinitramfs

---

### Post by fronglegoose on 2009-01-01
ok so now I've tried the solution in [http://ubuntuforums.org/showthread.php?t=992559](http://ubuntuforums.org/showthread.php?t=992559) which although for mdadm, sounded very similar. it added a delay into the initramfs-tools init script before mounting volumes, to ensure modules had time to load. I did this and noted the delay occurred (I used up to 50s), but it didn't help.

I suspect there is a bug in the dmraid scripts or hooks because (in /usr/share/initramfs-tools/scripts/local-top/dmraid) it uses dmraid-activate on each raid device (output of dmraid -r -c)and when I use this on the command line it fails to bring up the underlying raids, saying eg

No RAID sets and with names: "nvidia_bgaeeadf-0"

possibly because it hasn't got the other drive, or can't put an underlying raid together without the rest of the raid sets active. I will investigate further.

---

### Post by fronglegoose on 2009-01-01
does anyone know where the dmraid stuff as well as the initrd stuff is logged?? I've grepped everything in /var/log for strings appearing in log messages (like "No RAID sets") and can't find anything. doesn't help debugging.

---

### Post by fronglegoose on 2009-01-01
I've tried making changes to the dmraid initrd scripts, commenting out the dmraid-activate part and adding the command that does work, like so:

```
#for dev in $(dmraid -r -c); do
#       dmraid-activate $(basename $dev)
#done

# above replaced with this which works for complicated raid setups like 0+1
sleep 30
dmraid -ay
```

the sleep is in there so I could tell if it was running; there was no 30s delay, so this file is not being called. and yes, I did an update-initramfs before reboot. this is quite annoying.

---

### Post by nhorvath on 2009-01-15
> **fronglegoose said:**
> I've tried making changes to the dmraid initrd scripts, commenting out the dmraid-activate part and adding the command that does work, like so:

```
#for dev in $(dmraid -r -c); do
#       dmraid-activate $(basename $dev)
#done

# above replaced with this which works for complicated raid setups like 0+1
sleep 30
dmraid -ay
```

the sleep is in there so I could tell if it was running; there was no 30s delay, so this file is not being called. and yes, I did an update-initramfs before reboot. this is quite annoying.


I had this same problem and after much headache figured it out...

you can uncomment the lines you commented out in dmraid, they work

you need to chmod +x dmraid (whoever built this system must have forgotten that part)

i had to put a sleep 10 before the for loop (i might be able to reduce it to 5 but havent tried yet) in order for the devices to be ready to be found when the script ran.

---

### Post by fronglegoose on 2009-01-17
> **nhorvath said:**
> I had this same problem and after much headache figured it out...

you can uncomment the lines you commented out in dmraid, they work

you need to chmod +x dmraid (whoever built this system must have forgotten that part)

i had to put a sleep 10 before the for loop (i might be able to reduce it to 5 but havent tried yet) in order for the devices to be ready to be found when the script ran.

No freakin' way! That's such a massive oversight!

So I chmod +x'd it and uncommented the loop but I got errors on boot as I did before; 'No RAID sets and with names: "nvidia_bgaeeadf-0"' for each disk, which is what you get when you try to bring up the devices individually instead of all at once with dmraid -ay.

So I put my code back in with that and it worked!! It was loaded by fstab at boot and all :)

Now who do I talk to about fixing that permissions bug??

thanks again
frongegoose

---

### Post by fronglegoose on 2009-01-17
So just to clarify, the fix here is:

# make the dmraid initramfs script runnable by initrd (which was already the case with all the other scripts, as we found)
sudo chmod +x /usr/share/initramfs-tools/scripts/local-top/dmraid

# edit that script to add a sleep to allow modules to be ready, and in my case use dmraid instead of dmraid-activate; in fact that should work for everyone if using dmraid works for you.
sudo nano /usr/share/initramfs-tools/scripts/local-top/dmraid
# eg: 
```
# Activate any dmraid arrays that were not identified by udev and vol_id.

#for dev in $(dmraid -r -c); do
#       dmraid-activate $(basename $dev)
#done

# above replaced with this which works for complicated raid setups like 0+1
sleep 10
dmraid -ay

```
# you can make the sleep something smaller; 5s will probably be enough. 

# regenerate initramfs with the edited and chmod'ed script
sudo update-initramfs -k all -u

# reboot and test it!
sudo reboot

hope this helps someone.

---

### Post by nhorvath on 2009-01-26
By the way, sleep 5 worked fine for me. You should probably change it and save 5 seconds off your boot :)

---

### Post by djgollywog on 2009-01-27
Thanks champ.

Every other post was very vague on how to fix this. Yours was great. Much appreciated. Keep up the good work :D

---

### Post by fronglegoose on 2009-07-30
Thanks, and you're welcome djgollywog :)

An update: I upgraded my kernel and initramfs-tools must have upgraded too, but didn't warn me that it was overwriting scripts. So I tried to boot up and got warnings that it couldn't mount my raid, etc. I tried running update-initramfs, but that didn't help, and then when I rolled back to the old kernel it still didn't work because I had overwritten the old initramfs for that kernel. I also had to add dm_mod to the initramfs modules list again. Very annoying.

---

### Post by fronglegoose on 2009-07-30
hmm, it seems kernel 2.6.27-14-server can't load the raid on bootwhile it works with -9-server, although the modules load fine and dmraid -ay works?? is it not using the same initramfs as the earlier kernels??

---

### Post by fronglegoose on 2009-07-30
it worked once I copied my dmraid (wasn't sure if symbolic links would work) to /etc/initramfs-tools/local-top/dmraid01.
it did not work in 
/etc/initramfs-tools/init-top/
/usr/share/initramfs-tools/local-top/
/usr/share/initramfs-tools/init-top/

seriously, wtf. 

I'm pretty confused about the difference between the configs in /etc/initramfs-tools and /usr/share/initramfs-tools anyway. the man page is not clear except that configs can go in both. I imagine the /etc/ ones are for customisation (and hopefully not overwritten) while the /usr/share ones are distributed. but they seem to have changed it not to run scripts from /usr/share.../local-top, only from /etc? wtf.

---

