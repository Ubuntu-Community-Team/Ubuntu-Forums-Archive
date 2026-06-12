---
title: "brasero  crash when browsing music"
date: 2008-11-03
forum: Ubuntu Studio
---

### Post by frediE on 2008-11-03
if i open brasero (default intrepid 0.8.2) and browse a music directory it crashes with the following info.  anyone see anything like this?

```
 brasero
**
ERROR:gsttagdemux.c:418:gst_tag_demux_trim_buffer: assertion failed: (out_size > 0)
Aborted

```

---

### Post by Stochastic on 2008-11-04
Sounds like you should report this bug to launchpad.net

---

### Post by frediE on 2008-11-04
launchpad.net or gnome.org?  not sure i know the difference.

i did create one on gnome.org
[http://bugzilla.gnome.org/show_bug.cgi?id=559217](http://bugzilla.gnome.org/show_bug.cgi?id=559217)

---

### Post by Stochastic on 2008-11-04
Launchpad is the official Ubuntu bug reporting service, gnome.org deals with all gnome issues...  it's difficult to say if your bug is an Ubuntu specific thing, but I always file my bugs with Launchpad.

---

### Post by frediE on 2008-11-04
launchpad it is.
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/293776](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/293776)

---

### Post by frediE on 2008-11-04
for those who do not know how to create a debug trace, i just learned how....



Thank you for taking the time to report this bug and helping to make Ubuntu better.
A debug trace would be useful in this case.

Open a terminal (Applications > Accessories > Terminal)
Type:

```
brasero -g >> ~/brasero.log
```

Hit Enter.
Then brasero should open up, reproduce your bug. And then close brasero.
Go into your home folder and find the brasero.log file. Upload it as an attachment to this bug report.

---

