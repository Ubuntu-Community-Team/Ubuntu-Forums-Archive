---
title: "Lemur brightness hotkeys"
date: 2010-08-01
forum: System76 Support
---

### Post by msrinath80 on 2010-08-01
Hi again,

I plan to install OpenSUSE 11.3 on the Lemur. While I've figured out what needs to be done for the webcam driver by unpacking the System76 driver deb file and examining the python scripts in there, I was wondering if someone from System76 could point out the modifications done to make the Fn-keys for brightness work.

Thanks!

Update: I finished installing OpenSUSE 11.3 on the Lemur. So far, the only thing that does not work are the brightness hotkeys. However, the brightness itself can be adjusted using the command line or the KDE power management settings. Even the webcam worked right out of the box!

---

### Post by isantop on 2010-08-03
I did a bit of googling, and I found out on an OpenSuse forum that you'll need to add "acpi_osi=Linux" as a kernel parameter to make the brightness hotkeys work. 

I'm not sure if OpenSuse is still using legacy GRUB or GRUB2, so you'll need to check with the OpenSuse crowd as to how exactly to add a boot parameter.

---

### Post by msrinath80 on 2010-08-03
Thanks very much for that hint isantop. After trying acpi_osi="Linux", I googled a bit more and tried acpi_osi="!Linux", acpi_osi="Windows 2006" and acpi_osi="!Windows 2006". Neither of them worked!

Before I was about to give up, I decided to check out the complete list of options for the kernel parameter acpi_osi and found that one of the settings is simply:

```
acpi_osi=
```

without any strings appended after the "equal to" symbol. Apparently, this disables all strings since it seems that the kernel by default appends something to this parameter. And guess what, this worked!

Thanks a bunch!

---

### Post by isantop on 2010-08-03
Despite having given the wrong solution, I take pride in the fact that through my wrong solution, you were able to extrapolate the correct solution. This is what I love about Linux. If one person make a mistake, others grow on and learn from the mistake. Windows doesn't let you specify boot parameters to begin with, so it would never have made it that far.

Congratulations on fixing your problem. :)

---

### Post by msrinath80 on 2010-08-04
Totally concur :)

---

### Post by msrinath80 on 2010-08-05
Just an update. OpenSUSE 11.3 was sooooooo unstable. Flash with full screen playback would lock up, torcs would lock up in the middle of a race, as would quake3. I've reverted to Debian squeeze (32 bit with the bigmem kernel so I can use all 4 Gigs) for good. Ahh, the stability :) And yes, for anyone who is interested, everything works out of the box with Debian squeeze. Just the webcam requires some firmware and a rebuilding of a kernel module. Grab the system76 driver deb file, unpack it, and find the python script that downloads and builds support for the Lemur webcam. Follow those instructions and you're good to go!

---

