---
title: "samba slow performance"
date: 2006-05-23
forum: Server Platforms
---

### Post by acehigh on 2006-05-23
Hi all and tnx 4 the answers: I am unable to solve the speed problem that I'm encountering on a ubuntu linux server running samba and few clients (winXp and linuxes using samba). I'w read all about delayed ack, SO_RCVBUF and SO_SNDBUF, tcp delay and so on but nothing changes... I'm running a gigabit network, and doing a performance test with 'scp'  from cli to serv and vice versa i got a 18MByte/s, but with samba only at the top 4MByte/s either with linux or winxp client. Any suggestions?

---

### Post by Iowan on 2006-05-23
I read somewhere around here (I'll let YOU search for it... ;) ) about using CIFS versus SMBFS.

---

### Post by acehigh on 2006-05-23
Same bad performance with cifs. In any case, with winxp, i have no choice and the performance is slow.

---

### Post by Socratez on 2006-05-26
Could it be TCP Wrappers are slowing down the connection? Do you have encrytpion on or something like that??

---

### Post by acehigh on 2006-05-28
I don't have nothing special enabled.
It's is a plain vanilla ubuntu 5.10 server with samba. Nothing strange.

I suppose that is a samba problem, because copying the files with scp I get 5 times the speed of samba. Where am I wrong? Here is my smb.conf:

```

[global]
   workgroup = XXXXXXXXXXXX
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
  unix extensions = yes

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   security = user
   encrypt passwords = true
   passdb backend = tdbsam guest
   obey pam restrictions = yes
   invalid users = root

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .


socket options = TCP_NODELAY SO_SNDBUF=8192 

#======================= Share Definitions =======================
[share1]
 comment = Area privata di share1
 browseable = yes
 writable = yes
 create mask = 0700
 directory mask = 0700
 path = /home/share1
 valid users = share1

[share2]
 comment = Area privata di share2
 browseable = yes
 writable = yes
 create mask = 0700
 directory mask = 0700
 path = /home/share2
 valid users = share2


[share3]
 comment = Area privata di share3
 browseable = yes
 writable = yes
 create mask = 0700
 directory mask = 0700
 path = /home/share3
 valid users = share3


[share4]
 comment = Area comune share4
 browseable = yes
 writable = yes
 create mask = 0700
 directory mask = 0700
 valid users = share2 share1 share4
 force user = share4
 path = /home/share4

[share5]
 comment = Area comune
 browseable = yes
 writable = yes
 create mask = 0700
 directory mask = 0700
 valid users = share2 share3 share1 share4
 force user = share4
 path = /home/share4/share5

 
;[homes]
;   comment = Home Directories
;   browseable = yes

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

```

---

### Post by linuchsan on 2006-05-28
What is your ethernet hardware. Are you using the right drivers?

---

### Post by acehigh on 2006-05-29
The server runs on a Asus A8V Deluxe with AMD64. The driver is the default:

Here is cat /proc/pci
```
PCI devices found:
  Bus  0, device   0, function  0:
    Host bridge: PCI device 1106:0282 (VIA Technologies, Inc.) (rev 0).
      Master Capable.  Latency=64.
      Prefetchable 32 bit memory at 0xec000000 [0xefffffff].
  Bus  0, device   0, function  1:
    Host bridge: PCI device 1106:1282 (VIA Technologies, Inc.) (rev 0).
  Bus  0, device   0, function  2:
    Host bridge: PCI device 1106:2282 (VIA Technologies, Inc.) (rev 0).
  Bus  0, device   0, function  3:
    Host bridge: PCI device 1106:3282 (VIA Technologies, Inc.) (rev 0).
  Bus  0, device   0, function  4:
    Host bridge: PCI device 1106:4282 (VIA Technologies, Inc.) (rev 0).
  Bus  0, device   0, function  7:
    Host bridge: PCI device 1106:7282 (VIA Technologies, Inc.) (rev 0).
  Bus  0, device   1, function  0:
    PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South] (rev 0).
      Master Capable.  No bursts.  Min Gnt=10.
  Bus  0, device  10, function  0:
    Ethernet controller: Marvell Technology Group Ltd. Gigabit Ethernet Controller (rev 19).
      IRQ 17.
      Master Capable.  Latency=64.  Min Gnt=23.Max Lat=31.
      Non-prefetchable 32 bit memory at 0xfac00000 [0xfac03fff].
      I/O at 0xb400 [0xb4ff].
  Bus  0, device  15, function  0:
    RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 128).
      IRQ 20.
      Master Capable.  Latency=64.
      I/O at 0xd400 [0xd407].
      I/O at 0xd000 [0xd003].
      I/O at 0xc800 [0xc807].
      I/O at 0xc400 [0xc403].
      I/O at 0xc000 [0xc00f].
      I/O at 0xb800 [0xb8ff].
  Bus  0, device  15, function  1:
    IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 6).
      IRQ 20.
      Master Capable.  Latency=32.
      I/O at 0xfc00 [0xfc0f].
  Bus  0, device  16, function  0:
    USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 129).
      IRQ 21.
      Master Capable.  Latency=64.
      I/O at 0xd800 [0xd81f].
  Bus  0, device  16, function  1:
    USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2) (rev 129).
      IRQ 21.
      Master Capable.  Latency=64.
      I/O at 0xe000 [0xe01f].
  Bus  0, device  16, function  2:
    USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3) (rev 129).
      IRQ 21.
      Master Capable.  Latency=64.
      I/O at 0xe400 [0xe41f].
  Bus  0, device  16, function  3:
    USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4) (rev 129).
      IRQ 21.
      Master Capable.  Latency=64.
      I/O at 0xe800 [0xe81f].
  Bus  0, device  16, function  4:
    USB Controller: VIA Technologies, Inc. USB 2.0 (rev 134).
      IRQ 21.
      Master Capable.  Latency=64.
      Non-prefetchable 32 bit memory at 0xfae00000 [0xfae000ff].
  Bus  0, device  17, function  0:
    ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800 South] (rev 0).
  Bus  0, device  24, function  0:
    Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration (rev 0).
  Bus  0, device  24, function  1:
    Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map (rev 0).
  Bus  0, device  24, function  2:
    Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller (rev 0).
  Bus  0, device  24, function  3:
    Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control (rev 0).
  Bus  1, device   0, function  0:
    VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev 193).
      IRQ 11.
      Master Capable.  Latency=64.  Min Gnt=5.Max Lat=1.
      Non-prefetchable 32 bit memory at 0xfb000000 [0xfbffffff].
      Prefetchable 32 bit memory at 0xf0000000 [0xf7ffffff].

```

And here: lsmod | grep sk
```
 
skge                   38736  0

```

---

### Post by linuchsan on 2006-05-30
Try the sk98lin driver. Dón't forget to unload the skge module first.

---

### Post by acehigh on 2006-05-31
Linuchsan, you were almost right!

Unfortunately the problem is not as simple as I thought.

- With my hardware, sk98lin does not detect the device (If someone helps me...)
- I tried a PCI NIC, disabling the onboard yukon, the device is seen with the  r8169 module: result -> Great improve in speed! So it's probably a module problem.
```
0000:00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```

Tomorrow i'll do some speed measurements and i'll be more detailed.

---

### Post by acehigh on 2006-06-08
After some days I'm here again to tell you what's going on.

The network is a gigabit network with a server (ubuntu server 5.10) and some clients (some win xp sp2 boxes and a ubuntu desktop 5.10).

I was blaming for low speed from/to server to both kinds of client.

Incidentally dapped drake went out and I decided to upgrade the server. Everything went ok in the upgrade.
I decided to do some tests and I was astonished with the results I got.

Before server upgrade (test file size: about 600MBytes):
- Poor performance from/to winxp box (not measured but poor)
- Poor performance from/to linux client (about 4MByte/s) 
After server upgrade:
- Good performance from/to winxp box (about 30MBytes/s) 
- Poor performance from/to linux client (about 4MByte/s)

The problem for me was not in samba itself (I decided to test samba 3.0.20 before doing the upgrade having the same bad results of the standard samba that was with breezy) but in the nic module. The yukon nic integrated in the mb that before i fired on, now is behaving well.

I wanted to give a confirmation of this deciding to upgrade also the ubuntu client to dapper resulting in a nic not detected (gigabit ethernet rtl8169) after the upgrade (before was ok!). 

Switching the client nic to the 100mbit integrated on the mainboard gave me about 5 MByte/s, which is quite good for a 100mbit ethernet (have you got some figures about these transfer speeds?).

So I have to test the client with a gigabit ethernet detected by the kernel to complete the tests.

---

### Post by baux on 2006-06-11
Hi,

I'm new to ubuntu and I don't have lot of experience but I've got the same problem: I'm running kubuntu 6.06 and samba server version 3.0.22... network goes fine, but samba access goes very very slow...

before to install kubuntu I was trying SuSE 10.1 and Samba was ruuning fine (other problems make me to change to kubuntu)...

Did Someone know what to do?

TIA, baux

---

### Post by acehigh on 2006-06-12
The nic not detected was probably a problem of the k7-specific kernel (the linux client is a duron).
I decided to restart from scratch and reinstall dapper drake on the linux client from a clean hard disk.
Results:

The rtl8169 now is detected (i have the stock i386 kernel). Now I went to mount with smbfs my shares on the server: result:
Some performance improvement (I'm around about 8MBytes/s) but I'm far from 30MB/s of Ubuntuserver <-> XP.

But:
BIG BIG PROBLEMS WITH SMBFS at bootup! There is some strange problems in mounting the smbfs shares in /etc/fstab. When I boot I find that the shares are not mounted. I'f I do a mount -a I get sometimes the shares mounted, some other times I get a 'unable to resolve mount point' error. 
But probably this is OT. :-(

Still remains the poor performance of the linux client.
Any suggestions?

---

