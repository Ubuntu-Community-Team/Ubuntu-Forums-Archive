---
title: "Tascam US122 &amp; 55-tascam.rules"
date: 2009-03-05
forum: Ubuntu Studio
---

### Post by dawiba on 2009-03-05
I tried to install the Tascam tonight using the instructions found here:

[http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122)

However, I get a problem when I get to the section which starts:

'Create a special rule for UDEV to autoload the firmware in /etc/udev/rules.d/55-tascam.rules (requires a kernel > 2.6.15) by using any editor'

I use Text Editor and paste in the instructions and then try to save in the location given - /etc/udev/rules.d/55-tascam.rules, I then get a message telling me I don't have the necessary permissions.

Can anyone help?

---

### Post by simtaalo on 2009-03-05
if you type

```
gksu gedit /etc/udev/rules.d/55-tascam.rules
```

enter in your code then just hit save.

the gksu is the equivalent for programs in the gui to the "sudo" command, which gives your super-user access.

just one of the ways that linux protects you.

---

### Post by dawiba on 2009-03-05
Thanks simtaalo, but I'm afraid the Tascam is still not working. If you have any more suggestions I'd be grateful.

I'll also keep looking on the forums, but there seems to be lots of different advice which is leaving this noob a bit confused!

---

### Post by Cracauer on 2009-03-06
I just installed the deb packages and mine worked.

---

### Post by dawiba on 2009-03-07
I tried follwing the instructions here

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

and here

[http://ubuntuforums.org/showthread.php?t=194490](http://ubuntuforums.org/showthread.php?t=194490)

but when I try this

wget [ftp://chuck.ucs.indiana.edu/pub/array2/linux/opensuse/distribution/SL-10.0-OSS/inst-source/suse/noarch/alsa-firmware-1.0.9-4.noarch.rpm](ftp://chuck.ucs.indiana.edu/pub/array2/linux/opensuse/distribution/SL-10.0-OSS/inst-source/suse/noarch/alsa-firmware-1.0.9-4.noarch.rpm)

I get this

No such directory `pub/array2/linux/opensuse/distribution/SL-10.0-OSS/inst-source/suse/noarch'.

Perhaps, if you already have the deb file, you could make that available somehow?

---

### Post by Cracauer on 2009-03-07
I have it running in Debian, not Ubuntu.

You should send that error message to the package maintainer.

---

