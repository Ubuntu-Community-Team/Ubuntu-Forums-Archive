---
title: "Server connections cut out"
date: 2011-05-21
forum: Server Platforms
---

### Post by G1ZmO65 on 2011-05-21
Hi,

My 9.04 server ran fine with the current hardware configuration however since I upgraded to 10.10 then 11.04 (thinking it would fix it) I've had issues daily where the server just stops responding on the network. Samba shares are inaccessible, SSH gives "no route to host" and the apache server stops responding.

When it's rebooted it runs fine for a few hours then dies again.

Can someone suggest what log files I should be looking at please and/or what the problem is likely to be?

Thanks

Paul

p.s. The server is just running on a simple Athlon XP pc with 3 IDE drives, nothing complex and it did seem to work fine on 9.04

---

### Post by bestdayever on 2011-05-21
I am having a similar issue after upgrading from 9.04 to 10.04.  SSH doesn't work but samba does most of the time.  I have tried checking for iptables rules being messed up and ufw but haven't been able to get it going and can't ssh into it at all at this current time. Any help would be awesome.

---

### Post by G1ZmO65 on 2011-05-21
Well glad to know I'm not alone :)

---

### Post by G1ZmO65 on 2011-05-21
Actually on this occasion there was an error on the screen. I took a snap of it (Is this an HDD failure? any ideas?):

---

### Post by G1ZmO65 on 2011-05-22
Did any outstanding updates last night and left it running. It was still running this morning.

I decided to try to watch an avi which is on the server. It played for about 30 mins then the networking on the server died again.

This was the screenshot after it died and I logged in and ran ifconfig

Does all this look normal?

---

### Post by G1ZmO65 on 2011-05-22
erm. No suggestions at all?

c'mon, someone please give me a pointer?

The errors I saw were ata errors so I shut the server down earlier and ran manufacturers diags on all the HDDs. No fault found.

Looking for some guidance here :P

---

### Post by G1ZmO65 on 2011-05-23
Ok I've done some further testing and I think that the crashes occur when the server is receiving data

I left the server streaming 4 different AVI files on Sunday for several hours without a crash

It crashed again earlier this evening and showed some receive errors (see below)

Tonight I created a script to repeatedly copy a 20mb file to the server.

The IFCONFIG command shows that there seem to be a lot (is it a lot?) of receive errors, dropped and overruns
```
eth0      Link encap:Ethernet  HWaddr 00:30:1b:1f:1f:3a  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:fe1f:1f3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1928896 errors:1006 dropped:1652 overruns:648 frame:0
          TX packets:1333083 errors:0 dropped:0 overruns:4 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2613441113 (2.6 GB)  TX bytes:445898798 (445.8 MB)
          Interrupt:19 Base address:0xd000  
```

This happens whether the data is coming from my ubuntu desktop or my partners windows machine so I'm assuming it's down to either the server hardware, software or the network hardware. 

My next plan is to upgrade the 2 network switches with gigabit ones and continue tests. Might stick a gigabit card in the server too.

Any other suggestions gratefully received :)

Paul

---

### Post by G1ZmO65 on 2011-05-24
Community "support"? :(

---

### Post by headvampyre@hotmail.co.uk on 2011-05-25
Hi, it looks like there could be some HDD errors from the screenshots you posted.

Does the server totally freeze up when it stops responding? If not, you can probably rule that out.

Also - have you checked your cables/networking hardware?

Often, a lot of issues are due to dogy hardware.

---

### Post by koenn on 2011-05-25
> **G1ZmO65 said:**
> Community "support"? :(
yes, as in : if we know the solution, we'll tell you. 

for SLAs, contact Canonical.

---

### Post by koenn on 2011-05-25
network errors, especially the "I've got connectivity, but not always, and not always as fast as it should be" are difficult.
That you only get errors on the RX is interesting, but it can still mean anything from the RX-wires in your UTP cable or the RX contaxt in your NIC are failing to your server can't handle the incoming traffic (for whatever reason), its RX buffers overrun, and its dropping the packets because it doesn't know what else to do.

The latter could indicate a problem with the TCP/IP stack or the module ("driver") for the NIC. Seeing that 2 people mention this problem after an upgrade, is a hint in that direction. 
otoh it could also just mean that something completely unrelated is wrong with the machine, giving it a performance hit, or that there's excessive (broadcast) traffic on your network so the server has to deal with that as well as the files you sent to it.

If you messed with routing recently, that's also a usual suspect : bad routing, assymetric routes, multiple gateways for the same segment, ... can cause "bad" packets that will be dropped, cause retransmits, etc

Here are some network diagnosing and troubleshooting tips :
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting)

I'd concentrate on the hardware and link layer stuff (ethtool, ethernet errors) first


You might also look for bug reports, or file one if you can establish that it's related to the current OS version of your server, and that the problem goes away if you install a previous version.

---

### Post by G1ZmO65 on 2011-05-26
THanks headvampyre

No, the server doesnt completely freeze. It becomes inaccessible via the network. Cant SSH or ping it. However, on the local console I can still log in and reboot it.

Someone else mentioned running smartctl to diagnose problems. I'll do this and maybe change the cabling to the drives and the psu later tonight as well as backing up the relevant drive.

Paul

---

### Post by G1ZmO65 on 2011-05-27
Ok here's the update.

Smartctl indicated a lot of errors on the boot drive. (Odd that the Maxtor diags didnt show this though)

I decided to clone the drive to another to save the whole reinstall palaver but encountered some issues. (Not sure if I should be starting a new thread...)

Tried Clonezilla and Partimage to clone the drive but they had too many issues reading the source. I eventually used Acronis which saw the source partitions and said it had done the clone successfully.

However after connecting this new drive as the boot drive I just get a repeating cycle of POST then reboot.

Do I need to reinstall grub or something on the new drive to fix the boot partition?

Thx

---

### Post by G1ZmO65 on 2011-05-27
Whoop! Reinstalled grub and reconnected all drives. Everything back to normal again!

:)

Chuffed!

---

### Post by G1ZmO65 on 2011-05-29
Correction: The HDD issue is resolved but the networking issue is NOT :(

Browsed about 20 jpgs which are on the server and then the networking locked up as before. No error messages that I can find.

later....
I've now been running iperf for an hour and no crashes. Weird

---

