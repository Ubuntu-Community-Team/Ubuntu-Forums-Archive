---
title: "[SOLVED] VirtualBox"
date: 2008-11-12
forum: Virtualisation
---

### Post by anewguy on 2008-11-12
I was looking to re-install virtualbox again since I have need for another vm at this time.  Last time it went in fine.  I noticed that it is now part of Sun, and their download page says that one of the requirements is a CPU that supports virtualization.  I'm running core-duo E7300 and it doesn't support virtualization.  Am I going to be able to use virtualbox now?

Thanks in advance!
Dave :)

---

### Post by bodhi.zazen on 2008-11-12
If your CPU worked in the past it will very likely work now.

I installed the PUEL edition 2 days ago, went flawlessly.

If VBox does not work for some reason let us know and we can help find an alternate.

---

### Post by anewguy on 2008-11-12
Thanks, Bohdi.zazen!  I was hoping it would be you that answered since I know you are well versed in this!

Thanks again!
Dave:)

---

### Post by prshah on 2008-11-12
> **anewguy said:**
> I'm running core-duo E7300 

The E7300 is Core 2 Duo; are you sure of the spec? (core-duo?) Core 2 Duo CPUs all have Intel VT capabilities.

Besides which, VirtualBox has VT as an option when available, but does not _require_ it. In fact, VT extensions are disabled by default.

---

### Post by anewguy on 2008-11-12
Well, it installed and runs fine.

About the cpu extensions - when I installed Microsoft Virtual PC it claimed that my cpu doesn't support hardware virtualization.  Yes the cpu is listed in the system properties in Windows as Intel(R) Core(TM)2Duo E7300 @2.66Ghz.

Also - I enabled USB in VirtualBox, but it doesn't show my USB device when I plug it in (camera or usb thumb drive either one).  I tried having them plugged into a hub - didn't work.  So I plugged them into the port where the hub was plugged in - still no go.  Is there a limitation as to which ports virtual box sees?  When I look in device manager in Windows it shows 4 usb controllers and 1 usb2 enhanced controller followed by 5 usb root hubs.

Thanks again!
Dave

---

### Post by anewguy on 2008-11-12
I should have probably mentioned - I'm running VirtualBox in WindowsXP with Ubuntu 8.04 as the guest.  My old Ubuntu machine is disabled for the time being, and I still wanted Ubuntu, but require Windows for a work-from-home job as my primary OS.  Didn't want to dual boot, so I opted for VirtualBox since I had used in Ubuntu before to run Windows as a guest.

What's amazing is that my old Ubuntu machine is a PIII-500 with 512mb of memory, and in VirtualBox with 1 gig of memory allocated on my new Windows system (aforementioned core2duo)Ubuntu just screams!  It is SO much faster just in VirtualBox than it was on the stand-alone old box. 

Just another Ubuntu plus!:)

---

### Post by bodhi.zazen on 2008-11-12
I am not so sure about a windows host, but you need to add the usb devices to the guest.

The best link (with screen shots) I could find at the moment is here :

[http://servervirtualization.blogs.techtarget.com/2008/07/14/using-usb-device-filters-with-sun-xvm-virtualbox/](http://servervirtualization.blogs.techtarget.com/2008/07/14/using-usb-device-filters-with-sun-xvm-virtualbox/)

It is an older version of virtual box, but the general gist is the same.

If your usb devices are not listed, may I suggest the vbox forums ?

---

### Post by anewguy on 2008-11-12
Thanks again, Bohdi.Zazen.  I tried following the picture and the user guide but still no go.  Next stop - vbox forum!

Thanks!
Dave :)

---

### Post by anewguy on 2008-11-17
I closed this thread as I have a thread opened elsewhere about the USB problems I am experiencing, but VirtualBox did install and run fine.

prshah - just FYI, according to every review I have read on the net about the core2duo 7300, it does not support virtualization technology.

bodhi.zazen - thanks again for your input here, and in my thread about the USb problems!

Thanks everyone!
Dave :)

---

