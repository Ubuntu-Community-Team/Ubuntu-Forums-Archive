---
title: "wifislax iso file"
date: 2014-07-31
forum: Security
---

### Post by tendouser on 2014-07-31
I downloaded wifislax 4.9 but I can't create a bootable USB.  I am doing everything right ....using Unetbootin and UUI ....when I try an Lubuntu bootable USB I have no trouble and succesfuly get job done!

Any help?

---

### Post by uRock on 2014-07-31
Have you tried their forums? We don't typically offer support for other distros on Ubuntu Forums.

---

### Post by cariboo on 2014-08-02
Actually we do now have a section for support of other distro's, [here]("http://ubuntuforums.org/forumdisplay.php?f=401"). We haven't quite finished with the changes we are going to make, but there will be sections devoted to many other distributions.

Have you tired dd to create a bootable USB device? use the following command:

```
sudo dd if=<path to iso> of=/dev/sdx bs=1M
```

where <path to iso> = the name of the iso you wish to use.
where /dev/sdx = device label, in my case I use sdc.

---

