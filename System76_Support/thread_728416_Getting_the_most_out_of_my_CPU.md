---
title: "Getting the most out of my CPU"
date: 2008-03-18
forum: System76 Support
---

### Post by Replicon on 2008-03-18
Hi,

My Serval Performance just arrived, and I'm setting it up. I got one with the Core 2 Duo T7700 2.4 GHz 800 MHz FSB 4 MB L2.

When I run 'top', should I be seeing 2 CPUs or just one? I don't mind seeing just one, so long as it's an aggregate (and not just wasting the other core without using it to the fullest). Do I need to install maybe some smp package?

thanks

---

### Post by imhavoc on 2008-03-18
top doesn't display multiple CPUs by default any more. After firing up top, hit '1' to display the other CPU(s). You can probably set multiple CPU display as the default some how, but I haven't bothered to look in the documentation for it.

---

### Post by gtrtx on 2008-03-18
You may also want to try htop....like top but has a couple more features...it shows both cpus by default.

sudo apt-get install htop

---

### Post by Replicon on 2008-03-18
Ah good it works out of the box :)

htop is nice, but it seems to be inconsistent in its memory display. Based on /proc/meminfo, top is the one that's correct.

---

### Post by Dave_Connor on 2008-03-26
I like htop but it needs to be smaller since on my laptop it uses 2% of my dual CPU and it is a bit of a hog. Nice program but bulky at times.

---

