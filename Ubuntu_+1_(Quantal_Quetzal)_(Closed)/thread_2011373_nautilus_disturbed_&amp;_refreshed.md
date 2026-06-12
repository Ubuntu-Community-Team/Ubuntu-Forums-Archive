---
title: "nautilus disturbed &amp; refreshed"
date: 2012-06-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by dino99 on 2012-06-27
while nautilus is opened, if a terminal is used or an app is launched, then the nautilus columns are refreshed/redrawn changing their witdh, very strange ;)

---

### Post by philinux on 2012-06-27
> **dino99 said:**
> while nautilus is opened, if a terminal is used or an app is launched, then the nautilus columns are refreshed/redrawn changing their witdh, very strange ;)

Same thing happens when terminal is closed. Could it be a compiz or theme thing.

Ah also try giving focus to firefox and then nautilus.

---

### Post by dino99 on 2012-06-27
> **philinux said:**
> Same thing happens when terminal is closed. Could it be a compiz or theme thing.

Ah also try giving focus to firefox and then nautilus.

hm, will purge compiz to know, otherwise i'm using Ambiance theme

---

### Post by dino99 on 2012-06-27
Well now compiz is fully purged and the problem is still there.

---

### Post by balloons on 2012-06-27
> **dino99 said:**
> Well now compiz is fully purged and the problem is still there.

Can you use kazaam and get a video of this?

---

### Post by mc4man on 2012-06-27
It happens here with any session, both ambiance or adwaita.
Just needs a nautilus window where the contents are larger than window, then it's seen simply with focus on/off/on, ect.

---

### Post by dino99 on 2012-06-28
> **mc4man said:**
> It happens here with any session, both ambiance or adwaita.
Just needs a nautilus window where the contents are larger than window, then it's seen simply with focus on/off/on, ect.

Thanks for this video confirmation. Have reported it:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1018718](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1018718)

---

### Post by philinux on 2012-06-28
> **mc4man said:**
> It happens here with any session, both ambiance or adwaita.
Just needs a nautilus window where the contents are larger than window, then it's seen simply with focus on/off/on, ect.

I've uploaded the vid to the bug report.

---

### Post by dino99 on 2012-06-28
thanks

---

### Post by mc4man on 2012-06-28
It still happens with the new (proposed) nautilus though not quite as much
Though I wouldn't quite suggest upgrading gtk3, nautilus ect. from proposed just yet, it tends to crash a lot
(every few min. here, only tried unity so far - may be semi-related to  accessibility changes in gtk, ect.

---

### Post by dino99 on 2012-06-28
Curiously 3.5.3 is still not into the built queue

but i doubt now this event issue is only concerning nautilus, as i've now troubles with mouse clicking: need to repeat clicks, hard to grab & drop (playing aisleriot for example)

so this whole events disturbing each others let me thinking about whoopsie or something else like memory pointers loops

---

### Post by dino99 on 2012-06-28
oh i see, 3.5.3 has failed to built except on amd64 & powerpc, so i'm still using 3.5.2 here on i386

---

### Post by mc4man on 2012-06-28
> **dino99 said:**
> oh i see, 3.5.3 has failed to built except on amd64 & powerpc, so i'm still using 3.5.2 here on i386

I would hope it stays in proposed until it actually is usable, I'd say here on a unity session nautilus stays running for about a min. at best (there are at least 2 different crashes

On a positive side prior to the gtk3 upgrade all DnD of files/folders showed as empty white while being dragged, that's been fixed

Edit: - just tried Classic - same deal

---

### Post by philinux on 2012-06-28
Looks like it's imminent [https://launchpad.net/ubuntu/+source/nautilus/1:3.5.3-0ubuntu1](https://launchpad.net/ubuntu/+source/nautilus/1:3.5.3-0ubuntu1)

---

### Post by dino99 on 2012-06-28
something strange on i386 (panlong):

Started 43 minutes ago
Finished 35 minutes ago (took 8 minutes, 28.3 seconds)

and still no deb published.

---

### Post by dino99 on 2012-06-28
published now :)

---

### Post by mc4man on 2012-06-28
If you go ahead then the main crash after a retrace will get duped here
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/925503](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/925503)

There is another that comes shortly after a rename
(nautilus crashed with SIGSEGV in g_type_check_instance_is_a()

I'd think this may not be unexpected, if so then newer packages should be coming at some point.
Still think somehow related to this stuff
[https://bugzilla.gnome.org/show_bug.cgi?id=677491](https://bugzilla.gnome.org/show_bug.cgi?id=677491)

---

### Post by dino99 on 2012-06-28
Thanks for the heads up

but:
- i only get nautilus crash on logout (old crash never fixed: unknown vma)
- the issue is older than atk-bridge installation

and today becomes funky:
- nautilus dancing
- mouse click acting as a drunk device

so i've ran "sudo dpkg-reconfigure -a" into a terminal, but it higly use cpu and never ended. Sadly no warning/errors logged about that.

---

