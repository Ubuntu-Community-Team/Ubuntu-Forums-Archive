---
title: "video sluggish - XP Guest / U~ 8.04 Host"
date: 2008-12-22
forum: Virtualisation
---

### Post by aguitarplayer on 2008-12-22
I am running Netflix "Silverlight.2.0" movie viewer and it works but the video / audio is very sluggish (very marginally watchable)

I have a DEll 8300 (3Ghz w/ 1Gb memory) 
with 512MB configured for the XP guest in virtualbox (1.5.6_ose)

I will play around with memory settings but was looking to see if I am expecting too much to have video work as well on virtualbox as it does native.
I dont know which side (Host or Guest) needs more resources here. 

Any advice on how to manage this?  
I hate to have to go back to Windows as primary OS here.

(I have Verizon FIOS and run Starlight very nicely on other servers not using virtualbox)

########################
# some Ubuntu Host info
########################
$ uname -a
Linux DellUbuntu 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

tim@DellUbuntu:~/bin$ cat /proc/meminfo
MemTotal:      1034828 kB
MemFree:         14476 kB

########################
# some XP guest info
########################
OS Type Windows XP
Base Memory 512 MB
Video Memory 8 MB
Boot Order Floppy, CD/DVD-ROM, Hard Disk
ACPI Enabled
IO APIC Disabled
Hard Disks Primary Master XP.vdi [Normal, 10.00 GB]
CD/DVD-ROM Not mounted
Floppy Not mounted
Audio Adapter PulseAudio (oss & alsa did not provide sound in Windows)
Network Adapter 0 NAT 
Serial Ports Disabled 
Shared Folders None

---

### Post by inobe on 2008-12-23
8mb video ?


there is not enough vram, also consider the fact that virtual tools do not use 3d acceleration "Yet"

---

### Post by aguitarplayer on 2008-12-23
thanks, I did increase the video ram (as much as 200MB to the Guest from  256MB total ) 
not much diff but does seem to be a litle better so long as it is not full-screen.

---

### Post by inobe on 2008-12-23
version 2.1 uses experimental 3d acceleration via openGL !

if you want to test that out ?




soon of course' it will support direct 3d which is wonderful.

---

