---
title: "I like it, but...."
date: 2005-08-25
forum: The Cafe
---

### Post by joker on 2005-08-25
First off I want to say overall I like ubuntu, and linux in general for that matter, even though my skills are still very green.  I have a mythtv box running 24/7 in my livingroom, its been rock solid for months.  

So after a random windows worm/bug/whatever caused 4 lockups in 20 minutes, and corrupted 100GB of music (unrecoverable after windows scandisk "fixed" it), which was not on the primary drive BTW, all mine, I ripped them myself, and Yes I know I should have been backing up, I had only a handfull left to rip, I was waiting to do just one full backup... bad idea on my part I guess.  Anyways, after that I decided to kick windows to the curb.  

So far Ubuntu has really been a pleasure to work with.  I have been using it for about 3 weeks, installed multiple desktop environments (although I keep comming back to Gnome)  I have even sold my wife on it and my Dad and Sister both want me to install it on their machines!  

Now the delima, Ubuntu locks up when I try to rip music.  Sometimes is hard locks, sometimes just X locks and I can shutdown with a terminal, sometimes just Grip locks.  Grip will not terminate with a kill command - ever!.  It usually locks half to 3/4 through a CD.  I have tried multiple CDs, this is definitely repeatable.  

To further troubleshoot I installed Ubuntu onto an old 400mhz celeron (256mb ram) which was recently donated to me (using XFCE4 as the desktop)  Same symptoms.  So I thought the machine may just be overtaxed, so I installed damn small linux on it with grip (computer definitely seemed faster FYI) same result.

I am using Grip in its standard config, ogg encoding, with only "play at startup" disabled. I am starting it by clicking on "rip and encode" .  I know I am probibly just missing something but I don't know where to look.  I am using Grip as I ultimately want to use MP3 format and it seemed easier to configure, and it was recommended by others.  I have my reasons for wanting MP3... don't judge me... 

If anyone cares I used to use EAC (exact audio copy) with Lame under windows with great results.  I know the same is possible with linux.  I am tempted to dual boot to get the job done but really don't want to do that.

Someone please help enlighten me!

My main machine is a 2100+ AMD with 768 mb ram.

---

### Post by Stormy Eyes on 2005-08-25
You haven't set up DMA (Direct Memory Access) for your CD-ROM. [Read this HOWTO](http://ubuntuguide.org/#speedupcddvdrom).

---

### Post by joker on 2005-08-25
Why would DMA not being enabled cause grip to lock?  I thought it was only a speed issue.  I am not dobuting you, just trying to understand the situation.

I will try enabling DMA when I get home tonight.

---

### Post by Kvark on 2005-08-25
While you are re-ripping all that music anyway, rip it to a more modern format with better compression then mp3 (like ogg) or without quality loss (like flac). :wink:

---

### Post by Stormy Eyes on 2005-08-25
[QUOTE=joker]Why would DMA not being enabled cause grip to lock?  I thought it was only a speed issue.  I am not dobuting you, just trying to understand the situation.[/QUOTE]

Grip is locking up because the underlying tools -- cdparanoia, cdda2wav, etc. -- are locking up. The underlying tools are locking up because they can't get data off the CD fast enough. They can't get the data fast enough because without DMA enabled, they have to use slower programmed IO methods to extract the audio data from the CD.

---

### Post by joker on 2005-08-25
My main box aldeady has dma enabled for /dev/cdrom, but it is also a dvd burner, does this require setting another flag?

---

### Post by Gnobody on 2005-08-25
[QUOTE=joker]My main box aldeady has dma enabled for /dev/cdrom, but it is also a dvd burner, does this require setting another flag?[/QUOTE]
 tell me what this does: hdparm /dev/hdb


It may be another device, if you have all SATA hard drives it may be /dev/hda or if you have 2 PATA drives it maybe /dev/hdc and so on depending on how many IDE drives you have.

---

### Post by joker on 2005-08-25
the drive is /dev/hdc, here is the output from hdparm /dev/hdc

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

dma is enabled on all ide drives, I don't have any SATA drives

also, how do you force a process to end?  the kill command will not terminate grip or any processes spawned by it.  Nor will the process manager (which i assume to be a prettier form of top)

---

### Post by Wolki on 2005-08-26
I'm sorry, I can't help you with the ripping problem. Did you try SoundJuicer, it works fine for me.

To kill a process when kill <Process ID> or killall <Process Name> fails use the -9 switch like this:

kill -9 <Process ID>
or
killall -9 <Process Name>

To find out the Process ID, use ps -A or look for it in Gnome's System Monitor.

---

### Post by joker on 2005-08-27
here is the error messages i have seen in  /var/log/messages

Aug 24 18:44:06 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Aug 24 18:44:06 localhost kernel: hdc: command error: error=0x54
Aug 24 18:44:06 localhost kernel: ide: failed opcode was 100
Aug 24 18:44:06 localhost kernel: end_request: I/O error, dev hdc, sector 64
Aug 24 18:44:06 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Aug 24 18:44:06 localhost kernel: hdc: command error: error=0x54
Aug 24 18:44:06 localhost kernel: ide: failed opcode was 100
Aug 24 18:44:06 localhost kernel: end_request: I/O error, dev hdc, sector 1120736
Aug 24 18:44:06 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Aug 24 18:44:06 localhost kernel: hdc: command error: error=0x54
Aug 24 18:44:06 localhost kernel: ide: failed opcode was 100
Aug 24 18:44:06 localhost kernel: end_request: I/O error, dev hdc, sector 1119712
Aug 24 18:44:06 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Aug 24 18:44:06 localhost kernel: hdc: command error: error=0x54
Aug 24 18:44:06 localhost kernel: ide: failed opcode was 100
Aug 24 18:44:06 localhost kernel: end_request: I/O error, dev hdc, sector 1119488
Aug 24 18:44:06 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }

I also see this one sometimes:

Aug 27 12:20:12 localhost -- MARK --
Aug 27 12:40:26 localhost -- MARK --
Aug 27 12:43:04 localhost kernel: ide-cd: cmd 0x42 timed out
Aug 27 12:43:04 localhost kernel: hdc: irq timeout: status=0xd0 { Busy }
Aug 27 12:43:04 localhost kernel: hdc: irq timeout: error=0x00
Aug 27 12:43:04 localhost kernel: hdc: DMA disabled
Aug 27 12:43:04 localhost kernel: hdc: ATAPI reset complete
Aug 27 12:44:04 localhost kernel: ide-cd: cmd 0x25 timed out
Aug 27 12:44:04 localhost kernel: hdc: irq timeout: status=0xd0 { Busy }
Aug 27 12:44:04 localhost kernel: hdc: irq timeout: error=0x00
Aug 27 12:44:04 localhost kernel: hdc: ATAPI reset complete
Aug 27 12:45:04 localhost kernel: hdc: irq timeout: status=0xd0 { Busy }
Aug 27 12:45:04 localhost kernel: hdc: irq timeout: error=0x00
Aug 27 12:45:04 localhost kernel: hdc: ATAPI reset complete
Aug 27 12:45:09 localhost kernel: ide-cd: cmd 0x42 timed out
Aug 27 12:45:09 localhost kernel: hdc: irq timeout: status=0xd0 { Busy }

One of these two messages will conntinue until grip is closed.  while grip is locked the encoder (with both ogg and lame) will run for 10 seconds or so then stop for a minute and keep cycling like that.  When grip is killed the encoder will come alive again and finish the track it was working with.  I tried changing the nice settings on both grip and lame, but it did not make any difference.

Also after grip is killed the cd drive will not eject.  I made sure /dev/hdc was not mounted.  I am trying to eject with the button on the cd drive.

---

### Post by joker on 2005-08-27
If anyone knows of another program besides grip which will let me rip using cdparanoia (or another secure method, thats the only *nix solution I know of) and encode with lame (with command line options preferably) and write id3v2 tags please let me know.  I have done some searching but have not found anything other than grip that allows me to do these things under linux.  

The last couple of times I have attempted to rip CDs, I get to the second or third CD before it locks up.

---

### Post by joker on 2005-08-28
Ok, I don't think grip will work for me and i can't find any information  as to why, only that others also have a similar problem, I found no solutions.  

So, does anyone know of another program that will rip securly, encode with lame and write id3v2 tags?  Are there other secure rippers other than cdparanoia in linux?

---

### Post by Brunellus on 2005-08-28
[QUOTE=joker]here is the error messages i have seen in  /var/log/messages

Aug 24 18:44:06 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Aug 24 18:44:06 localhost kernel: hdc: command error: error=0x54
Aug 24 18:44:06 localhost kernel: ide: failed opcode was 100
Aug 24 18:44:06 localhost kernel: end_request: I/O error, dev hdc, sector 64
Aug 24 18:44:06 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Aug 24 18:44:06 localhost kernel: hdc: command error: error=0x54
Aug 24 18:44:06 localhost kernel: ide: failed opcode was 100
Aug 24 18:44:06 localhost kernel: end_request: I/O error, dev hdc, sector 1120736
Aug 24 18:44:06 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Aug 24 18:44:06 localhost kernel: hdc: command error: error=0x54
Aug 24 18:44:06 localhost kernel: ide: failed opcode was 100
Aug 24 18:44:06 localhost kernel: end_request: I/O error, dev hdc, sector 1119712
Aug 24 18:44:06 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Aug 24 18:44:06 localhost kernel: hdc: command error: error=0x54
Aug 24 18:44:06 localhost kernel: ide: failed opcode was 100
Aug 24 18:44:06 localhost kernel: end_request: I/O error, dev hdc, sector 1119488
Aug 24 18:44:06 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }

I also see this one sometimes:

Aug 27 12:20:12 localhost -- MARK --
Aug 27 12:40:26 localhost -- MARK --
Aug 27 12:43:04 localhost kernel: ide-cd: cmd 0x42 timed out
Aug 27 12:43:04 localhost kernel: hdc: irq timeout: status=0xd0 { Busy }
Aug 27 12:43:04 localhost kernel: hdc: irq timeout: error=0x00
Aug 27 12:43:04 localhost kernel: hdc: DMA disabled
Aug 27 12:43:04 localhost kernel: hdc: ATAPI reset complete
Aug 27 12:44:04 localhost kernel: ide-cd: cmd 0x25 timed out
Aug 27 12:44:04 localhost kernel: hdc: irq timeout: status=0xd0 { Busy }
Aug 27 12:44:04 localhost kernel: hdc: irq timeout: error=0x00
Aug 27 12:44:04 localhost kernel: hdc: ATAPI reset complete
Aug 27 12:45:04 localhost kernel: hdc: irq timeout: status=0xd0 { Busy }
Aug 27 12:45:04 localhost kernel: hdc: irq timeout: error=0x00
Aug 27 12:45:04 localhost kernel: hdc: ATAPI reset complete
Aug 27 12:45:09 localhost kernel: ide-cd: cmd 0x42 timed out
Aug 27 12:45:09 localhost kernel: hdc: irq timeout: status=0xd0 { Busy }

One of these two messages will conntinue until grip is closed.  while grip is locked the encoder (with both ogg and lame) will run for 10 seconds or so then stop for a minute and keep cycling like that.  When grip is killed the encoder will come alive again and finish the track it was working with.  I tried changing the nice settings on both grip and lame, but it did not make any difference.

Also after grip is killed the cd drive will not eject.  I made sure /dev/hdc was not mounted.  I am trying to eject with the button on the cd drive.[/QUOTE]
 gnome-volume-manager keeps wanting to mount it.  kill gnome-volume-manager, and you should be able to unmount/eject your cd

---

