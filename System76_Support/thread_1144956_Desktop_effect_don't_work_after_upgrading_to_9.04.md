---
title: "Desktop effect don't work after upgrading to 9.04"
date: 2009-05-01
forum: System76 Support
---

### Post by Peneus on 2009-05-01
Hi I just installed 32bit Ubuntu 9.04 on my daru2. For some reason I cannot get the desktop effects to work. I try to enable them but I get a message saying that "drivers could not be enabled" Does anyone know how to fix it?

Thanks

---

### Post by thomasaaron on 2009-05-01
Compiz has blacklisted your video card. The workaround is in the first post of this thread...

[https://answers.launchpad.net/ubuntu/+question/67975](https://answers.launchpad.net/ubuntu/+question/67975)

---

### Post by drewbenn on 2009-05-01
From what I understand, the workaround can cause your system to crash.  I haven't cared enough about compiz to try it yet.
This is also an issue on my panv3 (I assume we have the same video card).
This link, [https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392]("http://https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392"), implies there will be a fix soon.
I also found these two links interesting enough to bookmark:
[http://wiki.compiz-fusion.org/Hardware/Blacklist]("http://http://wiki.compiz-fusion.org/Hardware/Blacklist")
[https://bugs.launchpad.net/ubuntu/jaunty/+source/compiz/+bug/363821]("http://https://bugs.launchpad.net/ubuntu/jaunty/+source/compiz/+bug/363821")

---

### Post by Peneus on 2009-05-01
Thanks for the prompt replies. Two more questions. Is there any benefit to installing 64bit? 
Does everything work in 32 bit?

Thanks

---

### Post by Vaun on 2009-05-01
I wouldn't try any workarounds just yet as this fix just landed in jaunty-proposed for the Intel drive including un-blacklisting GM965 (8086:2a02) .

[https://lists.ubuntu.com/archives/jaunty-changes/2009-May/009769.html]("https://lists.ubuntu.com/archives/jaunty-changes/2009-May/009769.html")

---

### Post by thomasaaron on 2009-05-01
Vaun is right. If you can be patient, it will be fixed very soon. Nevertheless, I've had no crashes since implementing the work-around. And it's easy to undo once the real fix comes down the pike.

---

