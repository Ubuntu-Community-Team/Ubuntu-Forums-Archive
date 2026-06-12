---
title: "Odd wallpaper bug..."
date: 2011-12-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sgage on 2011-12-07
Here's a strange one...

If you go to select a wallpaper using the "+" option, you can navigate around the filesystem and pick something you like from wherever. Nice! Now change your wallpaper again to anything else. Now go back and try to pick the one you picked before - the "open" option is grayed out.

It seems that Ubuntu makes an entry in ~/.cache/gnome-control-center/backgrounds when you pick a wallpaper, giving it a catchy filename like "abe9c645b497f500c08a9225f9894f61af4a45c347eca62c6f525d6d25578245", and you can't pick it again as long as it has that entry there. Just delete the entries there, and you can pick anything you like again.

Weird.

---

### Post by cariboo on 2011-12-07
We had the same problem in Oneiric, I'll try and find the bug report.

---

### Post by sgage on 2011-12-07
> **cariboo907 said:**
> We had the same problem in Oneiric, I'll try and find the bug report.

I searched for an existing bug, but didn't find one... let me know what you turn up.

---

### Post by cariboo on 2011-12-07
I found the thread, where the problem was discussed, but it looks like no-one filed a bug. They found the same solution as you, and marked the thread solved.

---

### Post by mc4man on 2011-12-08
Maybe a bug - what is seems to do is the image is saved to ~/.cache/gnome-control-center/backgrounds but it then made available to be chosen  from the - 
Change Desktop Background > Pictures Folder dropdown

So possibly it's considered doing you a favor

---

### Post by Harry33 on 2011-12-08
> **mc4man said:**
> Maybe a bug - what is seems to do is the image is saved to ~/.cache/gnome-control-center/backgrounds but it then made available to be chosen  from the - 
Change Desktop Background > Pictures Folder dropdown

So possibly it's considered doing you a favor

This is very likely the truth here.

---

### Post by sgage on 2011-12-08
> **Harry33 said:**
> This is very likely the truth here.

I see what's happening now. I have so many pictures in my Pictures folder that I didn't noticed. I always wondered why after picking a wallpaper from some random directory it always ended up showing me the Pictures folder. Live and learn! :KS

---

### Post by JRV on 2011-12-08
> **sgage said:**
> I searched for an existing bug, but didn't find one... let me know what you turn up.

Here it is:
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/899647](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/899647)

---

### Post by cariboo on 2011-12-08
> **JRV said:**
> Here it is:
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/899647](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/899647)

That's the bug alright, but if the op or someone else doesn't post how to reproduce the problem, it'll be marked as incomplete.

---

### Post by sgage on 2011-12-09
> **cariboo907 said:**
> That's the bug alright, but if the op or someone else doesn't post how to reproduce the problem, it'll be marked as incomplete.

I added a comment with the relevant info.

---

### Post by VinDSL on 2011-12-11
I've experienced this problem for months (since UbuOO, as cariboo907 said).

Mentioned it several times, in the threads, but nobody else seemed to be affected and/or I didn't explain the prob well enough.

I finally gave up and started using "Image Viewer" to set my walls -- works better than "System Settings", anyway.  ;)

Here's the drill:

[LIST]
[*]Open Nautilus
[*]Navigate to your walls
[*]Open the wall you want with Image Viewer
[*]Click Image -> Set as Desktop Background, or Ctrl+F8
[/LIST]
Simple pimple...

---

### Post by sgage on 2011-12-11
> **VinDSL said:**
> I've experienced this problem for months (since UbuOO, as cariboo907 said).

Mentioned it several times, in the threads, but nobody else seemed to be affected and/or I didn't explain the prob well enough.

I finally gave up and started using "Image Viewer" to set my walls -- works better than "System Settings", anyway.  ;)

Here's the drill:

[LIST]
[*]Open Nautilus
[*]Navigate to your walls
[*]Open the wall you want with Image Viewer
[*]Click Image -> Set as Desktop Background, or Ctrl+F8
[/LIST]
Simple pimple...

Easy peasy! I never knew you could do that! Thanks for the tip! :KS

---

