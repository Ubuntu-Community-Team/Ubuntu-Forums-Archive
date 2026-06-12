---
title: "No audio in Finale 2008"
date: 2009-09-26
forum: Wine
---

### Post by alexander.clark35 on 2009-09-26
Hello all!

I am a veteran of the windows experience, but I am quite new to Linux. I really want to use Linux for everything, but I haven't been able get any audio after installing finale 2008. It installed perfectly, but when I tell it to play, I hear nothing. Many other posts that I have read have suggested different notation software, but I really need to use finale for the class that I'm in. Is there a way that I can get finale to work in ubuntu? I'd really rather not have to use windows any more for anything. Thanks in advance!

Alex

---

### Post by unmole on 2009-09-26
You installed in under Wine right ?

---

### Post by alexander.clark35 on 2009-09-26
That's correct. I'm using ubuntu 9.04. After installing all the necessary updates and such, I installed wine, and then I used wine to install finale. I am able to open music files, but it tells me that it is running on very low memory...on top of the fact that it won't play any audio :D

---

### Post by alexander.clark35 on 2009-09-27
Does anyone have any ideas on what the problem is and how to fix it? Thanks in advance!

---

### Post by dearingj on 2009-09-28
You might try getting the latest beta version of Wine (1.1.30) from [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) . I've found that it generally works much better than the stable version (1.0.1) which comes in Ubuntu's repository.

It also would be nice if you would post a review of Finale 2008 on [this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=10635&iTestingId=23307") page, so that other people who want to use it can see how well it works. The test results currently on that page are quite old.

---

### Post by alexander.clark35 on 2009-10-03
I installed the latest beta version of wine, uninstalled and reinstalled finale, but it still gives me the same error. It brings up a windows labeled "native instruments" and says "warning: memory is getting low. This may cause dropouts or other artifacts." I'm thinking that it is a driver issue, given that it installed perfectly in every other way, and while the file is playing, it shows everything correctly and moves along the score, just as it should. There just isn't any sound. Are there any drivers for wine that would fix this audio/midi problem? Thanks!

---

### Post by alexander.clark35 on 2009-10-07
Does anyone know if my problem is a driver issue, and if so, are there any driver updates for wine that will allow finale to function properly? Thanks

---

### Post by tom66 on 2009-10-07
Can you play audio in other Ubuntu applications...?

Edit: This Wine report suggests whilst it can't play MIDI files itself it can still save them. Maybe this is your problem.

> 
	
Things I've noticed
by Emma Cohen on Monday September 29th 2008, 3:15
-Upon opening it says "Error opening MIDI driver FINMIDI: Module not found." The console output specifies "err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\PROGRAM FILES\\FINALE 2008\\FINMIDI.DLL") not found. I think this is related to the lack of sound.

-Although it won't play any sounds itself, it will save a file as a MIDI to be played by another application; but movie player complains (/after/ playing the file) that it can't find the right codec (although that may just happen to me).

-'Save As' only shows alternative file types if I do it before doing anything else. If I make any changes beforehand or if I open the window a second time it shows a blank box there.

Oh, and wine's IE doesn't seem to be up to displaying the help files.


---

### Post by alexander.clark35 on 2009-10-08
Interesting. Audio in other applications seems to work perfectly...it's just finale in wine, so perhaps the thing you quoted has something to do with it? I ran wine through the terminal and copied the output:

alexanderclark@Brainiac2Ubuntu:~$ wine '/home/alexanderclark/.wine/drive_c/Program Files/Finale 2008/finale.exe' 
fixme:mixer:ALSA_MixerInit No master control found on USB camera, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1ffcf8,0x1ffc18): stub
fixme:reg:GetNativeSystemInfo (0x1264ff93) using GetSystemInfo()
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1268b09e): Stub!
InstList[-1]::setVisibleSize(200, 150)
InstList[-1]::setVisibleSize(200, 150)
InstList[-1]::setVisibleSize(200, 150)
InstList[-1]::setVisibleSize(200, 150)
InstList[0]::setVisibleSize(648, 456)
InstList[1]::setVisibleSize(648, 456)
InstList[2]::setVisibleSize(648, 456)
InstList[3]::setVisibleSize(648, 456)
InstList[0]::setVisibleSize(648, 456)
InstList[0]::setVisibleSize(649, 456)
InstList[1]::setVisibleSize(648, 456)
InstList[1]::setVisibleSize(649, 456)
InstList[2]::setVisibleSize(648, 456)
InstList[2]::setVisibleSize(649, 456)
InstList[3]::setVisibleSize(648, 456)
InstList[3]::setVisibleSize(649, 456)
InstList[0]::setVisibleSize(648, 456)
InstList[1]::setVisibleSize(648, 456)
InstList[2]::setVisibleSize(648, 456)
InstList[3]::setVisibleSize(648, 456)
InstList[0]::setVisibleSize(648, 456)
InstList[0]::setVisibleSize(649, 456)
InstList[1]::setVisibleSize(648, 456)
InstList[1]::setVisibleSize(649, 456)
InstList[2]::setVisibleSize(648, 456)
InstList[2]::setVisibleSize(649, 456)
InstList[3]::setVisibleSize(648, 456)
InstList[3]::setVisibleSize(649, 456)
InstList[0]::setVisibleSize(650, 527)
InstList[1]::setVisibleSize(650, 527)
InstList[2]::setVisibleSize(650, 527)
InstList[3]::setVisibleSize(650, 527)
InstList[0]::setVisibleSize(650, 527)
InstList[0]::setVisibleSize(649, 527)
InstList[1]::setVisibleSize(650, 527)
InstList[1]::setVisibleSize(649, 527)
InstList[2]::setVisibleSize(650, 527)
InstList[2]::setVisibleSize(649, 527)
InstList[3]::setVisibleSize(650, 527)
InstList[3]::setVisibleSize(649, 527)
InstList[0]::setVisibleSize(650, 527)
InstList[1]::setVisibleSize(650, 527)
InstList[2]::setVisibleSize(650, 527)
InstList[3]::setVisibleSize(650, 527)
InstList[0]::setVisibleSize(650, 527)
InstList[0]::setVisibleSize(649, 527)
InstList[1]::setVisibleSize(650, 527)
InstList[1]::setVisibleSize(649, 527)
InstList[2]::setVisibleSize(650, 527)
InstList[2]::setVisibleSize(649, 527)
InstList[3]::setVisibleSize(650, 527)
InstList[3]::setVisibleSize(649, 527)
InstList[0]::setVisibleSize(650, 527)
InstList[1]::setVisibleSize(650, 527)
InstList[2]::setVisibleSize(650, 527)
InstList[3]::setVisibleSize(650, 527)
InstList[0]::setVisibleSize(650, 527)
InstList[0]::setVisibleSize(649, 527)
InstList[1]::setVisibleSize(650, 527)
InstList[1]::setVisibleSize(649, 527)
InstList[2]::setVisibleSize(650, 527)
InstList[2]::setVisibleSize(649, 527)
InstList[3]::setVisibleSize(650, 527)
InstList[3]::setVisibleSize(649, 527)

Does this tell you anything? It doesn't mean much to me yet :D

---

### Post by alexander.clark35 on 2009-10-10
It also told me "fixme:jack:JACK_drvLoad error loading the jack library libjack.so.0, please install this library to use jack". I installed jack and downloaded the missing library. Then I went into winecfg and selected jack as the audio driver. However, finale now says that midimap.cfg is corrupted and tells me that it failed to start the VST engine...any ideas?

---

### Post by alexander.clark35 on 2009-10-15
Is this sort of thing an issue with the way I set it up, or is it because wine doesn't have support for this type of application yet?

---

### Post by gustafson on 2009-10-21
Try this.

Open up wine, then go to configure wine > open the audio tab > enable OSS driver.  You can test the sound from that page (note box to the right).  Do you have another program in WINE you can test for sound?

Gustafson

---

### Post by alexander.clark35 on 2009-10-21
I tried the OSS driver, but as soon as finale opens up, it says that "it has encountered a serious error and needs to close..." and so on. I've heard that finale 2007 and 2009 work really well, but 2008 doesn't, so maybe that's the issue. I don't know, I'm kind of out of ideas :D

---

### Post by gustafson on 2009-10-22
Yes.  I have Finale 2007 and it does work well. 

 If you upgrade to 2009, I think you could enjoy improvements made to the process they use to scan in music.... however... I have not heard how well that works in Linux or Ubuntu.

Gustafson

---

### Post by alexander.clark35 on 2009-10-22
I see. The newest they have out currently is finale 2010, and I can upgrade to that for a lot less than buying it separately. Do you know where I can find out if 2010 works well in WINE? If it doesn't, I don't really see a need to upgrade because my current version suits all of my purposes. :D

---

### Post by gustafson on 2009-10-22
The way I found out about 2007... was looking in the WINE forums.  

I share your opinion about upgrading.  2007 works fine for me.

Gustafson

---

### Post by alexander.clark35 on 2009-10-23
It may not be a bad idea for me to upgrade to either 2009 or 2010...problem is, I don't have the money to throw at an upgrade currently :D Unless I can get my current version of finale to work in WINE, I will have to use windows 7...not a bad OS for Microsoft, I must say, but it's still Microsoft :(

---

### Post by gustafson on 2009-10-24
I beta tested windows 7.... and it ran alright....still not as good as Linux...



I built an HD Media PC and it runs well... but I did a little overkill.  quad core... hd all in wonder, 2tbs of hardrive, 8 gig ram... however ... it is still windows.  I have to make adjustments when updates come out that screw with my pro audio and media center stuff.  Currently trying to configure Mythbuntu so I use windows less and less.

If you can deal with making constant adjustments to your virus software, and the bugs in windows.... that will at least get you running in Finale.  However, I would suggest a dual boot.  Save your work on an external hard drive in hopes that someone will write a patch that helps with Finale in 2008.

---

### Post by alexander.clark35 on 2009-10-24
Yeah, I used the release candidate of windows 7 for a while and liked it the most out of any windows OS. Since I'm a student, I was able to get the upgrade for 30 dollars, so that was good. I'd rather use linux for everything, but I use finale for 80% of everything, so until I can use it in linux, It's just more convenient to use windows, bugs and all. Windows has more problems, but I understand how to fix them :D

---

### Post by alexander.clark35 on 2009-10-24
p.s. that sounds like a sweet laptop...did you build it or have the company customize it?

---

### Post by gustafson on 2009-10-26
It was a desktop.  I home built it little by little.  I may try building a laptop.  I am working on a masters in Information Systems Security... and the more I learn... the more I want to tinker.  I have also thought of getting a system 76 laptop.  They're pretty sweet and one of the larger models comes with an Ubuntu logo on the back of the laptop screen.

FYI- Here is another possible solution.

Set OS to WinXP (Important, otherwise it has performance problems), and adjust other settings accordingly (I chose ALSA as the sound output method). Click OK
 Disable Human playback: go to ~/.wine/drive_c/Program\ Files/Finale\ 2007/ (or where you have Finale installed) and into "Component Files" dir. Rename HP.DLL to HP.DLL.OFF
Finale won't be able to find the file... and thus.... human playback will be disabled.

---

### Post by alexander.clark35 on 2009-10-27
Oh, I see. A masters, huh? Well done! Yeah, my friend helped me build my desktop, which is where I have ubuntu currently. I have three hard drives, and I can use one as an "experimental" hard drive until I figure out exactly what I want to do. School is pretty crazy for me right now, so I'll have to wait until the weekend before I can try you solution, but I'll give it a go and let you know if anything changes. Thanks for you help!

---

### Post by gustafson on 2009-11-09
Did it work for you?

---

### Post by alexander.clark35 on 2009-11-10
Well, I upgraded to the new ubuntu 9.10. It's really shiny and new looking, which is nice. I installed wine 1.2 and tried to run the installer. All it ever said was that the command failed and some other blah blah. I uninstalled that and did wine 1.0, and the installer runs, but it asks for the second of three discs, and after I put the second disc in a hit ok (after giving it time to mount and all that, which actually never happens...?), it immediately asks for the third disc, saying that the copy failed. Why might this be?

---

### Post by alexander.clark35 on 2009-11-10
I figured it out. Turns out, even though the computer spit my disc back out, it didn't unmount it. All I had to do was manually unmount the previous disc and wait until the new disc was mounted. Weird, but whatever :D So it installed, just as before, but even after trying your suggestions, it had the same errors. The process is: I open finale, it pops up and reminds me that I need to authorize it. I tell it to remind me later. It then says "Error loading MIDI driver FINMIDI: Module not found." Next, it gives me a human playback error (because I renamed the file like you suggested :D). Then it says "WARNING: memory is getting low. This may cause dropouts or other artifacts!" After all that, it brings up the start window. I choose a song to open, and it opens it, but not before it tells me that "one or more MIDI devices are not responding". Needless to say, when I tell it to play the file, nothing happens. However, I can still edit the file in other ways; I just can't hear anything. Here's the output of this process from the terminal:

alexander@Brainiac-Ubuntu:~$ wine '/home/alexander/.wine/drive_c/Program Files/Finale 2008/finale.exe'
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
fixme:mixer:ALSA_MixerInit No master control found on USB camera, disabling mixer
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\PROGRAM FILES\\FINALE 2008\\FINMIDI.DLL") not found
fixme:reg:GetNativeSystemInfo (0x997ff93) using GetSystemInfo()
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x99bb09e): Stub!
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
InstList[-1]::setVisibleSize(200, 150)
InstList[-1]::setVisibleSize(200, 150)
InstList[-1]::setVisibleSize(200, 150)
InstList[-1]::setVisibleSize(200, 150)
InstList[0]::setVisibleSize(648, 456)
InstList[1]::setVisibleSize(648, 456)
InstList[2]::setVisibleSize(648, 456)
InstList[3]::setVisibleSize(648, 456)
InstList[0]::setVisibleSize(648, 456)
InstList[0]::setVisibleSize(649, 456)
InstList[1]::setVisibleSize(648, 456)
InstList[1]::setVisibleSize(649, 456)
InstList[2]::setVisibleSize(648, 456)
InstList[2]::setVisibleSize(649, 456)
InstList[3]::setVisibleSize(648, 456)
InstList[3]::setVisibleSize(649, 456)
InstList[0]::setVisibleSize(648, 456)
InstList[1]::setVisibleSize(648, 456)
InstList[2]::setVisibleSize(648, 456)
InstList[3]::setVisibleSize(648, 456)
InstList[0]::setVisibleSize(648, 456)
InstList[0]::setVisibleSize(649, 456)
InstList[1]::setVisibleSize(648, 456)
InstList[1]::setVisibleSize(649, 456)
InstList[2]::setVisibleSize(648, 456)
InstList[2]::setVisibleSize(649, 456)
InstList[3]::setVisibleSize(648, 456)
InstList[3]::setVisibleSize(649, 456)
InstList[0]::setVisibleSize(650, 527)
InstList[1]::setVisibleSize(650, 527)
InstList[2]::setVisibleSize(650, 527)
InstList[3]::setVisibleSize(650, 527)
InstList[0]::setVisibleSize(650, 527)
InstList[0]::setVisibleSize(649, 527)
InstList[1]::setVisibleSize(650, 527)
InstList[1]::setVisibleSize(649, 527)
InstList[2]::setVisibleSize(650, 527)
InstList[2]::setVisibleSize(649, 527)
InstList[3]::setVisibleSize(650, 527)
InstList[3]::setVisibleSize(649, 527)
InstList[0]::setVisibleSize(650, 527)
InstList[1]::setVisibleSize(650, 527)
InstList[2]::setVisibleSize(650, 527)
InstList[3]::setVisibleSize(650, 527)
InstList[0]::setVisibleSize(650, 527)
InstList[0]::setVisibleSize(649, 527)
InstList[1]::setVisibleSize(650, 527)
InstList[1]::setVisibleSize(649, 527)
InstList[2]::setVisibleSize(650, 527)
InstList[2]::setVisibleSize(649, 527)
InstList[3]::setVisibleSize(650, 527)
InstList[3]::setVisibleSize(649, 527)
InstList[0]::setVisibleSize(650, 527)
InstList[1]::setVisibleSize(650, 527)
InstList[2]::setVisibleSize(650, 527)
InstList[3]::setVisibleSize(650, 527)
InstList[0]::setVisibleSize(650, 527)
InstList[0]::setVisibleSize(649, 527)
InstList[1]::setVisibleSize(650, 527)
InstList[1]::setVisibleSize(649, 527)
InstList[2]::setVisibleSize(650, 527)
InstList[2]::setVisibleSize(649, 527)
InstList[3]::setVisibleSize(650, 527)
InstList[3]::setVisibleSize(649, 527)

---

### Post by alexander.clark35 on 2009-11-15
Any ideas?

---

### Post by gustafson on 2009-11-21
[SIZE=3]well,  

The memory message is a problem with WINE.  As far as I could tell... the WINE site mentioned certain versions allocated more memory than others... I couldn't find how to adjust that.

As for the human playback... here is something else to try... 

[/SIZE]     	 	 	 	 	 	  [FONT=Verdana, sans-serif][SIZE=3]Set OS to WinXP (Important, otherwise it has performance problems), and adjust other settings accordingly (I tried ALSA as the sound output method). Click OK[/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=3]3) Install Final
[/SIZE][/FONT][FONT=Verdana, sans-serif][SIZE=3]4) DO NOT run Finale yet. Download the third (c) update from finalemusic web site and run it to install.[/SIZE][/FONT] [FONT=Verdana, sans-serif][SIZE=3]5) Workaround for silent playback problem - Disable Human playback: go to ~/.wine/drive_c/Program\ Files/Finale\ 2007/ (or where you have Finale installed) and into "Component Files" dir. Rename HP.DLL to HP.DLL.OFF[/SIZE][/FONT] [FONT=Verdana, sans-serif][SIZE=3]6) Run Finale 2008. A minor bug - the splash image will persist until you proceed form the initial screen; don't worry, it won't cause any problem. Finale will give two error messages that Human Playback (the caouse of problem for playback on Linux) component files cannot be loaded, since we renamed its DLL to disable it. Just press enter twice to continue.[/SIZE][/FONT] [SIZE=3]This is a workaround I found for 2007.  It MAY not work completely for 2008.[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]
[/SIZE] 
 [SIZE=3]

[/SIZE]

---

### Post by alexander.clark35 on 2009-12-11
No dice. I have, however, purchased an upgrade to finale 2010. I figured it was a good time to upgrade, plus they had it for 40 bucks off. I'm going to try that in ubuntu and see if it works. Do you have any suggestions and/or solutions to any known problems that I might run into? Thanks!

---

### Post by alexander.clark35 on 2009-12-18
I was able to install finale 2010; however, I was not able to successfully install the garritan instruments and such that go with it. Despite that, the program still started up and had audio. The problem is, the display consisted of various shades of purple and green...needless to say, not exactly useful :D Does anyone have any ideas on what the problem and how to fix it? Thanks!

---

