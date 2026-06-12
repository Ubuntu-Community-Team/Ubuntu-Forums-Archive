---
title: "What version of xulrunner to use w/3.5?"
date: 2009-07-01
forum: Ubuntuzilla
---

### Post by kansasnoob on 2009-07-01
I'd had both Firefox 3.0.11 and 3.5 Beta (aka:Shiretoko) installed in Jaunty. When the update showed up for 3.5 yesterday it installed with no problems so I removed the Beta version using synaptic. (After transferring my bookmarks-places.sqlite)

I then ran apt-get -f install from terminal which indicated to autoremove xulrunner 1.9.1 which I did and I noticed no regression, but I'm just curious what version xulrunner you recommend?

I tried to read the changelogs at the PPA for firefox daily:

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

But it's far beyond my intelligence level. So I'm just curious. No rush.

I also ran the update on Hardy and all seemed to go flawlessly. I didn't think to look and see but I'm sure it's still using xulrunner 1.9.

I'm uploading some torrents right now so I won't be able to reboot for a few hours.

---

### Post by nanotube on 2009-07-02
i have no idea... i'd say just use whatever dependencies the repositories recommend :)

---

### Post by kansasnoob on 2009-07-02
Thank you. I just updated a friends box and he'd removed Firefox 3.0, but your script forced the installation of 3.0 - then completed the update, so it's basically foolproof.

I did however have to transfer his settings and bookmarks from the old 3.5 folder to the new .mozilla. I just copied the entire "8random#.default" and replaced the newly created profile.

Bottom line: your script still works beautifully!

Many thanks ):P

---

### Post by nanotube on 2009-07-02
excellent news. :)

---

