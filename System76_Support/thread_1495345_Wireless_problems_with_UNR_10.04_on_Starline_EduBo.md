---
title: "Wireless problems with UNR 10.04 on Starline EduBook"
date: 2010-05-28
forum: System76 Support
---

### Post by cowbellemoo on 2010-05-28
I've done a fresh install of Ubuntu Netbook Remix 10.04 on my Starling Edubook (star2) and have persistent wireless problems in the form of networks not showing up most of the time, the usual list of known networks including my own (mere feet away) only appearing rarely, and when finally connected to my network I'm unable to load any webpages.  So basically, wireless isn't working with a fresh UNR 10.04 install.  The stock Edubuntu install, though, connected fine.

Things I've tried:

[LIST]
[*]Un-enabling/re-enabling wireless and all networking via the network manager
[*]sudo apt-get update/upgrade
[*]Installing system76-driver-2.4.9.deb, restarting
(Running the System76 driver gives me a message saying that only Ubuntu 9.10 and earlier versions are supported, and the program exits).
[*]Installing build-essential, restarting, etc.
[/LIST]

I realize that the model is spankin' new and the S76 driver package may not be updated with the new model's drivers yet.  Thanks for any immediate help you can provide or for an ETA on when the drivers should be ready.

Jeff

---

### Post by thomasaaron on 2010-05-28
Please establish a wired Internet connection. Then open a terminal (Accessories > Terminal) and run this command...

sudo apt-get install build-essential

THEN go to the System76 Driver and click the "Restore" tab and the "Restore" button.

When the driver finishes, reboot the computer. Did that fix it?

---

### Post by cowbellemoo on 2010-05-28
(deleted)

---

### Post by cowbellemoo on 2010-05-29
Neverrrrrmind.  All fixed.  apt-get upgrade doesn't install new kernels, but the plain update-manager does.  New kernel installed and now my wireless is doing fine.

yay!

Thanks for your time, though.

---

