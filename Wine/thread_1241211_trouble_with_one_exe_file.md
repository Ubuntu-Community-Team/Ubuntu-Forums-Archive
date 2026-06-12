---
title: "trouble with one exe file"
date: 2009-08-15
forum: Wine
---

### Post by mystmaiden on 2009-08-15
I'm running the wine I downloaded from synaptic in Jaunty. The program I use is Poser 5, which has run fine for me in wine to date. I just bought a bunch of stuff from daz today and all the exe's work fine except for one. It just won't open no matter what I do. I redownloaded it just in case and I've tried right clicking and opening with wine program loader, hard drive kicks in but nothing happens. I get a bitrock installer xml debug file in the Poser files. Not sure what to put in the command line to run something like this. I have the exe sitting on my desktop currently.

I'd appreciate any help to get it to run. Also I wondered if there is a way to get at what's in the file without executing it. In this case, the exe will have things that can easily be placed in the poser files manually if I could just pry them out of there. 

I have contacted daz, but since I'm using Linux and an older version of Poser, I would imagine all I can expect come Monday is maybe a refund on the product - I'd rather just get it working :)

mystmaiden

---

### Post by andrea000 on 2009-08-15
ok tood a look at there web page and it says
in the system requirements you need adobe flash
player 9 if you don't have that installed you
can install it with wine tricks.You can download
it [here]("http://wiki.winehq.org/winetricks") it may also need the vba runtime and the 
dot net framwork  2.0 i'm not sure on the other
two but it would not hurt to install them too.

---

### Post by Ranax on 2009-08-15
You could try updating your Wine from [here]("http://wine.budgetdedicated.com/archive/index.html")

---

### Post by mystmaiden on 2009-08-15
Thank you both for the quick replies!

I'm a bit confused about all that really. I've run Poser successfully in wine using hardy, ibex and now jaunty and only had trouble with one exe, with none of those things. What would make it suddenly necessary to have all that? I do have flash installed in Ubuntu, do I need to install it in wine somehow? I never use the ie explorer.

I'm truly not trying to be argumentative, just trying to understand.

mystmaiden

---

### Post by Ranax on 2009-08-15
> **mystmaiden said:**
> Thank you both for the quick replies!

I'm a bit confused about all that really. I've run Poser successfully in wine using hardy, ibex and now jaunty and only had trouble with one exe, with none of those things. What would make it suddenly necessary to have all that? I do have flash installed in Ubuntu, do I need to install it in wine somehow? I never use the ie explorer.

I'm truly not trying to be argumentative, just trying to understand.

mystmaiden

Try [this](http://get.adobe.com/flashplayer/thankyou/xpi/?installer=Flash_Player_10_for_Windows_-_Other_Browsers&g=)

---

### Post by mystmaiden on 2009-08-15
Thanks, Ranax.  Flash really doesn't have anything to do with Poser - so why would it help me to open an exe file that contains nothing but Poser files? 

still just trying to understand

mystmaiden

---

### Post by Ranax on 2009-08-15
> **mystmaiden said:**
> I do have flash installed in Ubuntu, do I need to install it in wine somehow? I never use the ie explorer.

I guess I misunderstood you.

---

### Post by mystmaiden on 2009-08-15
I think that's my fault, I wasn't really clear. Poser itself is running great, the exe file is just some content I bought today and I can't seem to open it to put the content in with the rest of my Poser files. I apologize for not making that clear. Also, I don't run animations in Poser, I just use the three d for stills.

myst

---

### Post by Ranax on 2009-08-15
> **mystmaiden said:**
> I think that's my fault, I wasn't really clear. Poser itself is running great, the exe file is just some content I bought today and I can't seem to open it to put the content in with the rest of my Poser files. I apologize for not making that clear. Also, I don't run animations in Poser, I just use the three d for stills.

myst

I have *no* idea what Poser is! :P

---

### Post by NightMKoder on 2009-08-15
Can we get the terminal output from running that exe? [http://wiki.winehq.org/FAQ#head-a37de3282d447376d2220d20a278ae52258551a4](http://wiki.winehq.org/FAQ#head-a37de3282d447376d2220d20a278ae52258551a4)

---

### Post by mystmaiden on 2009-08-16
NightMKoder, it took me a bit to get the command right (yesterday I was not capitializing Desktop and so getting no where). Here's what I got from the terminal command today finally, you can see I had a bit of a false start in there. Looks like I'm missing a dll file?

```
mystmaiden@hal:~$ cd Desktop
mystmaiden@hal:~/Desktop$ ls
8451_2_dpc_ChrystallineHair_2.exe  firefox.desktop  ps_ac2159b_NanaHair.exe
Daz.desktop                        Google.desktop   Rendo.desktop
DAZStudio_3.0.1.135_Win32.exe      pidgin.desktop   Ubuntu.desktop
epiphany.desktop                   Poser.desktop    VirtualBox.desktop
mystmaiden@hal:~/Desktop$ cd 8451_2_dpc_ChrystallineHair_2.exe
bash: cd: 8451_2_dpc_ChrystallineHair_2.exe: Not a directory
mystmaiden@hal:~/Desktop$ wine 8451_2_dpc_ChrystallineHair_2.exe
err:winedevice:ServiceMain driver L"TPkd" failed to load
fixme:comm:set_queue_size insize 4096 outsize 4096 unimplemented stub
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\windows\\temp\\twapi-2.0a7.dll") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\windows\\temp\\twapi-2.0a7.dll") not found
mystmaiden@hal:~/Desktop$ 

```

mystmaiden

---

### Post by mystmaiden on 2009-08-16
Ranax wrote

I have *no* idea what Poser is! :razz: 

It's a highly addictive and really fun 3d art program - all sorts of fun stuff you can buy to use with it and lots of freestuff made by other users to play with, too. Blender is an open source one that's available for free, I'm pretty sure quite a bit of poser's goodies work in it.

mystmaiden

---

### Post by Kazade on 2009-08-16
> **mystmaiden said:**
> NightMKoder, it took me a bit to get the command right (yesterday I was not capitializing Desktop and so getting no where). Here's what I got from the terminal command today finally, you can see I had a bit of a false start in there. Looks like I'm missing a dll file?

```
mystmaiden@hal:~$ cd Desktop
mystmaiden@hal:~/Desktop$ ls
8451_2_dpc_ChrystallineHair_2.exe  firefox.desktop  ps_ac2159b_NanaHair.exe
Daz.desktop                        Google.desktop   Rendo.desktop
DAZStudio_3.0.1.135_Win32.exe      pidgin.desktop   Ubuntu.desktop
epiphany.desktop                   Poser.desktop    VirtualBox.desktop
mystmaiden@hal:~/Desktop$ cd 8451_2_dpc_ChrystallineHair_2.exe
bash: cd: 8451_2_dpc_ChrystallineHair_2.exe: Not a directory
mystmaiden@hal:~/Desktop$ wine 8451_2_dpc_ChrystallineHair_2.exe
err:winedevice:ServiceMain driver L"TPkd" failed to load
fixme:comm:set_queue_size insize 4096 outsize 4096 unimplemented stub
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\windows\\temp\\twapi-2.0a7.dll") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\windows\\temp\\twapi-2.0a7.dll") not found
mystmaiden@hal:~/Desktop$ 

```

mystmaiden

Hi,

The problem seems to be that you are missing a DLL file (the VC++ 6 runtime to be exact). Because this dll is not part of a default Windows install, and is *supposed* to be distributed with the application, there is no Wine equivalent. The solution is to use a program called "winetricks" to download the dll file.

Follow the example here: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

You need vcrun6 which is actually what that example shows.

Winetricks can download a bunch of other stuff, it can also enable font smoothing which is nice. Try running plain "sh winetricks" to see a list of what can be enabled.

---

