---
title: "Transfer midi file to Yamaha keyboard"
date: 2011-10-23
forum: Ubuntu Studio
---

### Post by howlerbr on 2011-10-23
Hello, I have a Yamaha keyboard PSR E423 and I'd like to transfer some MIDIs that came with it on a CD.

In Windows there is a software for doing it. But I really don't know how to do it in Ubuntu Studio. 

Is there a program to transfer a MIDI file from the computer to Yamaha keyboard's flash memory like Windows?

How can I do that?

Thanks a lot! I'm just a beginner...

---

### Post by sgx on 2011-10-24
There is a chance that dolphin, pcmanfm, konqueror, or nautilus,
or other linux filemanager might see the flash memory as a storage device. Then you could drag/drop files using two-window
or two-panel filemanager setup.

Also, check the connections, and the manual to see if it uses a usbstick for file import, it might have a dos based filesystem
onboard that allows a number of midi files to be read from a
usbstick.

Cheers

---

### Post by howlerbr on 2011-10-24
Well I can't see the flash memory in any file manager. The cable is ok, when I use lsusb my keyboard is listed.

I don't want to use Windows only to transfer files back and forth to the keyboard.

Is there any other way of doing it?

Thanks,
Luiz

---

### Post by jejeman on 2011-10-24
Is it a internal built in memory, or a removable memory card that yamaha use?
Do you have sometning like "usb modes" on yamaha to switch beetween file/midi transfer?

---

### Post by howlerbr on 2011-10-24
It's an internal built in memory. I can't see any option in the keyboard regarding usb mode for transfering files.

In Windows, when I use Yamaha software, it lists the flash memory and when I click on it, the lcd in the keyboard automatically writes a message saying it is in the communications mode and the keyboard won't work until I close the Yamaha software. Using this software I can transfer files between PC and Yamaha.

Still not able to transfer under Ubuntu.

---

### Post by jejeman on 2011-10-24
Probably it uses some specific protocol for communication. You should write to Yamaha for support.
Does midi transfer works? A mean can it send midi messages, so you can use it like controler?

---

### Post by sgx on 2011-10-24
> **howlerbr said:**
> It's an internal built in memory. I can't see any option in the keyboard regarding usb mode for transfering files.

In Windows, when I use Yamaha software, it lists the flash memory and when I click on it, the lcd in the keyboard automatically writes a message saying it is in the communications mode and the keyboard won't work until I close the Yamaha software. Using this software I can transfer files between PC and Yamaha.

Still not able to transfer under Ubuntu.
Not guaranteed to work, but you can install wine, and run the yamaha installer with

wine name-of-yamaha.exe

run winecfg to configure wine, and choose alsa in the audio tab.

There will be a new windows environment in your .wine folder in
/home/username  Find the apps and start with

wine path-to-yamaha.exe

the path looks like  /home/you/.wine/drive_c/Program Files etc
Fill in gaps in windows titles like Program Files with a *  Program*Files
when issuing a wine command.
Cheers  

My daughter has that Yamaha, so I'll try it in a week or so, and
post here, or send you a PM with what I find. She has a couple of
linux setups on a laptop and desktop to test with.

---

### Post by sgx on 2011-10-24
You can also try manually copying the yamaha files from windows,
to the equivalent folders in .wine, in case the installer itself won't run correctly. I have resorted to that with some success in the past, as have other folks. Put them on a CD or usbstick, or if dualbooting, use a file manager to copy them.
Cheers

---

### Post by jockyburns on 2011-10-27
> **jejeman said:**
> Probably it uses some specific protocol for communication. You should write to Yamaha for support.
Does midi transfer works? A mean can it send midi messages, so you can use it like controler?


I just bought a Yamaha keyboard and was initially concerned that Yamaha only supply the usb drivers for their keyboards in Win or Mac format. I worried needlessly as connecting the keyboard via usb did indeed list it under lsusb. 
I downloaded Rosegarden midi sequencer software and on the midi device settings, pressed refresh and there was my keyboard. Works a treat BTW. 
For the OP are the midifiles on the cd just basic midifiles?  If so you could probably transfer these to your computer then out to the keyboard.;);)

---

