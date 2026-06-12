---
title: "Can't install my printer HP OfficeJet 2620 with new cups snap"
date: 2023-07-30
forum: Ubuntu Development Version
---

### Post by corradoventu on 2023-07-30
On recent ISO of Ubuntu Mantic cups is installed in snap format.
On my Ubuntu Mantic installed from ISO dated 20230722 I can't install my printer HP OfficeJet 2620.
I have the same problem with Mantic installed on same PC other partition from ISO dated 20230728.
I use the printer from the same PC, other partitions with Ubuntu Jammy and Lunar.
I opened a problem on snapcraft forum but i got no help
[https://forum.snapcraft.io/t/unable-to-add-printer-hp-officejet-2620/36109](https://forum.snapcraft.io/t/unable-to-add-printer-hp-officejet-2620/36109)
Here the snap installed on my Mantic:
```
corrado@corrado-n16-mm-0722:~$ snap list
Name                       Version              Rev    Tracking         Publisher      Notes
bare                       1.0                  5      latest/stable    canonical&#10003;     base
core22                     20230703             817    latest/stable    canonical&#10003;     base
cups                       2.4.6-4              980    latest/stable/…  openprinting&#10003;  -
firefox                    115.0.2-1            2916   latest/stable/…  mozilla&#10003;       -
ghostscript-printer-app    10.01.2-1            769    latest/stable/…  openprinting&#10003;  -
gnome-42-2204              0+git.ff35a85        120    latest/stable/…  canonical&#10003;     -
gtk-common-themes          0.1-81-g442e511      1535   latest/stable/…  canonical&#10003;     -
gutenprint-printer-app     5.3.4-1              702    latest/stable/…  openprinting&#10003;  -
hplip-printer-app          3.22.10-1            788    latest/stable/…  openprinting&#10003;  -
ipp-usb                    0.9.23+git8.9fae33b  101    latest/stable/…  openprinting&#10003;  -
ps-printer-app             20230715-1           1214   latest/stable/…  openprinting&#10003;  -
snap-store                 41.3-71-g709398e     959    latest/stable/…  canonical&#10003;     -
snapd                      2.59.5               19457  latest/stable    canonical&#10003;     snapd
snapd-desktop-integration  0.9                  83     latest/stable/…  canonical&#10003;     -
corrado@corrado-n16-mm-0722:~$ 
```

---

### Post by MyMurry on 2023-07-31
Same here (Dell Printer). Today's daily.

---

### Post by MyMurry on 2023-07-31
Have you opened a Ubuntu bug report?

---

### Post by MyMurry on 2023-07-31
sudo apt install system-config-printer

Now I could install a printer, but it doesn't work.

---

### Post by MyMurry on 2023-08-01
[https://discourse.ubuntu.com/t/cups-snap-call-for-testing/21266](https://discourse.ubuntu.com/t/cups-snap-call-for-testing/21266)
 
Have you tried this

[http://localhost:8000/](http://localhost:8000/)

---

### Post by corradoventu on 2023-08-07
For my HP printer the solution is [http://localhost:8003/](http://localhost:8003/)

Now my printer works but scanner is nos recognized [https://bugs.launchpad.net/ubuntu/+source/simple-scan/+bug/2028677](https://bugs.launchpad.net/ubuntu/+source/simple-scan/+bug/2028677)

---

### Post by corradoventu on 2023-08-10
I'm able to print a .txt document from gedit or gted and a picture from GIMP but can not print a pdf from evince or a document from Libreoffice.
[https://discourse.ubuntu.com/t/cups-snap-call-for-testing/21266/37](https://discourse.ubuntu.com/t/cups-snap-call-for-testing/21266/37)

Edit: But now cups snap will be abandoned
[https://discourse.ubuntu.com/t/cups-snap-call-for-testing/21266/57](https://discourse.ubuntu.com/t/cups-snap-call-for-testing/21266/57)
[https://discourse.ubuntu.com/t/cups-snap-call-for-testing/21266/59](https://discourse.ubuntu.com/t/cups-snap-call-for-testing/21266/59)

---

### Post by corradoventu on 2023-08-31
After return to CUPS deb I was able to install my printer applying changes suggested in: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/2033059](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/2033059)

---

