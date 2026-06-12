---
title: "How Do I Install WoW Patches?"
date: 2011-04-22
forum: Wine
---

### Post by El3mentGamer on 2011-04-22
Ubuntu 10.10---

When I try to manually install a WoW patch I get this error.
[IMG]http://i1211.photobucket.com/albums/cc434/El3mentGamer/Screenshot.png[/IMG]

I assumed it was because of the missing Microsoft C++ coding. SO, I downloaded 'Mono' from the Ubuntu Software Center. 

It didn't fix my problem. :(

---

### Post by Dlambert on 2011-04-23
Just let it run, in my experience. OR try using playonlinux. And actually install the runtime.

---

### Post by Tweak42 on 2011-04-25
> **El3mentGamer said:**
> Ubuntu 10.10---

When I try to manually install a WoW patch I get this error.
[IMG]http://i1211.photobucket.com/albums/cc434/El3mentGamer/Screenshot.png[/IMG]

I assumed it was because of the missing Microsoft C++ coding. SO, I downloaded 'Mono' from the Ubuntu Software Center. 

It didn't fix my problem. :(

From your screenshot it looks like the patcher is needing Internet Explorer to display patch notes or something. I know the Launcher.exe needs IE to run correctly, but not the individual manually downloaded and executed patches.  The new fancier launcher frontend is identified by the "wow themed" window boarders and buttons.

---

### Post by cwwilson721 on 2011-04-25
> **Tweak42 said:**
> From your screenshot it looks like the patcher is needing Internet Explorer to display patch notes or something. I know the Launcher.exe needs IE to run correctly, but not the individual manually downloaded and executed patches.  The new fancier launcher frontend is identified by the "wow themed" window boarders and buttons.
Not IE, per se, but at least the Gecko install.

When you first run winecfg, it has you install it. Never had a problem after that.

You DID run winecfg after you installed wine, and before you installed WoW (or any other application), right?

---

