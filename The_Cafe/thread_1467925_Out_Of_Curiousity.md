---
title: "Out Of Curiousity"
date: 2010-05-01
forum: The Cafe
---

### Post by Khakilang on 2010-05-01
Finally I upgraded to Lucid Lynx after 8 hours of download and 2 hours of installation. But something bothers me. I use System Monitor to see my download speed and it show 422Kbps but my Upgrade Manager show only 22Kbps. Why there is such a huge different in the download speed? If my Upgrade Manager were to download at 400Kbps, my upgrade will be something like 1 to 2 hours. Here's the attachment. Anyone care to explain? Nothing really just out of curiousity.
:confused::confused::confused:
[ATTACH]154937[/ATTACH]

---

### Post by Linuxforall on 2010-05-01
I would guess synaptic is showing the progress of a particular file whereas system monitor is showing the total bandwidth used.

---

### Post by ssj6akshat on 2010-05-01
Nay nothing is wrong with you,just the servers might be loaded with traffic

---

### Post by insane_alien on 2010-05-01
that will only show the progress of one file, however multiple files(usually two) will be downloaded at the same time.

if you convert them into the same units(system monitor is in kiloBITS per second, upgrade manager kiloBYTES) you have 52.9KB/s on resource monitor and 22KB/s on upgrade manager

this is what you would expect of two files downloading at the same speed plus some overhead.

---

### Post by Xbehave on 2010-05-01
1 kB = 8 kbits
22 kb = 176 kbits

so about half your d/l is being used on that file.

p.s in future use a mirror and your upgrades should d/l much faster

---

