---
title: "How come mono is installed by default and java isn't?"
date: 2008-10-15
forum: The Cafe
---

### Post by dixon on 2008-10-15
Why mono is installed by default and java isn't? OpenJDK should be now fully compatible with the sun Java 6, so I was expecting it will be installed by default. I think it could attract a lot(at least some) of the java developers if the java integration in Ubuntu is good.

---

### Post by Polygon on 2008-10-15
mono is open source

java6 is not.

HOWEVER, java 7 is open source, so whenever that comes out (has it already come out?) then it will be open source, and likely will be preinstalled.

---

### Post by zmjjmz on 2008-10-15
I think OpenJDK is pre-installed.

---

### Post by smartboyathome on 2008-10-15
> **zmjjmz said:**
> I think OpenJDK is pre-installed.

It is in Intrepid, though I can't get it to open my WebStart applications. :(

---

### Post by Mr. Picklesworth on 2008-10-15
One reason is because Mono is packaged more as a dependency. There is some really good end user software that Ubuntu ships as default choices, for example F-Spot, which needs Mono to live ;)

---

### Post by directhex on 2008-10-15
> **Mr. Picklesworth said:**
> One reason is because Mono is packaged more as a dependency. There is some really good end user software that Ubuntu ships as default choices, for example F-Spot, which needs Mono to live ;)

And, further to that, Mono is much smaller & less bloated. No, really. Tomboy, including all mono dependencies, takes 50 meg on disk - OpenJDK takes way more than that (about 75MB) with zero apps, due to packaging differences. Those Mono dependencies will shrink by a further 15-20MB in Jaunty.

Space on the liveCD is valuable. If there were killer Java apps people wanted by default, I think there'd be a lot more motivation to shrink down OpenJDK.

---

### Post by cardinals_fan on 2008-10-15
> **Mr. Picklesworth said:**
> One reason is because Mono is packaged more as a dependency. There is some really good end user software that Ubuntu ships as default choices, for example F-Spot, which needs Mono to live ;)
You shouldn't have said that.  Now I'll turn into an anti-Mono zealot simply for the pleasure of watching F-Spot (aka the Program of Pain) die.

---

### Post by bp1509 on 2008-10-15
d

---

### Post by Mr. Picklesworth on 2008-10-15
> **cardinals_fan said:**
> You shouldn't have said that.  Now I'll turn into an anti-Mono zealot simply for the pleasure of watching F-Spot (aka the Program of Pain) die.

Have you tried 0.5? It's a really nice update :)
Lots of clever changes that really justify the program's existence. Then again, I'm biased because I have *always* liked F-Spot. I love the way every facet of photo management can be handled with tags (and the more extensions taking advantage of that, like location tagging and face recognition, will make the feature's advantage very clear). Then again, I also use spatial Nautilus, use Scribes and hate tabbed document interfaces, so I'm a bit crazy.

Tomboy is also one of the Mono dependents, and it is loved by all! (So is GNOME Do, for that matter, although it isn't default).

---

### Post by cardinals_fan on 2008-10-15
> **Mr. Picklesworth said:**
> 
I love the way every facet of photo management can be handled with tags (and the more extensions taking advantage of that, like location tagging and face recognition, will make the feature's advantage very clear).

I'm a bit of a control freak.  gThumb allows me to tag my pictures so that I can find any picture in my 8000 photo library in under 30 seconds.  Kphotoalbum is even better, but it's a bit bloated for my liking.

---

