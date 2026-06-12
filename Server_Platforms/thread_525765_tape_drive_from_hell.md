---
title: "tape drive from hell"
date: 2007-08-14
forum: Server Platforms
---

### Post by voidlogic on 2007-08-14
I'm having problems getting a tape drive detected. It works dual booting into windows so I don't think its a hardware issue. Its using the megaraid driver. It should be the 2nd device on channel 0, but I don't see anything but my cd-roms in /proc/scsi/scsi. If I do an lspci I see the controller card is indeed detected. The card+drive worked for one boot yesterday for but some reason it only worked that once. Any ideas?

The card is a megatrends 1500 Enterprise and the tape drive is a Tandberg SCSI drive. The tape drive is external and is the only attached device. I already using their custom stinit.def and stinit, but as I thought, since the drive is not detected it did not work. :mad:

---

### Post by HermanAB on 2007-08-14
Look in /dev for something like /dev/tape.
Do lsmod to see whether the SCSI module is loaded.

To write to it, all you need to do is:
tar -f /dev/tape filename

---

### Post by voidlogic on 2007-08-14
I believe I have the mod I need: 
> lsmod | grep scsi
scsi_mod              142348  5 sg,sr_mod,sd_mod,megaraid,libata

As for it being in dev its not. If it was it would be st0 and in any case it must appear in /proc/scsi/scsi for it to be in dev.

Furthermore there is no message in /var/log/dmesg stating that any devices where found to be attached to the megaraid. Yet windows finds everything fine- :mad:

---

### Post by HermanAB on 2007-08-15
Hmm, you can re-initialize a driver by unloading and reloading it.

In one terminal:
tail -f /var/log/messages

In another terminal:
sudo rmmod megaraid
sudo modprobe megaraid

Maybe that will show you something in the log.

Cheers,

H.

---

### Post by voidlogic on 2007-08-15
Thanks Herman :guitar:, That seemed to work, very strange it doesn't work at boot though. :confused:

Now:

cat /proc/scsi/scsi
> 
...
host: scsi5 Channel: 04 Id: 02 Lun: 00
  Vendor: TANDBERG Model: TS400            Rev: 0330
  Type:   Sequential-Access                ANSI SCSI revision: 03
....
and
 mt -f /dev/st0 status
> SCSI 2 tape drive:
File number=-1, block number=-1, partition=0.
Tape block size 0 bytes. Density code 0x0 (default).
Soft error count since last status=0
General status bits on (50000):
 DR_OPEN IM_REP_EN

I guess I'll add reloading to the appropriate run level... Thanks for the help. I should also make sure that works everytime, Let  me know if you have any idea why it did not work at boot.

---

### Post by voidlogic on 2007-08-15
I rejoiced prematurely, after a reboot to unload-reload does not seem to be working. The reload is almost instantaneous and does not seem to properly search the channels for devices. :confused:

---

