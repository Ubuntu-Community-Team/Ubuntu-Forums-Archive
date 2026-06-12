---
title: "UPEK Fingerprint Reader on Daru2 Info from Company"
date: 2008-02-25
forum: System76 Support
---

### Post by reh4c on 2008-02-25
I contacted UPEK and received the information below.  I will try to obtain the beta SDK and post it here to help in getting the Daru2 fingerprint reader to work.  More to follow!!!

[I][B]As per VID and PID you stated in your hardware specification
(147e:2016), your fingerprint reader is only USB scanner with no
coprocessor, while TFM/ESS modules are using biometric coprocessor -
companion chip.

On TFM/ESS matching and all other things are done inside device. Our
BioAPI BSP for Linux supports only the coprocessor based modules, as for
Sonly (Sensor-Only) modules, you need also the matching algorithm as a
part of the library.

Currently, the only possibility to control Sonly devices on Linux is our
brand new BSAPI. It is not based on BioAPI framework, so you do not have
to install BioAPI.

Please note following limitations:
- It is a beta version
- Only 32bit library is available
- Sonly without EEPROM are not supported
- It was tested only on Mandriva (but it should work fine on Ubuntu, as
the kernel is same)

Please let me know if you are interested in getting this beta version of
SDK and what are your plans...

Full version of BSAPI for Linux, which will also support other UPEK
devices, is scheduled on 05/2008.

Best Regards,
[/B][/I]

---

### Post by reh4c on 2008-02-27
The UPEK rep has informed me that the BSAPI SDK is only in alpha stages of development right now, so it won't be available for public beta until April.  On the flip side, if system76 has achieved any true success in getting the reader to work with it's own R&D team, please post a comment or contact me.  I'll be glad to provide System76 with my UPEK contact info.  Thanks.

---

### Post by Bossieman on 2008-04-03
Any news on this?

---

### Post by Gorlith on 2008-04-09
Looking forward to this feature if we get it working.

---

### Post by reh4c on 2008-04-10
I started this thread, but unfortunately haven't heard anything further from UPEK.  The company rep mentioned May as a possible release date for an SDK or driver of some type.  I'll continue to push it.

---

### Post by leptons on 2008-04-11
would it help if we all send some emails to the company? I myself own a daru2 with ubuntu on it and would love to get the fingerprint sensor working.

---

### Post by reh4c on 2008-04-11
My point of contact at UPEK is Mr. Mirek Baran:
[email]miroslav.buran@upek.com[/email]

---

### Post by Gorlith on 2008-04-14
Miroslav Buran to me:
	
Dear Ray!

The first release is scheduled to end of this month (April 2008).

Please try to contact me again at beginning of May 2008.

Best Regards,

Mirek Buran
UPEK

---

### Post by greg_g on 2008-04-14
thanks for the update, I'm looking forward to May 2008 :)

---

### Post by Vadi on 2008-04-15
Same here.

It looks like fprint people meanwhile are going with reverse-engineering the drivers too on their own atm: [http://projects.reactivated.net/fprint/bugs/index.php?do=details&task_id=9](http://projects.reactivated.net/fprint/bugs/index.php?do=details&task_id=9)

Lets hope either one finishes a usable result soon.

---

### Post by shingalated on 2008-07-06
Are there any updates on this?

---

### Post by Vadi on 2008-07-07
None that I heard on this, but the other effort - to reverse-engineer the driver, apparently got some results now. A guy posted on a bug thread that he's got some basics working and would release soon.

---

### Post by Guranic on 2008-07-08
Really hope that someone writes nice HowTo as soon as those guys in fprint project gets the driver work.. I got this fingerprint reader in Acer TM 6292, would be nice to be able to use it :D Counting on you guys...

---

### Post by crichell on 2008-07-08
I've been working with Daniel Drake (libusb and fprint developer) on getting this device supported. We have direct contact with UPEK; however, we're currently stuck on an NDA they require to provide the necessary specifications. We're waiting to hear from the SFLC in regards to our modified NDA to ensure compliance with LGPL.

We're taking the route of developing the driver within fprint rather than UPEK's SDK due to the preference of using one API for device types rather than multiple API's from multiple vendors.

---

### Post by crichell on 2008-07-08
Great news! Just heard from Daniel and code is ready to go. We still have packaging and testing to go but we're close.

This driver will provide support for the fingerprint reader in the the Darter (daru2), Serval (serp3, serp4), Gazelle w/ nVidia (gazp5), and Pangolin w/ nVidia (panv3).

---

### Post by Vadi on 2008-07-09
OK excellent, because I was thinking I'd have to compile the thing manually.

---

### Post by Gorlith on 2008-07-11
> **crichell said:**
> Great news! Just heard from Daniel and code is ready to go. We still have packaging and testing to go but we're close.

This driver will provide support for the fingerprint reader in the the Darter (daru2), Serval (serp3, serp4), Gazelle w/ nVidia (gazp5), and Pangolin w/ nVidia (panv3).

Awesome!

---

### Post by Gorlith on 2008-07-13
just wondering if their is a rough timeline on getting this functionality?

---

### Post by crichell on 2008-07-14
I started a How To to compile and install the driver for those that want to play with their FP Reader before the packages are done. I haven't tested it completely (it will be finished tomorrow). Packages should be done sometime next week.

Feel free to give it a whack if you want. (No guarantee it will work right now)

[http://knowledge76.com/index.php/Fingerprint_Reader_Installation](http://knowledge76.com/index.php/Fingerprint_Reader_Installation)

---

### Post by Vadi on 2008-07-14
Everything worked perfect, except the last step... I get nothing when I click no the menu item.

I get this error in the terminal though:

> vadi@ubuntu-laptop:~/Programs/fpreader$ gksu fprint_demo
vadi@ubuntu-laptop:~/Programs/fpreader$ fprint_demo 
fprint_demo: error while loading shared libraries: libusb-1.0.so.0: cannot open shared object file: No such file or directory
vadi@ubuntu-laptop:~/Programs/fpreader$ 


---

### Post by crichell on 2008-07-14
> vadi@ubuntu-laptop:~/Programs/fpreader$ fprint_demo
fprint_demo: error while loading shared libraries: libusb-1.0.so.0: cannot open shared object file: No such file or directory

I found a Novell post that suggest:

```
sudo ln -s /opt/gnome/lib/libfprint.so.0 /usr/lib/libfprint.so.0
```

Not sure if it works.

---

### Post by Vadi on 2008-07-15
> vadi@ubuntu-laptop:~$ sudo ln -s /opt/gnome/lib/libfprint.so.0 /usr/lib/libfprint.so.0
ln: creating symbolic link `/usr/lib/libfprint.so.0': File exists
vadi@ubuntu-laptop:~$ fprint_demo 
fprint_demo: error while loading shared libraries: libusb-1.0.so.0: cannot open shared object file: No such file or directory
vadi@ubuntu-laptop:~$ 


Hm didn't quite help.

---

### Post by crichell on 2008-07-15
> Hm didn't quite help.

Found the fix, libusb should have had "./configure --prefix=/usr" rather than "./configure". It probably installed into /usr/local instead. Check user local and remove the libusb directory. Then follow the corrected instructions.

---

### Post by crichell on 2008-07-15
I've created a new thread in our main forum section. Please post new replies over here:

[http://ubuntuforums.org/showthread.php?t=860681](http://ubuntuforums.org/showthread.php?t=860681)

---

### Post by Vadi on 2008-07-15
Awesome. Thank you! Hope you can get it working with the Unlock thing too soon (although, imo, it is so annoying! I like gksudo better. It looks better, and isn't so confusing)

---

