---
title: "Ubuntu on windows network?"
date: 2008-04-14
forum: United Kingdom Team
---

### Post by Martin Flynn on 2008-04-14
I have a windows network set up between my desktop and laptop wired through homeplugs. I also have an old computer running 7.10 wired directly to my router. I can print from the linux m/c and can see/access  my other m/c's from it but I cannot access/see  the linux m/c from the other two.
Anyone able to help?
:(

---

### Post by pedro_orange on 2008-04-14
You can get onto Windows boxes from Ubuntu by using: smb://192.168.0.1 in Naut.

You can't see the linux box from the Windows boxes? 

Have you set up specific shares on the linux box you wish to share? Linux doesn't just broadcast it's availability to the world like Windows does.
You should be able to see shares on ur Linux box from Windows if you specifically share a folder on the Linux box.

You can use something like Samba if you need to do alot of Windows->Linux (And visa versa) transfers.

You might be better off asking this sort of question on the Networking part of the forums!

---

