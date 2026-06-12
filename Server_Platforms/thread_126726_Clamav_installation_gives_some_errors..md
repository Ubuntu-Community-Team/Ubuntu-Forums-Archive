---
title: "Clamav installation gives some errors."
date: 2006-02-07
forum: Server Platforms
---

### Post by Janzuka on 2006-02-07
Hello,

When installing Clamav via synaptic, after the installation it pops up a new window that tells me this. E: clamav-base: subprocess post-installation script returned error exit status 1
E: clamav-freshclam: dependency problems - leaving unconfigured
E: clamav-daemon: dependency problems - leaving unconfigured

So if anyone is able to help, i would appreciate it.

---

### Post by Janzuka on 2006-02-07
By the way, i used this guide when installing.  [https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29](https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29)

---

### Post by NotJustANewbie on 2006-02-07
After doing that go to terminal and type:

```
sudo apt-get install clamav
```

All will be solved (I had the same error message). I would suggest installing the clamav-daemon package too.

---

### Post by Janzuka on 2006-02-07
Thanks NotJustANewbie. Clamav is now working. The only thing i still have to figure out,is the updating. But i guess there are good how tos for that. If i can't figure it out on my own, i'll return here to ask some more questions ;)

---

