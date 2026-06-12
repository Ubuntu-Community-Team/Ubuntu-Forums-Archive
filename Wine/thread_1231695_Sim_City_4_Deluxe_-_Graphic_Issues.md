---
title: "Sim City 4 Deluxe - Graphic Issues"
date: 2009-08-04
forum: Wine
---

### Post by twshadow101 on 2009-08-04
I have searched high and low on how to do the graphics for Sims City 4 but have had no luck. So I figured i'd post two screen shots of what im getting and see if anyone can maybe help me fix this. I am using SC4 in Wine 1.0.1 on Ubuntu 9.04. Everything works fine such as audio, load time, and such but the graphics is a bit glitchy. I tried originally doing this in Virtualbox but that turned out even worse then using it in Wine.

I have a feeling it might be because it needs DirectX 7.

[IMG]http://kickthestereo.com/sim1.png[/IMG]

[IMG]http://kickthestereo.com/sim2.png[/IMG]

---

### Post by hikaricore on 2009-08-05
You do not need to install DirectX.
Sim City 4 has some known issues and they are listed here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10515](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10515)
There seem to also be a few workarounds listed.

---

### Post by twshadow101 on 2009-08-05
Oh okay, I looked and I don't have a Direct3D folder in my "wine regedit" at [HKEY_CURRENT_USER\Software\Wine] in Wine.

---

### Post by Bios Element on 2009-08-05
> **twshadow101 said:**
> Oh okay, I looked and I don't have a Direct3D folder in my "wine regedit" at [HKEY_CURRENT_USER\Software\Wine] in Wine.

Make it then.

---

### Post by twshadow101 on 2009-08-05
Oh yeah! I followed the details on the other page and with launching it with the command 

> wine C:\\Program\ Files\\Maxis\\SimCity\ 4\ Deluxe\\Apps\\SimCity\ 4.exe -d:software -intro:off

Works perfectly. I am sticking with Ubuntu for sure. It now has EVERYTHING I need. :)

---

### Post by charliewhizbeez on 2012-05-13
I've done everything here (in natty), but created the Direct3D folder.

Not sure I've done that correctly, as I am not a big wine expert.

Help would be greatly appreciated.

---

### Post by charliewhizbeez on 2012-05-15
Bump.

---

