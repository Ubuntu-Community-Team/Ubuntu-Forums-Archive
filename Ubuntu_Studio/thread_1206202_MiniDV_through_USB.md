---
title: "MiniDV through USB?"
date: 2009-07-06
forum: Ubuntu Studio
---

### Post by Kopachris on 2009-07-06
I have a JVC GR-D72U and am running Ubuntu 9.04.  I don't have a Firewire cable, but I do have a mini USB cable, and the camera has a mini USB connector.  Is there any way I can get video off of my camera and on to my computer with the USB, or do I need to buy a Firewire cable?

---

### Post by kayosiii on 2009-07-06
Usb is too slow for realtime transfer of DV. (firewire is just fast enough)... 

Many cameras that have a USB connection have this so you can access the camera's memory card. 

It is possible that some cameras do allow transfers of dv via USB but I am pretty sure that this would require special drivers.

I am assuming this is a minidv based camera, newer mp4 based cameras do allow USB transfer of video but in this case act as a mass storage device.

You will probably be saving yourself a lot of trouble by getting a firewire cable.

---

### Post by Kopachris on 2009-07-07
Okay.  Firewire cable it is, then.  Thanks.

---

### Post by jaypmcwilliams on 2011-02-02
> **kayosiii said:**
> Usb is too slow for realtime transfer of DV. (firewire is just fast enough)... 

Many cameras that have a USB connection have this so you can access the camera's memory card. 

It is possible that some cameras do allow transfers of dv via USB but I am pretty sure that this would require special drivers.

I am assuming this is a minidv based camera, newer mp4 based cameras do allow USB transfer of video but in this case act as a mass storage device.

You will probably be saving yourself a lot of trouble by getting a firewire cable.



My apologies, but NOT TRUE anymore. Firewire uses a direct stream thread just slightly above 2.0 (ie 2.1) Well, newer computers have this capability over USB 2.0 or higher. HENCE, the reason why manufacturers are doing away with IEEE1394. They now make a IEEE1394 to USB male adapter, which I have & you CAN stream from here. Tried it in Windows XP Pro (WITH SOME SPECIFIC DRIVERS). Therefore, it SHOULD be possible to do in Ubuntu 10.04, but we have NOT worked on this. WHY???? Jay

---

### Post by MontBlue on 2011-04-18
I have a jvc gr-d73 and have a firewire cable connected. I tried running kino but the computer doesn't recognize the  camera. I've checked the cable. It is a 6/4 pin which should be fine. Anyone have any luck getting a jvc to work in Ubuntu.

---

### Post by kayosiii on 2011-04-21
> **jaypmcwilliams said:**
> My apologies, but NOT TRUE anymore. Firewire uses a direct stream thread just slightly above 2.0 (ie 2.1) Well, newer computers have this capability over USB 2.0 or higher. HENCE, the reason why manufacturers are doing away with IEEE1394. They now make a IEEE1394 to USB male adapter, which I have & you CAN stream from here. Tried it in Windows XP Pro (WITH SOME SPECIFIC DRIVERS). Therefore, it SHOULD be possible to do in Ubuntu 10.04, but we have NOT worked on this. WHY???? Jay

Well this is kind of good news (except that this means that getting computers that work with all my firewire sound gear is going to get more difficult in future). I notice you say the words "specific drivers" that would mean that drivers would need to be written (which means that somebody who cares and can write the drivers needs to have a copy of the hardware).
The cable would almost certainly have to have a chip in it to do the heavy lifting in the conversion. So it could be as simple as having kino look at a usb device file rather than a firewire one(though probably not). Anyways if it were me I would talk to the kino developers and perhaps be prepared to gift one of these cables.

@MontBlue -- I would suspect a permissions issue (these are not always set up correctly) you can check this hypothesis by running the capture program as super user though this is not reccomended as a long term solution. The devices will most likely belong to a group and you will need to be a member of that group to access them. There has been a recent upgrade to the firewire system and that perhaps does not work with the specific programs you are using to capture video (kino?)

---

