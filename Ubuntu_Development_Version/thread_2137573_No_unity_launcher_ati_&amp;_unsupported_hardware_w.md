---
title: "No unity launcher ati &amp; unsupported hardware water mark"
date: 2013-04-21
forum: Ubuntu Development Version
---

### Post by Drakx on 2013-04-21
Hi,

I was running 12.10 and as I do with most releases of ubuntu a few days before the final release i tend to upgrade to the current +1. However this time I've ran into something I'm unable to fix.

After the upgrade I had no unity launcher just a blank desktop - so I removed the fglrx drivers and to ensure this was the case I purged them too. I then went on to download the new drivers from amd 13.1 and installed as per the normal way. This failed as it could not find version.h in /lib/modules/3.8.0.19-generic/build.

So Ok i undid what I just did and got into a blank desktop again luckly i was able to use alt + ctrl + t for a terminal in which i opened software-sources and installed the opensource ati driver (which makes my cards fan go at almost full speed). I've since done apt-get install fglrx and again I've got a desktop with no launcher when i try both ccsm and unity --replace my desktop crashes and I have to restart the pc.

below gives a summary of the commands I've used.

 ```

$ sudo sh /usr/share/ati/fglrx-uninstall.sh
$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx

$ sudo init 3
$ sudo sh /path/amd/drivers/13.1.sh --buildpkg Ubuntu/raring
$ sudo dpkg -i /path/to/amd/built/drivers/*.deb

(error version.h not found)

$ sudo sh /usr/share/ati/fglrx-uninstall.sh
$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx


$ sudo apt-get install fglrx


$ lspci | grep ATI
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cayman XT [Radeon HD 6970]
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cayman/Antilles HDMI Audio [Radeon HD 6900 Series]

$ uname -ar
Linux Jupiter 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

Can anyone help getting the unity launcher back and get ride of the water mark?

Thanks.

---

### Post by zika on 2013-04-21
It was a while (several years) that I've not looked back to fglrx...
But, I miss from Your log```
sudo aticonfig[COLOR=#000000] --[/COLOR]initial
```if I remember well...

---

### Post by chaos_monkey on 2013-04-21
I had the same issue as you on a 6670 card.
Resolved it by uninstalling the driver and using the one from the edgers repo.

---

