---
title: "Best way to control access?"
date: 2010-04-11
forum: Server Platforms
---

### Post by 1serveyou on 2010-04-11
I will admit I'm a noob to Linux, but after playing around for the past couple weeks, and injuring myself(ie, can't move around so I'm stuck near the computer, so it gave me time to learn Ubuntu), I've managed to setup Ubuntu Server 9.10, and created folders/files toview/edit/execute with Windows and Mac.

Now here is my dilemma, this is for a home server, and I will have 4 users(1 for myself, one with "admin" rights, my fiance(mac user), media pc, and a "guest" account for the computer or 2 that are out in the public(they don't need access to my taxes :P ).

I'd like to have it so that on my laptop, I can access the whole server, but some files/folders would even need me to put in a password. I want to do this because my fiance gets delete happy and deletes things, so if she goes on my computer she won't delete important info. I'd like her to have access to music, photos, and videos, as well as her having her own folder that she can treat as her hard drive. 

The question is, do I need to setup a domain for this, or can I get away with a workgroup? I really appreciate any help on this. If you have a good tutorial for what I'm looking for that would be great too!

Thanks!

---

### Post by dudumomo on 2010-04-12
So, what you can do is set only read permission on your files for everyone except you. This, I guess, will do the trick for your fiancé.
And you need a domaine name for that. Your IP (local IP) is enough.

---

### Post by 1serveyou on 2010-04-12
> **dudumomo said:**
> So, what you can do is set only read permission on your files for everyone except you. This, I guess, will do the trick for your fiancé.
And you need a domaine name for that. Your IP (local IP) is enough.

What about if I don't want them to even know there are other folders/files? And this question will really show my noobness, how does ubuntu know which user is accessing files? I've had it ask me for a login but it never asks, or I don't enter a password and it still allows me to access files(Yes these are from 2 different scenarios).

---

