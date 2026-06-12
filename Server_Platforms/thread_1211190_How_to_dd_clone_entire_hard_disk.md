---
title: "How to dd clone entire hard disk"
date: 2009-07-12
forum: Server Platforms
---

### Post by dragos2 on 2009-07-12
I am using 
```

dd if=/dev/sda1 ibs=4096 | gzip > /someotherpartition/sda1.img.gz

```

to clone sda1 partition in compressed format on another partition.

Any ideas of how to clone entire sda using dd and store the compressed
img on the same sda on some of its partitions while running ?

---

### Post by zetman on 2009-07-12
That seems unlikely, because eventually you will get to the part of the disk where you are writing the archive and start cloning it into itself. :shock:
The important point is to make sure that wherever your writing to is not part of the backup.  If you only have one drive, your best bet might be picking one partition to be the backup partition and then having a separate archive for each other partition.

---

### Post by dragos2 on 2009-07-12
> **zetman said:**
> That seems unlikely, because eventually you will get to the part of the disk where you are writing the archive and start cloning it into itself. :shock:
The important point is to make sure that wherever your writing to is not part of the backup.  If you only have one drive, your best bet might be picking one partition to be the backup partition and then having a separate archive for each other partition.

I thought of that too, so I must use a ssh tunnel and redirect it to another machine..hmm.

---

### Post by dragos2 on 2009-07-12
But I did a test in VirtualBox and it worked cloning the entire sda while running in top
of it. What does this mean ?

---

### Post by zetman on 2009-07-12
> **dragos2 said:**
> But I did a test in VirtualBox and it worked cloning the entire sda while running in top
of it. What does this mean ?

Chances are that the sda inside VitualBox is not the same sda from outside.  I'm not familiar enough with VirtualBox to know what the defaults would be, but the whole point is that it's creating a virtual environment.  I would think that includes remapping drives.  I could be wrong.

---

### Post by dragos2 on 2009-07-12
> **zetman said:**
> Chances are that the sda inside VitualBox is not the same sda from outside.  I'm not familiar enough with VirtualBox to know what the defaults would be, but the whole point is that it's creating a virtual environment.  I would think that includes remapping drives.  I could be wrong.

I also tested under real conditions now and still working. I am wondering if the restore
will work ?

---

### Post by zetman on 2009-07-12
Wait, it actually finished?  It should have gotten stuck in an infinite recursion.

---

### Post by dragos2 on 2009-07-12
> **zetman said:**
> Wait, it actually finished?  It should have gotten stuck in an infinite recursion.

Yes, it finished under real system too.

Can anyone clarity this please ?

---

### Post by unutbu on 2009-07-12
It is possible to use dd to copy a live root filesystem, but doing so may contain some errors since there is no way to stop files from changing while dd is running.

This leads me to believe that dd simply copies bit-for-bit whatever happens to be at bit location 1, then 2, then 3, etc, and it does not care if the filesystem is changing all the while. So you can save sda1 to a compressed image file on sda1, but there is no guarantee that the copy is free of corruption.

You may want to check out PartImage ([http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page) and [http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)). 

Be careful with monolithic backup files. If it is not made properly or somehow becomes  corrupt, you lose everything. It pays to practice restoring before you really need it. (Or use a file-copy backup method like rsync which is quicker and less vulnerable to disaster.)

---

### Post by druhboruch on 2009-07-12
Maybe it will be of some use to you:

[http://g4l.sourceforge.net/](http://g4l.sourceforge.net/)

---

### Post by zetman on 2009-07-12
> **unutbu said:**
> It is possible to use dd to copy a live root filesystem, but doing so may contain some errors since there is no way to stop files from changing while dd is running.


Of course dd finished, it does have any sort of error checking.  *smacks forehead*
So, yeah, those images are junk.
unutbu is right, find a utility specifically meant for this.

---

### Post by dragos2 on 2009-07-12
> **unutbu said:**
> It is possible to use dd to copy a live root filesystem, but doing so may contain some errors since there is no way to stop files from changing while dd is running.

This leads me to believe that dd simply copies bit-for-bit whatever happens to be at bit location 1, then 2, then 3, etc, and it does not care if the filesystem is changing all the while. So you can save sda1 to a compressed image file on sda1, but there is no guarantee that the copy is free of corruption.

You may want to check out PartImage ([http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page) and [http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)). 

Be careful with monolithic backup files. If it is not made properly or somehow becomes  corrupt, you lose everything. It pays to practice restoring before you really need it. (Or use a file-copy backup method like rsync which is quicker and less vulnerable to disaster.)

So there is a chance that the image be to more or less corrupted at some point if
I dd the whole disk while running.

But what if I redirect the stream(image) through ssh to another computer ?
Will this be safer ?

---

### Post by dragos2 on 2009-07-12
> **unutbu said:**
> It is possible to use dd to copy a live root filesystem, but doing so may contain some errors since there is no way to stop files from changing while dd is running.

This leads me to believe that dd simply copies bit-for-bit whatever happens to be at bit location 1, then 2, then 3, etc, and it does not care if the filesystem is changing all the while. So you can save sda1 to a compressed image file on sda1, but there is no guarantee that the copy is free of corruption.

You may want to check out PartImage ([http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page) and [http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)). 

Be careful with monolithic backup files. If it is not made properly or somehow becomes  corrupt, you lose everything. It pays to practice restoring before you really need it. (Or use a file-copy backup method like rsync which is quicker and less vulnerable to disaster.)

Can I use partimage to clone the running system ? I can't shut it down and plug
the cd and then power on - it is located in a remote datacenter.

---

### Post by unutbu on 2009-07-12
I am not an expert at this, so there might be solutions for backing up live systems that I do not know about. 

[list]
[*]
> But what if I redirect the stream(image) through ssh to another computer ?
Will this be safer ?

Nope, same problem. 

The only sound way to make a backup using dd (or any other cloning tool) is to backup the partitions while they are unmounted. Having the live system on a remote computer just makes it that much harder.
[*] > Can I use partimage to clone the running system ? 

Partimage (like dd) can be forced to operate on a live system, but there is no guarantee that the result will be corruption-free. 

[*] There is a special kind of partition/filesystem called LVM which solves the problem of backing up a live system. The problem is you'd have to repartition the drive and reinstall your operating system into an LVM.

Using LVM allows you to make a snapshot of your live filesystem.  The snapshot freezes the filesystem at a particular time, allowing you to make a sound backup. The LVM saves diffs of all modifications that occur after the snapshot, so you can continue using the live system and make a coherent backup at the same time. 

See
[http://tldp.org/HOWTO/LVM-HOWTO/snapshotintro.html](http://tldp.org/HOWTO/LVM-HOWTO/snapshotintro.html)
[http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)

[*] You could use rsync (instead of dd) to backup files. I think there is much less chance of corruption this way. This might be your simplest solution.

[*] If you stop other users from accessing the machine, your dd backup may have a better chance of coming through with less corruption. You may have some corruption anyway, since there are background processes which are always running and may be writing to /tmp or /var, but at least there would be less corruption. 

[*] If you use a database like MySQL, use the mysqldump facility instead of dd. Or shutdown myslqd before making the backup. 

[/list]

---

### Post by dragos2 on 2009-07-12
> **unutbu said:**
> I am not an expert at this, so there might be solutions for backing up live systems that I do not know about. 

[LIST]
[*]


Nope, same problem. 

The only sound way to back a backup using dd (or any other cloning tool) is to backup the partitions while they are unmounted. Having the live system on a remote computer just makes it that much harder.
[*] 
Partimage (like dd) can be forced to operate on a live system, but there is no guarantee that the result will be corruption-free.
[*] There is a special kind of partition/filesystem called LVM which solves the problem of backing up a live system. The problem is you'd have to repartition the drive and reinstall your operating system into an LVM.

Using LVM allows you to make a snapshot of your live filesystem.  The snapshot freezes the filesystem at a particular time, allowing you to make a sound backup. The LVM saves diffs of all modifications that occur after the snapshot, so you can continue using the live system and make a coherent backup at the same time. 

See
[http://tldp.org/HOWTO/LVM-HOWTO/snapshotintro.html](http://tldp.org/HOWTO/LVM-HOWTO/snapshotintro.html)
[http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)
[*] You could use rsync (instead of dd) to backup files. I think there is much less chance of corruption this way. This might be your simplest solution.
[*] If you stop other users from accessing the machine, your dd backup may have a better chance of coming through with less corruption. You may have some corruption anyway, since there are background processes which are always running and may be writing to /tmp or /var, but at least there would be less corruption.
[*] If you use a database like MySQL, use the mysqldump facility instead of dd. Or shutdown myslqd before making the backup.
[/LIST]


Thanks for the detailed response.

I remembered that Ubuntu has a default recovery mode kernel but it mounts the same
partitions and it uses the same disk drive so it is not of great help to my question.

---

### Post by unutbu on 2009-07-12
Actually, I think you have a pretty good idea here.

If you run
```

sudo init 1
```

your machine will got into single user mode (without you having to reboot the machine.) All the other users will get kicked off.

Many services will be shut down, so your system will be more quiet.
Using partimage, or dd from here may not be perfect, but perhaps better than running it on the machine in runlevel 2 (the default). 

Once the backup is done, you can resume runlevel 2 by running
```

init 2
``` 
(sudo is unnecessary since you are root in runlevel 1 (single user mode.)

It might be worth trying, but you should check that the backup is actually usable by seeing if the image.gz file can be restored to a spare drive.

---

### Post by dragos2 on 2009-07-13
> **unutbu said:**
> Actually, I think you have a pretty good idea here.

If you run
```

sudo init 1
```your machine will got into single user mode (without you having to reboot the machine.) All the other users will get kicked off.

Many services will be shut down, so your system will be more quiet.
Using partimage, or dd from here may not be perfect, but perhaps better than running it on the machine in runlevel 2 (the default). 

Once the backup is done, you can resume runlevel 2 by running
```

init 2
```(sudo is unnecessary since you are root in runlevel 1 (single user mode.)

It might be worth trying, but you should check that the backup is actually usable by seeing if the image.gz file can be restored to a spare drive.

That could be less error prone - I think I am going to try that.
Also I was thinking to ask the guys from the datacenter to plug that partimage cd into
the server.

But I have another idea, the cd from which I performed the Ubuntu 8.04 installation
is still in the dvd-rom but is ejected, if I find a way to close the tray I can reboot
and boot from cd and from there I can perform the safe dd.

But I have 2 problems with this approach

1. The ubuntu cd automatically ejects after finishing? Any ideas of how to disable
this behaviour?

2. How to close the cd tray ? The eject -t or -T does not seem to work:
```

root@ubu:/home/dragos# eject -T
eject: CD-ROM tray close command failed: Input/output error

```

---

### Post by windependence on 2009-07-13
> **dragos2 said:**
> That could be less error prone - I think I am going to try that.
Also I was thinking to ask the guys from the datacenter to plug that partimage cd into
the server.

But I have another idea, the cd from which I performed the Ubuntu 8.04 installation
is still in the dvd-rom but is ejected, if I find a way to close the tray I can reboot
and boot from cd and from there I can perform the safe dd.

But I have 2 problems with this approach

1. The ubuntu cd automatically ejects after finishing? Any ideas of how to disable
this behaviour?

2. How to close the cd tray ? The eject -t or -T does not seem to work:
```

root@ubu:/home/dragos# eject -T
eject: CD-ROM tray close command failed: Input/output error

```

You're making this far more complicated than it should be. 

To close the cd tray just give it a gentle push and it will close. :-)

Boot from the startup CD in recovery mode. If you have to have a GUI you are screwed here, but you should know how to do this anyway. No need to mount your filesystem to make a backup with dd, in fact you don't want to. Do an fdisk -l to find out what device name your live cd has assigned, and then do:

```
sudo dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc, noerror
```

Where sda is your source drive and sdb is your destination. If you want to write it to an image you have to write it to a file on the other device, and you could pipe it through gzip or bzip to compress it if you want.

dd is a fantsastic tool. It does a bit by bot copy of the drive or partition.

-Tim

---

### Post by Lampi on 2009-07-13
> **dragos2 said:**
> 1. The ubuntu cd automatically ejects after finishing? Any ideas of how to disable this behaviour?
Don't know about the ubuntu livecd, but knoppix livecd has a cheatcode (noeject) you can enter on boot. You better put knoppix or whatever distro you want to use for backup/maintenance on a usb stick anyway

---

### Post by HermanAB on 2009-07-13
Yes, good old Data Definition (DD) simply copies the disk and doesn't do any checks on the data integrity.

I usually copy a disk image to a server using a combination of dd, gzip and netcat, but with modern enormous drives, this is not so good anymore and you need a lot of patience, even with a gigabit speed network:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

---

### Post by dragos2 on 2009-07-13
> **windependence said:**
> You're making this far more complicated than it should be. 

To close the cd tray just give it a gentle push and it will close. :-)

Boot from the startup CD in recovery mode. If you have to have a GUI you are screwed here, but you should know how to do this anyway. No need to mount your filesystem to make a backup with dd, in fact you don't want to. Do an fdisk -l to find out what device name your live cd has assigned, and then do:

```
sudo dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc, noerror
```Where sda is your source drive and sdb is your destination. If you want to write it to an image you have to write it to a file on the other device, and you could pipe it through gzip or bzip to compress it if you want.

dd is a fantsastic tool. It does a bit by bot copy of the drive or partition.

-Tim

Hei Tim, thanks for stepping by this thread, but you did not read it all :p
I said that the server is located in a remote datacenter (another country)
so I can't just give it a gentle push :P

I think I'll use partimage from a bootable cd (maybe system rescue cd).

---

### Post by dragos2 on 2009-07-13
> **HermanAB said:**
> Yes, good old Data Definition (DD) simply copies the disk and doesn't do any checks on the data integrity.

I usually copy a disk image to a server using a combination of dd, gzip and netcat, but with modern enormous drives, this is not so good anymore and you need a lot of patience, even with a gigabit speed network:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

Maybe bzip2 or 7z through netcat would perform a little faster, in my case I have
enough processing power so I think dd | 7z -> netcat stream would be a pretty
fast combination.

The server completed my dd /dev/sda and it has 250 GB gzipped as high as my
/dev/sda6. So it did entered a loop. This was not the case on my test machine.
But reality proves that the method I used is not reliable and as I said earlier
I think I will stick with a bootable partimage cd.

---

### Post by windependence on 2009-07-13
> **dragos2 said:**
> Hei Tim, thanks for stepping by this thread, but you did not read it all :p
I said that the server is located in a remote datacenter (another country)
so I can't just give it a gentle push :P

I think I'll use partimage from a bootable cd (maybe system rescue cd).

OK, I'm confused, how are you going to boot from CD in another country (unless you have VMware installed)?

-Tim

---

### Post by dragos2 on 2009-07-14
> **windependence said:**
> OK, I'm confused, how are you going to boot from CD in another country (unless you have VMware installed)?

-Tim

I will kindly ask the guys from datacenter to burn the cd and plug into the cd tray :)

---

### Post by windependence on 2009-07-14
> **dragos2 said:**
> I will kindly ask the guys from datacenter to burn the cd and plug into the cd tray :)

Great! Essentially, you could dd the image from the server if you have a good connection. Just pipe it with scp or ssh.

-Tim

---

