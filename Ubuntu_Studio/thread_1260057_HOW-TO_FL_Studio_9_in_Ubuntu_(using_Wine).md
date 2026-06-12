---
title: "HOW-TO: FL Studio 9 in Ubuntu (using Wine)"
date: 2009-09-07
forum: Ubuntu Studio
---

### Post by falkTX on 2009-09-07
HOW-TO: FL Studio 9 in Ubuntu (using Wine)

Welcome to my "small" tutorial on how to run FL Studio 9 in Ubuntu.
This tutorial will explain how to install Wine and FL Studio, and then how to get the perfect setup.
I'm currently using Karmic, but all information covered here is also suitable for Jaunty and Intrepid.

If you found anything useful for this, feel free to comment it.
Let's get it started...



[SIZE="4"]Step 1 - Get & Install Wine[/SIZE]

If you already have the **latest** Wine installed, skip to step 2. If not, you should know that the installation method depends on your Ubuntu version.

For both **Intrepid and Jaunty**, you can install the latest Wine by using the official Wine repository for Ubuntu.
To install Wine (on Intrepid or Jaunty) just do:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/$(lsb_release -cs).list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine wine-gecko cabextract
```


For **Karmic** and **Lucid**, the latest Wine is available in a PPA, but has a different name. (to keep v1.0.1 "stable")
To install it on Karmic do:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.2 wine1.2-gecko cabextract
```




[SIZE="4"]Step 2 - Configure Wine[/SIZE]

_1. Activate "ALSA" and "Jack" as audio controllers_
First, open "Configure Wine" in apps -> Wine. On the "Audio" tab, set the audio controller to both "ALSA" and "Jack".
This will make possible the use of ALSA Midi while using WineASIO through Jack.
You should note that you will need to start Jack everytime before starting a Wine session.

_2. Direct-Access from ALSA_
To enable this "direct-access", do:
```
echo 'REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\Alsa Driver]
"UseDirectHW"="y"
' > /tmp/wine-sound.reg
regedit /tmp/wine-sound.reg
```

_3. Get & Install mfc42.dll and other dlls_
Some dlls are needed by some FL Studio plugins (at least 'Wasp' and 'Wasp XT'). FL Studio shows an error when the dlls are not found, so I recommend installing this too.
You can install it by doing: (needs internet connection)
```
cd /tmp
wget http://winezeug.googlecode.com/svn/trunk/winetricks
chmod +x ./winetricks
./winetricks allfonts vcrun2005 vcrun2008 mfc42 gdiplus vb6run riched20
```

_4. Use font smoothing_
Usually the "Fruity" fonts used inside FL Studio aren't properly displayed. This can be fixed by activating font smoothing in Wine.
To do it:
```
echo 'REGEDIT4

[HKEY_CURRENT_USER\Control Panel\Desktop]
"FontSmoothing"="2"
"FontSmoothingGamma"=dword:00000578
"FontSmoothingOrientation"=dword:00000001
"FontSmoothingType"=dword:00000002
' > /tmp/wine-fonts.reg
regedit /tmp/wine-fonts.reg
```

_5. Activate the OGG Vorbis codec_
FL Studio compresses it's wav files using a OGG codec (usually installed together with FLS). But, for some reason, Wine doesn't install it properly.
So, to fix it, just do:
```
sed -i 's/\[drivers32\]/\[drivers32\]\nMSACM.vorbis=vorbis.acm/' ~/.wine/drive_c/windows/system.ini
```



[SIZE="4"]
Step 3 - Get & Install WineASIO[/SIZE]

WineASIO is an ASIO driver for Wine, but outputs all sound to Jack. It's a smart way to combine low-latency ASIO and Jack technologies.
First, download wineasio:
[http://sourceforge.net/projects/kxstudio/files/DEBs](http://sourceforge.net/projects/kxstudio/files/DEBs)
Then you can open the deb file you've just downloaded and click "Install".
Just one last thing - do:
```
regsvr32 wineasio.dll
```
This will register the dll which will make applications see 'WineASIO' as a ASIO driver.




[SIZE="4"]Step 4 - Setting up Jack[/SIZE]

In order to start Jack, you could do it in a terminal... or using a GUI interface. The GUI is called 'Jack Control' and you can install it by doing:
```
sudo apt-get update
sudo apt-get install qjackctl
```
It will be available in apps -> Multimedia

Click on the "Setup" button. I recommend changing this settings:
1 - Disable 'Realtime' (Will not work with wineasio!)
2 - Enable 'Soft Mode' (better handling of overruns)
3 - Force 16bit (unless you need 32bit for a specific reason)
4 - Set 'Periods/Buffer' to 4
You can leave the rest as it is.

If for some reason you can't hear sound, on the QJackCtl GUI, click the "Connect" button, then:
1 - On the left side, click on the line that refers to Wine/Jack
2 - On the right side, click on 'system' line
3 - Click connect
This will activate the connection and you should hear sound now (the same thing can be done to send input to FL Studio)



[SIZE="4"]
Step 5 - Download & Install FL Studio 9[/SIZE]

Download URL - [http://demo.flstudio.com/]("http://demo.flstudio.com/")
To install it, just double click on the file or right-click on it and choose to open it with Wine.
ASIO4ALL will not work, and I recommend to disable the option to install it when installing FL Studio.

If you use other Linux music applications that support VST (like LMMS), I recommend the option to install the FLS VSTi (but not the DX/DirectX plugin). This VST will allow to use FL Studio as if it was a regular VST plugin.
If you just use FLS for making music, I recommend not to select that option, as it will give 2 warnings every time you recheck the plugin database
Another thing - when installing FLS9 you will got some "access control list" errors. Just click OK and the installation will proceed (this is a minor issue, the installation will NOT be affected)




[SIZE="4"]Step 6 - Final settings[/SIZE]

First of all, set the FLS audio driver to WineASIO!
There some FLS settings that may make it run faster under Wine. I recommend to disable the splash screen and any smooth stuff set in the FL Studio settings.
Be sure to UNCHECK the multiple processor check-box. Wine has some problems with multi-threading, making FLS more slow when enabled.

Unless you have a MIDI keyboard, another thing to do is to disable repeated keys (very annoying when using a regular keyboard in FL Studio).
The method for doing this may vary depending on the Ubuntu version, but usually there's a setting somewhere in the keyboard preferences.

If you haven't registered your FLS version yet, you can open the "Registry editor" (Alt+F2 and type 'regedit'), then you can import you FLS Regkey.

The FL Studio company, Image-Line, as modified the regcodes encryption - which allows Wine users to pass the "stack overflow" bug present in FLS8.
But some IL VSTs crash Wine sometimes. I advise you to use internal plugins as much as possible.





[SIZE="4"]Step 7 (Optional) - Midi input/output[/SIZE]

The first thing to do is to check if your MIDI Keyboard works. It should be working before starting FL Studio.
If you need Jack-MIDI, use the tool "a2jmidid" to bridge between ALSA and Jack MIDI.
Make sure you selected both ALSA and Jack as audio outputs in Wine Configuration!

You should start/enable your MIDI stuff _before_ starting FLS;
It will then appear in FL Studio MIDI section, really!




[SIZE="4"]Step 8 (Optional) - Using Jack for ALL applications[/SIZE]

--- This is optional and thus not required for running FL Studio ---

**-- KARMIC --**
As you might know, Jack is not included in the main Ubuntu repos (it's universe; community maintained).
For that reason, most of the important stuff does not have Jack support.
BUT, if you're using karmic (and not PowerPC), there's a PPA containing the exact same packages available in Ubuntu, but with Jack support enabled.
If can install all the packages by doing:
```
sudo add-apt-repository ppa:falk-t-j/jack4karmic
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install pulseaudio-module-jack
```
Download the pulse-jack deb and install it:
[http://ppa.launchpad.net/falk-t-j/lucid/ubuntu/pool/main/p/pulse-jack/](http://ppa.launchpad.net/falk-t-j/lucid/ubuntu/pool/main/p/pulse-jack/)
After Jack starts, you can just do:
```
pulse-jack
```
That gives you the possibility of listening to music or playing games while still running FL Studio.


**--- LUCID ---**
Just install the pulse-jack deb and run "pulse-jack" after Jack starts.




And... that's all

Thanks for reading my How-to. I hope it was useful
*(Comments are welcome)*

---

### Post by Stochastic on 2009-09-07
sweet! that's so much easier than ```
sudo apt-get install lmms
```


;) - sorry for the sarcasm.

---

### Post by tanfkap on 2009-09-12
The lowest form of wit stochastic :)

Falk thanks for all the tips. Brilliant! LMMS doesnt cut it.....yet.

Still crashing wine sometimes tho.  I think it may be my realtime kernel or something.  If you have tried with a realtime kernel and have  tip or 2 I would appreciate it .

Thx

---

### Post by falkTX on 2009-09-12
> **tanfkap said:**
> The lowest form of wit stochastic :)

Falk thanks for all the tips. Brilliant! LMMS doesnt cut it.....yet.

Still crashing wine sometimes tho.  I think it may be my realtime kernel or something.  If you have tried with a realtime kernel and have  tip or 2 I would appreciate it .

Thx

If you're using Image-Line VSTs, try going to the plugins website and download the installer again. Some plugins, like Sytrus, have been updated recently and no longer crash Wine

---

### Post by mint gum on 2009-09-16
awesome guide my windows xp is history lol   sorry for being a noob but how would i get a usb midi keyboard to work with this setup?  i have an oxygen 61 and i already downloaded the midisport firmware for it.  this guide will be perfect and complete for all the noobs out there who want to leave windows. please add a midi keyboard or controller section =)  thanks even if u don't, nice work!

---

### Post by falkTX on 2009-09-17
> **mint gum said:**
> awesome guide my windows xp is history lol   sorry for being a noob but how would i get a usb midi keyboard to work with this setup?  i have an oxygen 61 and i already downloaded the midisport firmware for it.  this guide will be perfect and complete for all the noobs out there who want to leave windows. please add a midi keyboard or controller section =)  thanks even if u don't, nice work!

I can't add a MIDI section to it cause I never used one, and also don't know how it works. But I know the "Virtual MIDI Keyboard" can be connected to Wine applications through Jack.
Try this: open 'Connections' then check the MIDI tab. It should see your USB-MIDI device and (maybe) you'll be able to connect it to Wine.

Please post if it works for you

---

### Post by mint gum on 2009-09-17
my usb midi keyboard only shows up on the alsa tab in jack connections, along with midi through. im using mint 7 gloria wich is based on ubuntu if that helps. also i only have a new and load button in jack patchbay. when i click load i try to open the wineASIO.xml you poasted i can't open the wineASIO.xml i just get an error message.  also i believe i read that to use midi on amd64 (which is what im on) you have to start jackbridge before jack. but i have to do more research on that.  thnx!

---

### Post by falkTX on 2009-09-17
> **mint gum said:**
> my usb midi keyboard only shows up on the alsa tab in jack connections. im using mint 7 gloria wich is based on ubuntu if that helps. also i only have a new and load button in jack patchbay. when i click load i try to open the wineASIO.xml you poasted i can't open the wineASIO.xml i just get an error message.  also i believe i read that to use midi on amd64 (which is what im on) you have to start jackbridge before jack. but i have to do more research on that.  thnx!

jackbridge was needed for older WineASIO versions (0.3). It is not needed for now (0.7.4)

Please post here any solution/work-arounds you find, that may be useful for other users.

(sorry but I can't help you more on this)

---

### Post by poisonkiller on 2009-09-27
Thank you so much! This tutorial totally made my FL Studio work. :guitar:

---

### Post by falkTX on 2009-09-28
Update - Just added 'winetricks riched20', that will be needed for 'Toxic Biohazard' plugin (or else FLS9 may crash when using it)

I also **may** have find a way to use MIDI through Wine/WineASIO.
When you connect a MIDI device, it will appear in 'Jack Control' -> 'Connections' -> 'MIDI'. If you connect your MIDI device to the output 'MIDI through', I think it will work on Wine apps.
I didn't really test this (I don't have a MIDI device), so please post if that works for you or not

---

### Post by billstei on 2009-09-28
@falkTX - You may want to mention the "access control list" issue under Step 5.  This "bug" does not affect anything critically that I am aware of (meaning you can just click OK each time it pops up).  The bug is being tracked here: [http://bugs.winehq.org/show_bug.cgi?id=18071](http://bugs.winehq.org/show_bug.cgi?id=18071)

---

### Post by falkTX on 2009-09-29
> **billstei said:**
> @falkTX - You may want to mention the "access control list" issue under Step 5.  This "bug" does not affect anything critically that I am aware of (meaning you can just click OK each time it pops up).  The bug is being tracked here: [http://bugs.winehq.org/show_bug.cgi?id=18071](http://bugs.winehq.org/show_bug.cgi?id=18071)

Thanks for reminding me that, updated now

---

### Post by nistrum on 2009-10-10
Haha, that's probably the best howto I've ever read. FL is the only thing that's got me booting into windows. Many many thanks dude :)

Does overrun a bit more than I'm accustomed to. Hopefully I can tweak the latency without resorting to a realtime kernel.

--M

---

### Post by falkTX on 2009-10-10
> **nistrum said:**
> Haha, that's probably the best howto I've ever read. FL is the only thing that's got me booting into windows. Many many thanks dude :)

Does overrun a bit more than I'm accustomed to. Hopefully I can tweak the latency without resorting to a realtime kernel.

--M

The "Periods/Buffer" setting can drastically reduce overruns. Set it to "4" and check if there's any change.
Usually 3 is enough, but it also depends on the hardware.

---

### Post by nistrum on 2009-10-10
> **falkTX said:**
> The "Periods/Buffer" setting can drastically reduce overruns. Set it to "4" and check if there's any change.
Usually 3 is enough, but it also depends on the hardware.

Thanks mate. I'm having a mess around with Jack at the moment. I've got it running at realtime priority which made a decent difference. Redrawing seems to be the main thing competing for CPU cycles.

Also some of the things I've changed seem to have stopped WineASIO appearing in the Jack connections list for more than a split second so looks like I've got some stuff to fix up.

If I learn anything relevant to the topic I'll post it here.

--M

---

### Post by Mr_Pag on 2009-10-10
Nice tutorial, cheers mate :)

I tried this before with FL Studio 7 a good while ago, the redraw rate (try opening a particularly knobby synth) was a little lacking under Wine, but this was a good while ago. I might give this a bash tho, see how things have progressed.

I made the switch to Renoise to compensate for FL in the interim, that's a nice app too. 

If I can get my head round supercollider or pd and Jack some homegrown synths in (one step at a time man). I think'll be pretty confident giving Windows the finger.

P

---

### Post by nistrum on 2009-10-11
It turned out that the ATI Catalyst driver was the thing chewing up all the CPU. So I've taken it off, installed the open source ATI driver and also compiled a realtime kernel (since fglrx was the only thing stopping me doing that).

I've finished up with about 20% less CPU usage playing back the demo song (on my Athlon 7850). I can't run compiz now but I've got a quicker system with a serviceable FL Studio install :). Thanks again.

--Matt

---

### Post by Incubus2012 on 2009-10-11
Hello,
I received this message and I followed all the steps, double checked, but I got this message when I tried to install FLS 9

"An error occurred while loading the archive.

[/tmp/flstudio_9.0_final.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /tmp/flstudio_9.0_final.exe or
          /tmp/flstudio_9.0_final.exe.zip, and cannot find /tmp/flstudio_9.0_final.exe.ZIP, period"

How can I fix this, if someone knows please help me.
[U]Thank you 
Nathan
Tempe, AZ
[/U]

---

### Post by Incubus2012 on 2009-10-11
Hello,
I was wondering if anyone knew too, if you can run FLS 9 in Jaunty Jackalope rather than booting to Windoze?
Thank you
Nathan

---

### Post by Incubus2012 on 2009-10-12
Hello everyone,
In the process of trying to install FL Studio 9 in Ubuntu Jaunty (64-bit HP)
I seem to be running into some last min. errors  After I installed FLS 9
When I open it up I get this error message:

'Couldn't create the direct sound main object'

that happens so when it opens up there is no sound when I press to play the demo?

anyone have some clues to what is taking place, and if so could you please help me out?

Thank you for your time
:)
Nathan

---

### Post by falkTX on 2009-10-12
> **Incubus2012 said:**
> Hello everyone,
In the process of trying to install FL Studio 9 in Ubuntu Jaunty (64-bit HP)
I seem to be running into some last min. errors  After I installed FLS 9
When I open it up I get this error message:

'Couldn't create the direct sound main object'

that happens so when it opens up there is no sound when I press to play the demo?

anyone have some clues to what is taking place, and if so could you please help me out?

Thank you for your time
:)
Nathan

You haven't started "Jack" yet. Configure the "Jack" using 'Jack Control' then press start, before opening the FL Studio.

---

### Post by Incubus2012 on 2009-10-12
Thank you FalkTX,
That brought the sound in. 
Do we Ubuntu users always have to press start before opening FLS 9 every time?

The sound works now however, there are other anomalies taking place that I do not understand.
Please help me out, I will try to explain this the best to my ability.

When FL Studio 9 Setup is running and the installation is taking place it first asks me where do I want to install FLS9 in (what folder?)
The destination defult folder it selects is:
z:\home\nathan\FL Studio 9 

is that right?  or should I be browsing for another location?

Next, when installing VSTi plugins
the destination defult folder is"
c:\Program Files\vstplugins

is that right?  It seems that they are in two different folders and that is why I might be getting error messages still?

During the install process after I just click next and choose the default folders to install in
@ create folder: z:\home\nathan\FL Studio 9
@create folder: c:\programfiles\outsim\synthmaker
@create folder: c:\Programfiles\Image-line\Hardcore
I get error messages that come up and say:

'Cannot read access control list
Error code 1400"

Do you know what that means, and could you please help me fix it.
Thank you for you time and expertise
Nathan :)

---

### Post by falkTX on 2009-10-13
> **Incubus2012 said:**
> Thank you FalkTX,
That brought the sound in. 
Do we Ubuntu users always have to press start before opening FLS 9 every time?

The sound works now however, there are other anomalies taking place that I do not understand.
Please help me out, I will try to explain this the best to my ability.

When FL Studio 9 Setup is running and the installation is taking place it first asks me where do I want to install FLS9 in (what folder?)
The destination defult folder it selects is:
z:\home\nathan\FL Studio 9 

is that right?  or should I be browsing for another location?

Next, when installing VSTi plugins
the destination defult folder is"
c:\Program Files\vstplugins

is that right?  It seems that they are in two different folders and that is why I might be getting error messages still?

During the install process after I just click next and choose the default folders to install in
@ create folder: z:\home\nathan\FL Studio 9
@create folder: c:\programfiles\outsim\synthmaker
@create folder: c:\Programfiles\Image-line\Hardcore
I get error messages that come up and say:

'Cannot read access control list
Error code 1400"

Do you know what that means, and could you please help me fix it.
Thank you for you time and expertise
Nathan :)

Have you *fully* read my tutorial...?

Like I say in there, that's normal.
Your folders locations are fine

---

### Post by NeoZiggy on 2009-10-14
> **Stochastic said:**
> sweet! that's so much easier than ```
sudo apt-get install lmms
```

;) - sorry for the sarcasm.

Yeah, but sometimes it feels more fun to abuse expensive windoze softwarez ;)

---

### Post by sgx on 2009-10-14
> **falkTX said:**
> Have you *fully* read my tutorial...?

Like I say in there, that's normal.
Your folders locations are fine
Sometimes a particular collection of hardware/software requires that
the app is installed in 

/home/username/.wine/drive_c/Program Files,

and that the .dll files are in

/home/username/.wine/drive_c/Program Files/Steinberg/VstPlugins

and some need the main folder (containing all subfolders) to be in

/home/username/.wine/drive_c/Program Files/Steinberg/VstPlugins.

Also some plugins not part of a DAW suite behave the same way, and
a few may even need their .fxb files to be inside the plugin folder.

So it behoves one to experiment, the vast differences in systems ensures
that some things are best not carved in stone.

Cheers

---

### Post by Shuur on 2009-11-18
Thanks a lot for this how-to! :D this simly great!

I just have a problem when I try to run FL Studio with jack in real-time (I have UbuntuStudio9.04, with real-time kernel configured and working fine with other apps).

I launch Jack with the real-time option checked and it starts normally but when I start FLStudio9, it appears in the qjackctl connections' window and then suddently disappears...

This is the output of the terminal when I lauch FL.exe
```
fixme:win:RegisterDeviceNotificationW (hwnd=0x147f48, filter=0x93ea28,flags=0x00000001),
    returns a fake device notification handle!
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8da, disabling mixer
fixme:win:LockWindowUpdate (0x2003a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:bitblt:client_side_dib_copy potential optimization: pixel format conversion
jack_client_thread zombified - exiting from JACK
fixme:xrender:X11DRV_AlphaBlend not a 32 bpp dibsection
^Cfixme:xrender:X11DRV_AlphaBlend not a 32 bpp dibsection
^Cfixme:asio:DllCanUnloadNow (void): stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:asio:DllCanUnloadNow (void): stub
```

And it's working fine whithout real-time...

Any help would be greatly appreciated! :-)

---

### Post by falkTX on 2009-11-18
> **Shuur said:**
> Thanks a lot for this how-to! :D this simly great!

I just have a problem when I try to run FL Studio with jack in real-time (I have UbuntuStudio9.04, with real-time kernel configured and working fine with other apps).

I launch Jack with the real-time option checked and it starts normally but when I start FLStudio9, it appears in the qjackctl connections' window and then suddently disappears...

This is the output of the terminal when I lauch FL.exe
```
fixme:win:RegisterDeviceNotificationW (hwnd=0x147f48, filter=0x93ea28,flags=0x00000001),
    returns a fake device notification handle!
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8da, disabling mixer
fixme:win:LockWindowUpdate (0x2003a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:bitblt:client_side_dib_copy potential optimization: pixel format conversion
jack_client_thread zombified - exiting from JACK
fixme:xrender:X11DRV_AlphaBlend not a 32 bpp dibsection
^Cfixme:xrender:X11DRV_AlphaBlend not a 32 bpp dibsection
^Cfixme:asio:DllCanUnloadNow (void): stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:asio:DllCanUnloadNow (void): stub
```

And it's working fine whithout real-time...

Any help would be greatly appreciated! :-)

I had the same problem before, and I fixed it, but I can't remember how...
(I had to re-format my HD)

Try messing around with the Jack settings.
Does it work fine without realtime?

---

### Post by Shuur on 2009-11-18
> **falkTX said:**
> I had the same problem before, and I fixed it, but I can't remember how...
(I had to re-format my HD)

Try messing around with the Jack settings.
Does it work fine without realtime?
Ok, at least I know that there is a solution. ;)
And yes It is working fine without real-time, but it's quite laggy....

---

### Post by MiCK.ca on 2009-11-18
I had no sound at first either. BUT here's what i did. I checked first to find that in the wine config under audio, both ALSA and jack were checked. even though i had only checked jack. fixed that. THEN i checked in FL Studio and found that under the audio tab that it was set to WINEASIO as a output device..changed that to "primary sound device" and wahla! sound!! much beautiful sound! 


You absolutely rock dude. I had bought FLStudio back when it was Fruity Loops! I finally purchased the producers edition in 2001 and then ...well moved to Linux. FL Studio was the only thing tying me to windows. I made the sacrifice and moved anyways. now!!! i have FL Studio back!!! FL Studio 9 Registered and fully functional!! (if you don't have a registered copy it is the only software that is worth the purchase because Image-Line gives LIFETIME updates!!) still playing with buffer and latency for those heavy hammered, gazillion track songs that are there. If I can adjust the latency to work with a heavy load then small production should be juice.    adjusting the buffer in both Jack and FLStudio helps. still fine tuning

here's playing a sample track in _REALTIME_ using JACK!!  Thank you for all your efforts!

p.s. If you are a dedicated FL user then i recommend buying the FL Studio Bible from Image-Line as well. it's worth it too!! AND LMMS is no where close to FL Studio yet...but they are working on it..

---

### Post by falkTX on 2009-11-18
I just updated the first post.

Changes are:
1 - For karmic, use the ubuntu-wine PPA to get the latest version
2 - Added vcrun2005 and vcrun2008 to the dlls to install via winetricks
3 - Added "Step 7" (optional), use Jack for ALL applications
4 - Updated the patchbay file (This one is more complete and *really* works. Re-Download recommended)

Enjoy!

---

### Post by MiCK.ca on 2009-11-20
The new XML file works great! There seems to be better flow inside FLS when multitasking tracks and sends. Awesome work dude! thanks again.

---

### Post by SonicEther on 2009-12-01
Okay so, I've tried a lot of things, I can't seem to get this fully working... Audio is fine, most things are working well... I have some GUI glitches that keep FL Studio from being usable for me...

The FL Studio emblem png thing that appears when you normally start FL Studio is invisible, and the area where it should be hides my mouse... Certain gui elements never go away which should, like if I right-click and enter the Piano Roll, the grey 'Piano Roll' menu item never fades away... This is pretty annoying! Also for some reason I couldn't get the font smoothing to work correctly... FL Studio is the only reason why I'd boot into Windows, if I could get this working I could forget about it :)

---

### Post by falkTX on 2009-12-02
> **SonicEther said:**
> Okay so, I've tried a lot of things, I can't seem to get this fully working... Audio is fine, most things are working well... I have some GUI glitches that keep FL Studio from being usable for me...

The FL Studio emblem png thing that appears when you normally start FL Studio is invisible, and the area where it should be hides my mouse... Certain gui elements never go away which should, like if I right-click and enter the Piano Roll, the grey 'Piano Roll' menu item never fades away... This is pretty annoying! Also for some reason I couldn't get the font smoothing to work correctly... FL Studio is the only reason why I'd boot into Windows, if I could get this working I could forget about it :)

You're using the latest Wine, v1.1.33? (I hope so).
I know that are some graphic rendering problems when using an Intel video card, but I don't think there's much we can do about it.

To be honest, FLS9 does not even "appear" on my desktop. However, FLS7 works just great. Maybe you could try FL7 to see if that changes anything.


Also, a new update was released (9.0.1), just download the installer again to get it.
The Image-Line has also made available 9.0.3beta (on their forums), so maybe you could try that too

---

### Post by sgx on 2009-12-02
> **SonicEther said:**
> Okay so, I've tried a lot of things, I can't seem to get this fully working... Audio is fine, most things are working well... I have some GUI glitches that keep FL Studio from being usable for me...

The FL Studio emblem png thing that appears when you normally start FL Studio is invisible, and the area where it should be hides my mouse... Certain gui elements never go away which should, like if I right-click and enter the Piano Roll, the grey 'Piano Roll' menu item never fades away... This is pretty annoying! Also for some reason I couldn't get the font smoothing to work correctly... FL Studio is the only reason why I'd boot into Windows, if I could get this working I could forget about it :)
Having these .dll files enables some vst software, there are free legal download sites for dll files:
msvcsv60
msvcp60
msvcp71
msvcp90
msvcr71
msvcr80
msvcr90
mfc42
mfc71
gdiplus
gdi32
I would then set your desktop to transparent, and install the Microsoft fonts, and Webcore fonts packages, should be in repos.
I would get on the nvidia linux forum, or heavy google for the nvidia
graphics card and chip best for linux. Buy it, or iiif on a laptop, get one with the best supported chip. Have you shut off non-essentials in the bios?
Cheers

---

### Post by SonicEther on 2009-12-02
> **falkTX said:**
> You're using the latest Wine, v1.1.33? (I hope so).
I know that are some graphic rendering problems when using an Intel video card, but I don't think there's much we can do about it.

To be honest, FLS9 does not even "appear" on my desktop. However, FLS7 works just great. Maybe you could try FL7 to see if that changes anything.


Also, a new update was released (9.0.1), just download the installer again to get it.
The Image-Line has also made available 9.0.3beta (on their forums), so maybe you could try that too

Hmm... Well, to be honest, I'm a huuge FL power-user and downgrading would really hinder my productivity... I am on a dell 1420 inspiron laptop, and unfortunately I am using an integrated Intel video card... Could this be causing my problems?

Hmm, glad you pointed out the version of Wine, I was just using 1.1, though I'm a bit skeptical about a mere 0.0.33 making a huge difference. I guess I'll see how that goes.

> I would then set your desktop to transparent, and install the Microsoft fonts, and Webcore fonts packages, should be in repos.
I would get on the nvidia linux forum, or heavy google for the nvidia
graphics card and chip best for linux. Buy it, or iiif on a laptop, get one with the best supported chip. Have you shut off non-essentials in the bios?
CheersWhoa whoa... I'm just installed Ubuntu a few days ago so I'm still pretty limp with it lol. I'll google around and figure out how to do those things you mentioned.

Thanks for the responses, guys. I know how much of a pain newbies like me can be sometimes. :P



EDIT: Okay so... I downloaded the latest version of Wine and things seem to be going better. My only problem is, something makes me think that my GPU is not being recognized at all. Things render very slowly (for example when I bring up the Mixer it takes about 5 seconds to draw all of the controls)... Scrolling is very choppy.. But at least everything is there now. Thanks for the help.

---

### Post by falkTX on 2009-12-03
Make sure you enable multi-core (not always enabled by default)

If you disable all the "smooth" stuff in options, some things will run a little faster. 
The splash screen can also be disabled as it is useless.

And, as far as I know, Intel and Wine always had problems, specially in 3D stuff.

Maybe we, Intel users, should still dualboot... sad thing...

---

### Post by sgx on 2009-12-03
@ SonicEther: Forgot to mention the .dll files go here:

/home/you/.wine/drive_c/windows/system32

There is an instructions readme included when installing the Microsoft fonts,
not having those fonts may cause wine to burn cpu preparing to use alternatives.

Wine versions are quite linear, 1.33 meaning nearly
33 separate releases since V1.1, each one hatched when significance
has been achieved. A lot goes into getting games and office apps
working, but we get the benefits of more stability.

nVidia graphics have by far the most support, if a deal comes around for such
a laptop, you might benefit in the long run.

Cheers

---

### Post by daedalus0x1a4 on 2009-12-03
hey guys? i installed fl studio 9 and loaded it. the browser wasn't displaying anything, when i selected items from drop down menus the menu would kind of stick to whatever was behind it, and it if i click play.. it doesn't. won't move. can't hear anything if i try to play notes from channel settings or piano roll, either.

:|

are there wine error logs i can dig through? somethhing? :|

---

### Post by falkTX on 2009-12-04
> **daedalus0x1a4 said:**
> hey guys? i installed fl studio 9 and loaded it. the browser wasn't displaying anything, when i selected items from drop down menus the menu would kind of stick to whatever was behind it, and it if i click play.. it doesn't. won't move. can't hear anything if i try to play notes from channel settings or piano roll, either.

:|

are there wine error logs i can dig through? somethhing? :|

Probably something wrong about Wine's audio settings.
Have you set the audio output, in Wine Config, to Jack?
Is Jack running?
Have you installed and registered WineASIO?
Did you use the patchbay file (or connected sockets manually)?

Anyway, all these are explained in the first post. Be sure to follow the instructions closely

---

### Post by daedalus0x1a4 on 2009-12-05
oh hey i went to test it again and i have sound in fl studio, and tracks play but the interface doesn't seem to update.

and if i click something on a drop down menu it kind of gets painted on the screen?

---

### Post by JDRising on 2009-12-05
I am having the same problems with my GUI in FL Studio 9.0.1. The browser is empty and the bits of menus being left behind and what not. I am using a Radeon HD4670 with their driver if that helps any.

---

### Post by falkTX on 2009-12-05
> **JDRising said:**
> I am having the same problems with my GUI in FL Studio 9.0.1. The browser is empty and the bits of menus being left behind and what not. I am using a Radeon HD4670 with their driver if that helps any.

Can you post a screenshot?

BTW, FL Studio v9.0.3 is out;
Check if the update changes anything.

---

### Post by JDRising on 2009-12-05
Well go figure, I open it up to take a screen shot of it not working and now it is working perfectly...

All I have done is reinstalled Wine 1.2 so maybe that will help the other guy too.

---

### Post by falkTX on 2009-12-05
> **JDRising said:**
> Well go figure, I open it up to take a screen shot of it not working and now it is working perfectly...

All I have done is reinstalled Wine 1.2 so maybe that will help the other guy too.

:lolflag:
I'm happy for you

---

### Post by sgx on 2009-12-05
> **JDRising said:**
> I am having the same problems with my GUI in FL Studio 9.0.1. The browser is empty and the bits of menus being left behind and what not. I am using a Radeon HD4670 with their driver if that helps any. 
In the long run, I would plan on horsetrading for, or purchasing an nvidia graphics product. Especially for more complicated apps like FL Studio. Reaper is still less than a 5 meg download, so if you need to record during the process of getting FL 9 stable, it s a good choice.
Cheers

---

### Post by daedalus0x1a4 on 2009-12-05
okay funny story, i installed the package named wine rather than wine1.2 thinking it was one of those meta-packages that installs the most current version. installed wine1.2 and the interface is working just fine. even the browser is populated. :)

---

### Post by JDRising on 2009-12-06
Glad to hear it worked for you too!

---

### Post by sgx on 2009-12-06
> **daedalus0x1a4 said:**
> okay funny story, i installed the package named wine rather than wine1.2 thinking it was one of those meta-packages that installs the most current version. installed wine1.2 and the interface is working just fine. even the browser is populated. :)
It might help someone in the future if you can post your hardware details.
People can arrange to purchase working replacements if the know what to get ;)

---

### Post by cbreaker on 2009-12-06
Two part question here, if you don't mind.

First part:  Anyone get MIDI to work with Jack and Wine?   My MIDI device list in Wine is always empty.   I have several MIDI ports available to the system, and when using ALSA, I see them in programs such as FL Studio and they work.   (Of course, sound is unusuable..)

Any help on the MIDI front would be really good.  FL Studio not very useful without controllers.   To me, anyway.

Second:  I have an unusual problem with sound, I think.  Running 9.10 with an rt kernel.  Using WINEASIO from a .deb found here.  

When I use WINEASIO with Jack, it only works when Jack is not in Realtime mode, and it works horribly.   Jack complains a lot about xruns and stuff, and the sound is garbage.

So, I can only get reasonable sound (but still not wonderful) is by using Jack with Realtime and NOT use WINEASIO.   But, I'm willing to  bet if I can get WINEASIO to work, it would be much better.

If anyone has any ideas...

Edit:  Yea, I guess the vorbis acm thing didn't go into system.ini properly.  Fixed that and now the wavs work.

PS.  Dispite the problems, FL Studio 9 works better in Ubuntu AMD64 than it does in Windows 7 x64.  (No asio support for FL Studio in Windows x64, because the sound card drivers only provide x64 ASIO and FL Studio is a 32-bit app.)

I'm so close I can taste it..

---

### Post by DerickX on 2009-12-07
I'm really in doubt whether this is the right way to go on Ubuntu...

Did you take a look at Qtractor in combination with the LMMS samples? Install whysynth (karmic) for the synths, use zynaddsubfx (2.4.0) via jack.

---

### Post by falkTX on 2009-12-07
It seems that FLS9/WineASIO doesn't work right in realtime. The only solution I found was to change the FLS output device evertime it gets kicked (WineASIO to default, then WineASIO again).
But this happens a lot in realtime, which is a pain when trying to make good music...

So I started making a special PPA for musicians/producers.
Check [https://launchpad.net/~falk-t-j/+archive/music](https://launchpad.net/~falk-t-j/+archive/music) for details.

So far I have:
 -> Enabled Jack for sound libs (alsa, portaudio, pulseaudio & xine)
 -> LV2 plugins (LV2 is LADSPA v2)
 -> Mixxx (updated)
 -> PortMIDI (updated)
 -> QSynth (updated)
 -> QTractor (updated)
 -> Virtual MIDI Keyboard (updated)
 -> ZynAddSubFX (updated)


Add the repo by running:
```
sudo add-apt-repository ppa:falk-t-j/music
```

Not sure who will use this, so give some feedback.

*Note: some packages are not compiled yet, they are waiting to build*

---

### Post by DerickX on 2009-12-07
To use Qtractor (with lmms samples) as alternative see also: [http://ubuntuforums.org/showthread.php?t=1348391](http://ubuntuforums.org/showthread.php?t=1348391)

---

### Post by falkTX on 2009-12-07
Great News!

A new WineASIO update has been released and it fixes the realtime problem!
It also will launch QJackControl when you click "ASIO Settings" button.

EDIT:
The source package is ready and I have send it to the PPA.
32bit and 64bit debs will be compiled and available soon

---

### Post by falkTX on 2009-12-07
**Warning!**

The latest Wine (1.1.34) introduces a _regression that makes FL Studio unusable_.
Updating is not recommended! (Wait for 1.1.35)

But there are good news, as the updated WineASIO is coming
(I already compiled for 64bit, 32bit will be soon in the PPA)

---

### Post by eightdollarbeer on 2009-12-12
this all looks great i usually have to build this stuff and mod fies for reatime @audio , only problem im getting is this .

Failed to load DLL wineasio.dll.so
sorry that was 
Failed to load DLL wineasio.dll


using new lucid and karmic repo . any ideas

---

### Post by MiCK.ca on 2009-12-12
Here's my update. I have wine 1.1.34 installed. Jack is NOT in realtime mode. BUT i went into FL Studio and under audio settings, unchecked the "multi-threaded" entries in the setup. that is both mixer and generator processing. 

FL Studio runs nicely with MUCH fewer peaks in the CPU. In jack my frames are set to 1024 and buffer is at 3!! Fl Studio is now the closet I have ever gotten it to run as if it were in a native Windows environment.

Let me know if this pans out for anyone else.

Edit: also forgot to add. when testing your settings each time. (this may be a no-brainer) but i loaded one of the more complex FL Studio demo tracks found under projects>funstuff. I used the same track to test my setting with. basically if i could get that track to play "bang-on" then anything would work.

---

### Post by falkTX on 2009-12-13
> **MiCK.ca said:**
> Here's my update. I have wine 1.1.34 installed. Jack is NOT in realtime mode. BUT i went into FL Studio and under audio settings, unchecked the "multi-threaded" entries in the setup. that is both mixer and generator processing. 

FL Studio runs nicely with MUCH fewer peaks in the CPU. In jack my frames are set to 1024 and buffer is at 3!! Fl Studio is now the closet I have ever gotten it to run as if it were in a native Windows environment.


So you just disabled multicore stuff and everything became nicer?
You're using dual-core?
That would be weird...

---

### Post by falkTX on 2009-12-13
> **eightdollarbeer said:**
> this all looks great i usually have to build this stuff and mod fies for reatime @audio , only problem im getting is this .

Failed to load DLL wineasio.dll.so
sorry that was 
Failed to load DLL wineasio.dll


using new lucid and karmic repo . any ideas

You'll to install wineasio package.
Check the first post again for a link

And the new wineasio still doesn't work in realtime. :(

---

### Post by MiCK.ca on 2009-12-13
Yep. dualcore AMD 2400 each. Better performance without multi-threading. Are we on to something here? Does wine not look at or maybe not even see the dual?

---

### Post by eightdollarbeer on 2009-12-14
> **falkTX said:**
> You'll to install wineasio package.
Check the first post again for a link

And the new wineasio still doesn't work in realtime. :(
this is my point the wineasio is installed , seems to have broken somewhere from 0.7.4 to 0.7.5 
7.4 registers fine 
i reverted back to karmic same problem.

---

### Post by MiCK.ca on 2009-12-14
Also it appears that Midi will work. Was able via qsynth & Zynaddsubfx to route through Jack and then into FL Studio 9. Only thing that appears not to work is the trigger to start recording on first note...perhaps the routing through jack is the issue. 

off to test some more...

edit: also i have noticed. (kinda forgotten Windows behavior) but the memory usage display [located next to the CPU usage meter on the menu bar] mine shows 0 (zero). as i recall in windows, when the CPU pushed up to 80% the program would dump responsibility of buffering to memory..i.e. this number would increase showing what the memory was helping compensate for. Under linux i get no memory usage. why? the memory amount is the same as your swap partition in linux. I believe that if we figured out how to enable swap usage with FL then that may help buffering/underruns issues

---

### Post by DejitaruJin on 2009-12-14
> **falkTX said:**
> **Warning!**

The latest Wine (1.1.34) introduces a _regression that makes FL Studio unusable_.
Updating is not recommended! (Wait for 1.1.35)


Well now, I'm glad I decided to read every post before asking a stupid question. I'm gonna go ahead and assume that my decision to update Wine immediately before installing FL Studio is why I don't have any sound output from it.

Edit: Yup, downgraded to 1.1.33, and I get sound output now. All that's needed now is the other half of the equation - MIDI in. JACK doesn't seem to be telling Wine/FL Studio that there's a controller hooked up, and it outright refuses to connect either of my MIDI input devices to MIDI Through on the ALSA tab.

---

### Post by falkTX on 2009-12-15
> **eightdollarbeer said:**
> this is my point the wineasio is installed , seems to have broken somewhere from 0.7.4 to 0.7.5 
7.4 registers fine 
i reverted back to karmic same problem.

I think it's the new Wine, 1.1.34; but not sure. (try using 1.1.33)
I moved already to Lucid to help UbuntuStudio, so I won't be able to help on this.

---

### Post by orin zolis on 2009-12-15
Hi i would love to get this working on linux however there are still a couple of things that i cant figure out 

1. this is what happens when i run regsvr32 wineasio.dll  

orin@laptop:~$ regsvr32 wineasio.dll
Failed to load DLL wineasio.dll
orin@laptop:~$ 

2. I don't know if i need 1 sorted first but when i open patchbay in jack there is no open option just new, load, save etc..
and i cannot find anywhere to download the attached file WineASIO-FLS.xml

thanks for any help as i really want to make the complete leap onto linux and flstudio is the only thing that has prevented me in the past. and has anyone considered putting together an ubuntu installation package with all the required plug-ins and updates to have fl run without going through all of this as when im done and have it working I will be creating one so i can transfer all of this to my other pc, that way I will happily supply the disk to anyone else who wants it as long as they pay postage

---

### Post by eightdollarbeer on 2009-12-15
yes ive move back to lucid again apears upgrade to lucid works better than fresh install . 
back to the point.
i tried wine 1.1.31 only other wine avail in my repos at the moment still doesnt register , and  wineasio 7.4 still works ok . 
im wondering if its more the wineasio than the wine , ill try building it later on when i have more time and report back.
thanks

---

### Post by eightdollarbeer on 2009-12-16
seems your deb installs to /usr/lib32/wine where when i build it it goes to /usr/lib/wine
guess its a problem possibly built on a dual core 64 bit os
easy fix people with a /usr/lib32 dir with only wine in it just move the files to lib or run these commands

sudo ln -s /usr/lib32/wine/wineasio.dll.so /usr/lib/wine/wineasio.dll.so
regsvr32 wineasio.dll
>>>>>>Successfully registered DLL wineasio.dll<<<<<<<<<

hope it helped someone

---

### Post by sgx on 2009-12-17
> **orin zolis said:**
> Hi i would love to get this working on linux however there are still a couple of things that i cant figure out 

1. this is what happens when i run regsvr32 wineasio.dll  

orin@laptop:~$ regsvr32 wineasio.dll
Failed to load DLL wineasio.dll
orin@laptop:~$ 

2. I don't know if i need 1 sorted first but when i open patchbay in jack there is no open option just new, load, save etc..
and i cannot find anywhere to download the attached file WineASIO-FLS.xml

thanks for any help as i really want to make the complete leap onto linux and flstudio is the only thing that has prevented me in the past. and has anyone considered putting together an ubuntu installation package with all the required plug-ins and updates to have fl run without going through all of this as when im done and have it working I will be creating one so i can transfer all of this to my other pc, that way I will happily supply the disk to anyone else who wants it as long as they pay postage
I would recommend installing Reaper, if only for testing purposes. If vst/asio/audio things work in Reaper, but not in FLS, you narrow down the list of things you can try to reconfigure. Did you FLS guys know your great Sytrus synth can load DX7 sysex files? Pretty cool, and Sytrus is
seriously under-rated!
Cheers

---

### Post by orin zolis on 2009-12-17
ok so my laptop is a dual core but iv tryed to get this on my desktop which is not and now it says this when i try to extract fruity: 

An error occurred while loading the archive. 

Archive:  /home/orin/Downloads/flstudio_9.0.3.exe
[/home/orin/Downloads/flstudio_9.0.3.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/orin/Downloads/flstudio_9.0.3.exe or
          /home/orin/Downloads/flstudio_9.0.3.exe.zip, and cannot find /home/orin/Downloads/flstudio_9.0.3.exe.ZIP, period.

however i did notice the wineasio-fls.xml attachment on here *slaps fore head* and have dl'd it 

this problem still exists 
orin@desktop:~$ regsvr32 wineasio.dll
Failed to load DLL wineasio.dll
orin@desktop:~$ 

and when i typ this into the terminal it does nothing 
sed -i 's/\[drivers32\]/\[drivers32\]\nMSACM.vorbis=vorbis.acm/' ~/.wine/drive_c/windows/system.inijust brings me back to orin@desktop:~$

 p, li { white-space: pre-wrap; }  this happens when i open jack

Could not open ALSA sequencer as a client.
 
 ALSA MIDI patchbay will be not available.


and just to clarify I'm using an earlier wine version 1.1.31. 

so in short I'm not gonna bother trying any more unless someone can guarantee that they have the solutions, too much time that could be spent mixing or otherwise and I'd rather offer cash to anyone in Brisbane and surrounding areas who is confident they can get this working on my system. I will not stand for the antics of Microsoft any longer and if there isn't anyone who I can pay. can someone with fl9 working in some version of Linux tell me the computer they are using and what packages they installed so i can be 100% sure that it will work if I get the same PC as u can see I am determined that I will have FL running in Linux. Rant Rahdy Rant Ra

---

### Post by eightdollarbeer on 2009-12-17
> **orin zolis said:**
> ok so my laptop is a dual core but iv tryed to get this on my desktop which is not and now it says this when i try to extract fruity: 

An error occurred while loading the archive. 

Archive:  /home/orin/Downloads/flstudio_9.0.3.exe
[/home/orin/Downloads/flstudio_9.0.3.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/orin/Downloads/flstudio_9.0.3.exe or
          /home/orin/Downloads/flstudio_9.0.3.exe.zip, and cannot find /home/orin/Downloads/flstudio_9.0.3.exe.ZIP, period.

however i did notice the wineasio-fls.xml attachment on here *slaps fore head* and have dl'd it 

this problem still exists 
orin@desktop:~$ regsvr32 wineasio.dll
Failed to load DLL wineasio.dll
orin@desktop:~$ 

and when i typ this into the terminal it does nothing 
sed -i 's/\[drivers32\]/\[drivers32\]\nMSACM.vorbis=vorbis.acm/' ~/.wine/drive_c/windows/system.inijust brings me back to orin@desktop:~$

 p, li { white-space: pre-wrap; }  this happens when i open jack

Could not open ALSA sequencer as a client.
 
 ALSA MIDI patchbay will be not available.


and just to clarify I'm using an earlier wine version 1.1.31. 

so in short I'm not gonna bother trying any more unless someone can guarantee that they have the solutions, too much time that could be spent mixing or otherwise and I'd rather offer cash to anyone in Brisbane and surrounding areas who is confident they can get this working on my system. I will not stand for the antics of Microsoft any longer and if there isn't anyone who I can pay. can someone with fl9 working in some version of Linux tell me the computer they are using and what packages they installed so i can be 100% sure that it will work if I get the same PC as u can see I am determined that I will have FL running in Linux. Rant Rahdy Rant Ra

try renaming the .zip to .exe and run it with wine.
and for wineasio
apt-get install wineasio
then 
sudo ln -s /usr/lib32/wine/wineasio.dll.so /usr/lib/wine/wineasio.dll.so
regsvr32 wineasio.dll

should be ok

---

### Post by orin zolis on 2009-12-17
it is named as an exe. and all other files i download in zip or as exe's say the same thing. ???

edit ok i'm loose as, i completely forgot to open it with wine

---

### Post by eightdollarbeer on 2009-12-17
> **orin zolis said:**
> it is named as an exe. and all other files i download in zip or as exe's say the same thing. ???

edit ok i'm loose as, i completely forgot to open it with wine

yea i dont like how ubuntu defaults exe's to archive manager and not wine. something u can set in preferred apps or properties of the file.

---

### Post by MiCK.ca on 2009-12-18
Kubuntu 9.10 does not have PulseAudio included in it. 

IF SO...My question here is does anyone currently use Kubuntu and how is your performance? I purged PulseAudio so my Ubuntu is Pulse-free and my FL Studio runs awesome...however in doing so i no longer have the "ubuntu-desktop" package. 

Does anyone here use Kubuntu? What is your take if you do? I am considering switching.

---

### Post by falkTX on 2009-12-18
Notice to all WineASIO users:
Launchpad compained about hosting non-free code in a PPA, so I had to remove it.

Can someone find another good & working WineASIO (0.7.5) ?

---

### Post by MiCK.ca on 2009-12-18
you could try a server like Megaupload or Rapidshare. post the link via a .txt file and everyone could go get as needed.

---

### Post by eightdollarbeer on 2009-12-19
> **falkTX said:**
> Notice to all WineASIO users:
Launchpad compained about hosting non-free code in a PPA, so I had to remove it.

Can someone find another good & working WineASIO (0.7.5) ?

just get concent from steinberg , im sure if you put a check here to agree to their terms in the deb install , save then alot of bw letting ppa host the asio.h tarther than us dload 250 meg tar.
or i dono name it winefasio kinda like a folex watch.
maybe sourceforge

---

### Post by MiCK.ca on 2009-12-25
For anyone who may (or may not) have bumped into problems with PulseAudio in their work. Either you tried purging and it hasn't worked right since or you just want something that is not filled with Pulse...here is a consideration: 

[]("http://www.apodio.org/")[http://code.goto10.org/projects/puredyne/](http://code.goto10.org/projects/puredyne/)

Puredyne is Xfce and is now based (loosely) on ubuntu but without the pulse AND a really good custom RT kernel in each. I'm currently running and testing Pure:dyne beta2 with FL Studio flawlessly happy! I'm running Pure:dyne as i type and it is proving to be a permanent OS on my system. Being ubuntu based now...all things U are here! (but with Xfce4)

---

### Post by falkTX on 2009-12-28
> **MiCK.ca said:**
> For anyone who may (or may not) have bumped into problems with PulseAudio in their work. Either you tried purging and it hasn't worked right since or you just want something that is not filled with Pulse...here is a consideration: 

[]("http://www.apodio.org/")[http://code.goto10.org/projects/puredyne/](http://code.goto10.org/projects/puredyne/)

Puredyne is Xfce and is now based (loosely) on ubuntu but without the pulse AND a really good custom RT kernel in each. I'm currently running and testing Pure:dyne beta2 with FL Studio flawlessly happy! I'm running Pure:dyne as i type and it is proving to be a permanent OS on my system. Being ubuntu based now...all things U are here! (but with Xfce4)

I already started working for a rocking Lucid release, but this could help a bit.
However, we should focus on only 1 distro, instead of creating lots of them...

---

### Post by FinalCoyote on 2009-12-29
Yeah man, good stuff, good tutorial, thanks a lot!

---

### Post by jdunka on 2009-12-31
There is a bit of sarcasm going on in this post.

---

### Post by HaightsW on 2010-01-01
> **eightdollarbeer said:**
> seems your deb installs to /usr/lib32/wine where when i build it it goes to /usr/lib/wine
guess its a problem possibly built on a dual core 64 bit os
easy fix people with a /usr/lib32 dir with only wine in it just move the files to lib or run these commands

sudo ln -s /usr/lib32/wine/wineasio.dll.so /usr/lib/wine/wineasio.dll.so
regsvr32 wineasio.dll
>>>>>>Successfully registered DLL wineasio.dll<<<<<<<<<

hope it helped someone

Cheers 8$B, that fixed it for me!  :guitar:

---

### Post by astroblack on 2010-01-16
Every time I try to install I get this message.

> Archive:  /home/astroblack/Downloads/flstudio_9.0.3.exe
[/home/astroblack/Downloads/flstudio_9.0.3.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/astroblack/Downloads/flstudio_9.0.3.exe or
          /home/astroblack/Downloads/flstudio_9.0.3.exe.zip, and cannot find /home/astroblack/Downloads/flstudio_9.0.3.exe.ZIP, period.


Can someone tell me what this means, and what I should do? :)

---

### Post by falkTX on 2010-01-17
> **astroblack said:**
> Every time I try to install I get this message.



Can someone tell me what this means, and what I should do? :)

Right click on the file, and select "Open With" -> "Wine"

---

### Post by thomasjw on 2010-01-18
> **eightdollarbeer said:**
> try renaming the .zip to .exe and run it with wine.
and for wineasio
apt-get install wineasio
then 
sudo ln -s /usr/lib32/wine/wineasio.dll.so /usr/lib/wine/wineasio.dll.so
regsvr32 wineasio.dll

should be ok

AHHH, that was the reason my wineasio.dll wouldn't register -- didn't have it in the right directory.  (Which I might've discovered sooner if regsvr32 gave me any helpful output like 'file not found,' rather than just saying 'failed to load dll.')  Heaping thanks!

---

### Post by senjito on 2010-01-27
Hi,

I did all step, but when i launch FL i have a problem with direct sound.. So i have no sound on FL.

What i can do? 

Thank you.

---

### Post by MiCK.ca on 2010-02-01
Assuming that you have followed each step...I had the same problem.

If you are running jack/wineasio and your patchbay has got the wine .xml file loaded, then go into FL Studio's config and under the audio tab click the dropbox and choose "wineasio". Your sound sound then route through that connection and it should work. Also just peek at the connections in jack to make sure things are routed correctly.

---

### Post by MrDelish on 2010-02-03
So I got it up and working first and then decided I wanted WineASIO. Although I got the installation of the DLL fine, FL Studio won't recognize it in the audio settings. Should I have to reinstall the program for it to work?

---

### Post by sgx on 2010-02-04
> **MrDelish said:**
> So I got it up and working first and then decided I wanted WineASIO. Although I got the installation of the DLL fine, FL Studio won't recognize it in the audio settings. Should I have to reinstall the program for it to work?
Hi, did you run the command 

regsvr32 wineasio.dll

?
It will reply that the .dll is registered, if successful. Then wineasio will appear in appropriate menu choices in windows host apps.

Cheers

---

### Post by MrDelish on 2010-02-05
> **sgx said:**
> Hi, did you run the command 

regsvr32 wineasio.dll

?
It will reply that the .dll is registered, if successful. Then wineasio will appear in appropriate menu choices in windows host apps.

Cheers

Yep, I just did it again to be sure:

```
regsvr32 wineasio.dll
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0xd8c:0x0c, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
Successfully registered DLL wineasio.dll
```

Then I got to FL Studio's audio settings and find "Primary Sound Driver" and three instances of "default". I don't think I missed any steps, but I wonder if it's a problem that I separate my installations using PlayOnLinux. Should I use some special command to run regsvr32?

---

### Post by m4443 on 2010-02-15
I have FL Studio and wineASIO running in realtime mode.

I'm using Jackdmp (aka JACK2 or Jack 1.9.4), wineASIO 0.7.5 and wine 1.1.38.
My audio card is Edirol's external firewire card (Fa-66), so I have to use FFADO driver (simply named 'firewire' in Jack).

Also, I run wine with command "chrt" to give realtime priority for FL Studio (dunno if it *really* works, but I've seen people using it with Reaper..)
```
chrt -f 80 wine <path to .exe>
```

Basically, this works pretty okay. However, I'm experiencing XRUNs. Not like continuous stream of them, but for example they may occur when playing big project or when loading a project. 

Somehow, it seems that these XRUNs are not result of my sound setup (soundcard, jack settings), but from wine itself, since they appear when I start fl studio, open a project or a plugin etc. Or at least this is what I believe. Now, the question for me is, can I live with these XRUNs. For most times, I don't hear them - I'm just a bit (too) perfectionistic person. :P

---

### Post by alvaroguillen on 2010-02-16
maybe midiyoke will work in wine? to get the notes from your keyboard.

---

### Post by ppine on 2010-03-04
Can someone supply a valid link for the wineasio 0.7.5 deb package please? i did download the wineasio package from sourceforge and the sdk from steinberg but i am having trouble compiling it.

---

### Post by falkTX on 2010-03-04
> **ppine said:**
> Can someone supply a valid link for the wineasio 0.7.5 deb package please? i did download the wineasio package from sourceforge and the sdk from steinberg but i am having trouble compiling it.

There you go:
[http://falktx.xtreemhost.com/outro/wineasio_0.7.5-0~ppa17_all.deb](http://falktx.xtreemhost.com/outro/wineasio_0.7.5-0~ppa17_all.deb)

Please note that it requires internet access when installing.
This package can be redistributed safely.
Enjoy!

---

### Post by ppine on 2010-03-04
Cool thanks :popcorn: , it works quite well on my system. The newstuff from FL9 demo it does not like tough, it eats my system. i have to start jackd from the system tray because the qjackctl tries to start it in realtime even if it's set not to. the only down side to this is i think it will now not make use of the patchbay xml thingy.

---

### Post by NikNikols on 2010-03-06
> **falkTX said:**
> There you go:
[http://falktx.xtreemhost.com/outro/wineasio_0.7.5-0~ppa17_all.deb](http://falktx.xtreemhost.com/outro/wineasio_0.7.5-0~ppa17_all.deb)

The link is broken. Please fix it.

---

### Post by ppine on 2010-03-07
> **NikNikols said:**
> The link is broken. Please fix it.

Just do: wget [http://falktx.xtreemhost.com/outro/wineasio_0.7.5-0~ppa17_all.deb](http://falktx.xtreemhost.com/outro/wineasio_0.7.5-0~ppa17_all.deb)

It will work.

---

### Post by falkTX on 2010-03-08
> **ppine said:**
> Just do: wget [http://falktx.xtreemhost.com/outro/wineasio_0.7.5-0~ppa17_all.deb](http://falktx.xtreemhost.com/outro/wineasio_0.7.5-0~ppa17_all.deb)

It will work.

Yeah, my host is a little weird... deb files always caused problems.

---

### Post by mrblowtatoes on 2010-03-25
So I have the latest development edition of wine and ubuntu, flstudio 9 works awesome, reg keys work, everything, gui is nice, but I want to change the sound system. I currently have it set to primary sound drive, which uses ALSA [it might even be pulseaudio] the quality itself is great, but there is a tick every second the note is held down, and the latency has to be extremely high, I am thinking of switching to oss, I was wondering if anyone has tried flstudio 9 with the most recent release of oss4, and if so did it work and how did you configure it?

i don't need midi

i am also using linux-rt

---

### Post by SiL3NC3 on 2010-03-27
what about using cubase5?
i cant get it to work ...
my dongle gets access but the licences are not found.
i another case the dongle was not found.

...
anybody tried cubase5 to get running with wine/ubuntu?

---

### Post by falkTX on 2010-04-21
First post now includes wineasio 0.7.5 debs (32bit and 64bit)

Enjoy!

---

### Post by BanannaButt on 2010-04-27
I'm a little new to Linux, and thanks to your help, I am very close to finally getting FL to work in Ubuntu.

For some reason, though, importing the regkey isn't working for me through regedit.  The key IS valid: I had it up and running on my previous Windows installation.  I see the regkeys in regedit too... FL just starts in the demo mode.

Is anyone else experiencing this problem?  I'm using Ubuntu 9.10 on a Gateway FX p-7805u [http://support.gateway.com/s/Mobile/2009/PSeries/P-78/P-78nv.shtml](http://support.gateway.com/s/Mobile/2009/PSeries/P-78/P-78nv.shtml).

---

### Post by BanannaButt on 2010-04-27
> **BanannaButt said:**
> I'm a little new to Linux, and thanks to your help, I am very close to finally getting FL to work in Ubuntu.

For some reason, though, importing the regkey isn't working for me through regedit.  The key IS valid: I had it up and running on my previous Windows installation.  I see the regkeys in regedit too... FL just starts in the demo mode.

Is anyone else experiencing this problem?  I'm using Ubuntu 9.10 on a Gateway FX p-7805u [http://support.gateway.com/s/Mobile/2009/PSeries/P-78/P-78nv.shtml](http://support.gateway.com/s/Mobile/2009/PSeries/P-78/P-78nv.shtml).
:lolflag:Haha, I figured it out...

[SIZE=5]NOTE TO ANYONE INTENDING TO RUN FL STUDIO: _**[SIZE=6]ADD THE REGKEY AS BOTH SUDO AND NORMALLY!!![/SIZE]**_[/SIZE]

---

### Post by falkTX on 2010-04-27
> **BanannaButt said:**
> I'm a little new to Linux, and thanks to your help, I am very close to finally getting FL to work in Ubuntu.

For some reason, though, importing the regkey isn't working for me through regedit.  The key IS valid: I had it up and running on my previous Windows installation.  I see the regkeys in regedit too... FL just starts in the demo mode.

Is anyone else experiencing this problem?  I'm using Ubuntu 9.10 on a Gateway FX p-7805u [http://support.gateway.com/s/Mobile/2009/PSeries/P-78/P-78nv.shtml](http://support.gateway.com/s/Mobile/2009/PSeries/P-78/P-78nv.shtml).

NOTE FOR ALL USERS OF WINE:
**DO NOT EVER RUN WINE AS SUDO!!!**

That is the true; sorry, but it really is that way.
We don't want windowze viruses on Linux, you know?

---

### Post by billstei on 2010-04-30
Just some notes (ha!):

I was able to get FL9.1 running in Lucid, but with my Soundblaster PCI512 card Jack would not work with the Periods = 4 as recommended in the first post, which had to be set to 2.  I'm using WineASIO 0.7.5 via Jack 0.118svn3796.  ALSA (and Jack) thinks that my EMU XBoard49 has a USB audio card in it, but it doesn't, and this is somewhat annoying because I don't always have it On at startup, so the device numbers shift (hw:1 or hw:2).  Pulseaudio is running, and Wine is routing through ALSA only.  Realtime priority for Jack does not work (as noted in the first post) and so I am using the generic 2.6.32-22 kernel.  GUI refreshes are painfully lagging the audio when FL is in Play -- this is using the proprietary NVidia driver 195.36.15 on a GEForce 6150, but this might be a CPU usage issue in FL.  I did not try FL with the new open source nv video driver, but other Wine apps' GUIs were performing very poorly with it.  Maybe these video issues are unique to this Wine, which is 1.1.43.

In general things are working okay, or at least they seem better than Karmic as I don't recall every getting FL to work there.

Bill

---

### Post by codyduncan on 2010-05-02
at step 3 I get the following error:

```
------------------------------------------------------
sha1sum mismatch!  Rename /home/cody/.winetrickscache/./times32.exe and try again.
------------------------------------------------------


```

---

### Post by sgx on 2010-05-02
> **codyduncan said:**
> at step 3 I get the following error:

```
------------------------------------------------------
sha1sum mismatch!  Rename /home/cody/.winetrickscache/./times32.exe and try again.
------------------------------------------------------


```
Not knowing the depths, as a general hint, the extra wine helper utilities,
anything other than wine, libwine, and wineasio, may be the cause of bazaar
problems. I would uninstall everything related to wine, make sure
/usr/share/wine, and /home/user/.wine are gone, and then reinstall just
wine, libwine, and wineasio.

If not installed, I add these downloadable .dll files to 

/home/username/.wine/drive_c/windows/system32 to add compatibility with Zebra, and other windows apps/instruments:

gdiplus
mfc42
mfc71
msvcp60
msvcp71
msvcr71
msvcr80
mscvsc60
msvcp90
msvcr90

Cheers

---

### Post by falkTX on 2010-05-03
> **codyduncan said:**
> at step 3 I get the following error:

```
------------------------------------------------------
sha1sum mismatch!  Rename /home/cody/.winetrickscache/./times32.exe and try again.
------------------------------------------------------


```

just delete that file:
```
rm /home/cody/.winetrickscache/./times32.exe
```
and re-run that part again. no need to reinstall wine

---

### Post by r3l1c on 2010-05-08
have not tried this .. but definitelly will. If this is going to work ... my only reason for keeping WINDOZE is gone !! Am I dreaming ? ? ...

---

### Post by MiCK.ca on 2010-05-14
Has anyone got their MiDi working in FL studio? The message about MIDImap.cgf being copied to the windows system directory keeps appearing...problem is that there isn't a midimap.cgf to copy because its not native windows. This config file is generated when windows first detects your sound setup...all of us haven't actually "installed" windows...so that part was skipped.

Ideas?

---

### Post by justified on 2010-05-14
> **MiCK.ca said:**
> Has anyone got their MiDi working in FL studio? 
I have my usb midi-keyboard working. I didn't actually had to do anything special for that, just followed instructions from the first post. It shows correctly in FL as USB Axiom 61 midi.

---

### Post by TommyTinkles on 2010-05-16
I noticed in the wine audio config dialog that alsa and oss have midi devices listed underneath them but JACK only has wave in and out - does wine not support jack midi at all? I can access my midi keyboard in FL when I tell wine to use alsa, but when I tell it to use JACK then of course it's not going to think anything's there. Does anyone have a solution for this? becuase I'd much rather use JACK so I can route wine output into ardour, and it's low latency, and realistically using a native app like lmms really isn't an option.

---

### Post by falkTX on 2010-05-16
> **TommyTinkles said:**
> I noticed in the wine audio config dialog that alsa and oss have midi devices listed underneath them but JACK only has wave in and out - does wine not support jack midi at all? I can access my midi keyboard in FL when I tell wine to use alsa, but when I tell it to use JACK then of course it's not going to think anything's there. Does anyone have a solution for this? becuase I'd much rather use JACK so I can route wine output into ardour, and it's low latency, and realistically using a native app like lmms really isn't an option.

Maybe enabling alsa midi emulation in Jack ? (QJackCtl -> Setup -> "midi driver" to 'seq').

I don't have a midi keyboard to test this.

---

### Post by TommyTinkles on 2010-05-16
That didn't work, but I did find a way to get it working - using dssi-vst and jack-dssi-host you can load FL Studio as a VSTi (you'd have to have made sure you installed as a VSTi at install) then go into the VstPlugins directory (by default) in your wine c: drive, copy FL Studio 7 VSTi.dll into ~/vst/, make sure you've ran dssi-vst-scanner, and then you should be able to run it with something like 'jack-dssi-host dssi-vst.so:FL*Studio*7*VSTi.dll', connect your midi keyboard up to it in the jack connections window and voila!

Well, it worked for me anyway, hope it's helpful.

---

### Post by noobuntu! on 2010-05-17
I am not sure what I may be doing wrong but **regsvr32 wineasio.dll** gives me the following:

[B]fixme:atl:AtlModuleInit SEMI-STUB (0x4042c8 0x404578 0x400000)
fixme:ole:CoInitializeSecurity (0x409838,-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceW ((null),L"Viewpoint Manager Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x71e9b4,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
Failed to load DLL wineasio.dll[/B]

Running FL Studio 9 gives me this error:

**Couldn't create the DirectSound main object.**


There is no sound when the program starts.

I have made sure to enable ONLY the JACK driver in the Wine audio configuration.

Thank you for any help!!!:P:KS

---

### Post by falkTX on 2010-05-17
> **noobuntu! said:**
> I am not sure what I may be doing wrong but **regsvr32 wineasio.dll** gives me the following:

[B]fixme:atl:AtlModuleInit SEMI-STUB (0x4042c8 0x404578 0x400000)
fixme:ole:CoInitializeSecurity (0x409838,-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceW ((null),L"Viewpoint Manager Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x71e9b4,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
Failed to load DLL wineasio.dll[/B]

Running FL Studio 9 gives me this error:

**Couldn't create the DirectSound main object.**


There is no sound when the program starts.

I have made sure to enable ONLY the JACK driver in the Wine audio configuration.

Thank you for any help!!!:P:KS


Can you try reinstalling the wineasio deb?

---

### Post by noobuntu! on 2010-05-17
> **falkTX said:**
> Can you try reinstalling the wineasio deb?


fixme:atl:AtlModuleInit SEMI-STUB (0x4042c8 0x404578 0x400000)
fixme:ole:CoInitializeSecurity (0x409838,-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceW ((null),L"Viewpoint Manager Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x71e9b4,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
**Successfully registered DLL wineasio.dll**

Yeaa! It worked!! However I still get** Couldn't create the DirectSound main object.** when I run the program.:confused:

---

### Post by falkTX on 2010-05-17
> **noobuntu! said:**
> fixme:atl:AtlModuleInit SEMI-STUB (0x4042c8 0x404578 0x400000)
fixme:ole:CoInitializeSecurity (0x409838,-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceW ((null),L"Viewpoint Manager Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x71e9b4,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
**Successfully registered DLL wineasio.dll**

Yeaa! It worked!! However I still get** Couldn't create the DirectSound main object.** when I run the program.:confused:

Try forcing 16bit, or any other settings in QJackCtl

---

### Post by noobuntu! on 2010-05-17
> **falkTX said:**
> Try forcing 16bit, or any other settings in QJackCtl

Wow!!!!!!!!!!!!!!! THANK YOU THANK YOU THANK YOU!!!!!:KS:KS:KS:KS:KS


I forced 16bit and started jack. The problems are now fixed! It has sound and runs much faster! Thanks again falk!!!!!:popcorn::popcorn:


:guitar:

---

### Post by falkTX on 2010-05-17
> **noobuntu! said:**
> Wow!!!!!!!!!!!!!!! THANK YOU THANK YOU THANK YOU!!!!!:KS:KS:KS:KS:KS


I forced 16bit and started jack. The problems are now fixed! It has sound and runs much faster! Thanks again falk!!!!!:popcorn::popcorn:


:guitar:

Glad to help.

---

### Post by MiCK.ca on 2010-05-17
ok. one more go at this....went out and picked up a Korg NanoKey and yes now Jack can see that...connection is made but FL Studio does not see it. still get that blasted "midimap.cfg" error...aaghhh! Two midi keyboards...no see either! Ideas?

Note: have tried loading a "blank" midimap.cfg file downloaded from Microsoft's support site and that wasn't good enough either. could a couple of people check to see if they have this file in their /windows/system directory? since it isn't native windows...is it even needed. those whose midi is working do they have such a file?

---

### Post by TommyTinkles on 2010-05-17
I got midi working with JACK and FL Studio using the VSTi of fl studio and dssi-vst - then loading the VSTi using jack-dssi-host as a standalone app, then connected by midi keyboard to it in the ALSA connections tab of jack control. I don't know anything about that error though.

---

### Post by karl.lensson on 2010-05-23
Awsome tut.
tried to get FL on my laptop a while back, it loaded and did nothing.

I finished installing and FL works fine, but after seeing that i could use pulse i tried to get that running. I went to write the following code

[LEFT][PHP]####@####-laptop:~$ sudo apt-get install pulseaudio-module-jack
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pulseaudio-module-jack: Depends: libpulse0 (= 1:0.9.19-0ubuntu4+withjack0) but 1:0.9.19-0ubuntu4.1 is to be installed
                          Depends: pulseaudio (= 1:0.9.19-0ubuntu4+withjack0) but 1:0.9.19-0ubuntu4.1 is to be installed
E: Broken packages
####@####-laptop:~$
[/LEFT]

As u can see it thinks i have missing dependencies, well i try to get these missing dependencies, only to find there already installed.

---

### Post by sgx on 2010-05-23
sometimes an install finds a library or dependancy is a link, not the actual file, or fails to find something that is in /lib instead of /usr/lib, or /usr/local/lib instead of /lib etc, so some sleuthing and linking may be needed. 
Cheers

---

### Post by falkTX on 2010-05-24
> **karl.lensson said:**
> Awsome tut.
tried to get FL on my laptop a while back, it loaded and did nothing.

I finished installing and FL works fine, but after seeing that i could use pulse i tried to get that running. I went to write the following code

[LEFT][PHP]####@####-laptop:~$ sudo apt-get install pulseaudio-module-jack
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pulseaudio-module-jack: Depends: libpulse0 (= 1:0.9.19-0ubuntu4+withjack0) but 1:0.9.19-0ubuntu4.1 is to be installed
                          Depends: pulseaudio (= 1:0.9.19-0ubuntu4+withjack0) but 1:0.9.19-0ubuntu4.1 is to be installed
E: Broken packages
####@####-laptop:~$
[/LEFT]

As u can see it thinks i have missing dependencies, well i try to get these missing dependencies, only to find there already installed.

You're probably using a PPA with mixed old/new packages.
Talk to to PPA author so he can fix that

---

### Post by falkTX on 2010-06-08
Good News!

I've updated the tutorial (1st post), and found a way to get MIDI into FL Studio!

hehe, just needed to enable both Jack and ALSA outputs... :lolflag:

The Patchbay thing was remove since Wine does not auto-connects to output.
pulse-jack and wineasio debs updated too

---

### Post by falkTX on 2010-06-11
> **karl.lensson said:**
> Awsome tut.
tried to get FL on my laptop a while back, it loaded and did nothing.

I finished installing and FL works fine, but after seeing that i could use pulse i tried to get that running. I went to write the following code

[LEFT][PHP]####@####-laptop:~$ sudo apt-get install pulseaudio-module-jack
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pulseaudio-module-jack: Depends: libpulse0 (= 1:0.9.19-0ubuntu4+withjack0) but 1:0.9.19-0ubuntu4.1 is to be installed
                          Depends: pulseaudio (= 1:0.9.19-0ubuntu4+withjack0) but 1:0.9.19-0ubuntu4.1 is to be installed
E: Broken packages
####@####-laptop:~$
[/LEFT]

As u can see it thinks i have missing dependencies, well i try to get these missing dependencies, only to find there already installed.


I have fixed this for u, now creating a new PPA for Jack on Karmic:
```
ppa:falk-t-j/jack4karmic
```

Enjoy!

---

### Post by MiCK.ca on 2010-06-14
Falk my friend , OUTSTANDING work!! My midi (both keyboards) are fully functional and FL Studio is 100% again! It works Exactly like it does under windows...thanks for all your hard work dude!

cheers!

---

### Post by falkTX on 2010-06-15
> **MiCK.ca said:**
> Falk my friend , OUTSTANDING work!! My midi (both keyboards) are fully functional and FL Studio is 100% again! It works Exactly like it does under windows...thanks for all your hard work dude!

cheers!

Thanks!

If you're kind of an advanced user, you can try editing your FL Studio.desktop file and add:
```
chrt -f -p 1 <app>
```

I also have a PPA with Wine compiled with Realtime scheduling (helps you get less xruns on low buffer sizes):
[https://launchpad.net/~falk-t-j/+archive/festige](https://launchpad.net/~falk-t-j/+archive/festige)

Just Add 'WINERT=X' before the wine app, so the final desktop file could look like this:
```
chrt -f -p 1 env WINERT=10 env WINEPREFIX=.....
```

---

### Post by MiCK.ca on 2010-06-15
I'm actually running only a hyper low latency kernel and it has less effect on apps when switching between FL Studio and say Ardour. Ardour runs exceptional with even the hyper low latency and i can keep the same settings in Jack with both apps.

I had some issues with a realtime kernel mainly on the latency side of things. the adjustments to Jack had no effect so switching to a low latency kernel improved overall performance. I have a M-Audio card and it handles things well.

If anyone else is having a issue with "choppy" performance try the low latency kernel that is recommended for Ubuntu Studio. It can be found here: lowlatency kernel is available in Abogani's PPA - [https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")

Havent found a realtime kernel that works as well as the one over at 64Studio but they are still in alpha/beta testing for their karmic/lucid flavour of that distro.

---

### Post by Kellahertz on 2010-06-19
Hey peep this is a great howto, i just installed Ubuntu today and i have FL9 in already :)

One thing i need to know is where to find realtime so i can disable it so i can enable wineasio...

Thanks again folks..

---

### Post by sgx on 2010-06-19
Hi, there is a file in your /home/user folder

.jackdrc

It can be edited, or generated by qjackctl, the gui for jackd
(qjackctl is named 'jack control' is some menus systems)

This qjackctl gui has all the settings boxes, configuration
options, and connections panels to link your hardware and software
in the most creative ways.

In cases where jack2 is installed, I've read where realtime is its
default, and  -rt must be in the .jackdrc to disable realtime

jackd -rt -d alsa -r 44100   (jack2 with realtime disabled

In the normal jackd, you would insert uppercase -RT to enable realtime:

jackd -RT -d alsa -r 44100    (standard jack with realtime enabled)

heres a couple good links

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.64studio.com/manual/audio/jack](http://www.64studio.com/manual/audio/jack)

---

### Post by Cigla on 2010-06-29
[INDENT][/INDENT]First, I wanna say thanks falkTX for this great FL recipe.
I did everything by your 1st post, very clear instructions.

[INDENT][/INDENT]The only thing that didn't work for me is from step 8(not so important), .deb won't install(see pic).My ver of pulseaudio is 1:0.9.19-0ubuntu4.2+withjack2, is that the cause, I should upgrade pulseaudio first?

[INDENT][/INDENT]FL works pretty good, but I still have a lot of those underruns, often delays, happening during playback of more complex songs, like those demo songs that load after installation of FL. 
I observed the Status window of Jack during playback and didn't see any XRUN detected, but I could clearly hear them happen.
So is this problem in Jack at all?
Or is it in Wine?
If it is in Jack, should I try to set Periods/Buffer to higher value(now it is =4)? I would best like if it could be possible to set buffer size to 2048, but that FL can see it. Now it is set to 2048 in Jack, but FL sees only 1024.

[INDENT][/INDENT]But if the problem is not Jack, than I have no idea, so I am asking for some advice.
At this moment I can't do any serious work, not to mention use of vst plugins like Amplitube or Toontrack ez drummer
 
I'm using Karmic, Wine 1.1.31, AMD dual-core, integrated HD sound-card.

---

### Post by Cigla on 2010-06-29
> **Kellahertz said:**
> Hey peep this is a great howto, i just installed Ubuntu today and i have FL9 in already :)

One thing i need to know is where to find realtime so i can disable it so i can enable wineasio...

Thanks again folks..

You can find Realtime in Jack's Setup.

---

### Post by falkTX on 2010-06-29
What do you guys think of a FL Studio in deb?

It should have pre-installed wineasio, alsa midi, and wine with special patches for less xruns.
The mfc42 and ogg codec fix would be included too.


What do you think?

---

### Post by falkTX on 2010-06-29
> **Cigla said:**
> [INDENT][/INDENT]First, I wanna say thanks falkTX for this great FL recipe.
I did everything by your 1st post, very clear instructions.

[INDENT][/INDENT]The only thing that didn't work for me is from step 8(not so important), .deb won't install(see pic).My ver of pulseaudio is 1:0.9.19-0ubuntu4.2+withjack2, is that the cause, I should upgrade pulseaudio first?

[INDENT][/INDENT]FL works pretty good, but I still have a lot of those underruns, often delays, happening during playback of more complex songs, like those demo songs that load after installation of FL. 
I observed the Status window of Jack during playback and didn't see any XRUN detected, but I could clearly hear them happen.
So is this problem in Jack at all?
Or is it in Wine?
If it is in Jack, should I try to set Periods/Buffer to higher value(now it is =4)? I would best like if it could be possible to set buffer size to 2048, but that FL can see it. Now it is set to 2048 in Jack, but FL sees only 1024.

[INDENT][/INDENT]But if the problem is not Jack, than I have no idea, so I am asking for some advice.
At this moment I can't do any serious work, not to mention use of vst plugins like Amplitube or Toontrack ez drummer
 
I'm using Karmic, Wine 1.1.31, AMD dual-core, integrated HD sound-card.

I never tested the pulse-jack thing in Karmic, but you can install the deb this way:
```
sudo dpkg -x pulse-jack*deb /
```

That will extract the deb to the root ("/") of your system, just like you were installing it.
There are no way to uninstall it though, you'll have to do it manually if you regret install...

---

### Post by Cigla on 2010-06-30
I played a little more with Jack's settings to see what happens, tried many combinations, and didn't get anywhere.(At least I finally learned more about Jack)
Then I decided to reread your 1st post, and noticed that I have skipped **turning off smooth stuff** in FL audio setup, guess I thought it was not so important. But I was wrong.
Now I have _much better performance_ of FL. Still have some underruns, but not too annoying.Good enough for preview of patterns and whole song too.
As long as I use just Image-line plugins, everything works like described, but with plugins like ezdrummer or Amplitube, performance is  bad-it can be used only for preparing drum patterns for windows installation of FL. For now. But I hope this will be inproved soon too.
By then, I am happy with this much.
Now I ve decided to give Ardour a chance. For me, FL, Cubase, Nuendo,..are all the same because I use just their basic functions, that can be found in any similar app. If it can use samples from those plugins I already mentioned then I have everything I need(it would be nice-but not crucial, if it could use those plugins installed through Wine, redirected through Jack).
I'm using all these things just for making demos, there will never be a computer substitute for real RnR. So I'll better stick my fingers on guitar more than on keyboard.
Thanks for quick reply, and I'll keep my eyes on this thread in future so we all together come to some improvements.

---

### Post by Hexonica on 2010-07-17
Ive got a bit of a problem on me hands. I followed the guide to installing FL studio through wine and it all worked out well. However, when I tried fiddling around with some of the effects on my 3xOsc channel, I lost all sound whatsoever, even outside of FL studio.

Here are the effects that I was using:

Fruity Reeverb
Fruity Flanger
Fruity Parametric EQ2

Heres the tutorial I was [following.]("http://forum.thegamecreators.com/?m=forum_view&t=116585&b=34")

---

### Post by stalefist on 2010-08-04
hey everyone, new guy here trying to get fl studio running on Lucid..

I can't get past step 2, where am I supposed to be using this code?? I already have wine installed and the alsa and jack boxes checked. any help is much appreciated!

---

### Post by falkTX on 2010-08-04
> **stalefist said:**
> hey everyone, new guy here trying to get fl studio running on Lucid..

I can't get past step 2, where am I supposed to be using this code?? I already have wine installed and the alsa and jack boxes checked. any help is much appreciated!

open a terminal paste it there (menu "apps" -> "accessories" -> "terminal" (or "console"))

---

### Post by stalefist on 2010-08-04
> **falkTX said:**
> open a terminal paste it there (menu "apps" -> "accessories" -> "terminal" (or "console"))

thanks, should i be running it as root or as a normal user??

---

### Post by falkTX on 2010-08-05
> **stalefist said:**
> thanks, should i be running it as root or as a normal user??

ALWAYS normal user for Wine stuff!

do *never* run Wine as root/sudo...
you don't want viruses in your linux system too... dont you?

---

### Post by falkTX on 2010-08-26
Is it just for me or the new FLS 9.1 doesn't work at all?

It just gives me a 'segfault', same thing for 9.5beta.


Does anyone have this issue too?
How does 9.1 works for you?

---

### Post by Totalchaos on 2010-08-27
I am using FL studio 9.1, Works solid rock. I installed it using this how-to, even add the lines  'chrt -f -p 1 env WINERT=10 env' in front of the app-starter (i can't feel the defference). i am using ubuntustudio10.04 with FalkTX-repos, lowlatency kernel and with pulseaudio removed from my system (using "Audiohacks" repository that allows to successfully remove pulseaudio and using alsa instead)

---

### Post by falkTX on 2010-08-27
> **Totalchaos said:**
> I am using FL studio 9.1, Works solid rock. I installed it using this how-to, even add the lines  'chrt -f -p 1 env WINERT=10 env' in front of the app-starter (i can't feel the defference). i am using ubuntustudio10.04 with FalkTX-repos, lowlatency kernel and with pulseaudio removed from my system (using "Audiohacks" repository that allows to successfully remove pulseaudio and using alsa instead)

Good to know,

What is your Wine version?


BTW, the 'WINE_RT' thing only works if you *don't* have the Wine PPA enabled
It only makes difference when you run FLS with small buffer sizes (<=128 )

---

### Post by Totalchaos on 2010-08-27
i am using wine 1.2 from your repository. good to know about the lowlatency sfuff \\:D/ by the way if it matters i started FLstudio with the ordinary, NOT the extended memory icon, if i start with extended memory icon it collapses the program (like in your case)
PS:what happened with your plans of making FLStudio demo to a deb file. if this can help you in my opinion the FLstudio7 was the the most linux friendly edition, i am using 9.1 in my system but i am keeping 64studio 2.1 on a different partition with FL7 on it

---

### Post by falkTX on 2010-08-27
> **Totalchaos said:**
> i am using wine 1.2 from your repository. good to know about the lowlatency sfuff \\:D/ by the way if it matters i started FLstudio with the ordinary, NOT the extended memory icon, if i start with extended memory icon it collapses the program (like in your case)

The 'extended' thing is suppose to give you the possibility to use 3Gb of RAM (since 32bit apps usually have 2Gb RAM limit in windows, afaik)

I have a page explaining the Wine-RT stuff in my page:
[http://kxstudio.sourceforge.net/index.php?option=com_content&view=article&id=56&Itemid=12](http://kxstudio.sourceforge.net/index.php?option=com_content&view=article&id=56&Itemid=12)

---

### Post by Matyas Maa on 2010-09-22
"Error: Dependency is not satisfiable: pulseaudio (>= 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14+withjack2)"

...while trying to install pulse-jack deb. What's wrong?

---

### Post by falkTX on 2010-09-24
> **Matyas Maa said:**
> "Error: Dependency is not satisfiable: pulseaudio (>= 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14+withjack2)"

...while trying to install pulse-jack deb. What's wrong?

Hm... thanks for reporting.
I'll fix this soon (look for a pulse-jack '0.9~ppa5' fixed package, soon)

---

### Post by Matyas Maa on 2010-09-25
Huge thanks to you, falkTX - without your work on this subject I'd probably be forced to use Windows.

---

### Post by jklopez on 2010-09-25
hey whats up people....1st i'm a complete noob to liinux so be gentle...i followed your how to(not easy 4 me) and read all 15 pages of post that followed ,so i installed fl 9 and it's fine just no sound , i'm not sure what i'm doing wrong but i think it's that this step (regsvr32 wineasio.dll) i get (Failed to load DLL wineasio.dll) and i did what the other people did in the post to resolve this but to no avail and i also get the error sometimes that says (failed to create directsound main object) and i did what the other people did to resolve but no dice it didnt work for me and the fact that when i open jack and get three different window that i don't understand and anytime i touch anything i loose all audio and i have to restart my computer holding the power button cuz my power and restart button get greyed out ,other than that everything went good i installed everything else...hopefuly the screen shots will help or if you need me to run a command and post results let me no(post commands as it needs to be run.i don't understand go to ~/\%usr/bin/whatever..lol.)...fl 9 is my only tie to windoze 7....thnx 4 any info...

---

### Post by Pablo_F on 2010-09-26
Divide et impera

You have installed FL studio, right. Now, leave it alone (close it) and solve the basics first.

For starters, you need to register wineasio.dll successfully.

Please give the output of the following informative commands so we can help:

uname -rm

sudo updatedb && locate wineasio (enter the password and wait a bit ....)

wine --version

It will continue...

Cheers! Pablo

---

### Post by falkTX on 2010-09-26
> **jklopez said:**
> hey whats up people....1st i'm a complete noob to liinux so be gentle...i followed your how to(not easy 4 me) and read all 15 pages of post that followed ,so i installed fl 9 and it's fine just no sound , i'm not sure what i'm doing wrong but i think it's that this step (regsvr32 wineasio.dll) i get (Failed to load DLL wineasio.dll) and i did what the other people did in the post to resolve this but to no avail and i also get the error sometimes that says (failed to create directsound main object) and i did what the other people did to resolve but no dice it didnt work for me and the fact that when i open jack and get three different window that i don't understand and anytime i touch anything i loose all audio and i have to restart my computer holding the power button cuz my power and restart button get greyed out ,other than that everything went good i installed everything else...hopefuly the screen shots will help or if you need me to run a command and post results let me no(post commands as it needs to be run.i don't understand go to ~/\%usr/bin/whatever..lol.)...fl 9 is my only tie to windoze 7....thnx 4 any info...

I can see the 'UNION' tag...


No comments

---

### Post by jklopez on 2010-09-27
hey thnx 4 responding,i would have answered earlier but i've been busy...we'll yesterday i got help from a friend that knows a little more than me and we got it working but i could'nt get all of ubuntu to work off jack cuz i think the command is karmic only...i don't know what a power pc is but i have a toshiba satellite with 32 bit lucid(10.04) is it possible ,do i use this repo. or is there a 10.04 only repo.  
    
[SIZE=4]Step 8 (Optional) - Using Jack for ALL applications[/SIZE]
**-- KARMIC --**
As you might know, Jack is not included in the main Ubuntu repos (it's universe; community maintained).
For that reason, most of the important stuff does not have Jack support.
BUT, if you're using karmic (and not PowerPC), there's a PPA containing  the exact same packages available in Ubuntu, but with Jack support  enabled.
If can install all the packages by doing:
 	Code:
 	sudo add-apt-repository ppa:falk-t-j/jack4karmic sudo apt-get update sudo apt-get dist-upgrade sudo apt-get install pulseaudio-module-jack[FONT=Verdana]   [/FONT]

 [FONT=Verdana][/FONT]Download the pulse-jack deb and install it:
[[FONT=Verdana][/FONT]http://ppa.launchpad.net/falk-t-j/lu.../p/pulse-jack/]("http://ppa.launchpad.net/falk-t-j/lucid/ubuntu/pool/main/p/pulse-jack/")[FONT=Verdana]
[/FONT]After Jack starts, you can just do:
 	Code:
 	pulse-jack 
That gives you the possibility of listening to music or playing games while still running FL Studio.

---

### Post by Matyas Maa on 2010-10-02
> **falkTX said:**
> look for a pulse-jack '0.9~ppa5' fixed package, soon

What's up with this? Any progress?

---

### Post by falkTX on 2010-10-03
> **Matyas Maa said:**
> What's up with this? Any progress?

Sorry my laptop is still broken
(why are they taking so long to repair it...? :()

I miss my, crappy, but good laptop...

---

### Post by sgx on 2010-10-03
They are charging you $$$ by the minute :guitar:

---

### Post by proxess on 2010-10-07
This unfortunately isn't working anymore (well, not on Maverick anyway). I think it's something to do with wineasio and jack version. Can someone please compile wineasio 0.8.0 in both 32 and 64 bit versions for Maverick (and Back-Port them too)?

---

### Post by Matyas Maa on 2010-10-10
The new pulse-jack package appeared and now works like a charm!

[SIZE=5]**Huge**[/SIZE] thanks to falkTX!

---

### Post by proxess on 2010-10-10
Hmm I just compiled the latest WineASIO and my problem persists. FL Studio crashes when I change the driver to WineASIO. Guitar Rig doesn't even start. I don't get any error messages, it just stalls.

---

### Post by falkTX on 2010-10-11
> **Matyas Maa said:**
> The new pulse-jack package appeared and now works like a charm!

[SIZE=5]**Huge**[/SIZE] thanks to falkTX!

:)

---

### Post by falkTX on 2010-10-11
> **proxess said:**
> Hmm I just compiled the latest WineASIO and my problem persists. FL Studio crashes when I change the driver to WineASIO. Guitar Rig doesn't even start. I don't get any error messages, it just stalls.

Does 'regsvr32 wineasio.dll' work?

If that doesnt work, nothing else will

---

### Post by proxess on 2010-10-11
regsvr32 wineasio.dll is successful. Its when I change the driver in the application to WineASIO. The applications always crash and never set the driver to Wine ASIO. Also, forcing the driver through regedit doesn't allow FL Studio to even start up.

---

### Post by falkTX on 2010-10-12
> **proxess said:**
> regsvr32 wineasio.dll is successful. Its when I change the driver in the application to WineASIO. The applications always crash and never set the driver to Wine ASIO. Also, forcing the driver through regedit doesn't allow FL Studio to even start up.

I would say you have some problem in Wine or Jack...

can you try installing FL Studio on a new 'Prefix':
```
export WINEPREFIX=$HOME/.wine-fls
wineboot
regsvr32 wineasio.dll
wine <path-to-fl-installer>
wine <path-to_FL.exe>

```

Also make sure Jack is started before using WineASIO and that other apps are able to use Jack Audio/MIDI Properly

---

### Post by proxess on 2010-10-12
I just don't get it. I followed your guide by the book, only difference was that I used wine1.3. I even uninstalled my wineasio and installed yours. Completely deleted all my wine folders and instalation and reinstalled.

Jackd is working, tested my guitar on rakarrack and it worked nicely. I just can't get FL Studio or Guitar Rig to start. They just freeze when I choose wineasio driver.

EDIT: Tried it with wine 1.2, same problem. Tried it with my own build, I get an error in wine saying "there are not enough output ports. At least 2 are required". I've got 2 out and 2 in on the connector, what else does it want...?

---

### Post by falkTX on 2010-10-13
> **proxess said:**
> I just don't get it. I followed your guide by the book, only difference was that I used wine1.3. I even uninstalled my wineasio and installed yours. Completely deleted all my wine folders and instalation and reinstalled.

Jackd is working, tested my guitar on rakarrack and it worked nicely. I just can't get FL Studio or Guitar Rig to start. They just freeze when I choose wineasio driver.

EDIT: Tried it with wine 1.2, same problem. Tried it with my own build, I get an error in wine saying "there are not enough output ports. At least 2 are required". I've got 2 out and 2 in on the connector, what else does it want...?

I've compiled WineASIO 0.8.1:
for 32bit - [http://sourceforge.net/projects/kxstudio/files/DEBs/wineasio_0.8.1_32bit.deb/download](http://sourceforge.net/projects/kxstudio/files/DEBs/wineasio_0.8.1_32bit.deb/download)
for 64bit - [http://sourceforge.net/projects/kxstudio/files/DEBs/wineasio_0.8.1_64bit.deb/download](http://sourceforge.net/projects/kxstudio/files/DEBs/wineasio_0.8.1_64bit.deb/download)

Try these

---

### Post by proxess on 2010-10-13
I'll try your new deb as soon as I get home. Did you compile then with wine-dev 1.2 or wine-dev 1.3? Jack2-dev?

EDIT: Same problem :(

---

### Post by yanni.ilousis on 2010-10-19
I had the same problem when using wineasio 0.7.5 (but with Reaper) and wine 1.3.5.

I bypassed the freezing by installing wineasio 0.8.1 and keep using wine 1.3.5. But, at this time I have no inputs and no outputs, despite of setting 4 inputs and 4 outputs, and test it by writing down (and after by doing restart of gnome session), one time exclusively and one time both, in files *.profile* and *.wineasiocfg*:

```
export ASIO_INPUTS=4
export ASIO_OUTPUTS=4
```

Ubuntu 10.10 64 bit

---

### Post by proxess on 2010-10-19
I didn't try putting it in .profile. I'll do that and give it a try later!

---

### Post by proxess on 2010-10-21
So... I gave that a try, didn't work. Tried the variables in /etc/profile, nothing either. Tried them in /etc/environment and still the same thing.

Jackd (and my guitar) work fine on Rakarrack, tho I don't know how to change the Jackd general volume.

Is it because I've got input on one sound card and output on another? I do this because Jackd doesn't start if I try to use my ESI UGM96, I get an Alsa error saying broken pipe on output, so I just use my gaming headphones for output.

Maybe I should roll back to Lucid? I got it working on Lucid before I upgraded to Maverick, tho it still makes no sense.

---

### Post by granadajose on 2010-10-22
Many many thanks for your tutorial!

---

### Post by davids5a on 2010-11-01
> **eightdollarbeer said:**
> try renaming the .zip to .exe and run it with wine.
and for wineasio
apt-get install wineasio
then 
sudo ln -s /usr/lib32/wine/wineasio.dll.so /usr/lib/wine/wineasio.dll.so
regsvr32 wineasio.dll

should be ok

This doesn't work for me.
I can't get wineasio.dll registered no matter what I do. :(

This is the output of commands Pablo F gave on page 15:

david@david-desktop:~$ uname -rm
2.6.32-25-generic x86_64
david@david-desktop:~$ sudo updatedb && locate wineasio
/home/david/Downloads/wineasio-beta_0.9.0~beta0_32bit.deb
/home/david/Downloads/wineasio-beta_0.9.0~beta0_64bit.deb
/usr/lib32/wine/wineasio.dll.so
/var/lib/dpkg/info/wineasio-beta.list
david@david-desktop:~$ wine --version
wine-1.2

---

### Post by MiCK.ca on 2010-11-14
Hey folks,

been a bit since my last offering but i have been reading the misfortunes of 10.10 users...I did however stumble on something VERY interesting (still using 10.04). I had installed the corporate Nvidia driver for my graphics card a long time back. It began to really flake out and so i rolled back to a regular VESA driver (current version) and the performance of FL Studio shot through the roof!! It runs exactly like it does in Windows....ALL the cool stuff songs load and play without even peaking the CPU meter...in fact it runs at 33-45%!!! 

So if you are running a nvidia driver, try using a VESA or other generic driver and see what that does to your experience.

cheers...off to  tinker with stuff...(BTW is that Pablo from the 64 Studio forum?)

MiCK

---

### Post by Pablo_F on 2010-11-14
> BTW is that Pablo from the 64 Studio forum?

Yep :popcorn:

---

### Post by MiCK.ca on 2010-11-15
Coolness Pablo! good to see you contributing to this little shindig. fun times to be had here at Ubuntu forums...64 studio is seemingly dead in the water....on that note.

Has anyone else found the generic graphics driver to help performance? Perhaps its a key to add to the things to do list when getting FL up and going.:)

---

### Post by ren-hoek on 2010-11-21
I have Ubuntu Studio 10.10 running and like proxess following the tutorial doesn't work. The wineasio reg was succesfull, but I got errors like proxess. I tried some configurations in jack but no result. Then I disabled jack in the wineconfig and deleted wineasio and only enabled alsa in wine. FL is running now. Haven't checked plugins yet and i also think about giving asio4all a try. I will report.
With 10.04 the tutorial worked very well and I like to thank falkTX very much for the work and time on this.

---

### Post by MiCK.ca on 2010-11-22
I know everyone, it's hard to resist the temptation to upgrade to the next newest and baddest Ubuntu. But 10.04 is an LTS and you can **update** the heck out of it and still have the wonderful stability of being able to run FL Studio, Guitar Rig etc. 

Having said that, would i still be running 8.04? NO. because when 12.04 rolls around we'll have another LTS and i'll upgrade then. It really does disappoint when you upgrade and the little things you worked hard to get going crash in the matter of minutes. I can recommend that we'll all stay (those who are running FL Studio) with this stable LTE and keep making great music. All the while tinkering on another partition to better the performance of FL Studio in 10.10, 11.04 etc. 

Just giving a little optimism to the flock...

---

### Post by falkTX on 2010-11-22
> **ren-hoek said:**
> I have Ubuntu Studio 10.10 running and like proxess following the tutorial doesn't work. The wineasio reg was succesfull, but I got errors like proxess. I tried some configurations in jack but no result. Then I disabled jack in the wineconfig and deleted wineasio and only enabled alsa in wine. FL is running now. Haven't checked plugins yet and i also think about giving asio4all a try. I will report.
With 10.04 the tutorial worked very well and I like to thank falkTX very much for the work and time on this.

You should really use WineASIO for audio...

You just have to find a version that works for you.

This is the one I use now:
[https://launchpad.net/~falk-t-j/+archive/lucid-latest/+sourcepub/1362638/+listing-archive-extra](https://launchpad.net/~falk-t-j/+archive/lucid-latest/+sourcepub/1362638/+listing-archive-extra)

---

### Post by proxess on 2010-11-22
> **falkTX said:**
> You should really use WineASIO for audio...

You just have to find a version that works for you.

This is the one I use now:
[https://launchpad.net/~falk-t-j/+archive/lucid-latest/+sourcepub/1362638/+listing-archive-extra](https://launchpad.net/~falk-t-j/+archive/lucid-latest/+sourcepub/1362638/+listing-archive-extra)

That is compiled with Jackd1 and not Jackd2.

To install it I had to use --force-all.

I'll give it a go when I get home (installed via SSH).

---

### Post by falkTX on 2010-11-22
> **proxess said:**
> That is compiled with Jackd1 and not Jackd2.

To install it I had to use --force-all.

I'll give it a go when I get home (installed via SSH).

I actually compiled it with jack2...

but anyway, tell me how it works when you have the chance

---

### Post by proxess on 2010-11-25
> **falkTX said:**
> I actually compiled it with jack2...

but anyway, tell me how it works when you have the chance

You created a dependency on libjack0 when I've got a more recent one, libjack-jackd2-0. Can you compile it on libjack-jackd2-dev please?

---

### Post by ren-hoek on 2010-11-25
> **falkTX said:**
> I actually compiled it with jack2...

but anyway, tell me how it works when you have the chance

Yeah, with this wineasio it works.  Thanks again very much falkTX. But to be honest, on the first view i don't see a big difference in the performance, so maybe someone could explain to me the advantages of using jack+alsa in the wineconf. and wineasio in FL, instead of using only alsa and default driver in FL. Both i have to configure with high latency and even then cool stuff projects run with massive dropouts and a cpu usage sometimes about 90. Own projects work fine, but they are minimalistic compared to the cool stuff.

---

### Post by falkTX on 2010-11-25
> **proxess said:**
> You created a dependency on libjack0 when I've got a more recent one, libjack-jackd2-0. Can you compile it on libjack-jackd2-dev please?

eeeh... it's jut I'm still on Lucid and you're on Maverick...
The code comes from here - [http://repo.or.cz/w/wineasio.git](http://repo.or.cz/w/wineasio.git)
(direct link to download - [http://repo.or.cz/w/wineasio.git/snapshot/3ba0b1a709934558ce96d24f8765fc08eb68f8ec.tar.gz](http://repo.or.cz/w/wineasio.git/snapshot/3ba0b1a709934558ce96d24f8765fc08eb68f8ec.tar.gz))

you'll need asio.h to compile, as usual.


OR,
you can just extract the content of the deb and copy it to /usr/lib/wine (or /usr/lib32/wine on 64bit pcs)

I'm guessing since it was compiled with jack2 (1.9.6), it should work for you without problems.

---

### Post by falkTX on 2010-11-25
> **ren-hoek said:**
> Yeah, with this wineasio it works.  Thanks again very much falkTX. But to be honest, on the first view i don't see a big difference in the performance, so maybe someone could explain to me the advantages of using jack+alsa in the wineconf. and wineasio in FL, instead of using only alsa and default driver in FL. Both i have to configure with high latency and even then cool stuff projects run with massive dropouts and a cpu usage sometimes about 90. Own projects work fine, but they are minimalistic compared to the cool stuff.

This is how I got the best results so far:

1 - Wine audio driver set to ALSA only
2 - FL Studio driver set to WineASIO
3 - Multithread disabled in FL Studio
4 - Use Wine-RT patch ([http://kxstudio.sourceforge.net/index.php?option=com_content&view=article&id=56&Itemid=12](http://kxstudio.sourceforge.net/index.php?option=com_content&view=article&id=56&Itemid=12))
(included in my ppa - [https://launchpad.net/~falk-t-j/+archive/lucid/](https://launchpad.net/~falk-t-j/+archive/lucid/))

then running FL Studio like this:
```
cd /path/to/FLS/install
export WINE_RT=15
export WINE_SVR_RT=10
chrt -f -p 1 wine FL.exe
```

This is a little advanced stuff though...

---

### Post by Totalchaos on 2010-11-30
> **falkTX said:**
> This is how I got the best results so far:

1 - Wine audio driver set to ALSA only
2 - FL Studio driver set to WineASIO
3 - Multithread disabled in FL Studio
4 - Use Wine-RT patch ([http://kxstudio.sourceforge.net/index.php?option=com_content&view=article&id=56&Itemid=12](http://kxstudio.sourceforge.net/index.php?option=com_content&view=article&id=56&Itemid=12))
(included in my ppa - [https://launchpad.net/~falk-t-j/+archive/lucid/]("https://launchpad.net/%7Efalk-t-j/+archive/lucid/"))

then running FL Studio like this:
```
cd /path/to/FLS/install
export WINE_RT=15
export WINE_SVR_RT=10
chrt -f -p 1 wine FL.exe
```This is a little advanced stuff though...

can you convert the code into a single command, that can be executed from a custom launcher, because it will be a lot easier ;)

---

### Post by falkTX on 2010-12-01
> **Totalchaos said:**
> can you convert the code into a single command, that can be executed from a custom launcher, because it will be a lot easier ;)

I'll probably create a script for all this soon...

---

### Post by LuisUK on 2010-12-04
> **falkTX said:**
> eeeh... it's jut I'm still on Lucid and you're on Maverick...
The code comes from here - [http://repo.or.cz/w/wineasio.git](http://repo.or.cz/w/wineasio.git)
(direct link to download - [http://repo.or.cz/w/wineasio.git/snapshot/3ba0b1a709934558ce96d24f8765fc08eb68f8ec.tar.gz](http://repo.or.cz/w/wineasio.git/snapshot/3ba0b1a709934558ce96d24f8765fc08eb68f8ec.tar.gz))

you'll need asio.h to compile, as usual.


OR,
you can just extract the content of the deb and copy it to /usr/lib/wine (or /usr/lib32/wine on 64bit pcs)

I'm guessing since it was compiled with jack2 (1.9.6), it should work for you without problems.

Hello!

First of all, thank you for the HOWTO. 

I'm not using FL Studio, but foobar2000.

I tried to compile wineasio from source, compile succeeded, it registered successfully, but I cannot get it to work.

I can see the Wine Jack DirectSound Driver in the app (foobar2000 in my case), but when I try to play anything, it just freezes and then gives me an error.

I also tried to use the .dll from wineasio-beta_0.9.0~beta0-1+build5_amd64.deb, but I got the same result.

Using jackd 1.9.6 and Wine 1.3.7 under Maverick 64-bit.

I have to downgrade to Jack 1 in order to make it work.

Any ideas what could be wrong?

Thanks in advance,

---

### Post by falkTX on 2010-12-04
> **LuisUK said:**
> Hello!

First of all, thank you for the HOWTO. 

I'm not using FL Studio, but foobar2000.

I tried to compile wineasio from source, compile succeeded, it registered successfully, but I cannot get it to work.

I can see the Wine Jack DirectSound Driver in the app (foobar2000 in my case), but when I try to play anything, it just freezes and then gives me an error.

I also tried to use the .dll from wineasio-beta_0.9.0~beta0-1+build5_amd64.deb, but I got the same result.

Using jackd 1.9.6 and Wine 1.3.7 under Maverick 64-bit.

I have to downgrade to Jack 1 in order to make it work.

Any ideas what could be wrong?

Thanks in advance,


I wonder why this never happens to me...

LuisUK, you're not doing anything wrong. We are just missing something...

Can you try enable jack audio in Wine config, try again, then enable ALSA and re-try?

---

### Post by LuisUK on 2010-12-04
> **falkTX said:**
> I wonder why this never happens to me...

LuisUK, you're not doing anything wrong. We are just missing something...

Can you try enable jack audio in Wine config, try again, then enable ALSA and re-try?

If I enable only ALSA, it will play through pulseaudio-jack.

If I enable only Jack or both Jack and ALSA, and then select Wine Jack DirectSound Driver, playback freezes and foobar will give me an error.

If I try to install wineasio (through Synaptic or GDebi), it removes jack 2 along with most audio programs, and installs jack 1, which (strangely enough) works with wineasio.

I also installed the latest wine ( 1.3.8 ), and tried to recompile jack and wineasio from source, but to no avail. 

I guess that wineasio and jack 2 just won't work for me...

Is there anything else I should try?

---

### Post by Pablo_F on 2010-12-04
I vote for jack1. Jack1 is not a worse jack, neither is obsolete. Don't get fooled by names. It is just a different implementation of jack which by the way is much more tested and more solid in general. Both implementations of jack are under active development. They are different from each other in some details though. If you are curious about this, visit the jackaudio website.

Cheers, Pablo

---

### Post by falkTX on 2010-12-05
> **LuisUK said:**
> If I enable only ALSA, it will play through pulseaudio-jack.

If I enable only Jack or both Jack and ALSA, and then select Wine Jack DirectSound Driver, playback freezes and foobar will give me an error.

If I try to install wineasio (through Synaptic or GDebi), it removes jack 2 along with most audio programs, and installs jack 1, which (strangely enough) works with wineasio.

I also installed the latest wine ( 1.3.8 ), and tried to recompile jack and wineasio from source, but to no avail. 

I guess that wineasio and jack 2 just won't work for me...

Is there anything else I should try?

Jack2 is not the issue. It's just that I'm using Lucid and you're in maverick, so packages sometimes conflict.
And I'm using Jack2 anyway, so I know it works with Jack2.

Can you try a fresh wineprefix?

---

### Post by LuisUK on 2010-12-06
> **falkTX said:**
> Jack2 is not the issue. It's just that I'm using Lucid and you're in maverick, so packages sometimes conflict.
And I'm using Jack2 anyway, so I know it works with Jack2.

Can you try a fresh wineprefix?

Do you mean rm -rf ~/.wine?

Will try that and see if it helps.

---

### Post by falkTX on 2010-12-06
> **LuisUK said:**
> Do you mean rm -rf ~/.wine?

Will try that and see if it helps.

no, I mean this:
```
export WINEPREFIX=~/.wine_test
wineboot
wine <apps>

```
This will create another directory for wine stuff (.wine_test) so you can test things there.
Make sure you always export WINEPREFIX and that you run all apps from that terminal (the one with the 'export')

---

### Post by LuisUK on 2010-12-06
> **falkTX said:**
> no, I mean this:
```
export WINEPREFIX=~/.wine_test
wineboot
wine <apps>

```
This will create another directory for wine stuff (.wine_test) so you can test things there.
Make sure you always export WINEPREFIX and that you run all apps from that terminal (the one with the 'export')

OK, tried that, but it makes no difference. 

I noticed that wineasio depends on libjack0, which conflicts libjack2-0 (the library that installs along with Jack 2).

I managed to make it work by installing jack2_1.9.6+ladifixes3-0 with --force-all, over the existing Jack 2, but I had to remove some dependencies from it.

I also had to remove some dependencies from wineasio 0.9 beta before i could install it.

I know it's not the most elegant solution, but it seemed to do the trick.

Nevertheless, it would be nice to find a way of making it work with the Jack 2 in the official Ubuntustudio repository.

---

### Post by Shintek on 2010-12-07
How is it that you guys have to go through all this trouble?

I just wine installed FL Studio 9.1 and it worked perfectly

Im on Ubuntu 10.10

---

### Post by falkTX on 2010-12-07
> **LuisUK said:**
> OK, tried that, but it makes no difference. 

I noticed that wineasio depends on libjack0, which conflicts libjack2-0 (the library that installs along with Jack 2).

I managed to make it work by installing jack2_1.9.6+ladifixes3-0 with --force-all, over the existing Jack 2, but I had to remove some dependencies from it.

I also had to remove some dependencies from wineasio 0.9 beta before i could install it.

I know it's not the most elegant solution, but it seemed to do the trick.

Nevertheless, it would be nice to find a way of making it work with the Jack 2 in the official Ubuntustudio repository.


Please dont install Lucid packages in Maverick...

You can just extract the content of the debs and install the driver yourself:
```
dpkg -x <some-dir> /path/to/wineasio.deb
```

go into the extracted folder, look for wineasio.so and copy it to the right place (/usr/lib/wine or /usr/lib32/wine)

as simple as that

---

### Post by krazh on 2010-12-08
For me everything works fine [COLOR=Black]now ! [/COLOR](Ubuntu 10.10 32 bits , Fl studio 9.1 )

You have to use jackd1 instead of jackd2 drivers in synaptic installer;

For wineasio use 0.8.1 version : [http://sourceforge.net/projects/kxstudio/files/DEBs/wineasio_0.8.1_32bit.deb/download](http://sourceforge.net/projects/kxstudio/files/DEBs/wineasio_0.8.1_32bit.deb/download)

(wineasio 0.9.0 dont work for my system)


And thanks for the tut ! :KS

---

### Post by gdpt on 2010-12-13
Yes thank you!

---

### Post by proxess on 2010-12-14
I'll be trying that later on then!

---

### Post by proxess on 2010-12-16
Krazh my hero!!! Working like a charm! Input on my UGM96 and output on my Steelseries 7.1!

EDIT: I even got Guitar Rig 4 working very nicely! The only thing I wasn't able to do was use Guitar Rig as a VST in FL Studio. There were no input channels for some reason...

---

### Post by ozno on 2010-12-18
hi i m new to the linux thing and i dont know much plz explain to me where do i have to enter those codes you got in the boxes there? i got a good feeling that your "small" guide on how to install fl studio will help me thank you very much

---

### Post by sgx on 2010-12-18
Hi, you type or copy/paste commands in a terminal window. Some commands
require the root password, using 'sudo', so in ubuntu, type

sudo synaptic   to start the synaptic software installer/uninstaller
and it will ask for your password

or

sudo dpkg -i yoshimi_0.056~autostatic1_i386.deb

to install a downloaded debian software package

linux allows us to command our computers, the giant corporate operating systems cater to a low common denominator of casual users
who prefer not to look under the hood, and tune the engine. If windows had
a terminal on the desktop, there would be chaos in a matter of hours! ;)
Cheers

Check the system menus if there is not a terminal icon on your taskbar or desktop.
gnome-terminal is a nice and full-featured, supports copy/paste from the other apps

---

### Post by proxess on 2011-01-03
Still haven't figured out how to use Guitar Rig as a VST. Anyone else use a wine app as a vst in another wine app?

---

### Post by falkTX on 2011-01-03
> **proxess said:**
> Still haven't figured out how to use Guitar Rig as a VST. Anyone else use a wine app as a vst in another wine app?

I did, several VSTs in the Windows version of Renoise.

'VSTHost' is a nice host/tool for usage and testing, you should try it:
[http://www.hermannseib.com/english/vsthost.htm](http://www.hermannseib.com/english/vsthost.htm)

just start the app, and load some Windows VSTs

---

### Post by JoseSalgado on 2011-01-17
Thank you very-very-very much for this tutorial, I thought it was impossible, thanks for the research and the time invested.

Ubuntu forums and people rock!

---

### Post by crazydudearam on 2011-01-26
First I want to that everybody in this thread for such a useful source of information. Almost everything is working now =)

But, I'm sorry guys I still don't have midi working. It's the whole reason I need to use FL (midi recorder that also records sustain pedal as midi).

I followed the entire first post exactly until the midi section and then followed the midi section. But i can get Qsynth working through jack but not FL.

---

### Post by sgx on 2011-01-26
> **crazydudearam said:**
> First I want to that everybody in this thread for such a useful source of information. Almost everything is working now =)

But, I'm sorry guys I still don't have midi working. It's the whole reason I need to use FL (midi recorder that also records sustain pedal as midi).

I followed the entire first post exactly until the midi section and then followed the midi section. But i can get Qsynth working through jack but not FL.
I see more things need to have

a2jmidid

installed, and the command run after jackd is running, it puts
ports in the midi tab of qjackctl connect panel.

also on the right of the main qjackctl screen, I tick

x unlock memory
x softmode

and raise the timeout m/sec to 1000 or 2000

This seems to help the windows apps that can be less stable, especially
synthedit plugins. Not scientifically, but musically proven.

I would try Reaper also, it is quite stable, basic midi works, I have not
done midi editing, just i/o, worth a shot!

---

### Post by sgx on 2011-01-26
> **proxess said:**
> Still haven't figured out how to use Guitar Rig as a VST. Anyone else use a wine app as a vst in another wine app?
For guitar rig, I painstakingly found all its windows files, and copied
them to their .wine equivalents. There may be an install log in your
windows FLS setup, or just search function the word Native, and then guitar, should be about 5 locations as I recall, a few will wind up in
/home/username I have done regular NI installs on linux, they do work,
Kontakt crashes sometimes, but the Reaktor, Absynth, Massive, FM8, GR3/4
all chortle about nicely! I use Reaper as the vst host, should work in FLS too

I see more things need to have

a2jmidid

installed, and the command run after jackd is running, it puts
ports in the midi tab of qjackctl connect panel.

also on the right of the main qjackctl screen, I tick

x unlock memory
x softmode

and raise the timeout m/sec to 1000 or 2000

This seems to help the windows apps that can be less stable, especially
synthedit plugins. Not scientifically, but musically proven.
Cheers

---

### Post by sgx on 2011-01-26
> **crazydudearam said:**
> First I want to that everybody in this thread for such a useful source of information. Almost everything is working now =)

But, I'm sorry guys I still don't have midi working. It's the whole reason I need to use FL (midi recorder that also records sustain pedal as midi).

I followed the entire first post exactly until the midi section and then followed the midi section. But i can get Qsynth working through jack but not FL.
I would look up Phenome soundfont player (8 layers, and synth knobs)
and the SafFron  soundfont player by Fretted Synth (a fine multi-fx section)
Both are free. I have used them in wine with Reaper as host.
Cheers

---

### Post by crazydudearam on 2011-01-26
Thanks for the suggestion. I may try it later but i really came back to say that I got it working. Somehow, i feel no latency WHATSOEVER, using the wineasio driver, with jack unchecked in the wine audio preferences (allows me to see the alsa midi in FL which for some reason doesn't work with both alsa and jack checked) but i must still keep jack running. Everything is working perfectly Thank you so much for all of your help =)

EDIT: Sorry I was wrong, once again. I think all I had to do was restart because apparently it's working now with jack checked as well =)

---

### Post by sgx on 2011-01-26
Great to hear it's working. These free but excellent softwares
are not made by folks in the same building, perhaps not the
same continents, or languages, so it is upon us as users to be
nimble, and when things suddenly work differently, to work together
in the sharing of solutions, and appreciative of the authors who
create software, and those hosting PPAs, and creating packages that
are easy to install. :guitar:

---

### Post by proxess on 2011-02-02
I'd like to add a little something to the guide for Maverick:

1) Install jackd-1, not jackd-2.


2) Find /etc/pulse/client.conf, and where it says
```
; autospawn = ...
```
and edit it to
```
autospawn = no
```


3) Add to your startup applications an application called "Pulse Audio" which runs the command
```
pulseaudio
```


4) In qjackctl "JACK Control", in "Setup", "Options", in the option that says "Execute script on Startup", add the command
```
pulseaudio -k
```
and in the option that says "Execute script on Shutdown", add the command
```
pulseaudio &
```


This will help avoid messages/problems with pulseaudio and JACK.

---

### Post by pepsifx357 on 2011-02-12
Is there a way to get more than just two outputs from FL studio.  That way I can record each instrument into its own track in ardour.

Thanks.

---

### Post by proxess on 2011-02-15
Have you tried multiple FL Studio sessions? Or do you mean each channel a different output?

---

### Post by mr.thraz on 2011-02-26
well after installing wine rt i find I'm getting better results launching with:

```
chrt -f -p 98 env WINE_RT=18 WINE_SRV_RT=18 WINEPREFIX="/home/mrthraz/.wine" wine C:\\windows\\command\\start.exe /Unix /home/mrthraz/.wine/dosdevices/c:/users/mrthraz/Start\ Menu/Programs/Image-Line/FL\ Studio\ 9/FL\ Studio\ 9\ \(extended\ memory\).lnk
```

---

### Post by MiCK.ca on 2011-03-30
Going to attempt a full install with addons of FL STUDIO 10!!! I have Hardcore, Sawer and Toxic  addons...all worked great with 9...will update as soon as I get this installed and tested...using the same install tuts as Falk did for 9...ALSO using KORG midi board....

keep all of you posted as time goes by...

---

### Post by MiCK.ca on 2011-03-31
****UPDATE****

All is well!!! everything is working! FL Studio 10 on Tango Studio is working! this rocks!!

---

### Post by MiCK.ca on 2011-04-23
Further update: Purchased a couple more plugins from Image-Line. install went flawless. All work as expected. Programs runs excellent with or without Jack started. I have the Primary sound device selected in audio setup.

Note: On the install of FL Studio 10 there were no error messages during install as there were with FLS 9.

---

### Post by sgx on 2011-04-24
> **mr.thraz said:**
> well after installing wine rt i find I'm getting better results launching with:

```
chrt -f -p 98 env WINE_RT=18 WINE_SRV_RT=18 WINEPREFIX="/home/mrthraz/.wine" wine C:\\windows\\command\\start.exe /Unix /home/mrthraz/.wine/dosdevices/c:/users/mrthraz/Start\ Menu/Programs/Image-Line/FL\ Studio\ 9/FL\ Studio\ 9\ \(extended\ memory\).lnk
```
Wow, you should start work on lotto numbers! You/ve definitely got the chops :guitar:  Charley Sheen calls out, "Winning!" :)

---

### Post by sgx on 2011-04-24
> **MiCK.ca said:**
> Further update: Purchased a couple more plugins from Image-Line. install went flawless. All work as expected. Programs runs excellent with or without Jack started. I have the Primary sound device selected in audio setup.

Note: On the install of FL Studio 10 there were no error messages during install as there were with FLS 9.
Pretty amazing! Do you have Sytrus? I tried the demo awhile back,
and loved the pure and energized sounds. Hoping it comes down in price,
or gets included in one of the lesser FLS bundles someday. :)
Cheers

---

### Post by MiCK.ca on 2011-04-24
Yes i do have Sytrus. as well as Maximus, Hardcore and Poizone and probably 12 other. I purchased the signature bundle plugins back in FL Studio 8. (at the time it was known as XXL edition upgrade) now its just signature edition. plus the Juice Pack. All work well. No problems. Fl Studio 10 is very solid and stable on any Ubuntu based system. I use Tango Studio because IT has NO PULSE AUDIO!

---

### Post by Samuel Bauman on 2011-04-27
First of all, I'm really new to Ubuntu... Just letting you guys know. But so far, I love Ubuntu, and the Ubuntu community and support is great.

I own FL Studio 10 and use it alot on Windows XP, so I tried the tutorial to install it on Ubuntu. I almost completed everything until I got to Step 4 about setting up Jack. It says Jack Control will be available in apps -> Multimedia... Where exactly does it mean? I looked under the Applications menu and found no 'Multimedia' or 'Jack Control'.

UPDATE: Nevermind. It's called Sound & Video not multimedia. But I am still having a tough time getting the sounds to work in FL Studio 10. 

Help please?

---

### Post by sgx on 2011-04-28
Hi, find the qjackctl wiki, there are several good links with screenshots and info, then in youtube, searching for ardour, hydrogen, qjackctl, and ubuntu studio, will give useful video tutorials. Also,
since reaper is popular with wineasio users, most of the wine/linux configuration info in those topics will also apply to FLS.
Cheers
after installing wineasio, run this command:

regsvr32 wineasio.dll

then choose wineasio in the preferences of FLS. If FLS does not
autoconnect in qjackctl, you just highlite the choice on
each of the two panels, and press 'connect'. Screenshots will
clarify my rambles :wink:

---

### Post by shaneo1 on 2011-05-02
Hi guys,

I have been scratching my head for a while over this problem I have with FL9 running wineasio 0.9.0 64bit with jackd2 and Qjackctrl.

When ever I move away from FL9 the connection disappears from Qjackctrl Connects and when I go back to FL9 it reappears again.  It works great apart from that little bug.

Is there any way on this gods green earth when I move away from FL9 it will stay in the jack connections window so I can port it through to say Ardour etc..

I am using Ubuntu 11.04, with Gnome Shell, have Jackd 2 wine 1.3 and wineasio 0.9.0 64bit.

I also had this issue with 10.10, jackd 1 and wine 1.2, with wineasio 0.7.4..... though one time it used to work, now it don't, I have no idea how I made it work all I know now that it doesn't.

This is my Jack outout when started:

```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]=256.[/COLOR]
 [COLOR=#999999]16:07:28.372 Startup script...[/COLOR]
 [COLOR=#990099]16:07:28.372 artsshell -q terminate[/COLOR]
 [COLOR=#990099]sh: artsshell: not found[/COLOR]
 [COLOR=#999999]16:07:28.777 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]16:07:28.777 JACK is starting...[/COLOR]
 [COLOR=#990099]16:07:28.778 /usr/bin/jackd -r -dalsa -dhw:2 -r44100 -p1024 -n4 -s -S[/COLOR]
 [COLOR=#990099]jackd 0.120.1[/COLOR]
 [COLOR=#990099]Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.[/COLOR]
 [COLOR=#990099]jackd comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#990099]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#990099]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#990099]Memory locking is unlimited - this is dangerous. You should probably alter the line:[/COLOR]
 [COLOR=#990099]     @audio   -  memlock    unlimited[/COLOR]
 [COLOR=#990099]in your /etc/limits.conf to read:[/COLOR]
 [COLOR=#990099]     @audio   -  memlock    3042318[/COLOR]
 [COLOR=#999999]16:07:28.792 JACK was started with PID=11605.[/COLOR]
 [COLOR=#999999]JACK compiled with System V SHM support.[/COLOR]
 [COLOR=#999999]loading driver ..[/COLOR]
 [COLOR=#999999]SSE2 detected[/COLOR]
 [COLOR=#999999]apparent rate = 44100[/COLOR]
 [COLOR=#999999]creating alsa driver ... hw:2|hw:2|1024|4|44100|0|0|nomon|swmeter|soft-mode|16bit[/COLOR]
 [COLOR=#999999]control device hw:2[/COLOR]
 [COLOR=#999999]ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode[/COLOR]
 [COLOR=#999999]configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 4 periods[/COLOR]
 [COLOR=#999999]ALSA: final selected sample format for playback: 16bit little-endian[/COLOR]
 [COLOR=#999999]ALSA: use 4 periods for playback[/COLOR]
 [COLOR=#9999cc]16:07:30.899 JACK connection change.[/COLOR]
 [COLOR=#999933]16:07:30.900 Server configuration saved to "/home/shane/.jackdrc".[/COLOR]
 [COLOR=#999999]16:07:30.900 Statistics reset.[/COLOR]
 [COLOR=#999999]16:07:30.902 Client activated.[/COLOR]
 [COLOR=#996633]16:07:30.905 Buffer size change (0).[/COLOR]
 [COLOR=#996633]SSE2 detected[/COLOR]

```

This also happens when using just primary direct driver settings, is there something in wine that could be the issue???

Any Ideas would be great, thanks in advance peeps.

Shane :guitar:

---

### Post by falkTX on 2011-05-02
> **shaneo1 said:**
> Hi guys,

I have been scratching my head for a while over this problem I have with FL9 running wineasio 0.9.0 64bit with jackd2 and Qjackctrl.

When ever I move away from FL9 the connection disappears from Qjackctrl Connects and when I go back to FL9 it reappears again.  It works great apart from that little bug.


This is an option in FL Studio (auto-close audio device).
Uncheck that option and restart FLS

---

### Post by shaneo1 on 2011-05-02
Haha, thanks :D  don't I feel silly now :)  your a :KS

Cheers

---

### Post by neu2buntu on 2011-05-13
for me i had no startup sound using flstudio 10 in ubuntu through jack, so to fix goto ~/.wine/drive_c/Program Files/Image-Line/FL Studio 10/Artwork/Skins/Default and open the "StartSnd.wav" with audacity, choose export (saving over the top of the original file), then in the metadat editor , then remove the value " vorbis.acm " from the ENCODER tag.  any audio metadata editor could probably be used ;)

---

### Post by DarkTide on 2011-05-15
I just have a problem when I try to run FL Studio with jack in real-time  (I have UbuntuStudio9.04, with real-time kernel configured and working  fine with other apps).

I launch Jack with the real-time option checked and it starts normally  but when I start FLStudio9, it appears in the qjackctl connections'  window and then suddently disappears...

> fixme:win:RegisterDeviceNotificationW (hwnd=0x147f48, filter=0x93ea28,flags=0x00000001),
    returns a fake device notification handle!
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8da, disabling mixer
fixme:win:LockWindowUpdate (0x2003a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:bitblt:client_side_dib_copy potential optimization: pixel format conversion
jack_client_thread zombified - exiting from JACK
fixme:xrender:X11DRV_AlphaBlend not a 32 bpp dibsection
^Cfixme:xrender:X11DRV_AlphaBlend not a 32 bpp dibsection
^Cfixme:asio:DllCanUnloadNow (void): stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:asio:DllCanUnloadNow (void): stub

---

### Post by binfacto on 2011-05-27
Followed everything to the t. Launching FL Studio with wineasio as the audio device I get this error:

Error while creating the ASIO driver.

I think I've just got the wrong combination of 64bit software...

Ubuntu 11.04 64bit, wineasio 64bit, this could be causing the issues...

Looking into 64bit Jack Server, no idea where I'm going with this.

Uninstalled jackd and attempting to install latest version of Jack2...

Jack2 installed, reinstalled qjackctl and everything is peachy.... for now...
```

 p, li { white-space: pre-wrap; }  [COLOR=#999999]15:52:11.305 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]15:52:11.306 Statistics reset.[/COLOR]
 [COLOR=#cccc99]15:52:11.313 ALSA connection change.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]15:52:11.321 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]15:52:12.497 JACK is starting...[/COLOR]
 [COLOR=#990099]15:52:12.498 /usr/bin/jackd -r -dalsa -r44100 -p1024 -n4 -s -S -D -Chw:0 -Phw:0[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 no message buffer overruns
 [COLOR=#999999]15:52:12.523 JACK was started with PID=9317.[/COLOR]
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2011 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in non-realtime mode
 control device hw:0
 control device hw:0
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|1024|4|44100|0|0|nomon|swmeter|soft-mode|16bit
 control device hw:0
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 4 periods
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: use 4 periods for capture
 ALSA: final selected sample format for playback: 16bit little-endian
 ALSA: use 4 periods for playback
 Clock source : system clock via clock_gettime
 [COLOR=#9999cc]15:52:14.587 JACK connection change.[/COLOR]
 [COLOR=#999933]15:52:14.588 Server configuration saved to "/home/c0d3/.jackdrc".[/COLOR]
 [COLOR=#999999]15:52:14.589 Statistics reset.[/COLOR]
 [COLOR=#999999]15:52:14.603 Client activated.[/COLOR]
 [COLOR=#cc9966]15:52:14.662 JACK connection graph change.[/COLOR]
 Clock source : system clock via clock_gettime
 [COLOR=#66cc99]15:52:18.118 ALSA connection graph change.[/COLOR]
 [COLOR=#cc9966]15:52:18.176 JACK connection graph change.[/COLOR]
 [COLOR=#9999cc]15:52:18.236 JACK connection change.[/COLOR]
 JackEngine::XRun: client = FL was not run: state = 2
 JackAudioDriver::ProcessGraphAsync: Process error
 [COLOR=#cc66cc]15:52:18.502 XRUN callback (1).[/COLOR]
 JackEngine::XRun: client = FL was not run: state = 1
 JackAudioDriver::ProcessGraphAsync: Process error
 JackEngine::XRun: client = FL was not run: state = 1
 JackAudioDriver::ProcessGraphAsync: Process error
 [COLOR=#cc99cc]15:52:18.638 XRUN callback (2 skipped).[/COLOR]
 JackEngine::XRun: client = FL was not run: state = 1
 JackAudioDriver::ProcessGraphAsync: Process error
 JackEngine::XRun: client = FL was not run: state = 1
 JackAudioDriver::ProcessGraphAsync: Process error
 JackEngine::XRun: client = FL was not run: state = 1
 JackAudioDriver::ProcessGraphAsync: Process error
 JackEngine::XRun: client = FL was not run: state = 1
 JackAudioDriver::ProcessGraphAsync: Process error
 JackEngine::XRun: client = FL was not run: state = 1
 JackAudioDriver::ProcessGraphAsync: Process error
 JackEngine::XRun: client = FL was not run: state = 1
 JackAudioDriver::ProcessGraphAsync: Process error
 [COLOR=#cc9966]15:52:19.195 JACK connection graph change.[/COLOR]
 [COLOR=#9999cc]15:52:19.240 JACK connection change.[/COLOR]
 [COLOR=#cc9966]15:52:19.290 JACK connection graph change.[/COLOR]
 [COLOR=#9999cc]15:52:19.442 JACK connection change.[/COLOR]
 [COLOR=#cc99cc]15:52:20.646 XRUN callback (5 skipped).[/COLOR]

```Next step to reduce error messages and get Akai APK Mini MIDI controller working.

Edit:
The system I'm working with is an ASUS G73j.

---

### Post by sgx on 2011-05-27
Those achieving success can help others purchase wisely by mentioning your sound and video card, motherboard chipset, and cpu.
It gets to the search engines quickly :o
Cheers

---

### Post by korgx9 on 2011-06-02
Hi
I just have installed FL Studio 10 on ubuntu 11.04. 
After installation it successfully runed, but when I changed sound driver to asio it got some error messages.
Winasio cannot be load.. also after these messages it doesn't runs any more and it is splash icon still on my desktop :). I followed this tutorial step by step.. but it seems i did something wrong. 
exception that i got is 
EExternalException in module ntdl.dll at 0002e198/
External exception C00000025 

After first Error I reinstalled FLStudio and started this Tutorial from begin. But I got the same error again.. 
Please, who knows what is my problem, HELP ME !!!:(:D

---

### Post by liquip on 2011-06-03
Hey korgx9, do you get "Error while creating the ASIO driver.", when running FL in a virtual Windows desktop? ( Wine>Configure Wine, and check the "Emulate a virtual desktop" in the Graphics tab. )

---

### Post by korgx9 on 2011-06-03
Yes in virtual desktop the same behavior.
I think problem with qjackc... in message I got can not allocate memory
when I just run FL studio with started qjackctl server immediately got error  
Error while creating the ASIO driver

---

### Post by liquip on 2011-06-03
korgx9: To overcome that "Error while creating the ASIO driver" I did what binfacto suggested and it worked. First I uninstalled qjackctl and jackd, then compiled and installed jack-1.9.7, reinstalled qjackctl and it started working!

binfacto: I'm trying to get my mpk-mini work with FL too :D (32-bit system), so could you please report if you find a way to get it working :).

---

### Post by korgx9 on 2011-06-06
> **liquip said:**
> korgx9: To overcome that "Error while creating the ASIO driver" I did what binfacto suggested and it worked. First I uninstalled qjackctl and jackd, then compiled and installed jack-1.9.7, reinstalled qjackctl and it started working!

binfacto: I'm trying to get my mpk-mini work with FL too :D (32-bit system), so could you please report if you find a way to get it working :).
Liquip:
I removed jackd and qjackctl was removed automaticly. After I installed jack-1.9.7. 
I downloaded it from [http://www.grame.fr/~letz/jack-1.9.7.tar.bz2](http://www.grame.fr/~letz/jack-1.9.7.tar.bz2) .
Then I did this 3 step
./waf configure
./waf build
./waf install

but unfortunately wasn't successful for me!

My machine details:
ubuntu 11.04 (natty)
Kernel Linux 2.6.38-8-generic
GNOME 2.32.1
Memory 2gb :)
Processor core 2 cpu 6400 2.13 ghz 
maybe this info will help :D

---

### Post by Pablo_F on 2011-06-06
korgx, 

Please, install qjackctl and jackd again and show the terminal outputs of these informative commands:

jackd --version
ulimit -r -l

Cheers, Pablo

---

### Post by korgx9 on 2011-06-07
Hi Pablo,
these the output of commands above:
:~$ jackd --version
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
jackdmp version 1.9.7 tmpdir /dev/shm protocol 8
-------------------------------------------------------------------
real-time priority              (-r) 0
max locked memory       (kbytes, -l) 64

---

### Post by Pablo_F on 2011-06-07
Hi, 

So you have to give your user memlock and rtprio privileges (the "couldn't allocate memory" message has to do with this). You don't need to compile jackd 1.9.7 as you already have it installed. In a terminal:

**sudo dpkg-reconfigure -p high jackd2**

Choose YES (TAB key).

And then add your user to the audio group:

**sudo adduser your_user_name audio**

Reboot the computer and try again.

---

### Post by korgx9 on 2011-06-08
Thanks for everyone who helps me!

Pablo_F I reconfigured jackd2 and added my user name to group audio. After that my FL Studio starts normally without crashes when I choose WineAsio driver. But it still doesn't works. I opened Qjackctl and read messages.
 p, li { white-space: pre-wrap; }  [COLOR=#999999]10:02:05.813 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]10:02:05.819 Statistics reset.[/COLOR]
 [COLOR=#cccc99]10:02:05.844 ALSA connection change.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]10:02:05.851 ALSA connection graph change.[/COLOR]
Then I tried to run it manually 
---------------------------------------------
 p, li { white-space: pre-wrap; }  [COLOR=#999999]10:06:17.186 JACK is starting...[/COLOR]
 [COLOR=#990099]10:06:17.187 /usr/local/bin/jackd -v -r -dalsa -dhw:0 -r44100 -p1024 -n4 -s -S[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server socket[/COLOR]
 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]
 [COLOR=#999999]Unknown driver "alsa"[/COLOR]
 [COLOR=#999999]jackdmp 1.9.7[/COLOR]
 [COLOR=#999999]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=#999999]Copyright 2004-2011 Grame.[/COLOR]
 [COLOR=#999999]jackdmp comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#999999]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#999999]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#999999]10:06:17.252 JACK was started with PID=2491.[/COLOR]
 [COLOR=#999999]10:06:17.289 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]10:06:19.379 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server socket[/COLOR]
 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]
[COLOR=Black]So there one message [/COLOR][COLOR=#999999]Unknown driver "alsa". [COLOR=Black]In settings I found jackd use driver alsa.... and I changed it to dummy [/COLOR][/COLOR][COLOR=Black][/COLOR]

then jackd started normally
here messages: [COLOR=#999999]10:09:35.624 JACK is starting...[/COLOR] 
[COLOR=#990099]10:09:35.624 /usr/local/bin/jackd -v -r -ddummy -r44100 -p1024[/COLOR] 
[COLOR=#990099]Cannot connect to server socket err = No such file or directory[/COLOR] 
[COLOR=#990099]Cannot connect to server socket[/COLOR] 
[COLOR=#990099]jack server is not running or cannot be started[/COLOR] 
[COLOR=#999999]10:09:35.656 JACK was started with PID=2521.[/COLOR] 
[COLOR=#999999]jackdmp 1.9.7[/COLOR] 
[COLOR=#999999]Copyright 2001-2005 Paul Davis and others.[/COLOR] 
[COLOR=#999999]Copyright 2004-2011 Grame.[/COLOR] 
[COLOR=#999999]jackdmp comes with ABSOLUTELY NO WARRANTY[/COLOR] 
[COLOR=#999999]This is free software, and you are welcome to redistribute it[/COLOR] 
[COLOR=#999999]under certain conditions; see the file COPYING for details[/COLOR] 
[COLOR=#999999]JACK server starting in non-realtime mode[/COLOR] 
[COLOR=#999999]Jack: Create non RT thread[/COLOR] 
[COLOR=#999999]Jack: ThreadHandler: start[/COLOR] 
[COLOR=#999999]Jack: JackDriver::Open capture_driver_name = dummy[/COLOR] 
[COLOR=#999999]Jack: JackDriver::Open playback_driver_name = dummy[/COLOR] 
[COLOR=#999999]Jack: Check protocol client 8 server = 8[/COLOR] 
[COLOR=#999999]Jack: JackEngine::ClientInternalOpen: name = system[/COLOR] 
[COLOR=#999999]Jack: JackEngine::AllocateRefNum ref = 0[/COLOR] 
[COLOR=#999999]Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0[/COLOR] 
[COLOR=#999999]Jack: JackEngine::NotifyAddClient: name = system[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::SetBufferSize size = 1024[/COLOR] 
[COLOR=#999999]Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0[/COLOR] 
[COLOR=#999999]Jack: JackDriver::SetupDriverSync driver sem in flush mode[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::SetBufferSize size = 1023[/COLOR] 
[COLOR=#999999]Jack: JackSocketServerChannel::Open[/COLOR] 
[COLOR=#999999]Jack: Bind: addr.sun_path /dev/shm/jack_default_1000_0[/COLOR] 
[COLOR=#999999]Jack: JackSocketServerChannel::BuildPoolTable size = 1[/COLOR] 
[COLOR=#999999]Jack: JackEngine::Open[/COLOR] 
[COLOR=#999999]Jack: Connect: addr.sun_path /dev/shm/jack_default_1000_0[/COLOR] 
[COLOR=#999999]Jack: JackEngine::ClientInternalOpen: name = freewheel[/COLOR] 
[COLOR=#999999]Jack: JackEngine::AllocateRefNum ref = 1[/COLOR] 
[COLOR=#999999]Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_freewheel val = 0[/COLOR] 
[COLOR=#999999]Jack: JackEngine::NotifyAddClient: name = freewheel[/COLOR] 
[COLOR=#999999]Jack: JackConnectionManager::DirectConnect first: ref1 = 1 ref2 = 1[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 1 ref2 = 1[/COLOR] 
[COLOR=#999999]Jack: JackDriver::SetupDriverSync driver sem in flush mode[/COLOR] 
[COLOR=#999999]Jack: JackAudioDriver::Attach fBufferSize = 1023 fSampleRate = 44100[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::AllocatePortAux port_index = 1 name = system:capture_1 type = 32 bit float mono audio[/COLOR] 
[COLOR=#999999]Jack: JackConnectionManager::AddOutputPort ref = 0 port = 1[/COLOR] 
[COLOR=#999999]Jack: JackAudioDriver::Attach fCapturePortList[i] port_index = 1[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::AllocatePortAux port_index = 2 name = system:capture_2 type = 32 bit float mono audio[/COLOR] 
[COLOR=#999999]Jack: JackConnectionManager::AddOutputPort ref = 0 port = 2[/COLOR] 
[COLOR=#999999]Jack: JackAudioDriver::Attach fCapturePortList[i] port_index = 2[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::AllocatePortAux port_index = 3 name = system:playback_1 type = 32 bit float mono audio[/COLOR] 
[COLOR=#999999]Jack: JackConnectionManager::AddInputPort ref = 0 port = 3[/COLOR] 
[COLOR=#999999]Jack: JackAudioDriver::Attach fPlaybackPortList[i] port_index = 3[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::AllocatePortAux port_index = 4 name = system:playback_2 type = 32 bit float mono audio[/COLOR] 
[COLOR=#999999]Jack: JackConnectionManager::AddInputPort ref = 0 port = 4[/COLOR] 
[COLOR=#999999]Jack: JackAudioDriver::Attach fPlaybackPortList[i] port_index = 4[/COLOR] 
[COLOR=#999999]Jack: Clock source : system clock via clock_gettime[/COLOR] 
[COLOR=#999999]Jack: JackServer::Start[/COLOR] 
[COLOR=#999999]Jack: JackThreadedDriver::Start[/COLOR] 
[COLOR=#999999]Jack: Create non RT thread[/COLOR] 
[COLOR=#999999]Jack: ThreadHandler: start[/COLOR] 
[COLOR=#999999]Jack: Create non RT thread[/COLOR] 
[COLOR=#999999]Jack: ThreadHandler: start[/COLOR] 
[COLOR=#999999]Jack: JackSocketServerChannel::ClientCreate socket[/COLOR] 
[COLOR=#999999]Jack: JackSocketServerChannel::BuildPoolTable size = 2[/COLOR] 
[COLOR=#999999]Jack: fSocketTable i = 1 fd = 5[/COLOR] 
[COLOR=#999999]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#999999]Jack: JackRequest::Notification[/COLOR] 
[COLOR=#999999]Jack: JackEngine::NotifyClient: no callback for event = 4[/COLOR] 
[COLOR=#999999]Jack: JackEngine::NotifyClient: no callback for event = 4[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::RecalculateLatency port_index = 3[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::RecalculateLatency port_index = 4[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::RecalculateLatency port_index = 3[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::RecalculateLatency port_index = 4[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::RecalculateLatency port_index = 1[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::RecalculateLatency port_index = 2[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::RecalculateLatency port_index = 1[/COLOR] 
[COLOR=#999999]Jack: JackGraphManager::RecalculateLatency port_index = 2[/COLOR] 
[COLOR=#9999cc]10:09:37.844 JACK connection change.[/COLOR] 
[COLOR=#999933]10:09:37.845 Server configuration saved to "/home/kishvar/.jackdrc".[/COLOR] 
[COLOR=#999999]10:09:37.846 Statistics reset.[/COLOR] 
[COLOR=#999999]10:09:37.867 Client activated.[/COLOR] 
[COLOR=#cc9966]10:09:37.900 JACK connection graph change.[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: JackSocketServerChannel::ClientCreate socket[/COLOR] 
[COLOR=#cc9966]Jack: JackSocketServerChannel::BuildPoolTable size = 3[/COLOR] 
[COLOR=#cc9966]Jack: fSocketTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: fSocketTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: Poll client error err = Success[/COLOR] 
[COLOR=#cc9966]Jack: JackSocketServerChannel::ClientKill ref = -1[/COLOR] 
[COLOR=#cc9966]Jack: Client was not opened : probably correspond to server_check[/COLOR] 
[COLOR=#cc9966]Jack: JackClientSocket::Close[/COLOR] 
[COLOR=#cc9966]Jack: JackSocketServerChannel::ClientCreate socket[/COLOR] 
[COLOR=#cc9966]Jack: JackSocketServerChannel::BuildPoolTable size = 3[/COLOR] 
[COLOR=#cc9966]Jack: fSocketTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: fSocketTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: JackRequest::ClientCheck[/COLOR] 
[COLOR=#cc9966]Jack: Check protocol client 8 server = 8[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: JackRequest::ClientOpen[/COLOR] 
[COLOR=#cc9966]Jack: JackSocketServerChannel::ClientAdd[/COLOR] 
[COLOR=#cc9966]Jack: JackEngine::ClientExternalOpen: uuid = 0, name = qjackctl [/COLOR] 
[COLOR=#cc9966]Jack: JackEngine::AllocateRefNum ref = 2[/COLOR] 
[COLOR=#cc9966]Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_qjackctl val = 0[/COLOR] 
[COLOR=#cc9966]Jack: JackSocketNotifyChannel::Open name = qjackctl[/COLOR] 
[COLOR=#cc9966]Jack: Connect: addr.sun_path /dev/shm/jack_qjackctl_1000_0[/COLOR] 
[COLOR=#cc9966]Jack: JackShmMem::new index = 2 attached = b2237000 size = 384 [/COLOR] 
[COLOR=#cc9966]Jack: JackExternalClient::Open name = qjackctl index = 2 base = b2237000[/COLOR] 
[COLOR=#cc9966]Jack: JackProcessSync::TimedWait time out = 5000000[/COLOR] 
[COLOR=#cc9966]Jack: JackProcessSync::TimedWait finished delta = 9472.0[/COLOR] 
[COLOR=#cc9966]Jack: JackEngine::NotifyAddClient: name = qjackctl[/COLOR] 
[COLOR=#cc9966]Jack: JackExternalClient::ClientNotify ref = 0 name = system notify = 0[/COLOR] 
[COLOR=#cc9966]Jack: JackExternalClient::ClientNotify ref = 1 name = freewheel notify = 0[/COLOR] 
[COLOR=#cc9966]Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 0[/COLOR] 
[COLOR=#cc9966]Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 0[/COLOR] 
[COLOR=#cc9966]Jack: JackSocketServerChannel::BuildPoolTable size = 3[/COLOR] 
[COLOR=#cc9966]Jack: fSocketTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: fSocketTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: JackRequest::Notification[/COLOR] 
[COLOR=#cc9966]Jack: JackEngine::NotifyClient: no callback for event = 4[/COLOR] 
[COLOR=#cc9966]Jack: JackEngine::NotifyClient: no callback for event = 4[/COLOR] 
[COLOR=#cc9966]Jack: JackEngine::NotifyClient: no callback for event = 4[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 3[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 4[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 3[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 4[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 1[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 2[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 1[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 2[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: JackClient::SetupDriverSync driver sem in flush mode[/COLOR] 
[COLOR=#cc9966]Jack: JackPosixSemaphore::Connect jack_sem.1000_default_qjackctl[/COLOR] 
[COLOR=#cc9966]Jack: Already connected name = qjackctl[/COLOR] 
[COLOR=#cc9966]Jack: Clock source : system clock via clock_gettime[/COLOR] 
[COLOR=#cc9966]Jack: JackLibClient::Open name = qjackctl refnum = 2[/COLOR] 
[COLOR=#cc9966]Jack: jack_set_graph_order_callback ext_client 86d16b8 client 86d16b8 [/COLOR] 
[COLOR=#cc9966]Jack: JackClient::Activate[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: JackRequest::ActivateClient[/COLOR] 
[COLOR=#cc9966]Jack: JackEngine::ClientActivate ref = 2 name = qjackctl[/COLOR] 
[COLOR=#cc9966]Jack: JackProcessSync::TimedWait time out = 5000000[/COLOR] 
[COLOR=#cc9966]Jack: JackProcessSync::TimedWait finished delta = 14563.0[/COLOR] 
[COLOR=#cc9966]Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 2[/COLOR] 
[COLOR=#cc9966]Jack: JackClient::kActivateClient name = qjackctl ref = 2 [/COLOR] 
[COLOR=#cc9966]Jack: WaitGraphChange...[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: JackRequest::Notification[/COLOR] 
[COLOR=#cc9966]Jack: JackEngine::NotifyClient: no callback for event = 4[/COLOR] 
[COLOR=#cc9966]Jack: JackEngine::NotifyClient: no callback for event = 4[/COLOR] 
[COLOR=#cc9966]Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 4[/COLOR] 
[COLOR=#cc9966]Jack: JackClient::kGraphOrderCallback[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 3[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 4[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 3[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 4[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 1[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 2[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 1[/COLOR] 
[COLOR=#cc9966]Jack: JackGraphManager::RecalculateLatency port_index = 2[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = [/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#cc9966]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#999999]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#999999]Jack: fPollTable i = 2 fd = 6[/COLOR] 
[COLOR=#999999]Jack: fPollTable i = 1 fd = 5[/COLOR] 
[COLOR=#999999]Jack: fPollTable i = 2 fd = 6[/COLOR]

[COLOR=#999999][/COLOR]
[COLOR=#999999][COLOR=Black]After it I even was able to choose WinAsio driver in fruity loops but unfortunately without any sound![/COLOR]
[/COLOR]

---

### Post by Pablo_F on 2011-06-08
Hi, 

The dummy driver is... dummy. Unless you have a firewire card, you need the _alsa driver_. In your case, you probably compiled jack without alsa support. When you compiled, you had to make sure that alsa driver support was there, see the output of ./waf configure. You should have installed the alsa development package (libasound-dev, IIRC).

Anyway, _you don't need to compile_ jack. Just install it via software center, synaptic or apt-get.

OTOH, do enable the realtime mode.

---

### Post by korgx9 on 2011-06-08
Hi,
I did ./waf configure result is
Linux detected 
Checking for program g++                 : ok /usr/bin/g++ 
Checking for compiler version            : ok 4.5.2 
Checking for program cpp                 : ok /usr/bin/cpp 
Checking for program ar                  : ok /usr/bin/ar 
Checking for program ranlib              : ok /usr/bin/ranlib 
Checking for g++                         : ok  
Checking for program gcc                 : ok /usr/bin/gcc 
Checking for compiler version            : ok 4.5.2 
Checking for program ar                  : ok /usr/bin/ar 
Checking for program ranlib              : ok /usr/bin/ranlib 
Checking for gcc                         : ok  
Checking for header samplerate.h         : not found 
Checking for alsa >= 1.0.18              : ok 
Checking for libfreebob >= 1.0.0         : ok 
Checking for libffado >= 1.999.17        : ok 
Checking for header sndfile.h            : not found 
Checking for header samplerate.h         : not found 
Checking for celt >= 0.5.0               : ok 
Checking for header ncurses.h            : not found 
Checking for library readline            : not found 
Checking for celt >= 0.11.0              : Package "celt (>= 0.11.0)" could not be found or the found version is too old. 
Checking for celt >= 0.8.0               : Package "celt (>= 0.8.0)" could not be found or the found version is too old. 
Checking for celt >= 0.7.0               : ok 

==================                      
JACK 1.9.7 exported from r4236
Build with a maximum of 64 JACK clients
Build with a maximum of 768 ports per application
Install prefix                           : /usr/local 
Library directory                        : /usr/local/lib 
Drivers directory                        : /usr/local/lib/jack 
Build debuggable binaries                : no 
C compiler flags                         : ['-Wall'] 
C++ compiler flags                       : ['-Wall'] 
Linker flags                             : ['-lm -lstdc++'] 
Build doxygen documentation              : no 
Build with engine profiling              : no 
Build with 32/64 bits mixed mode         : no 
Build standard JACK (jackd)              : yes 
Build D-Bus JACK (jackdbus)              : no 
Build with ALSA support                  : no 
Build with FireWire (FreeBob) support    : no 
Build with FireWire (FFADO) support      : no 

I did what you suggested and now  in qjackctl I got messages:
 p, li { white-space: pre-wrap; }  [COLOR=#999999]09:35:25.643 JACK is starting...[/COLOR]
 [COLOR=#990099]09:35:25.644 /usr/local/bin/jackd -v -dalsa -dhw:0 -r44100 -p1024 -n4 -s -S[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]09:35:25.673 JACK was started with PID=13759.[/COLOR]
 Unknown driver "alsa"
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2011 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]09:35:25.764 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]09:35:27.706 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started



I want to back my desktop to previous state... to the earliest state without any installed qjackctl or jackd. Is it possible?

---

### Post by Pablo_F on 2011-06-09
Hi, 

From the jack 1.9.7 folder, do a 

sudo ./waf uninstall

I will say it again: you don't need to compile jack. Just install from it from the software center. Or do not install it. Like you wish,

Cheers, Pablo

---

### Post by proxess on 2011-06-09
Exactly, uninstall your compiled jack, and install it through Synaptic or apt.

sudo apt-get install jackd.

Jackd2 won't work.

I wrote a complementary guide to this one a few pages back, use it.

---

### Post by Totalchaos on 2011-06-09
The arrival of "Ardour 3", will make "FL Studio" an obsolete program on Linux Environment
[http://www.archive.org/details/Introduction_to_Ardour_3.0_MIDI](http://www.archive.org/details/Introduction_to_Ardour_3.0_MIDI)

---

### Post by korgx9 on 2011-06-09
Thanks Pablo_F
I uninsulated jack 1.9.7  and reinstalled qjackctl amd it started to work. 
Thanks a lot.

---

### Post by binfacto on 2011-06-10
> **liquip said:**
> korgx9: To overcome that "Error while creating the ASIO driver" I did what binfacto suggested and it worked. First I uninstalled qjackctl and jackd, then compiled and installed jack-1.9.7, reinstalled qjackctl and it started working!

binfacto: I'm trying to get my mpk-mini work with FL too :D (32-bit system), so could you please report if you find a way to get it working :).

After plugging in the controller with qJackctl launched. (I did not mess with the connect interface.)

I made sure in wine config to enable ASLA drivers.

Launched FL Studio and it appears under: Options -> MIDI Settings
Just click enable on your Midi device.

---

### Post by sgx on 2011-06-11
> **Totalchaos said:**
> The arrival of "Ardour 3", will make "FL Studio" an obsolete program on Linux Environment
[http://www.archive.org/details/Introduction_to_Ardour_3.0_MIDI](http://www.archive.org/details/Introduction_to_Ardour_3.0_MIDI)
As good as ardour is and will be, the full version of FLS
and the full version of ardour, are apples Vs oranges, 
The commercial funding available to FLS developers, means
their successful business model, and regular release of new instruments and DAW capabilities, will move ahead.

Ardour has a narrower range of function, and their goal
is to master that range with excellence. The recent beta releases
indicate they are on track.
Cheers

---

### Post by beyoblue on 2011-07-02
I followed the Instructions from FalkTX and I'm still stuck with the same problem 
korgX9 had: FL starts, but echoes 

"Error while creating the ASIO driver"

```
jackd --version
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
jackdmp version 1.9.7 tmpdir /dev/shm protocol 8

``````
 ulimit -r -l
real-time priority              (-r) 95
max locked memory       (kbytes, -l) unlimited

```Did I possibly miss something?

I tried reinstalling a couple of times already.

Somebody help...plz

---

### Post by falkTX on 2011-07-02
> **beyoblue said:**
> I followed the Instructions from FalkTX and I'm still stuck with the same problem 
korgX9 had: FL starts, but echoes 

"Error while creating the ASIO driver"

```
jackd --version
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
jackdmp version 1.9.7 tmpdir /dev/shm protocol 8

``````
 ulimit -r -l
real-time priority              (-r) 95
max locked memory       (kbytes, -l) unlimited

```Did I possibly miss something?

I tried reinstalling a couple of times already.

Somebody help...plz

I had this problem once... it turned out I hadn't started JACK in the first place... :lolflag:

Is this your case?

---

### Post by beyoblue on 2011-07-02
nope. 

Jack is running and, at least for GStreamer, playback is working fine.

---

### Post by beyoblue on 2011-07-03
I wonder if it could be a problem that I have Pulseaudio still running?

---

### Post by beyoblue on 2011-07-03
FL; is running for now.  I have to admit I'm far from sure what happened.  I tried a lot of things including compile WineAsio on my own using Asio.h from Steinberg.  Still, WineAsio is disabled, giving the same old Error-Message.  But somehow I managed to get FL streaming to Alsa immediately, circumventing all those Problems with Jack.  Now I would like to get a little more Information on latency and so on.  Anybody's got a clue?

---

### Post by shaneo1 on 2011-07-08
):POk so this is what I can't understand.  I installed unbuntu11.04, with jackd2 and wineasio0.9 deb file. and then installed Fl9, and all worked a treat, even pusle-jack as well worked, I have no overruns nothing, then I had a issue with gnome3 shell and reinstalled ubuntu11.04 fro a clean install. Can I get wineasio to not overrun, can I for the love of cheese.

I have jackd2 and I have tried every setting under the sun to get it to stabilize and even used the same wineasio0.9 deb file as I had when I had everything running top dollar.

Please can someone post a step by step noddy guide. to have jack run wineasio through it with fruityloops, and have pusle-jack running as well.  I am so annoyed and frustrated, can produce my music without crackles ... Aaaaaaaahhhh.

---

### Post by neu2buntu on 2011-07-08
@ [shaneo1]("http://ubuntuforums.org/member.php?u=1238317") ... it could be something simple like config file , rem that FL cannot be run in realtime too. 1st maybe look to check that your username is a member of pulse, pulse-access & rtkit groups, do this by running command :-   groups   in the terminal 

2nd check wine and have alsa and and jack audio drivers enabled

3rd probably ensure that jack can run at high priority on your system check your /etc/security/limits.d/audio.conf file has these settings :-   @audio   -  rtprio     95
@audio   -  memlock    unlimited  (i have this part commented out as it is recommended not to be needed now #@audio   -  nice      -19)  

4th maybe check your gstreamer-properties and play about with the settings, try choosing pulseaudio for input/output or maybe even alsa.
*im still using jack1* but i guess the settings should be similar, well hope this helps ;)

---

### Post by shaneo1 on 2011-07-08
thanks for the reply, I surprisingly, have done all that you have mentioned, though bizarrely, I went to synaptic installed jackd1 and it never promoted to remove jackd2,  then I removed jackd2.

I now have jackd running in realtime, and FL9 is working better than ubuntu running windows 7 in a virtual box.  Oh I just got a overrun, my first, but all is good.

please dont ask me how I have it set up im not a wizz with all the ubuntu terminal jargon, but if anyone wants to could I will post the setting, if someone could guide me through terminal.

---

### Post by kutalion on 2011-07-09
Hi, I am having trouble using FLS with WineASIO driver. When I start FLS (10.0 version) and Jack before this I get sound but a slow and laggy as the sound driver is set to default sound driver (ALSA). As I try to open WineASIO I get a window that tells me it can't open sound driver and then a great number of error dialogs that simply has no end. I use WINE 1.3 beta but I've tried 1.2 and FLS 9 to no avail. I'll give you the terminal output too. I tried that under Ubuntu 11.04 32-bit, Ubuntu 11.04 64-bit and Ubuntu 10.04 64-bit

```
fixme:dwmapi:DwmIsCompositionEnabled 0x32f964
fixme:win:LockWindowUpdate (0x200c4), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:bitblt:client_side_dib_copy potential optimization: pixel format conversion
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x198308,0x198770): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x27be9ec): stub
fixme:avrt:AvSetMmThreadPriority (0x12345678)->(2) stub
fixme:shell:PathUnExpandEnvStringsA ("C:\\Program Files\\Image-Line\\FL Studio 10\\Artwork\\Skins\\Default\\StartSnd.WAV","",0x00000105)
fixme:shell:PathUnExpandEnvStringsA ("C:\\Program Files\\Image-Line\\FL Studio 10\\Artwork\\Skins\\Default\\StartSnd.WAV","",0x00000105)
err:bitmap:X11DRV_DIB_SetImageBits Out of memory!
err:bitmap:X11DRV_DIB_SetImageBits Out of memory!
err:bitmap:X11DRV_DIB_SetImageBits Out of memory!
err:bitmap:X11DRV_DIB_SetImageBits Out of memory!
err:bitmap:X11DRV_DIB_SetImageBits Out of memory!
fixme:asio:DllCanUnloadNow (void): stub
```

---

### Post by djzoid on 2011-07-21
hi all, 

bump the previous post by kutalion, i'm having similiar problems, if i start jack and then fl 9 (using 10.04) i get a message saying "error while creating asio driver, I have read through this thread and have had no success. when i change to wineasio in fl i get a bundle of error messages such as "invalid pointer operation" "DIB cannot be made" and the "error creating asio driver" one too.

if i leave fl on wineasio then close it, fl does not start up, but i get the error creating asio driver message.

any help would be appreciated!

---

### Post by sgx on 2011-07-22
> **djzoid said:**
> hi all, 

bump the previous post by kutalion, i'm having similiar problems, if i start jack and then fl 9 (using 10.04) i get a message saying "error while creating asio driver, I have read through this thread and have had no success. when i change to wineasio in fl i get a bundle of error messages such as "invalid pointer operation" "DIB cannot be made" and the "error creating asio driver" one too.

if i leave fl on wineasio then close it, fl does not start up, but i get the error creating asio driver message.

any help would be appreciated!
I would install reaper, remove and reinstall wine/wineasio. Run the

regsvr32 wineasio.dll    command, run winecfg, and choose alsa in
the audio panel

Start reaper and choose wineasio in reaper device preferences. If wineasio fails in reaper
you can assume you need a different wineasio version. Several should be available. One is an attachment from Falk in the top post of this thread:

[http://ubuntuforums.org/showthread.php?t=1241187](http://ubuntuforums.org/showthread.php?t=1241187)

or here:

[http://sourceforge.net/projects/kxstudio/files/DEBs/](http://sourceforge.net/projects/kxstudio/files/DEBs/)

Cheers

---

### Post by kutalion on 2011-09-02
I somehow (dunno how exactly) managed to get out of the situation but now another question come at hand. Since wine 1.3.25 there is no jack support anymore. Wether WineHQ are working on a new jack driver or not I don't know but since this is the light for the next stable version of Wine what should we do with wineasio does it run only with jack? From time to time I find it hard to run wineasio even with jack though.

---

### Post by falkTX on 2011-09-02
> **kutalion said:**
> I somehow (dunno how exactly) managed to get out of the situation but now another question come at hand. Since wine 1.3.25 there is no jack support anymore. Wether WineHQ are working on a new jack driver or not I don't know but since this is the light for the next stable version of Wine what should we do with wineasio does it run only with jack? From time to time I find it hard to run wineasio even with jack though.

From 1.3.25 on, the JACK driver has been removed.
You can still safely use WineASIO as usual, and the ALSA driver is still there for MIDI stuff.

---

### Post by sgx on 2011-09-02
> **kutalion said:**
> I somehow (dunno how exactly) managed to get out of the situation but now another question come at hand. Since wine 1.3.25 there is no jack support anymore. Wether WineHQ are working on a new jack driver or not I don't know but since this is the light for the next stable version of Wine what should we do with wineasio does it run only with jack? From time to time I find it hard to run wineasio even with jack though.
Hi, what does this mean?

"From time to time I find it hard to run wineasio"?

wineasio is not a command to run, it just waits for something
that uses it. I have never used the jackd checkbox in winecfg, just alsa, and things work well, reaper connects to jackd automatically, fst works on those plugins it likes, linux audio apps work alongside windows apps.
Cheers

---

### Post by LuisUK on 2011-09-03
Just in case anyone else comes across this...

It appears that foobar's asio plugin doesn't recognize wineasio as an asio driver. When I try to add it under ASIO Virtual Devices, it gives an error message box saying "No ASIO driver found".

I tried it in Reaper and it works. Also, i checked with asiocaps.exe and it also sees the wineasio driver.

So this is definitely a foobar issue.

---

### Post by kutalion on 2011-09-08
> wineasio is not a command to run

You run wineasio as you select it in your drop down menu as audio driver in whatever program you use. The problem is (and I tried Ubuntu natty, lucid, and Mint 11) wineASIO says that it can't connect to jack even if I have my jack up and running. I think I is problem in wineASIO 0.9.0 but as I recall I recently used this same version on a Macpup notebook and it ran like hell :) It just doesn't run. I once had it up and running but then I decided on installing gnome3 which totally messed my X and I had to reinstall afterwards no wineasio ever thought about running here :(
Here's what I get when I run FL 9.0 (with wineasio 0.9.0 and wine 1.3.27)

```
fixme:win:LockWindowUpdate (0x200ba), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:bitblt:clienzt_side_dib_copy potential optimization: pixel format conversion
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
err:bitmap:X11DRV_DIB_SetImageBits Out of memory!
```

I used to receive a message that wineasio cannot create thread = 11 (or something like this but this was in Mint 11) and complaining that jack isn't running except that it IS.

Furthermore I created a virtual Wine Desktop and ran FLS again. I received some very very weird output in terminal

```
fixme:win:LockWindowUpdate (0x200ba), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:bitblt:client_side_dib_copy potential optimization: pixel format conversion
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
err:bitmap:X11DRV_DIB_SetImageBits Out of memory!
err:bitmap:X11DRV_DIB_SetImageBits Out of memory!
err:bitmap:X11DRV_DIB_SetImageBits Out of memory!
err:bitmap:X11DRV_DIB_SetImageBits Out of memory!
err:bitmap:X11DRV_DIB_SetImageBits Out of memory!
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b839d72 (thread 0009), starting debugger...
err:seh:setup_exception_record stack overflow 864 bytes in thread 0009 eip 6802956a esp 00230fd0 stack 0x230000-0x231000-0x330000
libgcc_s.so.1 must be installed for pthread_cancel to work
err:seh:setup_exception_record nested exception on signal stack in thread 0009 eip 68000832 esp 7ffdb468 stack 0x231000-0x330000
libgcc_s.so.1 must be installed for pthread_cancel to work
err:seh:setup_exception_record nested exception on signal stack in thread 0009 eip 68000832 esp 7ffdab48 stack 0x231000-0x330000
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
marcus@marcus-eM355:~$ 0000000e services.exe
	0000001b    0
	00000016    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000017    0
	00000013    0
	00000012    0
00000018 plugplay.exe
	0000001c    0
	0000001a    0
	00000019    0
0000001d explorer.exe
	0000001e    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'
```

At first "err:bitmap:X11DRV_DIB_SetImageBits Out of memory!" I got a dialog "Cannot create wineASIO" and then at last one I got another "Cannot create wineASIO". Finally I got a dialog with critical wine error (something very familiar in windows I think?).
I tried WINEDEBUG=+wineasio before running FLS too. The result? It is seen above. I can't recall when WINEDEBUG ever helped me though (I HAVE wine1.3-dbg installed)...

And my simple question - WHAT THE...

I never ever had problems with wineasio untill natty after natty I can't even turn back to maveric or lucid because this problem is present there too. So I am seemed to be stuck with only chance - Windows which is not a good chance by the way (as you may agree) or Puppy (which is too minimalistic for my everyday computing and I also love apt-get commands, hehe :D)

Oh, and the only thing that FLS can play sound through is a Direct Sound Driver (alsa I suppose) which is incapable of processing fast enough for playing with a midi keyboard (I get buggy sounds even at 2048 samples buffer)

So anyone? Any ideas, I'm freaking out here... Please, please!

EDIT: I have found the actual problem with running under Ubuntu and any normal Linux system. It appears that one must their user in the audio group to actually allow wine apps to run with jack client. This solution explains why it would run under system like Puppy where the default user is a root and under root you're allowed to do anything, right? No matter if this is a real solution or just my system decided to let me runn FLS I would recommend anyone having problem with wineasio to add your user to audio group.

---

### Post by arsonal on 2012-05-22
Hey everyone. I'm running Ubuntu 11.10 (Oneiric Ocelot) and already have FL Studio 10.0.9c running with PlayOnLinux. However, I still cannot record any audio from my M-Audio Black Box Reloaded Interface. I installed the wine-audio deb package at the beginning of this forum and even registered its dll like "regsvr32 wineasio.dll" with no problem. I have a feeling it's something to do with the setup in one of the attached pictures below in the winecfg audio tab and that's the thing: it says I have no audio driver selected and everything else only has "System Default". I also attached a picture of my qjackctl to show how I have it setup. Please, any help with this would be greatly appreciated. Thank you. 

P.S. I can hear the beats I make perfectly through my Black Box Interface but I still cannot record raw audio such as guitar, bass or vocals.

---

### Post by sgx on 2012-05-22
Install a2jmidid and start it with

a2jmidid -j default

this will give you a jackd midi port in the qjackctl midi tab.

In the qjackctl alsa tab your screen-pic connection lines
should form an X  from blackbox to midi-through,
but are now drawn straight across  =

Start yoshimi synth, and its jackd midi appears in the midi tab of qjackctl on the right side, and should also open its audio port in the Audio tab on the left side. Make the audio and midi connections, while midi through is connected to blackbox in the alsa tab.


wine devs are moving away from pro audio, so the normal winecfg
options are gone, but an easy wine registry edit, means you
can still select alsa for audio, which would help for using
FLS

[http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound](http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound)

scroll down to 'configuring sound section' for directions.
Cheers

---

### Post by arsonal on 2012-05-23
hey SGX, did I do this correctly? I did aj2midid -j default and when I open up Yoshimi, it shows up automatically in qjackctl (See pics below). However, for some reason when I open up my FL Studio 10 (with wine), it doesn't show up in the Midi tabs at all. Also, I did the instructions on that wikipedia link you posted but every time I change the registry part of "Audio" to "alsa" and then restart the computer, that value goes right back to "jack" for some reason.

P.S. as you can see in the back, FL Studio is open but still doesn't show up in qjackctl under midi.

---

### Post by sgx on 2012-05-23
Hi, the yoshimi connections are just like mine,
and when I use reaper, it never displays anything
in the alsa or midi ports either, just functions like it
was back home with Granny XP

So you must choose asio as the device in FLS,
and wineasio in its asio preferences, then follow
the FLS way of scanning for plugins. When I run reaper,
it autoconnects  X to the Audio ports in qjackctl.

/home/you/.wine/drive_c/Program Files/Steinberg/VstPlugins

is a common/lucky plugin path. If an installer has other defaults,
I use those, and then link to this VstPlugins folder.

wine .wine/drive_c/Program*Files/Native*Instruments/Absynth*5/Absynth*5.exe 

In a command line, to start a stand-alone, I fill spaces or quote to bypass blank spaces.

[http://www.kvraudio.com/banks.php?s=list&what=1187&format=&order=date](http://www.kvraudio.com/banks.php?s=list&what=1187&format=&order=date)

get the Cormi, Laba 170, and Improved Collection (from folderol)
These are zynaddsubfx sounds and are excellent, and work in the newer
yoshimi.  i7 cpu users can build monster multi-timbral layers
:guitar:

Cheers

---

### Post by arsonal on 2012-05-23
Hey again SGX. About what you said in regards to choosing the ASIO in FLS, here's my problem: Wine-Asio doesn't show up in the Input/Output options and when I try to hover over the "IN" part of the mixer, it won't let me choose an Input to, for example, record vocals, guitar or bass (that's what my black box interface is for) and on the top left of the program under "File, Edit, Channels...etc" it says Audio Input Source (ASIO Devices Only).  See the pictures below for detailed illustration. 

P.S. my Blackbox and Midi Through Port-0 show up but no Wine-Asio option.

---

### Post by sgx on 2012-05-24
do reaper, festige, fst or dssi-vst work with your wineasio?

grab an ampsim, 

[http://www.igniteamps.com/index.php?option=com_content&view=article&id=47&Itemid=55&lang=en](http://www.igniteamps.com/index.php?option=com_content&view=article&id=47&Itemid=55&lang=en)

and 

fst NRR-1.dll or

vsthost /usr/lib/vst/NRR-1.dll

and feed it a sound connected from line-in

# Set DSSI_VST_PATH for Bash shell
if [ -n "\$DSSI_VST_VST_PATH" ]; then
   export DSSI_VST_VST_PATH="/usr/lib/vst"
fi

put such a path file in /etc/profile.d

you can rename .wine for now, and install a 1.3 or 1.2
version of wine, I've about seen the end of 1.4 for now.

Reinstall fls to its installer defaults, or copy it directly
from a dual boot partition.

make sure these are in .wine/drive_c/windows/System32
gdiplus
mfc42
mfc71
msvcp60
msvcp71
msvcr71
msvcr80
mscvsc60
msvcp90
msvcr90

Cheers

---

