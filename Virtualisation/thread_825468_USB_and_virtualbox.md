---
title: "USB and virtualbox"
date: 2008-06-11
forum: Virtualisation
---

### Post by Roen hayden on 2008-06-11
USB and virtualbox 

I installed virtualbox PUEL  useing this guide 
[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

and i followed the instructions but under devices>usb devices the connected usb devices are grayed out.  The os I'm running is windows vista and yes i have guest additions installed. 

any ideas what i did wrong?

---

### Post by niteshifter on 2008-06-11
Hi,

That procedure a little confusing. The steps for getting usb to work are:

1.Edit /etc/init.d/mountdevsubfs.sh - That part in procedure is correct.

2. Add your user to the vboxusers group. That part appears correct. 
Example from my system (/etc/group):
```
vboxusers:x:121:dlk
```
dlk was added to vboxusers, the GID of vboxusers is 121, and was determined when VBox was installed, should not be changed

3. Edit /etc/fstab to have these lines at the end:
```
#usbfs
none /proc/bus/usb usbfs devgid=121,devmode=664 0 0
```
One gets the number for devgid= from the vboxusers entry in /etc/group. The procedure implies two none /proc .... lines to added. Incorrect, there should be only one, like the example above.


This part of that procedure is NOT needed:> 
Allow access to /proc/bus/usb/
in a teminal type:
sudo chown -R root:vboxusers /proc/bus/usb

I would reset that (if you've done the above) with:
```
sudo chown -R root:root /proc/bus/usb
```

Last step: After doing the above, either log out and back in or reboot and your USB should should work.

---

### Post by Roen hayden on 2008-06-11
thanks i had actually got it to work useing that guide i just accidentally skipped a step and didn't realize it thanks again.

---

### Post by Roen hayden on 2008-06-11
> **niteshifter said:**
> 

I would reset that (if you've done the above) with:
```
sudo chown -R root:root /proc/bus/usb
```

Last step: After doing the above, either log out and back in or reboot and your USB should should work.

just wondering but why would i want to reset that?

---

### Post by Roen hayden on 2008-06-11
any one?

---

### Post by philinux on 2008-06-12
I'm interested too.

---

### Post by HyRax on 2008-06-13
I see no reason to have to chown /proc/bus/usb to root because root already owns it and (in my case) there weren't any other listings under it that would have even warranted the recursive switch.

That said, I wouldn't be surprised if not every distro worked like this (though I cannot conceive why root *wouldn't* own /proc/bus/usb at all in the first place!!).

---

### Post by tortoise1 on 2008-06-15
Thanks nightshifter.  Well written instructions.  This worked for me on the first try!

-tortoise1

---

### Post by docplastic on 2008-06-16
> **Roen hayden said:**
> USB and virtualbox 

I installed virtualbox PUEL  useing this guide 
[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)
...
any ideas what i did wrong?

No need to have all that trouble.
Check this for a (much) simpler way: [http://ubuntuforums.org/showthread.php?t=828927&highlight=howto+VirtualBox+hardy+usb](http://ubuntuforums.org/showthread.php?t=828927&highlight=howto+VirtualBox+hardy+usb)

---

### Post by DuGi on 2008-06-19
still doesn't work for me...

I have w active 2 filters but VBox says "No USB devices attached" :(

i find this in VBox.log:

> 
00:00:21.284 EHCI: Hardware reset
00:00:21.284 EHCI: USB Operational
00:00:21.737 OHCI: Software reset
00:00:21.737 OHCI: USB Reset
00:00:21.738 OHCI: USB Operational
[...]
00:00:25.547 OHCI: USB Suspended
00:00:25.659 EHCI: USB Suspended


---

### Post by spanella47 on 2008-06-19
may want to emphasize that the devgid may be different that 121...
also no need to restart or logout/login, just run

sudo mount -a

remounts all the filesystems in fstab, including the newly added usbfs. don't worry, doesnt affect anything.

---

### Post by ashwinvijayakumar on 2008-06-19
Hi,
Getting the USB running on VirtualBox seems to be quite confusing.

> **niteshifter said:**
> 
I would reset that (if you've done the above) with:
```
sudo chown -R root:root /proc/bus/usb
```


My Dell XPS 1330 is running on Ubuntu 8.04 as host and WindowsXP SP2 as guest in VirtualBox, I followed the instructions from [http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)
.The integrated devices (webcam, biometric reader, bluetooth module etc) will be recognized only if I change the owner ship from root to "root:vboxusers (your vbox username, mine is 124:ashwin)" but the guest fails to recognize an external USB pendrive, it shows the device ID in gray color. (yes I have added the device ID in the virtualbox USB settings panel).

Though the webcam is detected on the guest, it doesn't capture any video at all. All it does it show me a blank screen and the led next to the web cam is lit. (I am trying to run the webcam from My Computer->USB Video Device)

---

### Post by docplastic on 2008-06-20
> **ashwinvijayakumar said:**
> Hi,
Getting the USB running on VirtualBox seems to be quite confusing.

Have you tried the HOWTO at: [http://ubuntuforums.org/showthread.php?p=5224346](http://ubuntuforums.org/showthread.php?p=5224346)  ?

---

### Post by ashwinvijayakumar on 2008-06-22
> **docplastic said:**
> Have you tried the HOWTO at: [http://ubuntuforums.org/showthread.php?p=5224346](http://ubuntuforums.org/showthread.php?p=5224346)  ?

Thanks docplastic,
But I have actually got the USB running, the only problem is that it is not mounting the pen drives (though it is recognizing it). The webcam, biometric reader, bluetooth module are all being recognized and mounted as well. Again, problem with the webcam is that even though it is mounted it doesn't capture videos instead it shows be a gray screen (I am opening the webcam through USB video device from My Computer). Anybody come across this issue?

---

