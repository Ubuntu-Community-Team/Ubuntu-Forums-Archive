---
title: "Plymouth Command Failed, Etc."
date: 2011-08-17
forum: Ubuntu Studio
---

### Post by pHerretpHunk on 2011-08-17
Before I start, full disclosure here: I have been awake longer than is probably healthy, so my mind is in a bit of a shambles, to say the least. So, aside from being regularly n00b annoying, I have the added "enhancement" of not having actually written some things down, so I am working from memory here. I know for a fact that I am not being accurate with the exact error messages, but I hope what I can say is enough for someone to go on.

Okay, here goes.

I just installed Ubuntu Studio, and it won't boot. It gives me a "Plymouth command failed" message. I have no idea what this means. After hours of Googling until all my googly bits are sore, I have come to the conclusion that it is way beyond me to decipher what everyone else who has had this problem is saying or what the solution may be.

But wait, there's more. Somehow, now my Linux Mint and Windows installs are affected. Not by Plymouth, I don't think, but after the Ubuntu Studio install, now my computer is unable to mount my Mint or Windows unless I hit "m" to manually try to fix (or words to that effect, per the error message), at which point booting continues normally. This is sporadic with Windows, but it happens every time now with Mint, and it's damn annoying. What the H E double hockey sticks is going on here? Anyone know?

Thanks in advance, and again, apologies for my ignorance, lack of technical data, and all around rambling.

---

### Post by jejeman on 2011-08-17
Editing the kernel line in grub can remove plymouth from booting process. Just erase "splash" from kernel line. Also I suggest to erase and "quiet" to beter troubleshoot problems. After erasing just boot kernel.

---

### Post by pHerretpHunk on 2011-08-17
jejeman, I appreciate the advice. However, being the neophyte that I am at this, I really need some hand holding. Is there a step-by-step guide to do this posted online somewhere that you can direct me to?

---

### Post by pHerretpHunk on 2011-08-17
Also, doesn't editing grub mean having to recompile it or something? I'm not sure I'm up to that yet.

---

### Post by jejeman on 2011-08-18
When grub shows up, select frist entry from above. Than press E to go in edit mode. Find words "quiet splash" and erase 'em. Press ctrl+X to boot like that.
That's all.

---

### Post by pHerretpHunk on 2011-08-18
Well, I tried all that, and Plymouth still failed (it never gave me an option whether to load it or not, it just went ahead and did it). But at that point I pressed "m" and it booted to a black screen, then went to a command prompt. I started X, and it went black again. I logged out, and it said there are Nvidia driver problems. I rebooted, went through the same steps. This never happens with Mint, which is an Ubuntu derivative, so I am very confused. But regardless, even if those steps had worked, what good is an OS that I have to jump through so many hoops every time I boot? I have to re-edit Grub to turn off quiet splash every time, etc. This just is not worth it. I'll stick with Mint and Windows. They may not be perfect, but at least they work. When I want to drive a car, I don't want to have to hot wire it every time, and I certainly don't want to have to build it myself. I want to turn the key and put it in gear. That's what happens with Windows, that's what happens with Mint. That never happens, for me at least, with Ubuntu. Therefore I am giving up on it. If it works for you and you are happy with it, great, blessed be and more power to you. But I need to actually be productive and not spend all my time trying to make something work when I have 2 alternatives that already work out of the box. Peace to you all.

---

