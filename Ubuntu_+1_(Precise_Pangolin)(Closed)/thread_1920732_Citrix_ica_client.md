---
title: "Citrix ica client"
date: 2012-02-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-02-05
Hello All

[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

The instructions for 11.10 work on 12.04 64bit ok except I had to install the following libraries before I could install the Citrix ica client using dpkg...

```
sudo apt-get install libc6-i386 lib32z1 lib32asound2 nspluginwrapper nspluginviewer
sudo dpkg -i icaclient_12.0.0_amd64.deb
```

With the Citrix Receiver running, I can access my work desktop and use certain applications from there. Then no need at all for windows at home. I shall be testing this as 12.04 goes through more package changes.

---

