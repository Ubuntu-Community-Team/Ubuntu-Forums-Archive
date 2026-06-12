---
title: "baffling JACK/FFADO problems with Echo AudioFire12"
date: 2009-07-22
forum: Ubuntu Studio
---

### Post by ltwelve2 on 2009-07-22
Sorry to start another JACK/FFADO thread, but I can't seem to find one that addresses the problem I have.  Here goes...

When I try to run jack in Ubuntu Studio 9.04, I get the following error:

 p, li { white-space: pre-wrap; }  > 
loading driver ..
 00757461822:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 00:53:39
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire


I believe I have the permissions correct and the module loaded, but I just can't figure this out.  

 p, li { white-space: pre-wrap; }  lsmod | grep 1394 gives:
> raw1394                33116  0 
ohci1394               38832  0 
ieee1394               95932  2 raw1394,ohci1394

lspci | grep 1394 gives:
> 02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

ffado-test ListDevices finds the AudioFire:
> === 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x00309500a0046058  0x00003095  0x00000000   Linux - ohci1394  - 
   1       0x00148607c4428959  0x00001486  0x0000AF12   Echo Digital Audio - AudioFire12


I've also updated the /etc/udev/rules.d/60-raw1394.rules file with:
> KERNEL=="raw1394",    GROUP="audio"
KERNEL=="dv1394*",    GROUP="audio"
KERNEL=="video1394*",    GROUP="audio"
and added myself to the audio group.  

I am seriously out of ideas here.  Can anybody point me to the path out of the woods on this one?

---

### Post by trulan on 2009-07-23
In Jaunty Studio, to get firewire audio working I had to edit this file:
/lib/udev/rules.d/50-udev-default.rules

And add this line:
KERNEL=="raw1394",              GROUP="video"

Of course I need to be a member of group video as well as audio.  I suppose you could put "audio" instead of "video" in that line, but that's not how I was instructed to do it.

---

### Post by ltwelve2 on 2009-07-24
Thanks!  Unfortunately, I added that line, made sure I'm a member of both audio and video, and it still doesn't work.  I seem to have all the requisite permissions, but Jack just gives me the relatively uninformative "firewire ERR:  Error creating FFADO streaming device, cannot load driver module firewire" error and terminates.  

Any thoughts?  

I did notice that the "groups" command shows I'm a member of audio, but when I use the Users and Groups GUI, it doesn't show a group called audio at all.  That seems a little bizarre.

---

### Post by kayosiii on 2009-07-26
what does ls -a /dev/raw1394 show?

---

