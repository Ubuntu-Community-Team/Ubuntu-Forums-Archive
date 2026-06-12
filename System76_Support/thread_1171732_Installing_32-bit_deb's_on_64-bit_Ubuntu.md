---
title: "Installing 32-bit deb's on 64-bit Ubuntu?"
date: 2009-05-27
forum: System76 Support
---

### Post by imhavoc on 2009-05-27
Is there some good, clear documentation on installing 32-bit deb's on 64-bit Ubuntu out there? I have been using Bibble Pro for my photography for the last few years, and I've really been missing it since I got my new dSLR. Unfortunately, the version I have is 32-bit only, and no plans to release a 64-bit version for a while longer.

Any help would be appreciated. I've looked all over and found fragmented threads, but nothing helpful.

Thanks!

---

### Post by thomasaaron on 2009-05-28
The first thing to try is just installing it. I assume, though, that you have already done that.

The thing I've successfully done if that didn't work is using dpkg's force flag. So, something like...

sudo dpkg --install --force-all hsolink_1.0.118-1_i386.deb

...of course, substitute your own .deb.

Did that work?

---

### Post by imhavoc on 2009-05-28
you'll have to pardon me while I do my Happy Dance! (Don't look... it's not pretty.)

Woohoo!

> dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package bibblepro.
(Reading database ... 197029 files and directories currently installed.)
Unpacking bibblepro (from .../bibblepro_4.10.1-1_i386.deb) ...
Setting up bibblepro (4.10.1-1) ...
adding /usr/lib/bibblelabs/bibblepro/libs/ directory to /etc/ld.so.conf

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


---

### Post by riseringseeker on 2009-06-04
> **thomasaaron said:**
> The first thing to try is just installing it. I assume, though, that you have already done that.

The thing I've successfully done if that didn't work is using dpkg's force flag. So, something like...

sudo dpkg --install --force-all hsolink_1.0.118-1_i386.deb

...of course, substitute your own .deb.

Did that work?

Would 

```
sudo dpkg --install --force-architecture some_deb.deb
```

do what the OP wants and perhaps be some safer?

---

### Post by 3Miro on 2009-06-04
There might be dependencies that cannot be astisfied under the circumstances. You might need additional 32-bit libraries to run whatever you are installing. The 32-bit file might be wrongfully trying to link to the 64-bit library.

---

