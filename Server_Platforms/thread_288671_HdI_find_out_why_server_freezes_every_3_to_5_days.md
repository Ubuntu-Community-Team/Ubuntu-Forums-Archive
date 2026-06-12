---
title: "HdI find out why server freezes every 3 to 5 days?"
date: 2006-10-30
forum: Server Platforms
---

### Post by Juerg on 2006-10-30
My Unbuntu server 6.06.1 LTS is located in our internal network, behind a firewall. 
mainboard Intel D865GLC
1 GB RAM
2 SATA harddrives

Every 3 to 5 days the server freezes, it doesn't answer to pings and on the server console there are some weird messages. We have to unplug it to "boot". 
Syslog and all other logs don't show any hints about why the freeze happend. Most of the time it freezes during periods with no users connected to the system.
Further information:
- memtest86+: no failures
- UPS installed and OK
- system load < 10%

This already happend when only Samba server was turned on but it got more frequently when Lotus Domino Server was installed and in operation in addition to the Samba Server. (there is no graphical system installed)

All suggestions what I could do to find out the reason of the crashes are much appreciated.

Juerg

---

### Post by MJN on 2006-10-30
What are the 'weird messages'? That'll be a good place to start! :)
 
Mathew

---

### Post by Juerg on 2006-10-30
Yes I know, however it appears to be just the end of a number of "messages" consisting of hexadecimal figures and some name of processes. All I can say is that it is different after each crash (and damn difficult to manually write down).

Would it be possible to redirect those messages to a different Linux machine? I am sure the start of these messages is more helpful than the end.

I already keep a separate Ubuntu box running with a monitor process from  Webmin to alert me if the server doesn't answer anymore. How could I redirect the messages from the server console to the other Linux box with the monitoring task? 

This would enable me to read and possibly post them here.

Juerg

---

### Post by Chayak on 2006-10-30
Bah, that's just your hampster getting tired and passing out you need to run dual hamptsers to correct this.

But seriously you should have a crash dump log with those errors. There isn't much we can help with without the specific errors.  It sounds like you might have a hardware fault somewhere though.  I had a similar problem once and it ended up being a bad mobo.

---

### Post by Juerg on 2006-10-30
> **Chayak said:**
> But seriously you should have a crash dump log with those errors. 

Is there a special setting needed to get a "crash dump log"? My problem is indeed that all existing logs don't give me any hint. 

Regards

Juerg

---

### Post by Juerg on 2006-11-18
I finally managed to take a picture from the screen after a crash (see attachement). I am in a loss to understand what this means.

All hints will be greatly appreciated!

Juerg

---

### Post by tturrisi on 2006-11-19
what kernel? do:
~# uname -r
what hardware?
hints:
[http://ubuntuforums.org/showthread.php?t=251944](http://ubuntuforums.org/showthread.php?t=251944)

---

### Post by Juerg on 2006-11-19
Unbuntu server 6.06.1 LTS 
kernel 2.6.15-27-server
mainboard Intel D865GLC
1 GB RAM
2 SATA harddrives
1 modem on serial device
1 modem on USB device
server load is very low

In contradiction to what is mentioned in the referred thread, we never had any problems during booting. It normally happend after 3-5 days of continuos operation. So I we rebooted the server daily during the last 2 weeks. This seemed to work well, except yesterday, a crash happend just about 6 hours after rebooting...

I am also quite certain that the screen looks different after each crash. I can't remember having seen "soft lockup detected" before. 

It might be worth mentioning that we had the same problems using CentOS instead of Ubuntu. With CentOS it was even worse (i.e. more frequent crashes), so we switched back to Ubuntu Server.

Juerg

---

### Post by tturrisi on 2006-11-19
It sounds like it's most probably hardware-driver related though.  You could try a different kernel (downgraded more stable kernel like what's in etch currently, 2.6.17.2).

---

### Post by Juerg on 2006-11-20
I kind of doubt whether it is a kernel issue, because we had the problems with CentOS and with an earlier version of Ubuntu already.

Couldn't it be a hardware fault? And if yes, how would be the best method to find out which hardware is causing the problem?

All I've done so far is running a memory test - which was OK.

Juerg

---

### Post by r0ydster on 2006-11-21
This could be a heat issue as well.

I was having similar issues with an old P2 box I use as a print server, I was getting kernel panics about every 4 hours.  I swapped out the fans and had the same issues.  

It resolved itself when I turned off ACPI in grub:

```
title           Ubuntu, kernel 2.6.17-10-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-server boot=/dev/hde1 ro vga=791 [COLOR="Red"]acpi=off[/COLOR]
initrd          /boot/initrd.img-2.6.17-10-server
quiet
savedefault
boot

```
I'd try looking at those issues as this point, and maybe consider a more stable kernel.

Mike

---

### Post by Juerg on 2006-11-21
Mike,

Thank you for your suggestions. I tried to boot with acpi=off as you suggested, but then the USB-modem did not work correctly any more. So I had to remove this option again.

Since you are already the second person who recommends to use a more stable kernel: Is there a "howto" available for this? I am concerned to screw up apt whith replacing the existing kernel... And which kernel would be advisable?

Juerg

---

### Post by r0ydster on 2006-11-26
Re-reading the thread, it looks like that you are using the default 6.06 Server kernel, so I think you might be correct in that it is probably not a kernel issue.

It's probably hardware related as someone else pointed out - the hard part is figuring out which part is causing the problem.  You say you ran memtest86, which ran without errors.  I would start googling to find out about any issues with your motherboard and linux.  Maybe someone else is having the same problem.


Another option: Load Edgy 6.10 server on it or another drive and see if the same thing happnens - if so, that would almost guarantee that it is a hardware issue.

Mike

---

### Post by Juerg on 2006-12-02
Thank you for your suggestions. It does not seem to be a general problem of the motherboard - at least I could not find others having similar problems with googling.

However, contrary to what I have said earlier, **the server does still answer ping requests after a crash**. Does this information give a clue whether it is a kernel or a hardware issue?

Juerg

---

### Post by MJN on 2006-12-02
> **Juerg said:**
> Thank you for your suggestions. It does not seem to be a general problem of the motherboard - at least I could not find others having similar problems with googling.

However, contrary to what I have said earlier, **the server does still answer ping requests after a crash**. Does this information give a clue whether it is a kernel or a hardware issue?

Juerg

You said in your original post that it **doesn't** answer pings once 'crashed'... :confused:

This symptom is critical to working out what's wrong as if the 'backend' is still functioning it could be more of a video lockup problem.

Mathew

---

### Post by Juerg on 2006-12-02
Mathew,

Please accept my apologies for the confusion. I was 100% certain that "ping" was not working. Meanwhile we monitored the server with a second linux box based on answers to "ping" requests. The second linux box would have interrupted the power supply for several seconds to make the server boot. To our surprise it didn't work and so we found out that the server was still answering to "ping" requests. It doesn't react to keyboard entries nor to ssh or https (Webmin) requests, though.

> ...it could be more of a video lockup problem

How could we find out more?

Juerg

---

### Post by PilotJLR on 2006-12-02
So it does NOT respond to any services (ssh, https) after crash? I think the entire OS has still crashed, despite a successful ping. Here's why.

Your other computer probably is already aware of the MAC addrs of your server thru the arp cache. When you ping your server AFTER it crashes, the mac address still exists on the lan, though the IP may not. The reason it responds to a ping is because your NIC probably support PXE boot and/or Wake-on-LAN. Both of these features allow the NIC to operate using only ATX soft power... and both are basically bios-level, so the OS doesn't matter.

Again, this is presuming all services also stop responding after a crash.

I personally think it's either CPU / chipset overheating or a hardware problem. If this issue exists with CentOS too, I don't think the kernel is responsible.

---

### Post by Juerg on 2006-12-02
> **PilotJLR said:**
> 
Your other computer probably is already aware of the MAC addrs of your server thru the arp cache. When you ping your server AFTER it crashes, the mac address still exists on the lan, though the IP may not. The reason it responds to a ping is because your NIC probably support PXE boot and/or Wake-on-LAN. Both of these features allow the NIC to operate using only ATX soft power... and both are basically bios-level, so the OS doesn't matter.


This absolutely makes sense. During earlier tests, I checked "Ping" with a Windows PC, which was freshly started. And I am still certain the server did not reply to the ping requests of that PC (as indicated in the first post of this thread). 
However later, we added the above mentioned Linux box (a 2-3 years old Dell Notebook) to constantly monitor the server. And we were absolutely surprised to see that we still got answers to  ping requests after the server crash.

I don't think either that it is a kernel issue. But how can I find out about the true cause? What to do next? 

We have installed some sort of "automatic recovery system", which interrupts the power supply for some seconds after a crash. Shall we just hope it gets worse and some point in the future we will get an error message during startup?

Juerg

---

### Post by r0ydster on 2006-12-02
Do you see any info from your log files?

Are there any relevent error messages in /var/log/messages?
What about /var/log/kern.log, syslog, etc. ??

---

### Post by JeremyA on 2006-12-03
Have you tried booting with the options of:

noapic nolapic

?

I've had to deactivate lapic and apic on some uniprocessor systems in order to get anything approaching stability.  Asus seems to be particularly...uh, questionable.

Jeremy

---

### Post by Juerg on 2006-12-04
No, at least during operation of the system, there are no information available in the logs, which would give us some hints about potential problems.

During booting, we got 2 hints, see bold entries in syslog snippet below:

> Dec  4 10:13:53 UTD-Lx1 kernel: [42949377.800000] libata version 1.20 loaded.
Dec  4 10:13:53 UTD-Lx1 kernel: [42949377.800000] ata_piix 0000:00:1f.2: version 1.05
Dec  4 10:13:53 UTD-Lx1 kernel: [42949377.800000] ata_pci_init_one: pci_dev class+intf: 0x1018f
Dec  4 10:13:53 UTD-Lx1 kernel: [42949377.800000] ata_pci_init_one: NO_LEGACY == 0
Dec  4 10:13:53 UTD-Lx1 kernel: [42949377.800000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Dec  4 10:13:53 UTD-Lx1 kernel: [42949377.800000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Dec  4 10:13:53 UTD-Lx1 kernel: [42949377.800000] ata1: PATA max UDMA/133 cmd 0xE800 ctl 0xE402 bmdma 0xD800 irq 10
Dec  4 10:13:53 UTD-Lx1 kernel: [42949377.800000] ata2: PATA max UDMA/133 cmd 0xE000 ctl 0xDC02 bmdma 0xD808 irq 10
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.070000] ata1: dev 0 cfg 00:0c5a 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:207f 93:0000
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.070000] ata1: dev 0 ATA-6, max UDMA/133, 234441648 sectors: LBA48
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.070000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe7d60
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.070000] ata1: dev 0 configured for UDMA/133
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.070000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe7d60
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.070000] scsi0 : ata_piix
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.340000] ata2: dev 0 cfg 00:0c5a 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:207f 93:0000
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.340000] ata2: dev 0 ATA-6, max UDMA/133, 234441648 sectors: LBA48
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.340000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe7d60
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.340000] ata2: dev 0 configured for UDMA/133
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.340000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe7d60
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.340000] scsi1 : ata_piix
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.340000]   Vendor: ATA       Model: ST3120026AS       Rev: 3.18
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.340000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.340000]   Vendor: ATA       Model: ST3120026AS       Rev: 3.18
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.340000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.350000] **Driver 'sd' needs updating - please use bus_type methods**
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.350000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.350000] SCSI device sda: drive cache: write back
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.350000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.350000] SCSI device sda: drive cache: write back
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.350000]  sda: sda2 sda3
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.360000] sd 0:0:0:0: Attached scsi disk sda
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.360000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.360000] SCSI device sdb: drive cache: write back
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.370000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.370000] SCSI device sdb: drive cache: write back
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.370000]  sdb: sdb1
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.380000] sd 1:0:0:0: Attached scsi disk sdb
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.580000] usbcore: registered new driver usbfs
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.580000] usbcore: registered new driver hub
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.630000] USB Universal Host Controller Interface driver v2.3
Dec  4 10:13:53 UTD-Lx1 kernel: [42949378.630000] ****** SET: Misaligned resource pointer: c1a14dc2 Type 07 Len 0**


Is there something we should do regarding the above information?

Juerg

---

### Post by Juerg on 2006-12-04
Jeremy,

I just rebooted the system with the options of noapic and nolapic.

Thank you for the suggestions. I will inform as soon as I know more.

Juerg

**** Edit:
With both options, the USB modem did not restart after a call (pppd, mgetty). After about 5 minutes we got a system crash, similar to the other ones. The messages on the screen included:

> Call Trace
_do_softirq +0x72/0xe0
sys_softirq ...
_do_softirq +0x72/0xe0
apic_timer_interrupt
...

Does this give useful information?

We have now rebootet the system just with "noapic" (without nolapic). At least the USB modem is now working fine again.

---

### Post by JeremyA on 2006-12-04
Interestingly enough, I googled on that SET: misaligned pointer message, and found this:  [http://lkml.org/lkml/2006/1/20/12](http://lkml.org/lkml/2006/1/20/12)  -- turns out that you can safely ignore that particular message.

This is definitely a peculiar thing.  Have you run memtest86+ against the RAM for a few days to sniff out potential problems there?

---

### Post by Juerg on 2006-12-04
Jeremy,

Thank you for the above link. Regarding memtest86+: I only tested it for about 90 minutes and not for "a few days". Should we have tested it for longer time to make the test result meaningful?

The problem is that the server is used by about 80 external people to replicate information. They dial into the server using ISDN or analog modems basically day and night. This give a very low load on the server, but on the other hand the server should be available 24 hours a day and 7 days per week. But if needed we could announce a down time of 24 hours or whatever is appropriate for the memory test.

Juerg

---

### Post by Juerg on 2006-12-18
**noapic seems to be the solution**

The server has been in operation for 2 weeks without crash after we have booted with the option "noapic". And it is still running fine...

So I assume that "noapic" is the solution to our problem. If the problem should return back, I will post again to this thread.

Thank you very much again to everybody, who helped!

Juerg

---

### Post by JeremyA on 2006-12-18
Wonderful, Juerg!  I'm very glad to have helped.

It does appear that many machines have wonky APIC implementations.

Jeremy

---

