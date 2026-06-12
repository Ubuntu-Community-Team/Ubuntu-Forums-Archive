---
title: "Any first person RPG shooters?"
date: 2010-07-17
forum: Wine
---

### Post by Nick_Jinn on 2010-07-17
So I am missing Fallout 3. I dont expect anything on quite the same scope, but are there any games that play natively on Linux that have a similar feel? Something that combines first person action with RPG elements?

I would also go for a fantasy version. Paid games are fine, but native is what I am looking for.

---

### Post by ronnielsen1 on 2010-07-17
It's rated gold in winehq. Have you tried running fallout 3 in wine?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322)
> [SIZE=2]It seems that practically  everything works and it works just out of the box! Performance is good, sounds work *** well. There is no need to use any of the native dlls. Great work![/SIZE]
   [SIZE=2]I am using 64-bit  version of wine running on Sabayon Linux 5.3.[/SIZE]
 
**What does not**
 	 	   
[SIZE=2]There was one small problem while loading the game. I wasn't able to hear the initial music, which is played while loading the game. It probaly is a bug, so I decided to report it here. Nevertheless, it is not a very annoying error and I think Fallout3 deserves gold rating![/SIZE]
   There is a way to overcome this problem by installing a native  quartz.dll with winetricks:
    winetricks quartz
   Unfortunately, after installing a native quartz.dll I have observed  some strange graphics errors in the game, especially noticeable  when  you look into someone's face in a short distance.                         

[http://www.junauza.com/2010/05/8-best-mmorpg-games-for-linux.html](http://www.junauza.com/2010/05/8-best-mmorpg-games-for-linux.html)

---

### Post by Nick_Jinn on 2010-07-17
Mine is crashing at startup. There is a problem with the DLL loader or something. Maybe I made a mistake by installing winetricks and a few other random folders that I might not have needed but looked useful from Synaptic....someday I will learn my lesson about downloading random packages from Synaptic unless I need them.

I might try again with a fresh install after I figure out how to copy a microcrap partition from my laptop hard drive (I need it for a class) as a bootable OS, and then I plan to reinstall Ubuntu.

Funny. I got Fallout 3 playing on my old computer before I upgraded. I wonder if its a problem with the 64bit platform and something I downloaded.


I got Oblivion playing on the highest settings, only with no sound :(

---

### Post by ronnielsen1 on 2010-07-17
winetricks shouldn't be a problem. Try running it from a terminal. It might give you clues on errors

---

### Post by Nick_Jinn on 2010-07-17
How do I do that?

---

### Post by Cresho on 2010-07-17
off the top of my head, downgrading wine to 1.37 gets sound in oblivion working.

---

### Post by Nick_Jinn on 2010-07-17
> **Cresho said:**
> off the top of my head, downgrading wine to 1.37 gets sound in oblivion working.


Is that in the archives somewhere?

Playonlinux is using that number, but I dont know what version of wine I am using.

---

### Post by ronnielsen1 on 2010-07-17
> How do I do that?

Go to Accessories > Terminal


Type in [COLOR=Blue] cd ~/.wine/drive_c/Program\ Files/[/COLOR]

Type in [COLOR=Blue]ls[/COLOR]

This will list all folder and files in your wine program files directory

[COLOR=Black]The \ is necessary if the folder has more than one word with a space. For example to change into [COLOR=Blue]Windows  [/COLOR][/COLOR][COLOR=Blue]Media Player[/COLOR], you would type in [COLOR=Blue]cd Windows\ Media\ Player[/COLOR]

cd (change directory) into your fallout program and look for the exe file

wine fallout3.exe (example - I don't have it installed)

---

### Post by Nick_Jinn on 2010-07-17
[COLOR=Blue] cd ~/.wine/drive_c/Program\ Files/[/COLOR]


cd ~/.wine/drive_c/Program\ Files/
bash: cd: /home/djinn/.wine/drive_c/Program Files/: No such file or directory

---

### Post by ronnielsen1 on 2010-07-17
> off the top of my head, downgrading wine to 1.37 gets sound in oblivion  working.

What wine version are you running. AFAIK wine 1.2 just came out yesterday

> July 16, 2010
    The Wine team is proud to announce that the stable release Wine 1.2  is now available.

[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by ronnielsen1 on 2010-07-17
> [COLOR=Blue]cd ~/.wine/drive_c/Program\ Files/[/COLOR]


cd ~/.wine/drive_c/Program\ Files/
bash: cd: /home/djinn/.wine/drive_c/Program Files/: No such file or  directory

That's weird. Type in [COLOR=Blue]winecfg[/COLOR]

You should get a window like 
[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-Wineconfiguration.png[/IMG]

Go to Drives Tab and click autodetect > Apply

---

### Post by Nick_Jinn on 2010-07-17
[COLOR=Blue]winecfg

 winecfg
Warning: could not find DOS drive for current working directory '/home/djinn', starting in the Windows directory.


But then I DID get that box thingy. Let me see what happens when I do that. 



I guess I dont have a C drive......"This is not so great". 
[/COLOR]

---

### Post by ronnielsen1 on 2010-07-17
From googling I came across this post

[http://ubuntuforums.org/archive/index.php/t-336270.html](http://ubuntuforums.org/archive/index.php/t-336270.html)

> rm -rf ~/.wine
and run winecfg again

which WILL remove any wine config files that you may have but it sounds like you have issues anyway

---

### Post by Nick_Jinn on 2010-07-17
I am thinking about doing a clean install. I didnt have any sound drivers installed I noticed when I was playing around. I think I installed some.....How do I do the scrolling quote thing?




rm -rf ~/.wine
djinn@studioproject ~ $ winecfg
wine: created the configuration directory '/home/djinn/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfd4
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x1a4e0c (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0xa60e8d8, overlapped 0xa60e8e0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x1ded484 (nil)
wine: configuration in '/home/djinn/.wine' has been updated.
djinn@studioproject ~ $ winecfg
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
^Cdjinn@studioproject ~ $

---

### Post by ronnielsen1 on 2010-07-17
A new install of wine might be best. I'm not sure what's going on with yours.

> How do I do the scrolling quote thing?and then copy and paste the text in between [QUOTE] and /QUOTE]


[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-UbuntuForums-ReplytoTopi.png[/IMG]

---

### Post by Nick_Jinn on 2010-07-17
I know how to > asdfasdfasdf
But isnt there a different quote that scrolls so it doesnt take up as much space? You just leave the second bar out?

---

### Post by ronnielsen1 on 2010-07-17
> But isnt there a different quote that scrolls so it doesnt take up as  much space? You just leave the second bar out?

Not that I'm aware of. I hope you get wine working alright. I'm going to have to go do some work :cry:

---

### Post by Nick_Jinn on 2010-07-18
I am having no luck with Fallout 3 or Oblivion. I have gotten both of these games to play on Ubuntu before though. I dont know what the problem is.

---

### Post by Nick_Jinn on 2010-07-19
Im not sure what it is, but WINE 1.2 must not like something about my hardware or configuration. Its not working for Fallout3/Oblivion.



Can anyone tell me a thing or two about booting XP in virtualbox? How is gaming in Virtualbox?

---

### Post by Nick_Jinn on 2010-08-06
Hell Yeah! Its working!!!

After a clean install, upgrading Wine to 1.3, adding some tools and the proprietary Nvidia driver from the webite, actually following instructions this time and marking those files as native as in the WineHQ page, its working on the highest settings!!!!:popcorn:

---

