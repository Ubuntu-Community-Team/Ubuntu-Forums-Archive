---
title: "Connect Garmin GPS to MapSource"
date: 2011-06-30
forum: Wine
---

### Post by sanderd17 on 2011-06-30
I have installed MapSource 6.16.3 in wine 1.3.22, the installation worked, and I'm able to view maps and all those things, but I have installed MapSource mainly to send maps (from OpenStreetMap) to my Garmin GPS (Nüvi 1390).

According to the different tutorials and tips that I have read, I should see my GPS as /dev/ttyUSB0, but when I plug the USB in, I only see it as an extra HDD. This is my /dev before I plugin the GPS:

```

agpgart		 mem		     sda2      tty28  tty60	 ttyS6
autofs		 net		     sda5      tty29  tty61	 ttyS7
block		 network_latency     sda6      tty3   tty62	 ttyS8
bsg		 network_throughput  sda7      tty30  tty63	 ttyS9
btrfs-control	 null		     sda8      tty31  tty7	 uinput
bus		 oldmem		     sg0       tty32  tty8	 urandom
cdrom		 pktcdvd	     sg1       tty33  tty9	 usbmon0
cdrw		 port		     shm       tty34  ttyprintk  usbmon1
char		 ppp		     snapshot  tty35  ttyS0	 usbmon2
console		 psaux		     snd       tty36  ttyS1	 v4l
core		 ptmx		     sr0       tty37  ttyS10	 vcs
cpu		 pts		     stderr    tty38  ttyS11	 vcs1
cpu_dma_latency  ram0		     stdin     tty39  ttyS12	 vcs2
disk		 ram1		     stdout    tty4   ttyS13	 vcs3
dri		 ram10		     tty       tty40  ttyS14	 vcs4
dvd		 ram11		     tty0      tty41  ttyS15	 vcs5
dvdrw		 ram12		     tty1      tty42  ttyS16	 vcs6
ecryptfs	 ram13		     tty10     tty43  ttyS17	 vcs63
fb0		 ram14		     tty11     tty44  ttyS18	 vcs8
fd		 ram15		     tty12     tty45  ttyS19	 vcsa
full		 ram2		     tty13     tty46  ttyS2	 vcsa1
fuse		 ram3		     tty14     tty47  ttyS20	 vcsa2
hpet		 ram4		     tty15     tty48  ttyS21	 vcsa3
input		 ram5		     tty16     tty49  ttyS22	 vcsa4
kmsg		 ram6		     tty17     tty5   ttyS23	 vcsa5
log		 ram7		     tty18     tty50  ttyS24	 vcsa6
loop0		 ram8		     tty19     tty51  ttyS25	 vcsa63
loop1		 ram9		     tty2      tty52  ttyS26	 vcsa8
loop2		 random		     tty20     tty53  ttyS27	 vga_arbiter
loop3		 rfkill		     tty21     tty54  ttyS28	 video0
loop4		 root		     tty22     tty55  ttyS29	 zero
loop5		 rtc		     tty23     tty56  ttyS3
loop6		 rtc0		     tty24     tty57  ttyS30
loop7		 scd0		     tty25     tty58  ttyS31
mapper		 sda		     tty26     tty59  ttyS4
mcelog		 sda1		     tty27     tty6   ttyS5

```

And this is after I have plugged in my GPS:

```


agpgart		 mem		     sda2      tty24  tty57	 ttyS30
autofs		 net		     sda5      tty25  tty58	 ttyS31
block		 network_latency     sda6      tty26  tty59	 ttyS4
bsg		 network_throughput  sda7      tty27  tty6	 ttyS5
btrfs-control	 null		     sda8      tty28  tty60	 ttyS6
bus		 oldmem		     sdb       tty29  tty61	 ttyS7
cdrom		 pktcdvd	     sdc       tty3   tty62	 ttyS8
cdrw		 port		     sg0       tty30  tty63	 ttyS9
char		 ppp		     sg1       tty31  tty7	 uinput
console		 psaux		     sg2       tty32  tty8	 urandom
core		 ptmx		     sg3       tty33  tty9	 usbmon0
cpu		 pts		     shm       tty34  ttyprintk  usbmon1
cpu_dma_latency  ram0		     snapshot  tty35  ttyS0	 usbmon2
disk		 ram1		     snd       tty36  ttyS1	 v4l
dri		 ram10		     sr0       tty37  ttyS10	 vcs
dvd		 ram11		     stderr    tty38  ttyS11	 vcs1
dvdrw		 ram12		     stdin     tty39  ttyS12	 vcs2
ecryptfs	 ram13		     stdout    tty4   ttyS13	 vcs3
fb0		 ram14		     tty       tty40  ttyS14	 vcs4
fd		 ram15		     tty0      tty41  ttyS15	 vcs5
full		 ram2		     tty1      tty42  ttyS16	 vcs6
fuse		 ram3		     tty10     tty43  ttyS17	 vcs63
hpet		 ram4		     tty11     tty44  ttyS18	 vcs8
input		 ram5		     tty12     tty45  ttyS19	 vcsa
kmsg		 ram6		     tty13     tty46  ttyS2	 vcsa1
log		 ram7		     tty14     tty47  ttyS20	 vcsa2
loop0		 ram8		     tty15     tty48  ttyS21	 vcsa3
loop1		 ram9		     tty16     tty49  ttyS22	 vcsa4
loop2		 random		     tty17     tty5   ttyS23	 vcsa5
loop3		 rfkill		     tty18     tty50  ttyS24	 vcsa6
loop4		 root		     tty19     tty51  ttyS25	 vcsa63
loop5		 rtc		     tty2      tty52  ttyS26	 vcsa8
loop6		 rtc0		     tty20     tty53  ttyS27	 vga_arbiter
loop7		 scd0		     tty21     tty54  ttyS28	 video0
mapper		 sda		     tty22     tty55  ttyS29	 zero
mcelog		 sda1		     tty23     tty56  ttyS3

```

As you see, there are some extra devices (most notably sdb and sdc), but nothing that looks like /dev/ttyUSB0. Some tutorials also suggest 
```

sudo modprobe garmin_gps

```
to make it appear as /dev/ttyUSB0, but that did change nothing at all.

Once I have it as ttyUSB0, I should make a softlink from the com0 port of Wine to that device. Than I could connect MapSource to the GPS. But since I don't have ttyUSB0, I can't make the softlink.

So if anyone can make it appear as /dev/ttyUSB0 or knows another way to put maps on it (without removing the maps that already are on it), please tell me.

**TLDR**: My GPS should show as /dev/ttyUSB0, but it doesn't.

---

### Post by MrSpike16 on 2011-07-01
The articles about "ttyUSB0" is for the first generation Garmin gps units to have a USB connection like my GPSmap76C.  They require a Garmin USB driver to communicate with MapSource.   After this Garmin used USB Mass Storage (shows up as a drive on your computer) so no proprietary driver needed.

On my desktop, my Nuvi 750 just worked with MapSource in Ubuntu 10.04.  However in Ubuntu 11.04 on my netbook (also had problem with a earlier version of Ubuntu), MapSource couldn't find my Nuvi.

The problem is Wine is not detecting your Nuvi flash drive.

Plug in your Nuvi, let it mount and then run Configure Wine and under the Drives tab look for your Nuvi.  Mine is called GARMIN on desktop so shows up as GARMIN in Wine Configuration.

It probably isn't  listed and Autodetect button probably won't find it either.  Even if listed it may not work yet.

If your Nuvi isn't in the list of drives then click the Add button and add a drive letter.

Next click the Browse button and browse to the /media folder, and highlight, but don't open the Nuvi drive.  Click OK.  My drive is E:   /media/GARMIN/  for example.

Now click the Show Advanced button and for Type: change it to Floppy disk.
Note: It will not work unless drive type is floppy disk.

Apply the changes and MapSource will now find your Nuvi and is persistent so won't need to add it in Wine Configuration again.

---

### Post by sanderd17 on 2011-07-01
Thank you. I tried adding it as a device, but I didn't set the type to floppy.

Since I already added the /media/GARMIN as a device, setting the type to floppy was the easiest for me.

---

### Post by jtappin on 2011-08-29
> **MrSpike16 said:**
> 
Now click the Show Advanced button and for Type: change it to Floppy disk.
Note: It will not work unless drive type is floppy disk.

Apply the changes and MapSource will now find your Nuvi and is persistent so won't need to add it in Wine Configuration again.

just one warning, on some but not all machines the floppy setting is not persistent. On my desktop it is, but on the laptop it resets back to "automatic".

---

