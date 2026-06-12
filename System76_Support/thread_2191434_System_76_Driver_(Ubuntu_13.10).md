---
title: "System 76 Driver (Ubuntu 13.10)"
date: 2013-12-02
forum: System76 Support
---

### Post by fredsea2 on 2013-12-02
I have updated my Lemur laptop to Ubuntu 13.10, and, while hunting for printer setup in KDE (no luck: where is it, do you know?), I clicked on the "System 76 Driver" icon which reponded that it only supports Ubuntu up to 12.10! Firing up Synaptic, the application is installed, and it says in the details to click on the "power icon in the upper right" - I am in Unity right now, and there is no power icon anywhere (there is a battery icon, but it does not lead to anything related). This is a bit confusing. Any suggestions? Thank you.

---

### Post by him610 on 2013-12-02
Hello fredsea2,

I too recently upgraded to Ubuntu 13.10. Since you are using Unity this should be no problem. Locate your Systems Settings icon - it looks like a gray gear with an open-ended wrench (spanner) lying across it at an angle. Click on the icon to open it; you should see both an icon for printers and one for power. Click the Printer icon to add your printer; click on the Power icon to adjust your power settings.
If the System 76 Driver indicates it supports only 12.10, you might want to download the latest version of the System 76 Driver from system76.com.

Hope this helps.

---

### Post by isantop on 2013-12-06
It sounds like you have the driver installed from Planet76.com. The current driver is actually handled via a PPA. You can add it and install the driver using these commands:

```
sudo add-apt-repository ppa:system76-dev/stable
sudo apt-get update
sudo apt-get install system76-driver
```

---

