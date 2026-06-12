---
title: "Starcraft 2 issues - Can't install"
date: 2010-07-27
forum: Wine
---

### Post by chummers on 2010-07-27
I'm really new to linux, and I cant get it to install, it keeps saying no installer data could be found.  I tried this from running it from /media/SC2-L100-D1 Installer.exe then after I mounted I tried it from the /mnt/cdrom location and still the same thing.  I tried to upgrade Wine but it shows I have the latest even though I believe their are more release of wine-1.2 but I can't get it to upgrade.  Any suggestions, I'm a complete noob to Linux. So this is a freshly installed box.

OS:     Ubuntu 10.04 64 Bit
Kernel: 2.6.32-24-generic
$ wine --version
wine-1.2
$ sudo mount -t udf -o ro,unhide,uid=1000 /dev/sr0 /mnt/cdrom

---

### Post by slvr42 on 2010-07-27
after it's mounted do a mount -o remount,unhide /dev/sr0

I'm having a problem now where the installer just won't run at all.

---

### Post by chummers on 2010-07-27
Thx, that looks like to be getting me somewhere, however I get this message now. 

/mnt/cdrom$ ./Installer.exe 
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000

---

### Post by slvr42 on 2010-07-27
That's where I'm at now.  I tried running it in a win7 virtualbox but it's having video driver issues.  It installs fine then when you actually try and play the game it can't get access to the video card.

I just read that some people are having more luck by downloading the digital edition from battle.net and installing it. I'm going to DL it and give that a try.

---

### Post by chummers on 2010-07-27
I asked this question on the Wine forum and got the response below.  I went through removed that hidden directory and wine and reloaded.  I'm currently able to install it now.


	
RE: Doesn't load anything I get this error
by Will on Tuesday July 27th 2010, 21:47
remove your ~/.wine directory and reload (or set an alternate WINEPREFIX=). Also make sure you are using wine version 1.2 and not something older.

---

### Post by slvr42 on 2010-07-27
Found this

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376)

and 

[http://dominikdorn.com/2010/07/starcraft-2-dvd-with-linux-wine/](http://dominikdorn.com/2010/07/starcraft-2-dvd-with-linux-wine/)

---

### Post by slvr42 on 2010-07-27
wipe out .wine and reload wine all together?

Got it working by copying the disc to my PC and installing from there...so far so good anyway.

---

### Post by chummers on 2010-07-28
Ya I completely wiped wine and restarted. But its run really slow compared to the game installed on XP its about 40-50 FPS on XP compared to 10-15 FPS on Ubuntu.

---

### Post by Sobooban on 2010-07-28
hmm I get it to install but cant run it. wen i try it just  keeps showing my desktop but i cant interact with it so have to do a hard reboot. 
I'm using lucid 64bit. recompiled wine as who-to said got an error on last patch thou

wine-1.2-495-g20f51c2

---

### Post by Coreo1 on 2010-09-29
I'm trying to install a brand new copy of Starcraft 2 on Vista Ultimate. At 89% I get the error message below. Does anyone know how to fix this? It installed just fine on my son's Windows 7.

[COLOR="red"]The installer was unable to read the file "Repack-MPQ\fileset.base#Mods#Liberty.SC2Mod#base.SC2Assets\Assets\Textures\planetview_charterrainspecular.dds". This error may be caused by problems with the media or drive at E:\--for example, a scratched or dirty CD-ROM/DVD-ROM, hard drive corruption, or a networking problem while downloading the installer. (The error code was 5.) If this problem persists, please contact Blizzard Technical Support. (ReadJob::Execute)[/COLOR]

[COLOR="Black"]The hard disk and cd are both fine and i'm not seeing anything on google regarding this issue.[/COLOR]

---

### Post by beastrace91 on 2010-10-01
> **Coreo1 said:**
> I'm trying to install a brand new copy of Starcraft 2 on Vista Ultimate. At 89% I get the error message below. Does anyone know how to fix this? It installed just fine on my son's Windows 7.

[COLOR="red"]The installer was unable to read the file "Repack-MPQ\fileset.base#Mods#Liberty.SC2Mod#base.SC2Assets\Assets\Textures\planetview_charterrainspecular.dds". This error may be caused by problems with the media or drive at E:\--for example, a scratched or dirty CD-ROM/DVD-ROM, hard drive corruption, or a networking problem while downloading the installer. (The error code was 5.) If this problem persists, please contact Blizzard Technical Support. (ReadJob::Execute)[/COLOR]

[COLOR="Black"]The hard disk and cd are both fine and i'm not seeing anything on google regarding this issue.[/COLOR]

This is a help forum for getting Windows games working under **Linux** using [Wine](http://www.winehq.org/).

Take your issue with your closed source OS to Microsoft.

That is why I no longer use the that operating system. Too many instances of things that should "just work" that give FAR too much head over the years.

~Jeff

---

