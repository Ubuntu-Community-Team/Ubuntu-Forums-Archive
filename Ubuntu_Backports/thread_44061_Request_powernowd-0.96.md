---
title: "Request: powernowd-0.96"
date: 2005-06-24
forum: Ubuntu Backports
---

### Post by dresnu on 2005-06-24
[http://www.deater.net/john/powernowd.html](http://www.deater.net/john/powernowd.html)

---

### Post by acascianelli on 2005-06-24
> NEW! (5/8/2005) Version 0.96 (threads_per_core fix)
(2/5/2005) Version 0.95
(2/8/04) Version 0.90, see the "ChangeLog" section for details

What's New (5/8/2005)
Just a quick update to 0.96. This fixes the Centrino problem, where the automatic HT detection made Pentium-M systems think they had 0 threads, instead of 1. With this update you should no longer need to run with '-c 1' explicitly set on the command line on those systems. Let me know if there are further issues. For the record, we just default to 1 if we get a weird number. I can't test this locally, but it looks solid. Also fixed a bug with the new table based code broke on systems without scaling_available_frequencies (eg, PPC). If you had problems with 0.95, please upgrade. 0.96 should return powernowd to the simple "run and forget" daemon it was in 0.90.

Thats the changelog for 0.96.

---

### Post by jdong on 2005-06-24
ok

---

### Post by dresnu on 2005-06-25
thank you

---

### Post by acascianelli on 2005-06-27
When the package is updated will it be made available on the backports repository thru synaptic?

I thought it was done allready, I haven't seen it become available yet.

---

### Post by Darrena on 2005-06-27
[QUOTE=acascianelli]When the package is updated will it be made available on the backports repository thru synaptic?

I thought it was done allready, I haven't seen it become available yet.[/QUOTE]
 It is available via staging at this time.

---

### Post by acascianelli on 2005-06-27
[QUOTE=Darrena]It is available via staging at this time.[/QUOTE]

Pardon my ignorance but...whats that mean?

nm, I found it. thx.

How long until it comes out of staging?

---

### Post by Majlo on 2005-06-27
Just add staging repo to your sources list 

*sudo gedit /etc/apt/sources.list* 

And add at the end

[I]## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted[/I] 

Then

*sudo apt-get update*

---

