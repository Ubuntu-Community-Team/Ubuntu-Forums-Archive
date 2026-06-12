---
title: "libavcodec2 broken?"
date: 2005-11-03
forum: Repositories &amp; Backports
---

### Post by Zyphrexi on 2005-11-03
john@ubuntu:~$ sudo apt-get install mencoder-custom
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mencoder-custom: Depends: libavcodec2 but it is not installable
E: Broken packages


what does this mean?

---

### Post by Xian on 2005-11-03
Looks like somebody overlooked this one. No biggie.
Here's the file you need: [libavcodec2](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/ffmpeg/libavcodec2_0.4.9-pre1-0.2_i386.deb)

Download to your /home/username directory.
Then install with the dpkg -i command.

You will then be able to install the mencoder-custom pkg.

```
$ sudo dpkg -i libavcodec2_0.4.9-pre1-0.2_i386.deb
```

---

### Post by Zyphrexi on 2005-11-03
awesome thanks

---

### Post by elemental666 on 2005-12-17
I see your thank you, and raise you a question, is there a way to add /home/<username> to synaptic's repositories so that it will look for libavcodec2 (or anyother .deb files I dl automatically?

---

