---
title: "Steam freezes when installing any games from profile"
date: 2009-07-05
forum: Wine
---

### Post by Jonas007 on 2009-07-05
Okay, I've literally spent my entire day searching and couldn't come up with a fix for this on here, or anywhere on google.

Here's the basics, I ran through the wine install which went fine (newest version available today), installed the recommended packages to go with it all went fine as well.

Installed steam from the .msi file, worked perfectly.  launched steam from the applications>wine>steam and it opens fine.  Logged in using existing steam account, also worked, I go to "My Games" tab, and click on Left 4 Dead (or any other game I own), and click "Install", then install button depresses and changes colour, then the steam screen basically freezes.  If I go into the system monitor the steam.exe app is using 50% cpu, and looking at performance its using one of the cores at 100%.

I've tried installing various versions of wine, and reinstalling wine and steam about 10 times with no luck.  When I run the same thing from terminal, here's the output when the cpu pegs at 100%:

err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1

Please help, I refuse to go back to windows after MS screwed me over by declaring a paid valid windows copy was "illegitmate and out of warranty" and want my games back (even if they'll run slower on here)

System is an AMD Phenom X2 550 (@ 3.7ghz per core) 4GB 1066 ram, Nvidia Geforce 9600GT 1GB video card, running Ubuntu 9.04.

THANKS!

---

### Post by ackanao on 2009-07-06
I'm not that familiar with Steam but it looks like there's some Active Scripting issues again (someone'll correct me if I'm wrong).

There is a workaround but it's a bit messy and I can't guarantee that it will work for Steam.

Try by installing IE - because it will almost certainly mess up your Wine configuration, it is better to create a new wineprefix for Steam.

Use this command to create new wineprefix:
```
WINEPREFIX=~/Desktop/Steam wineboot
```
*This will create Steam wineprefix on your Desktop*

Use this command if you want to configure your Steam wineprefix:
```
env WINEPREFIX=~/Desktop/Steam winecfg (regedit, whatever...)
```

Downlad winetricks:
```
wget http://www.kegel.com/wine/winetricks
```

Install ie6:
```
WINEPREFIX=~/Desktop/Steam sh winetricks ie6
```

Install Steam:
```
env WINEPREFIX=~/Desktop/Steam wine /path/to/Steam/Installer/Steam.exe
```

Use this command to start Steam:
```
env WINEPREFIX=~/Desktop/Steam wine "C:\Program Files\Steam folder\Steam.exe"
```

Here you'll find everything you need to know about winetricks and how to use it:
[http://wiki.winehq.org/winetricks]("http://wiki.winehq.org/winetricks")

I really don't know if this helps or not, but you can try...

---

### Post by Jonas007 on 2009-07-06
Thanks Ackanao, I'll try that tonight when I get home from work.

---

### Post by Jonas007 on 2009-07-06
Didn't work unfortunately...reinstalled wine, then winetricks, and nearly every package within that.  Now the same problem happens, and I get this in terminal:

fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x195708)->(0x32cbb0)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0xb6e670 0xb6e668
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0xb6e670 0xb6e668
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0xb6e670 0xb6e668
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0xb6e670 0xb6e668
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16

If I leave it for a long time, the cpu stays cranked at 100%, and that last bit will repeat itself in terminal window every minute or so:

fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0xb6e670 0xb6e668
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16

I'm not a programmer so can't debug what that line means...anyone??

---

### Post by Jonas007 on 2009-07-06
A bit more info, as apparently it will eventually stop the process, here is what it shows in the end:

wine client error:0: version mismatch 381/386.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime Optimization Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000457,(nil),0x0001,0x00000000,0xb6e234,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime Optimization Service (clr_optimization_v2.0.50727_32) - Service reached limit of transient errors. Will shut down. Last error returned from Service Manager: 0x8007054f.\n"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 4 0xc6e984 0xc6e97c
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime Optimization Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000454,(nil),0x0001,0x00000000,0xb6e2a8,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

the version mismatch part looks the most interesting to me...now how the hell do I find this version 381 to delete it?

---

### Post by NightMKoder on 2009-07-06
From what I remember what you were experiencing was perfectly normal, although I doubt right now would be a good time to know that. You just have to wait a little while while steam allocates disk space for your game.

Now to get your wine back in shape, lets clean it up:
```

sudo apt-get purge wine
rm -rf ~/.wine

```

which removes EVERYTHING you have installed (not the menu items, but doesn't matter).

Now install the latest wine version (1.1.25), install steam, and just wait for a little while (even if it "turns grey"). If it is still frozen after an half hour or so maybe then you might worry.

To answer your question about wineserver - you probably updated wine while you had a windows app running - hence the wineserver stayed open and you got version mismatches. If you want to kill the wineserver, do:
```
wineserver -k
```

EDIT: On a sidenote, be sure you know what winetricks do before running them. ie6 is a huge component of windows and it really messes with wine to have that much stuff replaced.

---

### Post by Jonas007 on 2009-07-07
Ok, thanks for the tips, I'll try the cleanup thing when I get home tonight.

I do find it a little odd though that it would take that long to allocate space for the game, the system is a dual 3.7Ghz, seems like taking 20-30 mins to allocate some space is alot.  It also to this point has never started actually downloading anything.  Is there a specific folder I can somehow create and force the memory allocation to begin with?

Alternatively as I've seen some Steam installers people get with through the command line (for Halflife 2), does anyone know a command line install to pull down Left 4 dead?  I already own this game, just need to download it.

---

### Post by ackanao on 2009-07-07
If you followed my instructions you don't need to uninstall Wine and delete ".wine" folder - The only thing that is messed up is your "Steam" wineprefix (default wineprefix is untouched). Just delete "Steam" wineprefix. Your Wine is just fine... That's why I told you to create new wineprefix and install ie6 in it.

---

### Post by Jonas007 on 2009-07-07
> **ackanao said:**
> If you followed my instructions you don't need to uninstall Wine and delete ".wine" folder - The only thing that is messed up is your "Steam" wineprefix (default wineprefix is untouched). Just delete "Steam" wineprefix. Your Wine is just fine... That's why I told you to create new wineprefix and install ie6 in it.
I'll try running through this again, as I think I decided to ignore the first few lines of your instructions for some dumb reason; apparently I shouldn't drink wine while working on wine.

---

### Post by ackanao on 2009-07-07
Jonas007

That's the beauty of wineprefixes - as long as you use different wineprefixes to install/test applications, your default wineprefix ("~/.wine" folder) will be intact. You can do whatever you want with your wineprefixes - if one of them is messed up completely just delete it, create a new one and start all over again...

As I said I'm not that familiar with Steam so I don't know exactly where's the problem...

Install Steam only, run it from terminal and post full terminal output.

---

### Post by ackanao on 2009-07-07
maybe you'll find this page useful:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554")

As you can see in the first test by volcano, almost everything works with ie6 installed - he's using Wine 1.1.25

---

