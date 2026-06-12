---
title: "gstreamer-properties and error about UI file"
date: 2015-10-15
forum: Ubuntu Development Version
---

### Post by zika on 2015-10-15
I've got tired of receiveing this error for so long and I did need that app so I've fixed it with big hammer:
in file /usr/share/gstreamer-properties/gstreamer-properties.ui replace (twice)```
<property name="has_separator">False</property>
```with```
<!-- property name="has_separator">False</property-->
```Bigger hammer would be deleting those two lines... ;)

---

### Post by QDR06VV9 on 2015-10-15
Thanks zika for the share. I just started getting that error only on Unity.
I have a different install for Wily Mate with no errors on that one??
Regards

---

### Post by mc4man on 2015-10-15
On a fresh 15.10 Ubuntu install it isn't even going to open anymore. The source is quite dated & only seems to be for gst-0.10
gnome-media is no longer inc. in a default Ubuntu or Ubuntu-gnome install

---

### Post by zika on 2015-10-15
> **mc4man said:**
> On a fresh 15.10 Ubuntu install it isn't even going to open anymore. The source is quite dated & only seems to be for gst-0.10
gnome-media is no longer inc. in a default Ubuntu or Ubuntu-gnome installPatch given above is just for that case. After patch You should be able to use gstreamer-properties as You did before...
Yes, it is for gst-0.10 but it should be present still on fresh install as far as I know.

---

### Post by VMC on 2015-10-15
I don't even have that folder. I guess its distro related.

---

### Post by mc4man on 2015-10-15
> **zika said:**
> Patch given above is just for that case. After patch You should be able to use gstreamer-properties as You did before...
Yes, it is for gst-0.10 but it should be present still on fresh install as far as I know.

not seen - 
[http://cdimage.ubuntu.com/daily-live/current/wily-desktop-amd64.manifest](http://cdimage.ubuntu.com/daily-live/current/wily-desktop-amd64.manifest)
[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/wily-desktop-amd64.manifest](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/wily-desktop-amd64.manifest)

But yes, your changes do allow to open. If it does have any value in use then you should file a bug on if one hasn't been already

---

