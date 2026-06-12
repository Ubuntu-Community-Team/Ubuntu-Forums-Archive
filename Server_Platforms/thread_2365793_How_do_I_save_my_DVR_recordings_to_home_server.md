---
title: "How do I save my DVR recordings to home server?"
date: 2017-07-10
forum: Server Platforms
---

### Post by jakr2 on 2017-07-10
I've recently just got a security system set up at home. It has 1TB storage and on a 7 day loop. I have a home server with 4TB running ubuntu. I would appreciate some help or a link on how to get my recordings to go to the server. Preferably for example, when the storage runs out on the DVR. That another TB of video saved to the server or if that isn't possible, 2TB of video storing on the server. Thanks in advance.

---

### Post by TheFu on 2017-07-10
Cannot answer without knowing the security system.  Some use proprietary video storage, so copying the files off is less than useful.

---

### Post by jakr2 on 2017-07-10
It's a lorex lh1000 dvr

---

### Post by ajgreeny on 2017-07-10
What filetype are the recordings; .mts, .ts?

Many cameras record one or the other of those, but your system could easily be a proprietary filetype which can not be played by Linux.

---

### Post by TheFu on 2017-07-10
[https://help.lorextechnology.com/link/portal/57356/57366/Article/1516/FLIR-Cloud-Client-Downloading-recorded-video-on-PC-Mac](https://help.lorextechnology.com/link/portal/57356/57366/Article/1516/FLIR-Cloud-Client-Downloading-recorded-video-on-PC-Mac) implies the video is stored in the cloud and some sort of client is needed to access it.  Often, those cloud interfaces aren't complex.

I can only suggest that you review the manual for the specific device and send a support request asking how to do what you want from Linux.

Over the years, I've learned to do this sort of research concerning Linux compatibility BEFORE buying.  If it doesn't look easy or the company isn't willing to help, then I'd return the device ASAP.  Certainly there are Linux-friendly solutions that would be happy to have your business.

---

### Post by slickymaster on 2017-07-10
*Thread moved to **Server Platforms**.*

---

### Post by lisati on 2017-07-10
I've had a look at a [user manual]("https://www.lorextechnology.com/downloads/security-dvr/LHV1000/LHV1000_SERIES_MANUAL_EN_R1.pdf") for the LHV1000 series DVRs. It seems that it is possible to copy recordings to USB devices, which might be useful as intermediate storage. The file formats include DAV and ASF formats. The manual goes on to suggest the use of VLC for playback.

---

### Post by jakr2 on 2017-07-10
> **TheFu said:**
> [https://help.lorextechnology.com/link/portal/57356/57366/Article/1516/FLIR-Cloud-Client-Downloading-recorded-video-on-PC-Mac](https://help.lorextechnology.com/link/portal/57356/57366/Article/1516/FLIR-Cloud-Client-Downloading-recorded-video-on-PC-Mac) implies the video is stored in the cloud and some sort of client is needed to access it.  Often, those cloud interfaces aren't complex.

I can only suggest that you review the manual for the specific device and send a support request asking how to do what you want from Linux.

Over the years, I've learned to do this sort of research concerning Linux compatibility BEFORE buying.  If it doesn't look easy or the company isn't willing to help, then I'd return the device ASAP.  Certainly there are Linux-friendly solutions that would be happy to have your business.



[https://help.lorextechnology.com/link/portal/57356/57366/Article/1575/Recorded-Video-File-formats](https://help.lorextechnology.com/link/portal/57356/57366/Article/1575/Recorded-Video-File-formats) 

There are 4 common file formats DVR / NVR systems use in video backups. .dav Certain models of DVR / NVR create .dav or proprietary video files by default. To view a .dav file, download the Lorex by FLIR video player application available online for PC and Mac. Click here for more information on locating software downloads. .asf files These files can be played on most computers using readily available free software from the Internet. To play an .asf file, use a third party media player such as VLC Media Player. VLC Media Player will play .asf files, and is available for both Windows and Mac operating systems.

With this system. I can watch the video live on any PC in my home but only with the manufacturers software. Do you think I'll be able to watch with other software for ubuntu?

---

### Post by jakr2 on 2017-07-13
Bump

---

