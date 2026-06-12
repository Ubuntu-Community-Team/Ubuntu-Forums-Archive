---
title: "Larger than 800x600 inside Virtual Box (not OSE)"
date: 2008-07-06
forum: Virtualisation
---

### Post by Greyed on 2008-07-06
I'm trying to get KUbuntu to run at a resolution higher than 800x600 inside Virtual Box on an XP host.  Wish it were the other way around but there's a pretty stern requirement that XP be the host.  I've tried all of the suggestions I have found in Google and Ubuntuforum searches to no avail.  I have installed the guest OS utils, twice, edited my xorg.conf file to point to vboxvideo, added the display line with higher resolutions and still am stuck on 800x600.

---

### Post by Greyed on 2008-07-06
How interesting.  I zipped up the image when it was fresh to move to my main box here at home.  Installed the guest additions here and the first reboot it has a larger display.  o.O

---

### Post by Greyed on 2008-07-06
Continuing on the stream of consciousness.  I cannot find a vboxvideo driver anywhere.  On the other hand I do have it set to scale the guest display and X is happily running 1600x1050 with the VESA driver.  o.O

---

### Post by Masoris on 2008-07-07
That's a bug. Read this: [http://www.virtualbox.org/ticket/1689](http://www.virtualbox.org/ticket/1689)

---

