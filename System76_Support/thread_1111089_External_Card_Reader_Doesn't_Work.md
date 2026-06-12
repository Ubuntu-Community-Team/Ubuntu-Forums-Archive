---
title: "External Card Reader Doesn't Work"
date: 2009-03-30
forum: System76 Support
---

### Post by Teasdale on 2009-03-30
I've done searches all over for this, and it seems that it's common for people to have problems with Ubuntu not detecting internal card readers - lots of questions on forums, but no responses or solutions. Most commonly, people are told to get an inexpensive external card reader because those seem to work with no problem.

I have a fairly new System76 Ratel Value with Ubuntu 8.10. It doesn't have a built-in card reader, so I got an inexpensive Targus card reader at Walmart. I installed pmount. When I plug the card reader into the USB, the PC picks up that there's something in the USB slot, but it doesn't know what it is and says "unable to mount volume." I've been able to use my digital camera from the same USB slot, so I know the slot works.

I'm at a loss. Ubuntu has never worked with my Palm TX, which seems to be another common Linux problem with few success stories - but if I can just get things on and off my SD card, I can still use my PDA. What I'm having to do now is wait until my son visits from college with his Windows laptop just so I can borrow his internal card reader, but it seems like there ought to be a way to do this on my own PC. Do I need a driver? Where would I begin to search for the one I'd need?

I also have an Ohm card reader; it didn't work, either, so I bought the Targus hoping it was the card reader that was the problem.

---

### Post by thomasaaron on 2009-03-30
It's *probably* not the card reader itself. Although Googling something like "Ubuntu+<model_number_of_card_reader>" would give you a better idea of whether or not there are any issues with that particular reader.

Most likely, it is the actual card. We've run into issues in the past where Ubuntu didn't know how to mount SD cards which were formatted by Palm devices.

To see if this is the case, I'd try using the card from your camera in the card reader and see if *it* works.

---

### Post by Teasdale on 2009-03-30
Thanks for your response - after I posted, I started thinking this very thing - maybe it's not the card reader, but the card itself. I'll try the camera card in the reader.

If it turns out to be the card, is there any fix? Or is that just a limitation pf Ubuntu that I'll have to live with, and continue waiting until I can get on a Windows PC to update the PDA/card?

---

### Post by thomasaaron on 2009-03-30
Well, you could re-format the card using Partition Editor, but that may prohibit the Palm device from using it. 

Most likely, it is just an inconvenient incompatibility.

---

### Post by jdb on 2009-03-30
> **Teasdale said:**
> I've done searches all over for this, and it seems that it's common for people to have problems with Ubuntu not detecting internal card readers - lots of questions on forums, but no responses or solutions. Most commonly, people are told to get an inexpensive external card reader because those seem to work with no problem.

I have a fairly new System76 Ratel Value with Ubuntu 8.10. It doesn't have a built-in card reader, so I got an inexpensive Targus card reader at Walmart. I installed pmount. When I plug the card reader into the USB, the PC picks up that there's something in the USB slot, but it doesn't know what it is and says "unable to mount volume." I've been able to use my digital camera from the same USB slot, so I know the slot works.

I'm at a loss. Ubuntu has never worked with my Palm TX, which seems to be another common Linux problem with few success stories - but if I can just get things on and off my SD card, I can still use my PDA. What I'm having to do now is wait until my son visits from college with his Windows laptop just so I can borrow his internal card reader, but it seems like there ought to be a way to do this on my own PC. Do I need a driver? Where would I begin to search for the one I'd need?

I also have an Ohm card reader; it didn't work, either, so I bought the Targus hoping it was the card reader that was the problem.

My palm has been broken for years so I haven't done it lately,
but I used to be able to sink it using the Evolution mail/caledar application.

Below are some old notes that might be helpful:


```
Palm Pilot:
->edit->Synchronization Options:
 Device Settings: Name Cradle, Type USB, Device usb:, Speed 115200
 PDA Identification: No, Owner dad, PAD ID 27651
 PDA Attributes: Name of PDA MyPilot, Local Folder /home/dad/MyPilot
 Conduits:
  Backup, Time : Enabled
  Eaddress, Ecalander, MemoFile : Synchronize
  EMemos, EToDo, Expense, File, Mail, Sendmail, Test : Disabled
  Settings on each of the above: one time action->copy to PDA
ps -A | grep gpilot
	if there is output (gpilotd) kill the processes
/usr/share/gnome-pilot/devices.xml contains:
        <!-- Palm Tungsten T -->
	<device vendor_id="0830" product_id="0060" />
Pilots
	Name MyPilotReleases:
	ID 27651
	UserName dad
Devices
	Name Cradle
	Port /dev/ttyUSB1
	Speed 115200
	Type USB
Restore backups: kill gpilot as above & use pilot-xfer (Synaptic pilot-link)
	pilot-xfer -p /dev/ttyUSB1 -r /root/MyPilot
         -b <dir> (backup to directory), -l & -L (list commands)

```

jdb

---

### Post by Teasdale on 2009-03-31
I have an EEEPC with Xandros - and the card/reader works fine in there. So I'll just have to use it to transfer files to and from the card for the Palm. It's not the most convenient, but it's workable.

---

