---
title: "Swiftfox Questions..."
date: 2007-04-16
forum: The Cafe
---

### Post by GSF1200S on 2007-04-16
Ive been contemplating the use of Swiftfox for a while now. Ive tried Opera, and while I dont mind it, I miss my extensions. I dont doubt that some of you feel that Opera is lighter, but at least since 2.0.0.3 firefox, it just doesnt seem the case.

My 2 questions:
1) Can I use firefox extensions with Swiftfox?
2) Is there a version I can use on my dual core? Ive looked but it seems they only have single core processors listed...

Any help would be appreciated :)

---

### Post by argie on 2007-04-16
Yeah, all Firefox extensions I've tried so far work on Swiftfox too.

---

### Post by GSF1200S on 2007-04-16
> **argie said:**
> Yeah, all Firefox extensions I've tried so far work on Swiftfox too.

Cool, thats one down...

Does anybody know if theyve released a version for the core2duo, or could I just use a P4 edition?

---

### Post by ssam on 2007-04-16
you might also want to try epiphany browser, its quite a bit lighter than firefox

have a look at [http://live.gnome.org/Epiphany](http://live.gnome.org/Epiphany)

note:  the package in apt is called epiphany-browser (epiphany is a game), and make sure you get the epiphany extensions package too

---

### Post by zanglang on 2007-04-16
[http://www.getswiftfox.com/proc.htm](http://www.getswiftfox.com/proc.htm)

The Prescott version would work. ;)

---

### Post by igknighted on 2007-04-16
You could always compile firefox yourself with the exact optimizations you want/need.  Thats really all swiftfox is, they compile it with certain optimizations for certain processors.  If you did it locally you could probably tweak it a little more.

---

### Post by GSF1200S on 2007-04-16
> **igknighted said:**
> You could always compile firefox yourself with the exact optimizations you want/need.  Thats really all swiftfox is, they compile it with certain optimizations for certain processors.  If you did it locally you could probably tweak it a little more.

I would LOVE to do that.. but honestly the words 'compile firefox' is new to me. I wouldnt know where to begin... What do I need to know to make Fox faster?

Do I actually need to compile Fox out of source code, or are you talking about optimizing it with extensions like "faster fox" etc?

If any of you have any ideas where I could find an online resource that deals with optimizing fox, I could really use it. Google searches usually turn up random forum entries of people with claimed ways to optimize fox, and I dont really know if I can trust them. 

Definitely a good idea though.. I really hadnt thought of it until you mentioned (prolly to nervous to think of it).

---

### Post by igknighted on 2007-04-16
> **GSF1200S said:**
> I would LOVE to do that.. but honestly the words 'compile firefox' is new to me. I wouldnt know where to begin... What do I need to know to make Fox faster?

Do I actually need to compile Fox out of source code, or are you talking about optimizing it with extensions like "faster fox" etc?

If any of you have any ideas where I could find an online resource that deals with optimizing fox, I could really use it. Google searches usually turn up random forum entries of people with claimed ways to optimize fox, and I dont really know if I can trust them. 

Definitely a good idea though.. I really hadnt thought of it until you mentioned (prolly to nervous to think of it).

It would be a compile from source.  If you want to give it a shot check this page out: [http://developer.mozilla.org/en/docs/Build_Documentation](http://developer.mozilla.org/en/docs/Build_Documentation), especially the attached page about Configuring Build Options.  It's a lot of info, but if you build into /opt then you won't risk overwriting your other FF install.  Also, to compile quicker on your dual core, parallel build with -j2 is what you want I believe.  This will build with both cores to speed up the compile, but I don't think thats the option to enable it after the build... I'm sure it says somewhere in the documentation.

---

