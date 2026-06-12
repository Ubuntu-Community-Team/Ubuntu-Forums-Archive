---
title: "target size of ubuntu-core keeps growing during update"
date: 2015-10-04
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-10-04
(107)

I am just updating an install of snappy_personal and I notice now definitively that the target size uf ubuntu- core keeps growing dynamically with the actual size downloaded. I am assuming that this may be a security feature of how the new snappy repositories will work  or, perhaps, it is just anomalous atm since the image is still experimental.

Regards..

---

### Post by ventrical on 2015-10-04
Most recent update appears to have broken system.
Regards..

---

### Post by ventrical on 2015-10-04
No space left on device error.

back to square one with different hdd.

---

### Post by grahammechanical on 2015-10-05
I have been getting out of disk space messages on my desktop wily install even though I increased the partition size. It was happening because personal_x86.img is measuring 10 GB in size. Which reminds me. I need to download another Personal image. I made the mistake of maximising Browser and the max, min, & close buttons disappeared into the top panel just like on a desktop but they do not appear in the top panel so as to be clicked. Re-installing the image is the only way I can think of to get Browser back to default size.

Regards.

---

### Post by ventrical on 2015-10-05
Thanks Graham.

Umm .. what I also meant was that I am getting strange numbers during:

```

sudo snappy update


```

and then

```

30mb/120mb[========>
40mb/140mb[=========>
60mb/200mb[===========>


```

so that is happening on cli in one line during update - the target grows as it updates...so I don't get  the logic of it at all.

Regards..

---

### Post by grahammechanical on 2015-10-05
Having a new daily image there are no updates but I think that in your case it could be downloading more than one file at a time. And switching output between the downloads.

Anyway, today's image has the new wily wallpapers and I was able to get a dialog to put in the WiFi passphrase so it now connects to WiFi. Browser crashes. App store still faking the installation of apps. Now that I have a WiFi connection I will try to install apps with the ethernet cable disconnected.

When I restarted to desktop Wily Unity failed to load. Once I deleted the 10GB personal image I could restart to a working desktop.

"Oh, what fun it is to ride on a one horse open sleigh. Oh, Jingle ..."

Regards.

---

### Post by ventrical on 2015-10-05
On one machine with nVidia card (that was snappy workhorse) I got what appeared to be mir-scatter with the mouse. I switched to  new machine with Intel Xeon HD graphics (plus new hdd) and browser is working just swell. Lost the ability in browser to click and drag side scroll bar but it smooths scrolls when clicked on empty dialog space.

---

### Post by ventrical on 2015-10-05
'about this computer' is working. it even gives accurate size of free disk space on hdd. Not much else though for (108).

---

### Post by ventrical on 2015-10-05
looks like 'mir' is working super fast because I get the side stack shuffle working really well when I bring the mouse arrow over to right hand side of screen.

---

