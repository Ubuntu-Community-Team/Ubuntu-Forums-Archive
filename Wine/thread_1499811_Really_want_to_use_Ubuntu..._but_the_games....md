---
title: "Really want to use Ubuntu... but the games..."
date: 2010-06-02
forum: Wine
---

### Post by Espionage724 on 2010-06-02
I am a hardcore player of most games by Blizzard Entertainment. I play the following games:

```
Diablo II: Lord of Destruction
StarCraft Brood War
StarCraft II
WarCraft III: The Frozen Throne
World of Warcraft
Unreal Tournament GoTY
Rune Halls of Valhalla
```

The only games that give me trouble is World of Warcraft and StarCraft II. I can manage everything else somewhat decently. Now this is mostly because of my hardware I assume, but surely something can be done?

Hardware:

```
CPU: Intel Celeron M 420 @ 1.6Ghz
RAM: 2GB DDR2 667Mhz (not 100% sure on speed)
HDD: Samsung 120GB 5400RPM
Graphics: Intel 950GMA (Mobile 945GM Chipset)
Chipset: Intel i940
Audio: Realtek/Intel High Definition Audio ALC883 Codec

```

I am a very active member of 9xxssf (group dedicated to help users with the intel graphics cards in their systems), and I understand most factors that can make a game work/not work and whatnot. Theres a few things I don't understand though.

```
- Wine with World of Warcraft, it will not let me choose OpenGL (I can choose D3d but it's fail performance)
- RuneScape HD in Firefox or Google Chrome will not allow HW OpenGL
- StarCraft II doesn't open (crashes with D3D error)
```

I have considered Dual Booting, but idk I think having a copy of XP would be overkill just to have 2 games (SC2 and WoW) work properly. Idk though It's not like I really gave dual booting a chance though. I would really like to have those 2 games running if anything though.

Any suggestions/feedback from anyone would be highly welcome (except telling me to get better hardware, because I have that coming in a few months maybe)

---

### Post by asdfoo on 2010-06-02
> **Espionage724 said:**
> I am a hardcore player of most games by Blizzard Entertainment. I play the following games:

```
Diablo II: Lord of Destruction
StarCraft Brood War
StarCraft II
WarCraft III: The Frozen Throne
World of Warcraft
Unreal Tournament GoTY
Rune Halls of Valhalla
```

The only games that give me trouble is World of Warcraft and StarCraft II. I can manage everything else somewhat decently. Now this is mostly because of my hardware I assume, but surely something can be done?

Hardware:

```
CPU: Intel Celeron M 420 @ 1.6Ghz
RAM: 2GB DDR2 667Mhz (not 100% sure on speed)
HDD: Samsung 120GB 5400RPM
Graphics: Intel 950GMA (Mobile 945GM Chipset)
Chipset: Intel i940
Audio: Realtek/Intel High Definition Audio ALC883 Codec

```

I am a very active member of 9xxssf (group dedicated to help users with the intel graphics cards in their systems), and I understand most factors that can make a game work/not work and whatnot. Theres a few things I don't understand though.

```
- Wine with World of Warcraft, it will not let me choose OpenGL (I can choose D3d but it's fail performance)
- RuneScape HD in Firefox or Google Chrome will not allow HW OpenGL
- StarCraft II doesn't open (crashes with D3D error)
```

I have considered Dual Booting, but idk I think having a copy of XP would be overkill just to have 2 games (SC2 and WoW) work properly. Idk though It's not like I really gave dual booting a chance though. I would really like to have those 2 games running if anything though.

Any suggestions/feedback from anyone would be highly welcome (except telling me to get better hardware, because I have that coming in a few months maybe)


The problem is going to partly lay with your video card, the issue is that compared to Windows Intel has not developed proper video drivers for linux.  What can try doing though is testing the latest version of mesa/dri because there are constant updates and fixes being worked on for this hardware, but the version ubuntu ships may lag behind.   As for the procedure on doing this I don't know the best method to recommend, it would be best asking in another subforum.  Personally I have a nvidia card so it is a little more straight forward.

Alternatively, check the AppDB pages for each application and see if they have any recommendations.

---

