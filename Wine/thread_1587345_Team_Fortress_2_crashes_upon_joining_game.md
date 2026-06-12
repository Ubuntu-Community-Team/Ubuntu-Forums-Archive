---
title: "Team Fortress 2 crashes upon joining game"
date: 2010-10-03
forum: Wine
---

### Post by ZeroCore on 2010-10-03
I just recently got Team Fortress 2 to install and whenever I try to join a game, the load bar goes up to 99% (sending client info), stops, and the game quits. Steam is still running and operational afterward however. Also, the game's menu and start-up sequences work just fine. The only problem is that I can't join a game. 

I'm running Ubuntu 10.04 Lucid Linux with an 80 gig hard drive, have Wine 1.2 installed, am running an ATI Radeon 9600 graphics card (which ran Team Fortress 2 just fine when I used to run Windows XP), I have my wine configured to Windows XP, am not running any DLL overrides, I have my windows settings (in wine config) to "allow the windows manager to decorate windows" and "allow windows manager to control windows".

Also, I have no theme for desktop integration, have the sound driver set to ALSA Driver, hardware acceleration is at full with the default sample rate at 44100 and the default bits per sample at 16.

My Internet connection is DSL. It's slow, but it ran TF2 fine before when I used to run Windows XP. 

Also (again), I have desktop visual effects disabled.



If anyone can offer any advice on what to do, I'd appreciate it.

---

### Post by beastrace91 on 2010-10-04
> **ZeroCore said:**
> running an ATI Radeon 9600 graphics card 

Nuff said. Want to game under Wine get an nVidia chip. Maybe try running it in Windowed mode or with -dxlevel 81

If neither of those help odds are it is just a limitation in the ATI drivers that are still horrid.

~Jeff

---

### Post by ZeroCore on 2010-10-05
I don't have the ATI proprietary driver installed though. Also, I just talked to a software engineer today, and he said that it should work if I install the driver.
 
If it doesn't work, are you absolutely sure that I must get a new graphics card (I can't afford one at the moment and most likely won't for a long time, which is why I'm asking)?

---

### Post by TUA85550 on 2010-10-06
Your graphics card doesn't meet the minimum requirements.  And it's really outdated.  You can purchase a newer graphics card on Newegg or eBay really cheap.

---

### Post by ZeroCore on 2010-10-08
> **TUA85550 said:**
> Your graphics card doesn't meet the minimum requirements.  And it's really outdated.  You can purchase a newer graphics card on Newegg or eBay really cheap.

Incorrect. 

The card ran all of my steam games just fine back when I used to run windows.

---

### Post by Dukenukemx on 2010-10-09
> **TUA85550 said:**
> Your graphics card doesn't meet the minimum requirements.  And it's really outdated.  You can purchase a newer graphics card on Newegg or eBay really cheap.

The Radeon 9600 is more the adequate to run TF2.  It has been for years, as the Half Life 2 engine was made 6 years ago.  

It's becoming a problem when every solution in Linux is "get new hardware".

---

### Post by Dukenukemx on 2010-10-09
BTW, I have the same problem as the OP.  Though, TF2 would run before I installed updates to Wine.  Albeit, upside down and without sound.  Now, it freezes just as it's finishing loading the map.  I'm also using the ATI proprietary drivers.

---

### Post by ZeroCore on 2010-10-09
> **Dukenukemx said:**
> BTW, I have the same problem as the OP.  Though, TF2 would run before I installed updates to Wine.  Albeit, upside down and without sound.  Now, it freezes just as it's finishing loading the map.  I'm also using the ATI proprietary drivers.


Any help available then?

---

### Post by Dukenukemx on 2010-10-09
> **ZeroCore said:**
> Any help available then?

I'm also clueless to the problem.  Rather new to Linux.  I remember once how to fix the upside down issue, I never fixed the lack of sound.

---

