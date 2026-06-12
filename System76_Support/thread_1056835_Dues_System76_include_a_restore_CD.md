---
title: "Dues System76 include a restore CD?"
date: 2009-02-01
forum: System76 Support
---

### Post by rodm1 on 2009-02-01
I'm looking for a new system and System76 looks like the best option. Do they include a factory restore disk with all notebooks? How easy is there wireless to setup using WPA-TKIP encryption or WPA2?

Thanks,

---

### Post by MorphWVUtuba on 2009-02-01
They do not.  See here:

[http://knowledge76.com/index.php/Restoring_Your_System]("http://knowledge76.com/index.php/Restoring_Your_System")

The only thing you need is an Ubuntu Desktop (live) CD & do a default install, enable the ATI or NVIDIA drivers, and install the System76 Driver.  You can do that by downloading it from a link on that page I linked to or by adding this:

```
deb http://planet76.com/repositories/ ./
```

... to your /etc/apt/sources.list then run

```
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```

... and

```
sudo apt-get install system76-driver
```

... to install.  The app is under System>>Administration.  Hit the "Install" button under the "Install Drivers" tab, then reboot.

Done! :D

---

### Post by rodm1 on 2009-02-02
thank you

---

