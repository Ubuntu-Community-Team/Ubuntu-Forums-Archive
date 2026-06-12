---
title: "Call of Duty 2, Wine help"
date: 2009-07-25
forum: Wine
---

### Post by keithwwalker on 2009-07-25
I have been having a horrible time trying to get COD2 to run.

I am running 9.04, with Wine 1.1.26.

I could not get COD2 to install cleanly at all.  I even tried installing it by going back to an old version of Wine but it hung up at the registration phase - if I canceled registration, it would just hang up, but if I chose registration, it would give a blank Gecko registration screen.

Anyway, I decided to be tricky and since I run a dual boot machine, thought I would just copy the relevant files from one partition to another.

**Key question is:  Which folders besides Activision do I copy over???**

I copied the Activision and overwrote it, and I get as far as:

[I]Winsock Initialized
Opening IP socket: localhost:28960
Hostname: keithwwalker-desktop
IP: 127.12.34.56
WARNING: IPX_Socket: bind: WSAEINVAL
----- Initializing Renderer ----
Mismatched REF_API_VERSION: expected 59, got 60
-------------------------------
Error during initialization:
Failed to initialize renderer: version mismatch.[/I]

Can anyone give advice?  Or post a way to do a clean install???

Thanks
Keith Walker

Here is the complete console:
```
CoD2 MP 1.3 build win-x86 May  1 2006
----- FS_Startup -----
Current language: english
Current search path:
C:\Program Files\Activision\Call of Duty 2\main\z_iss_message_generator.iwd (9 files)
C:\Program Files\Activision\Call of Duty 2\main\z_iss_message_generator.68d712de.iwd (9 files)
C:\Program Files\Activision\Call of Duty 2\main\zz_map_pack_v5.0.iwd (96 files)
C:\Program Files\Activision\Call of Duty 2\main\zzz_oneshot.iwd (127 files)
C:\Program Files\Activision\Call of Duty 2\main\zzz_oneshot.fe3dfae0.iwd (127 files)
C:\Program Files\Activision\Call of Duty 2\main\zzz_nodustmod_v2.iwd (17 files)
C:\Program Files\Activision\Call of Duty 2\main\zzz_nodustmod_v2.19ee43a4.iwd (17 files)
C:\Program Files\Activision\Call of Duty 2\main\zzz_map_pack_v4.1.iwd (184 files)
C:\Program Files\Activision\Call of Duty 2\main\zzz_Bash.iwd (9 files)
C:\Program Files\Activision\Call of Duty 2\main\zzz_Bash.970e6816.iwd (9 files)
C:\Program Files\Activision\Call of Duty 2\main\zzz_all_rifles_v1.5.iwd (18 files)
C:\Program Files\Activision\Call of Duty 2\main\zombieu.iwd (27 files)
C:\Program Files\Activision\Call of Duty 2\main\zombie.iwd (30 files)
C:\Program Files\Activision\Call of Duty 2\main\zmp3.iwd (94 files)
C:\Program Files\Activision\Call of Duty 2\main\zmp2.iwd (118 files)
C:\Program Files\Activision\Call of Duty 2\main\zmp1.iwd (60 files)
C:\Program Files\Activision\Call of Duty 2\main\zmp1.c4e9372f.iwd (57 files)
C:\Program Files\Activision\Call of Duty 2\main\zed.iwd (14 files)
C:\Program Files\Activision\Call of Duty 2\main\zcmpack.iwd (255 files)
C:\Program Files\Activision\Call of Duty 2\main\zcmp.iwd (107 files)
C:\Program Files\Activision\Call of Duty 2\main\zchmpack.iwd (128 files)
C:\Program Files\Activision\Call of Duty 2\main\zbv5.iwd (11 files)
C:\Program Files\Activision\Call of Duty 2\main\z9.iwd (14 files)
C:\Program Files\Activision\Call of Duty 2\main\z7.iwd (14 files)
C:\Program Files\Activision\Call of Duty 2\main\z6.iwd (33 files)
C:\Program Files\Activision\Call of Duty 2\main\z54.iwd (17 files)
C:\Program Files\Activision\Call of Duty 2\main\z46.iwd (36 files)
C:\Program Files\Activision\Call of Duty 2\main\z43.iwd (25 files)
C:\Program Files\Activision\Call of Duty 2\main\z402.iwd (15 files)
C:\Program Files\Activision\Call of Duty 2\main\z398.iwd (22 files)
C:\Program Files\Activision\Call of Duty 2\main\z38.iwd (24 files)
C:\Program Files\Activision\Call of Duty 2\main\z376.iwd (176 files)
C:\Program Files\Activision\Call of Duty 2\main\z37.iwd (37 files)
C:\Program Files\Activision\Call of Duty 2\main\z351.iwd (23 files)
C:\Program Files\Activision\Call of Duty 2\main\z35.iwd (22 files)
C:\Program Files\Activision\Call of Duty 2\main\z345.iwd (101 files)
C:\Program Files\Activision\Call of Duty 2\main\z342.iwd (56 files)
C:\Program Files\Activision\Call of Duty 2\main\z340.iwd (46 files)
C:\Program Files\Activision\Call of Duty 2\main\z34.iwd (19 files)
C:\Program Files\Activision\Call of Duty 2\main\z339.iwd (86 files)
C:\Program Files\Activision\Call of Duty 2\main\z324.iwd (140 files)
C:\Program Files\Activision\Call of Duty 2\main\z32.iwd (14 files)
C:\Program Files\Activision\Call of Duty 2\main\z313.iwd (16 files)
C:\Program Files\Activision\Call of Duty 2\main\z308.iwd (44 files)
C:\Program Files\Activision\Call of Duty 2\main\z285.iwd (17 files)
C:\Program Files\Activision\Call of Duty 2\main\z275.iwd (14 files)
C:\Program Files\Activision\Call of Duty 2\main\z26.iwd (13 files)
C:\Program Files\Activision\Call of Duty 2\main\z252.iwd (93 files)
C:\Program Files\Activision\Call of Duty 2\main\z251.iwd (22 files)
C:\Program Files\Activision\Call of Duty 2\main\z243.iwd (148 files)
C:\Program Files\Activision\Call of Duty 2\main\z234.iwd (22 files)
C:\Program Files\Activision\Call of Duty 2\main\z233.iwd (16 files)
C:\Program Files\Activision\Call of Duty 2\main\z22.iwd (9 files)
C:\Program Files\Activision\Call of Duty 2\main\z21.iwd (35 files)
C:\Program Files\Activision\Call of Duty 2\main\z179.iwd (14 files)
C:\Program Files\Activision\Call of Duty 2\main\z169.iwd (59 files)
C:\Program Files\Activision\Call of Duty 2\main\z160.iwd (17 files)
C:\Program Files\Activision\Call of Duty 2\main\z134.iwd (39 files)
C:\Program Files\Activision\Call of Duty 2\main\z131.iwd (109 files)
C:\Program Files\Activision\Call of Duty 2\main\z127.iwd (71 files)
C:\Program Files\Activision\Call of Duty 2\main\z125.iwd (20 files)
C:\Program Files\Activision\Call of Duty 2\main\wwpaknew.iwd (253 files)
C:\Program Files\Activision\Call of Duty 2\main\uar.iwd (17 files)
C:\Program Files\Activision\Call of Duty 2\main\trip.iwd (16 files)
C:\Program Files\Activision\Call of Duty 2\main\szs3.iwd (43 files)
C:\Program Files\Activision\Call of Duty 2\main\szm4.iwd (293 files)
C:\Program Files\Activision\Call of Duty 2\main\szm3.iwd (140 files)
C:\Program Files\Activision\Call of Duty 2\main\szm2.iwd (168 files)
C:\Program Files\Activision\Call of Duty 2\main\szm1.iwd (221 files)
C:\Program Files\Activision\Call of Duty 2\main\sewersV2.iwd (15 files)
C:\Program Files\Activision\Call of Duty 2\main\pow.iwd (22 files)
C:\Program Files\Activision\Call of Duty 2\main\oneway.iwd (40 files)
C:\Program Files\Activision\Call of Duty 2\main\napsfav2.iwd (243 files)
C:\Program Files\Activision\Call of Duty 2\main\Nap5.iwd (120 files)
C:\Program Files\Activision\Call of Duty 2\main\mp_villa.iwd (30 files)
C:\Program Files\Activision\Call of Duty 2\main\mp_ug_funbox_final.iwd (16 files)
C:\Program Files\Activision\Call of Duty 2\main\mp_tunnelsV3.iwd (12 files)
C:\Program Files\Activision\Call of Duty 2\main\mp_roofsv2.iwd (12 files)
C:\Program Files\Activision\Call of Duty 2\main\mp_moh_town.iwd (74 files)
C:\Program Files\Activision\Call of Duty 2\main\mp_kingofthehill.iwd (12 files)
C:\Program Files\Activision\Call of Duty 2\main\mp_darkhouse.iwd (31 files)
C:\Program Files\Activision\Call of Duty 2\main\mp_comproom_v1.iwd (39 files)
C:\Program Files\Activision\Call of Duty 2\main\mappack3.iwd (53 files)
C:\Program Files\Activision\Call of Duty 2\main\mappack2.iwd (172 files)
C:\Program Files\Activision\Call of Duty 2\main\ma.iwd (46 files)
C:\Program Files\Activision\Call of Duty 2\main\kzmpck5.iwd (81 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_15.iwd (85 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_14.iwd (4038 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_13.iwd (22624 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_12.iwd (1016 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_11.iwd (1462 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_10.iwd (1936 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_09.iwd (2142 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_08.iwd (2723 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_07.iwd (3384 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_06.iwd (990 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_05.iwd (928 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_04.iwd (698 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_03.iwd (26 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_02.iwd (40 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_01.iwd (16 files)
C:\Program Files\Activision\Call of Duty 2\main\iw_00.iwd (102 files)
C:\Program Files\Activision\Call of Duty 2\main\hobb.iwd (35 files)
C:\Program Files\Activision\Call of Duty 2\main\egm.iwd (256 files)
C:\Program Files\Activision\Call of Duty 2\main\egi.iwd (91 files)
C:\Program Files\Activision\Call of Duty 2\main\egf.iwd (136 files)
C:\Program Files\Activision\Call of Duty 2\main\ega.iwd (366 files)
C:\Program Files\Activision\Call of Duty 2\main\eg7.iwd (242 files)
C:\Program Files\Activision\Call of Duty 2\main\eg1.iwd (173 files)
C:\Program Files\Activision\Call of Duty 2\main\dpzs1.iwd (52 files)
C:\Program Files\Activision\Call of Duty 2\main\dpzm1.iwd (288 files)
C:\Program Files\Activision\Call of Duty 2\main\chmpack.iwd (229 files)
C:\Program Files\Activision\Call of Duty 2\main\chedit.iwd (23 files)
C:\Program Files\Activision\Call of Duty 2\main\cas.iwd (32 files)
C:\Program Files\Activision\Call of Duty 2\main\bhc_tfo.iwd (72 files)
C:\Program Files\Activision\Call of Duty 2\main\bhc_maps_2.iwd (111 files)
C:\Program Files\Activision\Call of Duty 2/main
C:\Program Files\Activision\Call of Duty 2/raw
C:\Program Files\Activision\Call of Duty 2/raw_shared
C:\Program Files\Activision\Call of Duty 2/devraw
C:\Program Files\Activision\Call of Duty 2/devraw_shared
C:\Program Files\Activision\Call of Duty 2\main\localized_english_iw11.iwd (1 files)
    localized assets iwd file for english
C:\Program Files\Activision\Call of Duty 2\main\localized_english_iw10.iwd (414 files)
    localized assets iwd file for english
C:\Program Files\Activision\Call of Duty 2\main\localized_english_iw09.iwd (98 files)
    localized assets iwd file for english
C:\Program Files\Activision\Call of Duty 2\main\localized_english_iw08.iwd (8 files)
    localized assets iwd file for english
C:\Program Files\Activision\Call of Duty 2\main\localized_english_iw07.iwd (1014 files)
    localized assets iwd file for english
C:\Program Files\Activision\Call of Duty 2\main\localized_english_iw06.iwd (3110 files)
    localized assets iwd file for english
C:\Program Files\Activision\Call of Duty 2\main\localized_english_iw05.iwd (5310 files)
    localized assets iwd file for english
C:\Program Files\Activision\Call of Duty 2\main\localized_english_iw04.iwd (6240 files)
    localized assets iwd file for english
C:\Program Files\Activision\Call of Duty 2\main\localized_english_iw03.iwd (6580 files)
    localized assets iwd file for english
C:\Program Files\Activision\Call of Duty 2\main\localized_english_iw02.iwd (6404 files)
    localized assets iwd file for english
C:\Program Files\Activision\Call of Duty 2\main\localized_english_iw01.iwd (5510 files)
    localized assets iwd file for english
C:\Program Files\Activision\Call of Duty 2\main\localized_english_iw00.iwd (4764 files)
    localized assets iwd file for english

File Handles:
----------------------
89159 files in iwd files
execing default_mp.cfg
couldn't exec language.cfg
execing players/Walker/config_mp.cfg
execing safemode_mp.cfg
========= autoconfigure
configure_mp.csv: using CPU configuration 2 GHz 512 MB
execing configure_mp.cfg
configure_mp.csv: using GPU configuration "GeForce FX"
Measured CPU speed is 3.39 GHz
System memory is 1002 MB (capped at 1 GB)
Video card is "NVIDIA GeForce FX 5600"
Streaming SIMD Extensions (SSE) supported

Winsock Initialized
Opening IP socket: localhost:28960
Hostname: keithwwalker-desktop
IP: 127.12.34.56
WARNING: IPX_Socket: bind: WSAEINVAL
----- Initializing Renderer ----
Mismatched REF_API_VERSION: expected 59, got 60
-------------------------------
Error during initialization:
Failed to initialize renderer: version mismatch.


```

---

### Post by snargfish on 2009-07-25
Probably a stupid suggestion, but have you tried downloading the demo & seeing if that works?

You can get it here: [http://www.gamershell.com/download_10902.shtml](http://www.gamershell.com/download_10902.shtml)

---

### Post by keithwwalker on 2009-07-26
So what specifically would that prove?

I already know that the hardware will run COD2, as I have dual boot and it runs on XP...

> **snargfish said:**
> Probably a stupid suggestion, but have you tried downloading the demo & seeing if that works?

You can get it here: [http://www.gamershell.com/download_10902.shtml](http://www.gamershell.com/download_10902.shtml)

---

### Post by snargfish on 2009-07-26
> **keithwwalker said:**
> So what specifically would that prove?

I already know that the hardware will run COD2, as I have dual boot and it runs on XP...

It might help show if there was a graphics issue. I'm not questioning the hardware.

---

### Post by NightMKoder on 2009-07-26
You can't just copy things to wine and expect them to work.

Delete your wine prefix (rm -rf ~/.wine) and try installing it again. Appdb suggests that it works fine.

---

### Post by keithwwalker on 2009-08-02
I said in my original post that I could not get COD2 to install when running through wine.

Copying the files over from the XP hard drive partition got me farther along.

Perhaps I will just delete the whole Activision folder and do a clean copy and paste.

> **NightMKoder said:**
> You can't just copy things to wine and expect them to work.

Delete your wine prefix (rm -rf ~/.wine) and try installing it again. Appdb suggests that it works fine.

---

### Post by NightMKoder on 2009-08-02
You can't copy and paste. The program probably installs registry entries that it needs for startup. It can also install a host of other things that aren't copied over. You can usually do that in linux, but not in windows.

If you delete your wine prefix, there is a good chance it will install and run just fine.

---

### Post by dtoolman on 2010-02-24
> **NightMKoder said:**
> You can't copy and paste. The program probably installs registry entries that it needs for startup. It can also install a host of other things that aren't copied over. You can usually do that in linux, but not in windows.

If you delete your wine prefix, there is a good chance it will install and run just fine.

But u can do that in Windows for COD2. You can copy and paste the install folder from say a backup drive to your main partittion and then just run the exe. When u play a game for the first time it "will" ask u to enter the product key, but otherwise it will run fine in XP and Win7.

---

