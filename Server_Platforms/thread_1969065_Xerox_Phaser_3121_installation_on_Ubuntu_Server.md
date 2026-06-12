---
title: "Xerox Phaser 3121 installation on Ubuntu Server"
date: 2012-04-29
forum: Server Platforms
---

### Post by evgeny9 on 2012-04-29
I'm trying to set up a print server on my Ubuntu Server (12.04, x386).
My printer model is Xerox Phaser 3121, there are official [Linux drivers]("http://www.support.xerox.com/support/phaser-3121/downloads/enza.html?operatingSystem=linux&fileLanguage=en_GB") ([http://www.support.xerox.com/support/phaser-3121/downloads/enza.html?operatingSystem=linux&fileLanguage=en_GB](http://www.support.xerox.com/support/phaser-3121/downloads/enza.html?operatingSystem=linux&fileLanguage=en_GB)).
I set up CUPS with the help of some tutorial, but the printer cannot be found through the web interface.
Moreover, I don't even see it in lsusb output:
```

    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
```I cannot install printer drivers following official help, as I have not got GUI on server. At the same time, [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersXerox](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersXerox) says that my model (its "brother" 3120) should work out of the box...
Couldn't you  help me with the installation process?
Thank you in advance.

---

