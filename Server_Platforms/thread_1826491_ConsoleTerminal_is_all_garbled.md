---
title: "Console/Terminal is all garbled"
date: 2011-08-16
forum: Server Platforms
---

### Post by timstar on 2011-08-16
Hi everyone, I just installed ubuntu server 11.04 on an older machine and the install is fine but my console is completely garbled. I can't read anything. When I reboot, the grub loader looks fine but as soon as I select my os and it puts me on a command line(I didn't want a gui system)it turns into a mess. If while I'm in grub I choose c for grub console and then pick videoinfo, it seems to fix itself but the fix isn't permanent. This problem does not manifest itself if I ssh into the box from my other pc. Any Ideas on how I can fix this and why it's happening? For a screenshot of the problem please follow this link, [https://plus.google.com/106771927507695556928/posts/TpknAL31U7r](https://plus.google.com/106771927507695556928/posts/TpknAL31U7r)

---

### Post by timstar on 2011-08-18
No one has any ideas? :(

---

### Post by PierreRobiquet on 2011-08-18
I've heard of this happening with a bad GPU but since GRUB is displaying fine I can't think of much else. Have you tried running a memtest? That would be my second thought that maybe a stick of RAM is bad.

---

### Post by timstar on 2011-08-19
Definitely not a bad gpu, this beast is ancient, I'm pretty sure it doesn't have one. I haven't tried a memtest, that's not a bad idea. I have no graphics set up on this thing at all which is why I'm so confused. If I did I would think it's an xconf issue but when it's the pure console, I'm baffled.

---

