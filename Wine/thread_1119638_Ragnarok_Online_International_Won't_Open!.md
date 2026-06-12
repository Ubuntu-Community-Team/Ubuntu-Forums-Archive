---
title: "Ragnarok Online International Won't Open!"
date: 2009-04-08
forum: Wine
---

### Post by LiamWilson on 2009-04-08
Hey all, I just downloaded the International Version of ragnarok online. After a whole day of downloading it, I go to open it, and it doesn't work!

I'm using Wine Version 1.1.18, and when I go to open it in a virtual Desktop, it the virtual dektop opens, but then it closes straight away!

I looked on the AppDB, and I saw that you needed 2 DLL's, so I downloaded them, and nothing- It still wont open. So I went the whole hog and copied every DLL from my c:\windows\system32 folder and replaced the original one with them. But still to no avail. Has anyone got any idea how to get it working?

Thanks in advance;
LiamWilson

---

### Post by asdfoo on 2009-04-08
> **LiamWilson said:**
> So I went the whole hog and copied every DLL from my c:\windows\system32 folder and replaced the original one with them.

congrats, you just destroyed your Wine prefix.

either remove or move it and never do this again.

rm -rf ~/.wine


What is the terminal output after removing your old prefix?

---

### Post by LiamWilson on 2009-04-08
thanks for the reply, but i found out the source of the problem; I had cancelled the download of the game. I re-downloaded it, and it works fine. Thanks anyway.

---

