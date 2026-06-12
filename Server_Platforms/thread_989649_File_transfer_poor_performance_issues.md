---
title: "File transfer poor performance issues"
date: 2008-11-21
forum: Server Platforms
---

### Post by kingnubian on 2008-11-21
Here is my setup.

-> SMC EZSwitch 8 Port Gigabit Ethernet Switch

Intel D945GCLF2
1gig DDR2-667
1Tb Seagate 7200.11 SATA2 Hard Drive
Intel Pro/1000MT Nic (MTU set to 9000)
Ubuntu Server 8.10 

Network includes:

Vista Business 64bit based workstation
Vista Home Premium based HTPC
XP Based Laptop
Linux Mint 5 based workstation
Ubuntu Server 8.10 based server


Seeing as the driver for the integrated nic doesn't support setting MTU's at my desired 9000 rate as it is with the rest of my home network I disabled it in the motherboard's bios & installed the Intel nic in its place.

Setting up a file share was a breeze but here si where the problem starts. Reading from the file share on any of the machines comes in at around 30Meg/sec which is lower than what I had hoped seeing that tranfer between the two Vista machines is closer to 60Meg/sec. This isn't the issue I'm bringing up here though.

Writing to the server share results in transfer that for a very brief moment starts at ~30meg/s then rapidly , in the space 1-2 seconds, seems to stall momentarily then slow down to somewhere between 1.5 & 3Meg/s. This transfer is not smooth at all stopping & starting in fits, for 1- seconds at a time, until the transfer is completed. This happens Windows->Linux & Linux->Linux btw. 

This same issue happened with a ClarkConnect install and is also seen when transferring files to the Linux Mint 5 box as well.

Is this a Samba issue? Any insight or solutions would be very appreciated.

---

### Post by jonobr on 2008-11-21
Hello

Whats the MTu on you other system?
Just guessing but if there is a huge mismatch in MTU maybe it  needs to throttle back to support the other system?

just a wag

---

### Post by kingnubian on 2008-11-21
> **jonobr said:**
> Hello

Whats the MTu on you other system?
Just guessing but if there is a huge mismatch in MTU maybe it  needs to throttle back to support the other system?

just a wag


9000 all around.

---

### Post by jonobr on 2008-11-21
oki, Ill get back in my box:-)

Recommend you try using something like iperf or similar to do some traffic testing and test on uplink/downlink tcp/udp and at different sizes

---

### Post by kingnubian on 2008-11-22
> **jonobr said:**
> oki, Ill get back in my box:-)

Recommend you try using something like iperf or similar to do some traffic testing and test on uplink/downlink tcp/udp and at different sizes

Could you give me a quick rundown on how to do this?

---

### Post by kingnubian on 2008-11-23
Just for reference I installed SME server 8.0b3 and my Samba transfer speed are as good or better than with windows at 50-68Meg/s in each direction. This means it's got to be a config issue in 8.10 server. 

Any insight would be very welcomed.

---

### Post by cariboo on 2008-11-23
That problem has been around since hardy.

> Recommend you try using something like iperf or similar to do some traffic testing and test on uplink/downlink tcp/udp and at different sizes

Iperf is available in the repositories. You install it on your server and run it as a server then install it on the other computers and test up/don transfer speeds. Iperf is also available for windows. For more info once you have installed iperf see:

```
man iperf
```

Jim

---

### Post by kingnubian on 2008-11-23
> **cariboo907 said:**
> That problem has been around since hardy.



Iperf is available in the repositories. You install it on your server and run it as a server then install it on the other computers and test up/don transfer speeds. Iperf is also available for windows. For more info once you have installed iperf see:

```
man iperf
```

Jim

Thanks very much for the info. 

If this is a known problem are there any indications that a solution is being worked on or available? As it stands now it is very frustrating.

---

