---
title: "[SOLVED] Distribution Update"
date: 2008-07-25
forum: System76 Support
---

### Post by ewg on 2008-07-25
Update manager keeps displaying a Distribution Update for Gimp: libgtk1.2 but it is always "grayed out" making it non-selectable for me. I do have and use Gimp. Any ideas on why the update is listed but not really available?

Thanks,

---

### Post by thomasaaron on 2008-07-25
Hmmm....

I'm not seeing that one.

It could be that they put it in for download and then realized something was wrong with it, or they don't have some dependency quite ready yet. I've seen that happen before.

---

### Post by Hedley on 2008-09-12
This same file has been sitting in my update manager for quite a while now, as well. 

Attached list of changes:

[INDENT]Version 1.2.10-18.1build2: 

  * Triger another rebuild so that hppa gets to do the libglib1.2 as well.


Version 1.2.10-18.1build1: 

  * Rebuild for libglib1.2 -> libglib1.2ldbl transistion.


Version 1.2.10-18.1: 

  * 0-day NMU, authorized by one of the package uploaders (Marc
    Brockschmidt).
  * High-urgency upload for RC bugfix.
  * Replace use of deprecated ${Source-Version} substvar with
    ${source:Version} or ${binary:Version} according to the use, making
    the package installable in the face of binNMUs.  Closes: #433253.
[/INDENT]

---

### Post by GreaterCore on 2008-12-26
Hi guys,

I had the same problem too, but I think I fixed it after running 'sudo apt-get install libgtk1.2'. So far I have managed to remove it from the update list and no problems with the rest of the software yet.

Hope this helps!

---

### Post by ewg on 2008-12-26
Yes, that's what i did also. It's fixed. I should have marked it solved back then.

---

### Post by lxowle on 2009-10-05
I had the same problem with "ubuntu-desktop" on 9.10 beta. The solution described here worked too. Thanks.

---

