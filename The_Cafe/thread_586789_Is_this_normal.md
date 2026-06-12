---
title: "Is this normal"
date: 2007-10-22
forum: The Cafe
---

### Post by Paul820 on 2007-10-22
Tracker is really taking over my system, is this normal that it's taking so much memory? And if it is, WHY!! It is now up to 891.6Mb

---

### Post by Anessen on 2007-10-22
My trackerd sometimes goes insane too. I think it might be related to Folding At Home?

---

### Post by Steveway on 2007-10-22
That's normal, it is indexing your whole computer, wich takes a lot of CPU-time and needs pretty much memory.
It will use less when it is finished.
You can set it to a lower priority in the settings.

---

### Post by Paul820 on 2007-10-22
It seems to be a lot of memory for indexing files, it's now at 916.4Mb :shock:

@Steveway, it is at low priority, it's set to 19. I hope it doesn't do it too often because my mouse jumps across the screen :lolflag:

---

### Post by Paul820 on 2007-10-22
This thing has been going since around 4.00 O'clock (UK), and it's still indexing :lolflag:

---

### Post by n3tfury on 2007-10-22
did you just install ubuntu?  i disabled that garbage.  don't use it anyway.

---

### Post by Wiebelhaus on 2007-10-22
I turn it off , but it's using unused resources to index once it's done it'll kick into a sniff type mode and won't use so much.

---

### Post by Paul820 on 2007-10-22
Yeah, i had loads of junk on my drive from when i was testing RC. I wanted a clean system.

---

### Post by kc8hr on 2007-10-23
> **Steveway said:**
> That's normal, it is indexing your whole computer, wich takes a lot of CPU-time and needs pretty much memory.
It will use less when it is finished.
You can set it to a lower priority in the settings.

I just removed it. Tracker was killing my old Althlon 1100XP

Thanks!
Tim

---

### Post by Nameless_one on 2007-10-25
Tracker shouldn't be using more than 4-5 mbs even when indexing. Version 0.5.0 had some problems with hiogh CPU usage, but I've never heard of this! It works very well for me, it's not garbage. It's much faster and better than beagle.

---

### Post by Paul820 on 2007-10-25
> **Nameless_one said:**
> Tracker shouldn't be using more than 4-5 mbs even when indexing. Version 0.5.0 had some problems with hiogh CPU usage, but I've never heard of this! It works very well for me, it's not garbage. It's much faster and better than beagle.

Well there must be something wrong somewhere if it's only supposed to use 4-5Mbs. I had to kill it as my computer nearly stopped responding, when i moved the mouse it took about 10 seconds to move the pointer. I have switched it off now, i stopped it indexing after nearly 8 hours of it. Why it takes 8 hours( or more if i left it on ) to index 66,000 filles i don't know! It was only set to index my home directory, nowhere else.

---

### Post by kc8hr on 2007-10-25
The issue wasn't high CPU usage, it was excessive disk usage. I will re-install tracker and try it again.

Thanks,
Tim

---

### Post by Crashmaxx on 2007-10-25
Why did they included tracker by default anyway? I've seen very few people that actually like it. And a lot of people with it just consuming tons of resources. I don't know what they were thinking.

---

### Post by Beebock on 2007-10-26
> **Crashmaxx said:**
> Why did they included tracker by default anyway? I've seen very few people that actually like it. And a lot of people with it just consuming tons of resources. I don't know what they were thinking.

linux's new 'blotware'??

---

### Post by Qinjuehang on 2007-10-28
It might not be indexing...maybe just watching for file changes.

---

### Post by n3tfury on 2007-10-28
> **Qinjuehang said:**
> It might not be indexing...maybe just watching for file changes.

when you first install gutsy, trust me, it's indexing.

---

### Post by Polygon on 2007-10-28
notice the nice level: 19

that means it is the absolute LOWEST priority program running on your computer

so even though it looks like its taking over your ram and CPU usage, if anything else intensive wants resource, linux is going to give that program what it needs, cause trackerd is at the bottom of the totem pole

so its using 700+mb of ram cause you have 700+mb of ram free not doing anything, so linux gave it to trackerd. same thing happens with shared computing programs like BOINC and [email]Folding@home...it[/email] uses up 100% of your cpu...but since its the lowest priority level i experience no system slowdown.

---

### Post by n3tfury on 2007-10-28
> **Polygon said:**
> notice the nice level: 19

that means it is the absolute LOWEST priority program running on your computer

so even though it looks like its taking over your ram and CPU usage, if anything else intensive wants resource, linux is going to give that program what it needs, cause trackerd is at the bottom of the totem pole

so its using 700+mb of ram cause you have 700+mb of ram free not doing anything, so linux gave it to trackerd. same thing happens with shared computing programs like BOINC and [email]Folding@home...it[/email] uses up 100% of your cpu...but since its the lowest priority level i experience no system slowdown.

that's great for you.  it was making my laptop unusable and even surfing was an absolute chore until i nuked trackerd.

---

