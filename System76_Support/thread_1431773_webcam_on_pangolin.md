---
title: "webcam on pangolin"
date: 2010-03-17
forum: System76 Support
---

### Post by rumpledge on 2010-03-17
Help,
Pangolin Performance, Running Koala.
I plugged in a USB webcam for a silly reason, it was unplugged long ago but now my only available webcam on various programs (Skype, Cheese) is
USB2.0 Camera (/dev/video0)
also when running lsusb the first line which I can turn on and off with FnF10 is
ALi Corp USB 2.0 Camera
I have reinstalled the System 76 driver and it did not change anything and my webcam doesn't work.
Help?
TIA,
Rob Edge

---

### Post by rumpledge on 2010-03-17
Crap.
Somehow, I've managed to stop my microphone and speakers from being recognized aswell. I'm going to try to blame this on reinstalling the system 76 drivers as I don't think I did anything else relevant.
BTW it's a panp5
thanks,
Rob

---

### Post by rumpledge on 2010-03-17
Sorry,
my bad. the sound works well.
The webcam is still not functioning or being recognized correctly.
Rob

---

### Post by thomasaaron on 2010-03-17
Try booting from a 9.10 64-bit live CD and running...

sudo apt-get install cheese

...and see if the webcam works.

You might want to see if it appears in...

lsusb

...before opening cheese. If it's not, press Fn-F10 to turn it on. If it doesn't work from the live CD, you have a hardware issue.

The System76 Driver has nothing to do with the webcam on a PanP5 in Ubuntu 9.10.

Did you install 64-bit Ubuntu or 32-bit? We recommend 64-bit, as we no longer test with 32-bit.

---

### Post by rumpledge on 2010-03-17
Once again thanks for the quick helpful response.
Makes sense. I'm using 64-bit, and the live CD check didn't work.
It would appear it is a hardware issue. The camera has functioned well for many hours and perhaps I have finally nuked it. I have used it for multiple 6hour sessions of conferencing. Unfortunately the inconvenience of getting it fixed outweighs the inconvenience of being sans laptop for any amount of time and using a peripheral camera.
FYI I have found a logitech camera that works right out of the box.
thanks again,
ROb

---

### Post by miniyak on 2010-03-17
Rumpledge, search "panp5 webcam" within the s76 forum. You will find that this issue has affected a handful of users including myself.

Personally, at this point i plan on leaving things as they are.. My panp5 gets used anywhere between 2-5hours a day. Its sort of mission critical and if i need a webcam i can just use an external one. The eyetoy in karmic works for me.

 I have a couple of questions for Tom. Lets say we were sure this was a hardware defect and the same issue is affecting a large number of customers.  

 Also I understand normally this is probably looked at on a per problem basis, but what is s76's policy on rectifying this type issue? Do you talk with the oem?

---

### Post by thomasaaron on 2010-03-18
I've actually only seen a handful of these issues with the PanP5. It's turned out to be a bad webcam in about every case.

If it doesn't work from a live 9.10 64-bit CD, it's a bad webcam. 

We can have the machines repaired. Just contact me via email.

support...at...system76...dot...com

---

### Post by ArielSonique on 2011-04-25
Hi,

I bought a System76 Pangolin in March. The camera used to work with skype and cheese initially. However, after a reinstall of the Ubuntu 64bit version, the camera is not even being recognized any more. I tried the lsusb command at the terminal but the camera is not in the list. Cheese tells me that "no device was found". 

Please help!

Thanks.

---

### Post by ArielSonique on 2011-04-25
Thanks, Ian and Thomas for the extremely fast support email. My camera has started working again. I rebooted the system, pressed Fn+F10 and restarted cheese and skype. 

I was a bit worried there, but it was an easy solution! :-)

---

### Post by val67 on 2011-04-25
> **ArielSonique said:**
> Thanks, Ian and Thomas for the extremely fast support email. My camera has started working again. I rebooted the system, pressed Fn+F10 and restarted cheese and skype. 

I was a bit worried there, but it was an easy solution! :-)

well, can you please post the solution as well, not just the thanks to your benefactors. 

Or was it as simple as rebooting the computer &c.

---

### Post by isantop on 2011-04-27
Rebooting and pressing Fn+F10 was all it took. Glad to hear your system is back up and running.

---

### Post by ArielSonique on 2011-04-27
> **val67 said:**
> Or was it as simple as rebooting the computer &c.

Yes, that was it. I wonder how it turned off in the first place... Must have been the reinstall. I had Linux Mint on it and then migrated to Ubuntu again - that's when the camera must have turned off.

---

### Post by smarmytime on 2011-04-28
It may just be that you have to turn the cam on every time you reboot... I have to hit Fn-F10 every time I reboot, if I want the cam on on my PanP7.

---

