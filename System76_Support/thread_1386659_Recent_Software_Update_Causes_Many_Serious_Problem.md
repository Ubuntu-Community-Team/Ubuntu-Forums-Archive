---
title: "Recent Software Update Causes Many Serious Problems!!!"
date: 2010-01-20
forum: System76 Support
---

### Post by DonnyViszneki on 2010-01-20
First of all, my system is pretty much pristine. I haven't installed anything complicated. It's pretty much exactly as it came from System76.

I recently indulged Software Update and now several things are chronically going wrong:

1) When booting, Ubuntu tells me a filesystem is not available, identifying it by UUID.

2) When playing a 3D game (Urban Terror) eventually my system experiences a hiccup during which the display turns black for about one second. After this time, the next thing happens:

**UPDATE:** I have discovered this problem can occur without running Urban Terror. I was simply working on other software with Firefox, System Monitor, Gnome Terminal, and GVim running. Now suddenly one of my four CPU cores is being pegged. I can, however, still utilize my other CPU cores. As expected, Xorg is the process using all my CPU, regardless of the fact that I'm not doing anything graphically intensive.

3) The frame rate of 3D game I play appears to the game to be very high (at a self-imposed limit of 120 FPS) however the actual picture shown is at a very low frame rate.

4) After exiting the game I realize that one of my four CPU cores is at a **constant** 100% of capacity. This problem is caused by:

5) Xorg is using 99-100% of my CPU constantly. This problem is exacerbated by:

6) Only one of my four CPU cores is being used. Trying to run more things does not result in my other CPU cores being utilized.

7) Using the "OnDemand" power profile, my CPU never switches up from 2.00 GHz to 2.83 GHz.

8) Sometimes I cannot switch to a VT. Sometimes I cannot run gnome-terminal.

9) Firefox tells me this when starting it up:

```
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)

```

The system is VERY slow! How can I rollback the updates? This is absolutely terrible!

Please see this for my system's details: [http://ubuntuforums.org/showthread.php?p=8655524#post8655524](http://ubuntuforums.org/showthread.php?p=8655524#post8655524)

Interacting with my system without running my game (Urban Terror) and only using Firefox to report this bug and gnome-terminal to explore the symptoms of this problem:

I notice that opening a new tab in gnome-terminal causes another CPU core to get 100% used for about 6 consecutive seconds. It looks like a 90-degree angle square blip on my CPU usage meter.

**UPDATE:** It would seem that switching to a VT is permanently messed up as soon as I can login. I just get a garbled screen. I'm using HDMI.

---

### Post by spark43 on 2010-01-21
Hi,
I have a similar problem that also started after the last update.
Shortly after boot up and before starting any programs one or two of my CPUs goes to 100%. System Monitor does not identify the process but top does.
It shows root is running one or two instances of aptd and each takes a CPU to 100%
I can use sudo kill to stop them and CPU usage returns to normal.
Xorg only uses 8% in my case.

Does anyone know what is aptd?

Regards
David

---

### Post by jml on 2010-01-21
aptd may be short for aptdaemon.  Googling a bit, searching on the term "aptd" brought up a bug report from 2009 describing a prolem with apt.  I did not quite understand all of the detals, but it seems to be related to a Linux system running two instances of the software manager, one a scheduled process and the other manually started.  I don't know if this bug is related to your problem, but it was all I couold find.  Hopefully someone else will be able to add more information.  good luck.

Joe

---

### Post by jdb on 2010-01-21
> **DonnyViszneki said:**
> First of all, my system is pretty much pristine. I haven't installed anything complicated. It's pretty much exactly as it came from System76.

I recently indulged Software Update and now several things are chronically going wrong:

1) When booting, Ubuntu tells me a filesystem is not available, identifying it by UUID.

2) When playing a 3D game (Urban Terror) eventually my system experiences a hiccup during which the display turns black for about one second. After this time, the next thing happens:

**UPDATE:** I have discovered this problem can occur without running Urban Terror. I was simply working on other software with Firefox, System Monitor, Gnome Terminal, and GVim running. Now suddenly one of my four CPU cores is being pegged. I can, however, still utilize my other CPU cores. As expected, Xorg is the process using all my CPU, regardless of the fact that I'm not doing anything graphically intensive.

3) The frame rate of 3D game I play appears to the game to be very high (at a self-imposed limit of 120 FPS) however the actual picture shown is at a very low frame rate.

4) After exiting the game I realize that one of my four CPU cores is at a **constant** 100% of capacity. This problem is caused by:

5) Xorg is using 99-100% of my CPU constantly. This problem is exacerbated by:

6) Only one of my four CPU cores is being used. Trying to run more things does not result in my other CPU cores being utilized.

7) Using the "OnDemand" power profile, my CPU never switches up from 2.00 GHz to 2.83 GHz.

8) Sometimes I cannot switch to a VT. Sometimes I cannot run gnome-terminal.

9) Firefox tells me this when starting it up:

```
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)

```

The system is VERY slow! How can I rollback the updates? This is absolutely terrible!

Please see this for my system's details: [http://ubuntuforums.org/showthread.php?p=8655524#post8655524](http://ubuntuforums.org/showthread.php?p=8655524#post8655524)

Interacting with my system without running my game (Urban Terror) and only using Firefox to report this bug and gnome-terminal to explore the symptoms of this problem:

I notice that opening a new tab in gnome-terminal causes another CPU core to get 100% used for about 6 consecutive seconds. It looks like a 90-degree angle square blip on my CPU usage meter.

**UPDATE:** It would seem that switching to a VT is permanently messed up as soon as I can login. I just get a garbled screen. I'm using HDMI.

ctrl-alt-F1 will switch out of gnome to a shell
ctrl-alt-F7 will switch back

Switch to shell with ctrl-alt-F1 and see if a lot of stuff about not
finding a mount is continually scrolling by.

jdb

---

### Post by DonnyViszneki on 2010-01-22
> **jdb said:**
> ctrl-alt-F1 will switch out of gnome to a shell
ctrl-alt-F7 will switch back

I didn't know there was any other way to switch to a VT!

> **jdb said:**
> Switch to shell with ctrl-alt-F1 and see if a lot of stuff about not finding a mount is continually scrolling by.

As I mentioned in my post, my VT's were completely inaccessible.

**UPDATE:** I have made the bugs go away, but at a price: I disabled my swap. I commented out these lines in my fstab:

```
# swap was on /dev/sda2 during installation
#UUID=4dcb7a74-0f73-4f1f-9215-a1dcef29549e	none	swap	sw	0	0	# /dev/sda2
#/dev/sda2                            	        none	swap	sw	0	0	# /dev/sda2
#/dev/mapper/cryptswap1 none swap sw 0 0
```

I've seen other people having problems with a recent Ubuntu update if they had chosen an encrypted home filesystem when they set up their account. It seems that this update tried to enable encryption for swap and failed.

I'm not exactly sure how everything works, so I can't propose a solution that will let you keep your swap just yet. But the root of the problem might be that the partition which was reported as unavailable at startup was my swap partition, and it seems to have disappeared:

```
donny@donny-desktop:~/src/hg/gpsee$ ls /dev/disk/by-uuid
2c20b79b-bb2c-4422-9d48-d1cc487b189f  46ad1127-89ed-4d27-886e-3ad3898f9243  c0bb7577-4587-4b9d-8dc6-48a3df1b9079
```

Of course a new UUID is in its place. I suspect the problem is that the encrypted swap system blows the UUID of the partition away, making it unmountable by UUID, which is the default way fstab is set up these days. I'm going to try changing my fstab to use /dev/sda2 instead of UUID to identify the correct partition, and see if that will fix the problem.

---

### Post by jdb on 2010-01-22
> **DonnyViszneki said:**
> I didn't know there was any other way to switch to a VT!



As I mentioned in my post, my VT's were completely inaccessible.

**UPDATE:** I have made the bugs go away, but at a price: I disabled my swap. I commented out these lines in my fstab:

```
# swap was on /dev/sda2 during installation
#UUID=4dcb7a74-0f73-4f1f-9215-a1dcef29549e	none	swap	sw	0	0	# /dev/sda2
#/dev/sda2                            	        none	swap	sw	0	0	# /dev/sda2
#/dev/mapper/cryptswap1 none swap sw 0 0
```

I've seen other people having problems with a recent Ubuntu update if they had chosen an encrypted home filesystem when they set up their account. It seems that this update tried to enable encryption for swap and failed.

I'm not exactly sure how everything works, so I can't propose a solution that will let you keep your swap just yet. But the root of the problem might be that the partition which was reported as unavailable at startup was my swap partition, and it seems to have disappeared:

```
donny@donny-desktop:~/src/hg/gpsee$ ls /dev/disk/by-uuid
2c20b79b-bb2c-4422-9d48-d1cc487b189f  46ad1127-89ed-4d27-886e-3ad3898f9243  c0bb7577-4587-4b9d-8dc6-48a3df1b9079
```

Of course a new UUID is in its place. I suspect the problem is that the encrypted swap system blows the UUID of the partition away, making it unmountable by UUID, which is the default way fstab is set up these days. I'm going to try changing my fstab to use /dev/sda2 instead of UUID to identify the correct partition, and see if that will fix the problem.

I don't have an encrypted home directory but I do encrypt several other partitions & swap.
I don't know how Ubuntu does it but /dev/sda2 might not work.
The drive that needs to be mounted might be under /dev/mapper.

Just as an example this is how mine is set up.

I encrypt swap, mount it & turn it on in rc.local:

```
cryptsetup create a7 /dev/sda7 SWAP -c aes-xts-plain -h whirlpool -s 512
mkswap /dev/mapper/a7
swapon -a
```

and my fstab entry is:

```
/dev/mapper/a7	swap		swap	defaults
```

The password for swap is random, it gets recreated each boot.
Suspend hasn't got a ghost of a chance with my method so I doubt
that Ubuntu uses the same encryption on swap but am pretty sure it
will end up as some device under /dev/mapper.

jdb

---

### Post by DonnyViszneki on 2010-01-22
> **jdb said:**
> I don't know how Ubuntu does it but /dev/sda2 might not work.
The drive that needs to be mounted might be under /dev/mapper.

Right, the problem is that Ubuntu's cryptsetup package didn't automatically disable the original swap entry in fstab when it repurposed the swap partition. In my original post you can see right below the original swap fstab entry there is a cryptswap entry pointing at /dev/mapper/cryptswap1. I commented both out, as a temporary fix.

More recently I have uncommented the /dev/mapper/cryptswap1 line, and it seems to be working fine!

Thanks all!

**UPDATE:** [Launchpad ticket]("https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/511137")

---

