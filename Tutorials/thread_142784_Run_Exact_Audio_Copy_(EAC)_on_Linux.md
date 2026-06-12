---
title: "Run Exact Audio Copy (EAC) on Linux"
date: 2006-03-11
forum: Tutorials
---

### Post by quandar on 2006-03-11
**Introduction**
Hands down, it is often agreed that EAC is the best CD ripper out there. And it was one of the things I took for granted when I switched. So basically, I set out to use it using WINE, and really, its just as fast, and runs perfectly, no problems in any feature from what I can see.

[IMG]http://gui.deletefactory.net/ubuntu/wine1.png[/IMG]
(If you want to make WINE look better without msstyles read [this guide]("http://www.ubuntuforums.org/showthread.php?t=142741").)

**Configuring WINE: Part I**
Open your terminal in type in:
```
winecfg
```
And go to the "Drives" tab, and press the "Auto_d_etect..." button. 
It should scan for drives, and find a handful of them. Find /media/cdrom drives, if you have more than one then apply this step to all of them. Click on the drive letter ( in my case E: ) and press the "Show Advanced" button, and then select the "Type" of the drive to be "CD-ROM", apply to every drive that is a CD drive, and press "OK".

**Installing EAC**
Download the installer for [Exact Audio Copy](http://www.exactaudiocopy.de/eac-0.95b4.exe), then double-click eac-0.95b4.exe on the downloaded file and simply install like any other app.

**Configuring WINE: Part II**
Go into your terminal and type:
```
winecfg
```
and in the Applications tab, press the "Add Applcation" button and browse to EAC.exe, and click on it and select a NT operating system from the Windows select box (those being NT/2000/XP), and press "OK". 
As it launches cancel the wizard, and press F9, and under the "Interface" tab, select "Native Win32 Interface for NT/2000/XP".  Press "OK", and restart the app. Put a CD in your drive, and hopefully all will go well.
You should now be able to simply launch by using```
wine ~/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy/EAC.exe
```in your favorite terminal.

---

### Post by whythehellcantilogon on 2006-03-13
Hi, I am super glad that I have, because to you, finally gotten EAC to work without booting back into windows. Thanks. 

There is just one thing that I would like to mention that might save some folks a little bit of time.

When I was setting up the drives in the initial 'winecfg' I needed to have cds in the drives or else they wouldn't stay set to CD-ROM, they would switch back to Local Hard Disk.

And I believe this is a fault on my end but I can't get the EAC.desktop file to work, for some reason it just won't start. Copying the command to the terminal works just fine and is sufficient for me so I am not going to worry to much. 

-Erik

Edit: Considering the user below me is having the same problem with the shortcut it might not be my fault but I am not knowledgeable enough to fix it.

---

### Post by PtS on 2006-03-14
EAC doesn't find any cd drives. I've changed /media/cdrom0 from autodetect to cd drive in winecfg. When I started EAC in terminal (I can't get the shortcut I made in the menu to work) I get these error messages:

```
[fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:win:SetWindowTextA setting text "CD Title " of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "CD Artist " of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Year " of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Genre " of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "freedb " of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text " Various Artists " of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Load" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Save" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "New" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete" of other process window (nil) should not use SendMessage

``` Somebody with same problem or a solution to it?

---

### Post by junior aspirin on 2006-03-14
note: this is not bashing or a flame

i am just wondering why you would want to use eac unter linux. isnt that what sound juicer does, it also rips them into lovely oggs rather than mpee3s? i would rather have it the other way round sound juicer on windows, but thats just me, ill settle with cdex, as it ripps to ogg.

---

### Post by PtS on 2006-03-14
[QUOTE=junior aspirin	]i am just wondering why you would want to use eac unter linux. isnt that what sound juicer does, it also rips them into lovely oggs rather than mpee3s? i would rather have it the other way round sound juicer on windows, but thats just me, ill settle with cdex, as it ripps to ogg.[/QUOTE]
Why I don't use ogg? Because my Mp3 player (USB) can't play ogg. If it could, I would definitely use ogg.

---

### Post by stu on 2006-03-14
EAC can also rip into Ogg Vorbis, but the idea is that it works very hard to get a PERFECT copy.

Sound-Juicer and most other CD-rippers will sometimes let errors through (often very minor and probably inaudible ones)... and paranoid folks like to make sure they are getting a quality rip.

---

### Post by Syco54645 on 2006-03-14
> originally posted by junior aspirin
note: this is not bashing or a flame

i am just wondering why you would want to use eac unter linux. isnt that what sound juicer does, it also rips them into lovely oggs rather than mpee3s? i would rather have it the other way round sound juicer on windows, but thats just me, ill settle with cdex, as it ripps to ogg.

it should also be noted that eac is the only app that is accepted for ripping live recording that have been burnt to cd audio.  top quality guide quandar.

-Syco54645

---

### Post by whythehellcantilogon on 2006-03-15
[QUOTE=PtS]EAC doesn't find any cd drives. I've changed /media/cdrom0 from autodetect to cd drive in winecfg. When I started EAC in terminal (I can't get the shortcut I made in the menu to work) I get these error messages:
 [/QUOTE]

I believe you need to tell EAC to use the Win32 interface. I was able to recreate your error when I switched from Win32 to the default.

Start EAC-->press F9 --> click on the interfaces tab --> select the native win32 interface. 

Hope this helps.

-Erik

---

### Post by Parkotron on 2006-03-15
Again, not trying to flame or anything, but does EAC do anything quality-wise that cdparanoia in full paranoia mode doesn't? Personally, I've always used abcde to rip my CDs but there are plenty of GUI front ends for the paranoia library, too. I guess I'm saying why go through the effort of wine when there are native and open source programs that are (as far as I know) just as good?

Then again, maybe I'm wrong and EAC does something that cdparanoia doesn't. Any additional info from someone more knowledgeable would be appreciated.

---

### Post by dpaint4 on 2006-03-16
Oh my god oh my god oh my god. I never thought this would happen thank you so much. This is great. Now I can believe in my rips and I can use all the latest codecs by just pointing the program towards whatever command line encoder I want. I missed AoTuV Vorbis soooooooo much. This rocks. Thanks for making there be 100% no reason for me to ever need to boot back to Windows.

---

### Post by klahjn on 2006-03-16
[QUOTE=dpaint4]Oh my god oh my god oh my god. I never thought this would happen thank you so much. This is great. Now I can believe in my rips and I can use all the latest codecs by just pointing the program towards whatever command line encoder I want. I missed AoTuV Vorbis soooooooo much. This rocks. Thanks for making there be 100% no reason for me to ever need to boot back to Windows.[/QUOTE]

i'm guessing you like EAC?

---

### Post by dpaint4 on 2006-03-16
[QUOTE=klahjn]i'm guessing you like EAC?[/QUOTE]

Yeah. I really really do. It's not just blind faith in the program, but there really are great features, like multiple passes to ensure and compare for accuracy, at seemingly no cost to speed.

And like easily switching out command line codecs without touching or effecting the rest of your system. (That's a BIG one for me, because I always like to have the latest codecs, but I don't like to have to put my cute little Ubuntu laptop through all the stress of making and updatinng multiple system-wide media engine changes and the like.)

Yeah, this changes everything. I'm so glad you found a configuration that works (and boy does it!).

---

### Post by Syco54645 on 2006-03-16
> Originally posted by Parkotron 
Again, not trying to flame or anything, but does EAC do anything quality-wise that cdparanoia in full paranoia mode doesn't? Personally, I've always used abcde to rip my CDs but there are plenty of GUI front ends for the paranoia library, too. I guess I'm saying why go through the effort of wine when there are native and open source programs that are (as far as I know) just as good?

Then again, maybe I'm wrong and EAC does something that cdparanoia doesn't. Any additional info from someone more knowledgeable would be appreciated.

i am not sure if it does, but it is what etree says to use to rip live concernts from cd.  i posted that before.  they say that if you must to use cdparanoia.  everyone that i have talked to has preferred eac over any other program regardless of if they use linux windows or mac.  eac running in wine isnt really anything new, i just never had a need to do it and i really give dan props for figuring it out, just as i got dc++ to work in wine.  others have done it, i just figured it out on my own.  i should make a guide for it.  so the moral is that i have no idea how eac and cdparanoia compare, but i would think that they have basically the same feature set.  windows stuff in wine isnt new, people just dont try it.

-Syco54645

ps dan i didnt put you down, if you have a problem with my post come fight me Christmas day on the roof down 20 Oxford street!!!! Oi Oi!

---

### Post by VCSkier on 2006-03-19
iirc, cdparanoia is practically worthless on drives that cache audio data (most new drives), where as EAC has a feature to flush the cache after every read (at the expense of some speed).  it is commonly accepted on hydrogenaudio.org, *the* digital audio forum, that EAC is the best ripper available.

edit: ps, thank you very much quandar, this makes my transition much easier and more plesant.  thank you so much.

---

### Post by VCSkier on 2006-03-20
now if only i can get the new foobar2000 0.9 to work through wine...  any suggestions?

---

### Post by muishkin on 2006-03-22
[quote=VCSkier]now if only i can get the new foobar2000 0.9 to work through wine...  any suggestions?[/quote]

Foobar2000 0.9 is running fine here in wine.  I think it runs fine as long as you don't try out the column_ui plugin.

---

### Post by bionnaki on 2006-03-26
does eac allow you to transcode .shn files to, say, ogg or mp3?

---

### Post by VCSkier on 2006-03-26
nope.  eac just rips/encodes, and burns on occasion.  :)

---

### Post by bionnaki on 2006-03-26
I vaguely remember being able to transcode files in eac back in my windows days...2 or 3 years ago. can anyone else confirm this?

---

### Post by quandar on 2006-03-28
I am fairly sure EAC does not do transcoding, if you want to do that I suggest picking up the GNOME app soundconverter, its really quite nice, try it.

---

### Post by bionnaki on 2006-03-28
I have that, but it does not do .shn

---

### Post by MetalMusicAddict on 2006-03-28
Nice guide sir. Ive always been an Audiograbber man myself. I have it working under WINE. I like Grip but I cant get help with it and I cant figure some things out so I still use AG. ;)

---

### Post by VCSkier on 2006-03-29
has anyone been able to get AccurateRip to work w/ EAC under wine yet?  it dosen't seem to be working for me, but again, i've very new all all this.

edit: nevermind.  it works now.  i was just being dumb.  :)

---

### Post by hugmenot on 2006-03-29
[QUOTE=VCSkier]iirc, cdparanoia is practically worthless on drives that cache audio data (most new drives), where as EAC has a feature to flush the cache after every read (at the expense of some speed).  it is commonly accepted on hydrogenaudio.org, *the* digital audio forum, that EAC is the best ripper available.[/quote]

To calm you fanatics down a little bit...
Flushing the cache on drives that do that is the only feature that EAC has in advantage to other rippers like cdparanoia. This is the crucial point. As soon as you *know* your drive doesn't cache cdparanoia, CDex and the new Foobar2000 secure ripper are just as secure. They read twice, compare and by this pretty much establish that the rip is unflawed.
I have a fairly recent laptop. The drive doesn't cache. Many other laptop cd drives I saw don't cache as well.
I really don't think it's worth the fuzzy warm feeling. Peter Pawlowski would comment with &#8220;meh&#8221; on that. I mean back then I even setup AccurateRip in EAC to determine the read-in and write-in offsets shuffling through dozens of CDs to find a known reference disc. Nowadays I see it's completely useless.

---

### Post by VCSkier on 2006-03-30
sorry if this is another dumb question, but i'm having a hard time getting it to use the linux version of oggenc.  do i have to use the windows version, oggenc.exe?  or am i doing something wrong?

---

### Post by hugmenot on 2006-04-03
oggenc.exe

---

### Post by M3ta7h3ad on 2006-04-04
Nice one. Just found this how-to after searching for some software to do the same thing on linux. Glad EAC is available through wine. zero learning curve for me :) Tiz fantastic.

Good work boyo :)

---

### Post by marsanpin on 2006-04-17
Almost there but some problems:

I followed this how-to and got wine installed,
mario@ubuntu01:~$ wine --version
Wine 0.9.11

then, for some unknown reason (to me) after writing the "EAC.desktop" (where should it be saved? ~/ or ~/.wine/.../EAC/ ?, I saved to ~) simply doesn't work.

if I start from command line,
mario@ubuntu01:~$ wine EAC.exe
wine: could not load L"c:\\windows\\system32\\EAC.exe": Module not found
I get above error message.

On winecfg I really don't know which emulation is the appropriate (for Breezy-gnome), NT4, NT3.5, Win2000, XP ...:confused: 
](*,) 
Can someone enlight me about this?
I'm so close to get some Hi-Quality rips... :-| 

Thanks a lot.
Mario

---

### Post by Syco54645 on 2006-04-24
[QUOTE=VCSkier]now if only i can get the new foobar2000 0.9 to work through wine...  any suggestions?[/QUOTE]

quod libet is basically foobar for linux.  the version in dapper is great.

---

### Post by Slim Odds on 2006-04-25
[QUOTE=VCSkier]nope.  eac just rips/encodes, and burns on occasion.  :)[/QUOTE]

More specifically, it rips Audio CD's only.

---

### Post by Slim Odds on 2006-04-25
[QUOTE=quandar]I am fairly sure EAC does not do transcoding, if you want to do that I suggest picking up the GNOME app soundconverter, its really quite nice, try it.[/QUOTE]

EAC can call an external program to do the transcoding for each track that it rips.

---

### Post by quandar on 2006-04-25
[QUOTE=Slim Odds]EAC can call an external program to do the transcoding for each track that it rips.[/QUOTE]

Actually EAC dosn't transcode at all, what you are thinking of is *encoding* from a WAV to any sort of external encoder. 
And EAC dosn't only just rip audio CDs, it also can burn them (it has a full featured audio writing area in the program).

---

### Post by VCSkier on 2006-04-25
[QUOTE=Slim Odds]EAC can call an external program to do the transcoding for each track that it rips.[/QUOTE]
using the word "transcoding" in this context is misleading...  i think it is clearer to say that EAC rips the tracks into pcm waves (images or individual tracks), and then can optionally call a command line encoder to encode the wav files.

edit: quandar beat me to it.

---

### Post by quandar on 2006-04-25
[QUOTE=Syco54645]quod libet is basically foobar for linux.  the version in dapper is great.[/QUOTE]
I second this, QuodLibet is absolutely fantastic.

---

### Post by VCSkier on 2006-04-25
[QUOTE=quandar]I second this, QuodLibet is absolutely fantastic.[/QUOTE]
thanks, ill try it out.

---

### Post by Slim Odds on 2006-04-27
[QUOTE=VCSkier]using the word "transcoding" in this context is misleading...  i think it is clearer to say that EAC rips the tracks into pcm waves (images or individual tracks), and then can optionally call a command line encoder to encode the wav files.

edit: quandar beat me to it.[/QUOTE]

True, I simply used the same word that was in the original quote.

EAC rips PCM audio and can call an external program to convert to a compressed audio format.

---

### Post by kotti on 2006-06-21
Thanks for the guide. I too was having problems with EAC not recognicing either of my drives even though I followed all the instructions. I searched around for a bit and found [THIS](http://forums.gentoo.org/viewtopic-t-386370.html) page which had the cure for me. I'll quote:

> Wine does really oddball things when trying to detect CDROM drives with ide-cd. It does not recognize I am a member of the cdrom group, it seems to only check for ownership of the device file. The only way to get it to work with EAC is for the current user to be the owner of the CDROM device file (/dev/hdc is used in this example.) Before you run Wine, you need to make sure that you are the owner:

```
computer ~ $ ls -l /dev/hdc
brw-rw----  1 danomac cdrom 22, 0 Jan 10 17:57 /dev/hdc 
```

To set it manually, use chown as root (danomac is the username used in this example): 

```
root@computer ~ $ chown danomac /dev/hdc
```

**_Replace 'danomac' above with your own username!_**

I'm still having problems getting EAC (or wine itself, I'm not sure) to recognise my second drive which is better suited (i.e. faster :)) for ripping but I'll have to look into that later. I was having the same problem (no recognised drives) with DVDDecrypter earlier, I'll check if this little 'trick' helps with that too.

Edit: Yes, DVDDecrypter finds one drive now too. Using 6.06 Dapper by the way.

---

### Post by citizenkeith on 2006-07-01
[QUOTE=quandar]
**Finishing Touches**
Go into your terminal and type:
```
gedit EAC.desktop
```
and in that file put in:
```
[Desktop Entry]
Version=0.95
Encoding=UTF-8
Name=No name
Type=Application
Exec=wine ~/.wine/drive_c/Program\\ Files/Exact\\ Audio\\ Copy/EAC.exe
TryExec=
Icon=gnome-dev-cdrom-audio.png
X-GNOME-DocPath=
Terminal=false
Name[en]=Exact Audio Copy
GenericName[en]=Exact Audio Copy
Comment[en]=Rips CDs, Exact Audio Copy using WINE.

```
and then proceed to click on the launcher in Nautilus. [/QUOTE]

Everything works perfectly, except for this one. When I click on the new EAC icon, nothing happens.

Otherwise everything works fine. I launch from the command line instead of using the icon. :) Thanks for the tutorial! In the past, when using Fedora, I was never able to use EAC. This is makes life easier, since I'm creating a music server and I want good log files for each rip.

---

### Post by yaztromo on 2006-07-02
Running Kubuntu Dapper

Everytime I change the drive option to "Native Win2000/NT interface", EAC will crash next time it is opened.

Anyone else with Kubuntu got it working?

---

### Post by citizenkeith on 2006-07-02
I've been using EAC in wine to make FLAC files. I have the Compression tab setup to pass to FLAC.exe, which I copied over from my Windows partition.

When I look at the properties of each file (right-click > Propertied), it lists the File Type as MP3, even though it really is a FLAC file. In EAC, I have the compressor set to "User Defined," the extension set to .flac, and the following command line options:

```
T "artist=%a" -T "title=%t" -T "album=%g" -T "date=%y" -T "tracknumber=%n" -T "genre=%m" %s
```

The Bit Rate dropdown menu is still available, and it is set to 128 kBit/s. When I do this in Windows, it doesn't effect FLAC encoding.

Any ideas?

Keith

PS I'm still having trouble with the EAC short-cut (see my last post).

---

### Post by fhqwhgads on 2006-07-14
oops, didn't realize this was a howto thread, sorry :-#

---

### Post by spooner on 2006-10-24
Just thought I'd mention that if you want a clickable link to EAC then add it to the menu using Alacarte Menu Editor and the command

xterm -hold -e wine /home/uname/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy/EAC.exe

with uname replaced with your user name.
This solves the terminal from closing straight after the wine command is run (closing wine doh!). Please note that for some reason(that I'm not too bothered about) it doesn't work with the ~ command so the full path needs to be used hence the need to replace uname with your username.

---

### Post by Stormx on 2006-10-28
I can't get it to install. The installer loads, etc. Gets to

Extract: EAC.exe

Then freezes. I get this on the console:

```

err:ntdll:RtlpWaitForCriticalSection section 0x7e9dc000 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7e6af000 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000d, blocked by 0009, retrying (60 sec)
wine: Critical section 7e9dc000 wait failed at address 0x7efaddf0 (thread 000c), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) (null)
        0000000c    0
        0000000b    0
00000008 
        0000000d    0
        00000009    0
wine client error:b: write: Bad file descriptor
wine: Critical section 7e6af000 wait failed at address 0x7efaddf0 (thread 000d), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) (null)
        0000000d    0
        00000009    0

```

---

### Post by philbar on 2006-12-02
> **yaztromo said:**
> Running Kubuntu Dapper

Everytime I change the drive option to "Native Win2000/NT interface", EAC will crash next time it is opened.

Anyone else with Kubuntu got it working?

I'm running Ubuntu Edgy and had the same problem.

When I went back into winecfg I noticed the cd drive that was autodetected was not there so I redetected it and clicked "apply" rather than "ok" and then ran EAC will winecfg was still open. Unfortunately, when I close winecfg it loses my CD drive so I have to manually do that. If anyone knows how to fix that I'd love to hear about it.

---

### Post by Stormx on 2006-12-03
**ISSUES! Using external compressor...**

Looks very much like EAC is feeding the wrong file into the compresser. In this case its LAME. Heres the output its giving when I wine EAC.exe

Could not find "d:\BEIR~GFY\0tmp1!542.wav".
Could not find "d:\BEIR~GFY\0tmp660-!.wav".
Could not find "d:\BEIR~GFY\0tmp556)!.wav".
Could not find "d:\BEIR~GFY\0tmp58)58.wav".

That "BEIR~GFY" should be beirut - gulag orkestar

I'ma try this on ext3, see if its any different!

---

### Post by old_geekster on 2007-02-05
> **spooner said:**
> Just thought I'd mention that if you want a clickable link to EAC then add it to the menu using Alacarte Menu Editor and the command

xterm -hold -e wine /home/uname/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy/EAC.exe

with uname replaced with your user name.
This solves the terminal from closing straight after the wine command is run (closing wine doh!). Please note that for some reason(that I'm not too bothered about) it doesn't work with the ~ command so the full path needs to be used hence the need to replace uname with your username.
I installed EAC.  It works great.  I made the clickable link as suggested and that works well, also.

Since I have never used EAC before, it will take some experimenting to get things down pat.

---

### Post by 4cpo on 2007-02-08
I had the problem of no CDROM detected in EAC.

Got the problem solved after removing all/any free drive letters in winecfg.

---

### Post by 4cpo on 2007-02-09
> **citizenkeith said:**
> I've been using EAC in wine to make FLAC files. I have the Compression tab setup to pass to FLAC.exe, which I copied over from my Windows partition.

When I look at the properties of each file (right-click > Propertied), it lists the File Type as MP3, even though it really is a FLAC file. In EAC, I have the compressor set to "User Defined," the extension set to .flac, and the following command line options:

```
T "artist=%a" -T "title=%t" -T "album=%g" -T "date=%y" -T "tracknumber=%n" -T "genre=%m" %s
```

The Bit Rate dropdown menu is still available, and it is set to 128 kBit/s. When I do this in Windows, it doesn't effect FLAC encoding.

Any ideas?

Keith

PS I'm still having trouble with the EAC short-cut (see my last post).


I followed the information on this page:
[http://wiki.hydrogenaudio.org/index.php?title=EAC_and_Flac](http://wiki.hydrogenaudio.org/index.php?title=EAC_and_Flac)

I have not had the problem you describe - the files are all in FLAC.

---

### Post by Elim on 2007-02-23
> **whythehellcantilogon said:**
> I believe you need to tell EAC to use the Win32 interface. I was able to recreate your error when I switched from Win32 to the default.

Start EAC-->press F9 --> click on the interfaces tab --> select the native win32 interface. 

Hope this helps.

-Erik
I tried to do this, but when I run EAC the only interface available is "Installed external ASPI interface"; the "Native Win32 interface" is greyed out.  Any idea what's going on, and how to fix it?

---

### Post by Jarn on 2007-02-26
When I switch to the Native interface and restart the program, it freezes when it comes up. I have to forcefully terminate it and when I open it then it is back to using the default.

EDIT: Uninstalling and reinstalling EAC fixed it. I <3 this guide. Thanks guys!

---

### Post by Jay1 on 2007-03-28
> **Elim said:**
> I tried to do this, but when I run EAC the only interface available is "Installed external ASPI interface"; the "Native Win32 interface" is greyed out.  Any idea what's going on, and how to fix it?

I had this problem too.

Check in the ~/.wine/dosdevices/ directory for a pair of links for your optical drive. Mine has d: --> /media/cdrom0 and d:: --> /dev/hdc.

I had to create the second link with the command:

ln -s /dev/hdc d::

Note: The second : is not a typo.

-Jay

---

### Post by PyroMessiah on 2007-04-01
I'm sure this is a stupid question, but I'm new.  When you install EAC, where can I find the exe file?  I'm used to Program Files of course.  :confused:

---

### Post by stokedfish on 2007-04-01
1. EAC is *by far* the best ripper for *scratched* CDs
2. EAC is not better than linux rippers in any way for unscratched CDs
3. OGG sucks. I much prefer MP3. Why? You can't even hard-gain OGGs, no thanks...

---

### Post by MetalMusicAddict on 2007-04-01
For anyone looking for a native solution please look at my [GRIP HOW-TO]("http://www.ubuntuforums.org/showthread.php?t=183125hp?t=25151").

---

### Post by ajm2005 on 2007-04-18
:)

---

### Post by ajm2005 on 2007-04-18
> **PyroMessiah said:**
> I'm sure this is a stupid question, but I'm new.  When you install EAC, where can I find the exe file?  I'm used to Program Files of course.  :confused:


it's stored in the hidden ".wine" directory in your home (~/) folder. the exact location is:

[FONT="Courier New"]~/.wine/drive_c/Program Files/Exact Audio Copy/EAC.exe[/FONT]

Starting from your home directory, type (in a terminal window):

[FONT="Courier New"]cd ".wine/drive_c/Program Files/Exact Audio Copy"[/FONT]

to change to the Exact Audio Copy directory. From here you can type:

[FONT="Courier New"]wine EAC.exe[/FONT]

to launch Exact Audio Copy.

Or you can type straight from your home directory:

[FONT="Courier New"]wine ~/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy/EAC.exe[/FONT]

You can set up either icons, or a little script, to launch the program (so you don't have to type the above every time you want to run the program).

---

### Post by beachreader on 2007-04-21
this command line ; wine ~/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy/EAC.exe  is a lot memorize....is there a way to create a short cut. thanks!!

---

### Post by beachreader on 2007-04-22
how do uninstall EAC...I am having lots of problems and cna't find the files anywhere. thanks!

---

### Post by eyelessfade on 2007-04-22
if its the only wine program you have installed, just do a rm -rf ~/.wine

---

### Post by eyelessfade on 2007-04-22
To bad that EAC doesn't run native on linux. Most of what makes EAC great is gpl or bsd lisence so it would be nice if he gave back and released the source.

---

### Post by HeelsFan on 2007-04-24
I was able to run EAC in WINE great.  I even was able to use a LAME encoder with a specific preset.

My only issue is that when I rip CDs I have EAC automatically delete the WAV files and just keep the MP3s.  While running EAC in WINE, it did not delete the WAV files and in addition did not label my MP3 files correctly.  The MP3 file names remained the temporary file names for some reason.

Anyone run into this problem and have a solution?

Thanks in advance!

---

### Post by ajm2005 on 2007-05-11
:)

---

### Post by brodiepearce on 2007-05-11
I can't get it to detect my CD-Drive, When I do the "Auto detect NOW" under the drive settings menu (F10), "No Audio CD Detected" pops up immediately.

---

### Post by JamesAt43 on 2007-05-18
> **ajm2005 said:**
> when I try to retrieve track information from the online freedb database (Process batch freedb queries, from the Database menu) the program freezes. I end up having to kill it via ctrl-alt-escape, which leaves a zombie processes that hangs around forever. anyone else have this problem?

Yes, I have the same problem.  I haven't figured out why.

---

### Post by yahooadam on 2007-05-25
> **JamesAt43 said:**
> Yes, I have the same problem.  I haven't figured out why.
im geting exactly the same problem

does anyone have any ideas on this, anything to do with cddb and it crashes ....

Im using EAC0.9B4 (which is required for "uber" standard rips)

---

### Post by Jarn on 2007-06-10
When I try to switch it to the Native Win32 ASPI and then restart EAC, it freezes when it opens and I'm left with it at the Installed external ASPI.

EDIT: Fixed this, turns out the problem has something to do with installing EAC when Wine doesn't like your drive setup. I deleted the ~/.wine/dosdevices folder, ran wineprefixcreate, had it autodetect my drives, and reinstalled.

However, I, too, am now having the problem where it freezes while trying to contact freedb. I am currently trying to run it with winedebug set to all and saving the output to a file, but it's moving very slow from all the output that I'm not sure I'll ever get there and the log file has surpassed the 750mb mark.

---

### Post by yahooadam on 2007-06-10
> **Jarn said:**
> When I try to switch it to the Native Win32 ASPI and then restart EAC, it freezes when it opens and I'm left with it at the Installed external ASPI.

EDIT: Fixed this, turns out the problem has something to do with installing EAC when Wine doesn't like your drive setup. I deleted the ~/.wine/dosdevices folder, ran wineprefixcreate, had it autodetect my drives, and reinstalled.

However, I, too, am now having the problem where it freezes while trying to contact freedb. I am currently trying to run it with winedebug set to all and saving the output to a file, but it's moving very slow from all the output that I'm not sure I'll ever get there and the log file has surpassed the 750mb mark.
is it checking the CDDB, and do you see anything at all ?

Also does the command line come up with any errors ?

---

### Post by Jarn on 2007-06-10
No errors in the command line. It happens at connecting. It freezes then.

---

### Post by spooner on 2007-06-15
> **ajm2005 said:**
> when I try to retrieve track information from the online freedb database (Process batch freedb queries, from the Database menu) the program freezes. I end up having to kill it via ctrl-alt-escape, which leaves a zombie processes that hangs around forever. anyone else have this problem?

What version of wine are you using?
Type "wine --version" in command window.
I had this problem when I upgraded to the new 0.9.38 version in the wine repositories. If you switch back to 0.9.33 in the standard repos it works fine again.
Also, if you want to simulate a windows reboot the command "wineboot" is useful
I also noticed that only the first word was being displayed per line of code. I hope this does not become and accepted version as that would suck! Way too buggy to be a release!

---

### Post by ajm2005 on 2007-08-03
:)

---

### Post by ChrisNiemy on 2007-08-03
when running **winecfg** before, you should switch in the settings to Windows 2000 or WinXP. Then you should choose in the EAC setting the use of the native interface. Restart EAC, then it should work.

When EAC freezes run **winecfg** and disable some graphic features, no directx, no acceleration, not using metacity as window manager etc.

---

### Post by iceolate on 2007-08-18
I'm having a problem with it. I set up everything fine, but it's doesn't like my read commands. I specified MMC1 in the drive settings, but it tells me i don't have the right one. Can someone help?

---

### Post by flowbot on 2007-10-10
> **HeelsFan said:**
> I was able to run EAC in WINE great.  I even was able to use a LAME encoder with a specific preset.

My only issue is that when I rip CDs I have EAC automatically delete the WAV files and just keep the MP3s.  While running EAC in WINE, it did not delete the WAV files and in addition did not label my MP3 files correctly.  The MP3 file names remained the temporary file names for some reason.

Anyone run into this problem and have a solution?

Thanks in advance!

Same problem for me, using Wine repos (not ubuntu ones) .... no solution from me, though :(

---

### Post by Nike T on 2007-12-06
Help, I switched over, since I think that this is better than Windows.  I want to use eac with React.  I'm using wine 0.9.5 and eac V.99 prebeta 3.  I downloaded it and installed it, I tried to change it to native win32 whatever and it always freezes, I tried everything here, at least twice for all of them.  It just doesn't work.  And also React would work on ubuntu right?  O yea and I can't do anything with freedb either that freezes it too, and I don't know what to do

---

### Post by VCSkier on 2007-12-09
For those having difficulties, I'd recommend Rubyripper.  Check it out [here]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper") or [here]("http://code.google.com/p/rubyripper/").  K3B can also be good, if you need images and cue sheet's, though it's rather big and bloated, and not completely secure.

---

### Post by VCSkier on 2007-12-14
abcde (A Better CD Encoder) is also an excellent ripper, but it is command-line only.  It seems to me to have the most extensive set of features, which can all be configured rather easily by editing the configuration file.  It can be found in in the Universe repo.  It's not secure either, but supports replaygain, as well as ripping to single-file FLAC's w/ embedded cue sheets, and some other excellent and unique features.

---

### Post by coderipper on 2008-02-23
> **flowbot said:**
> Same problem for me, using Wine repos (not ubuntu ones) .... no solution from me, though :(

> **HeelsFan said:**
> I was able to run EAC in WINE great.  I even was able to use a LAME encoder with a specific preset.

My only issue is that when I rip CDs I have EAC automatically delete the WAV files and just keep the MP3s.  While running EAC in WINE, it did not delete the WAV files and in addition did not label my MP3 files correctly.  The MP3 file names remained the temporary file names for some reason.

Anyone run into this problem and have a solution?

Thanks in advance!

Press F11 (Compression Options) and select the "Waveform" tab.

Check the box "Do not write WAV header to file"

Enter the file extension ".mp3" then click on "OK".

You're done.  Ripped filenames will now end with ".mp3".

---

### Post by waldbauernbub on 2008-03-17
I solved the problem (on my machine, hope it works for you, too)

Problem: 
EAC doesn't recognize my CD drives and I am not able to select the "Native Win32 Interface for NT/2000/XP" in the EAC interfaces option
(as described at the beginning of this thread)

under the drive tab in Alt+F2 winecfg I had 3 CD-drives listed although I only have 2 installed:
K: /media/cdrom0
L: /media/cdrom1
M: /media/cdrom2 (this is the drive that doesn't exist)

I deleted the third drive (in the wincfg) and now I can apply the all setting in EAC and have just ripped my first CD under Ubuntu.

Attention: Maybe this third drives serves any purpose I am not familiar with.

much luck
harald

---

### Post by sm2uyn on 2008-05-04
I've had EAC running flawlessly for about 6 months, but when I started it today I got some unexpected behaviour:

Either (1) program freezes after a while. If not before then when trying to rip. or (2) EAC accualy starts ripping (or what to call it), but doesn't spin up CD and produces 40 sec files of silence.

Anyone who knows if this is related to wine 0.9.61, (K)Ubuntu 8.04 or to something else? I haven't installed any programs through wine or made any changes to my wine configuration except upgrading a few versions since ripping was last working ok two weeks ago.

I've noticed that the device ID reported in EAC has changed, and another application I run through wine (CATraxx music database) can no longer scan CDs.

---

### Post by chooban on 2008-05-20
I've just been having similar problems with EAC. It would hang on gap detection, or when I tried to rip the disc it would spin up and then just get no further.

I seem to have got around the issue by using the 2.6.22-14 kernel that comes with Hardy. It's ripping at the moment, anyway!

---

### Post by Craig73 on 2008-07-23
> **chooban said:**
> I've just been having similar problems with EAC. It would hang on gap detection, or when I tried to rip the disc it would spin up and then just get no further.

I seem to have got around the issue by using the 2.6.22-14 kernel that comes with Hardy. It's ripping at the moment, anyway!

Can you clarify - did you go to a newer or an older kernel?  I'm running Kernel 2.6.24-19-generic with Hardy and I am getting the same symptoms.

---

### Post by jaems-kun on 2008-07-24
hmm, I can't get the files to encode in flac.  It doesn't turn any errors up or anything, eac says "running external codec program", but the files stay uncompressed wav.  

I was using the included flac.exe, I tried installing the windows flac from the flac website.  It installed, but during the process it gave me an error saying a file couldn't be installed properly, it didn't tell me what exactly, but it said that flac frontend might not work (which it doesn't, the window just closes as soon I open it).  I figured that shouldn't be a big deal since I wouldn't be using the frontend anyway, but the results with eac were the same, so maybe I do need the frontend?

Can I whine about that here or is there a more specific flac thread I should be checking out?

---

### Post by stepdown on 2008-09-08
Just followed this guide with 0.99pb4, and used the FLAC.exe included with the install.

Worked perfectly.

---

### Post by canakas on 2008-10-30
Hi community,

Very nice guide indeed.

One tip that should not pass us by, in case EAC stops detecting your drives for some reason after you reboot is this:

[http://www.winehq.org/pipermail/wine-users/2007-June/027348.html](http://www.winehq.org/pipermail/wine-users/2007-June/027348.html)

What it suggests is to put a data cd in the drive, let it mount, then use winecfg to make sure the /media/yourmounteddisc is set as a CDROM.
Now restart EAC and your drive will be detected. Switch to an audio CD and get started.

This worked for me after having EAC not detect the drive anymore after a reboot. 

Now I can use the drive tests in EAC, and I have AccurateRip working. Encoding with the FLAC package bundled with EAC works great.

I use UbuntuStudio (Hardy) 2.6.24-21-rt, with Wine 1.1.7 (repo) and EAC 0.99b4. The drive is a NEC 3540 in an external box connected through firewire.

Hope this helps someone :p

-canakas

---

### Post by kgdowley on 2008-12-10
> **jaems-kun said:**
> hmm, I can't get the files to encode in flac.  It doesn't turn any errors up or anything, eac says "running external codec program", but the files stay uncompressed wav.  

I was using the included flac.exe, I tried installing the windows flac from the flac website.  It installed, but during the process it gave me an error saying a file couldn't be installed properly, it didn't tell me what exactly, but it said that flac frontend might not work (which it doesn't, the window just closes as soon I open it).  I figured that shouldn't be a big deal since I wouldn't be using the frontend anyway, but the results with eac were the same, so maybe I do need the frontend?

Can I whine about that here or is there a more specific flac thread I should be checking out?

I was having a similar problem.  I used the wiki guide on hydrogenaudio to configure flac and eac.  They recommend to use the "Use external program for compression option".  In the 'additional command-line options' box, I put: -5 -T "artist=%a" -T "title=%t" -T "album=%g" -T "date=%y" -T "tracknumber=%n" -T "genre=%m" %s

This is where I found an error.  There was an extra space after %s, and I'm fairly certain this is what was causing the problem.

You might also consider checking: 'check for external programs return code'.  It might help you debug a bit.

Hopefully this helps!

---

### Post by dirty_von_Shotgun on 2009-01-30
> **jaems-kun said:**
> hmm, I can't get the files to encode in flac.  It doesn't turn any errors up or anything, eac says "running external codec program", but the files stay uncompressed wav.  

I was using the included flac.exe, I tried installing the windows flac from the flac website.  It installed, but during the process it gave me an error saying a file couldn't be installed properly, it didn't tell me what exactly, but it said that flac frontend might not work (which it doesn't, the window just closes as soon I open it).  I figured that shouldn't be a big deal since I wouldn't be using the frontend anyway, but the results with eac were the same, so maybe I do need the frontend?

Can I whine about that here or is there a more specific flac thread I should be checking out?


This solution worked for me:

Go to your Windows partition C:/Program Files->Exact Audio Copy->Flac and copy Flac.exe to your Ubuntu partition wherever you want.

Then go to EAC compression options and point the external compressor to the Flac.exe file on your ubuntu partition.

I wish I could give better details but I'm ripping a CD right now so I can't look at the options. 

Let me know if this helps or if you need me to be clearer on anything.

---

### Post by UncleStinky on 2009-02-08
> **quandar said:**
> **Introduction**
**Installing EAC**
Download the installer for [Exact Audio Copy](http://www.exactaudiocopy.de/eac-0.95b4.exe), then double-click eac-0.95b4.exe on the downloaded file and simply install like any other app.


This is the first application that I am trying to get working under Wine.  So far, no matter what I do, I cannot get the EAC package to install.  Here is the error message I receive when double clicking on eac-0.99pb4.exe:

[/media/Data/Download/Software/EAC/eac-0.99pb4.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/Data/Download/Software/EAC/eac-0.99pb4.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/Data/Download/Software/EAC/eac-0.99pb4.exe or
          /media/Data/Download/Software/EAC/eac-0.99pb4.exe.zip, and cannot find /media/Data/Download/Software/EAC/eac-0.99pb4.exe.ZIP, period.

How do I get EAC to install?  Any suggestions?


Thanks

---

### Post by mailforbiz on 2009-03-03
Sorry, I wish I could help you UncleStinky. For me, EAC worked fine under Wine. The questions I have are: (a) what is the best compressor to use (FLAC, Lame etc) (b) why can't I seem to be create MP3 out of WAVs? I click on the MP3 button in EAC and it brings up the dialog for where to save and it only has WAV as the type to store in the dropdown. Any thoughts?

UPDATE: Ok, so I answered my own questions and I'm somewhat embarassed now for asking them. Answer (a): FLAC is a archival-quality format as opposed to mp3 which is what portable players support. Lame still seems to be the best to use for general purpose. Answer (b) Once I installed lame and pointed to it in the external compressor, I was able to get the wav->mp3 working. Hopefully, this will help some newbie someday. :-)

---

### Post by ATL_Braves on 2009-03-18
Please Help Me!!

I've used EAC w/ WINE for some time. I always converted my CD's to .ogg files without any problems. 

Now I want to convert my discs to .mp3 (Rockbox isn't available on my new ipod). I downloaded LAME (from here: [http://www.rarewares.org/mp3-lame-bundle.php](http://www.rarewares.org/mp3-lame-bundle.php)) added a new profile with these settings: [http://i40.tinypic.com/119uejo.png](http://i40.tinypic.com/119uejo.png) . The additional command line options I used were: -V 2 –vbr-new –add-id3v2 –ta "%a" –tt "%t" –tg "%m" –tl "%g" –ty "%y" –tn "%n" %s %d . This is the error I get: [http://i40.tinypic.com/2vnf72h.png](http://i40.tinypic.com/2vnf72h.png) . I have scoured the internet, as well as other forums (here and hydrogen audio), and I cannot find a solution. 

Any thoughts?

---

### Post by logos34 on 2009-03-19
you could maybe try disabling CRC and using the shortened command line options, as described here:

[http://www.teqnilogik.com/tutorials/eac.shtml#CompressionOptionsMP3](http://www.teqnilogik.com/tutorials/eac.shtml#CompressionOptionsMP3)

check your tag options too

That's what I use and it works fine

---

### Post by DD0C on 2009-05-01
I just installed EAC on Jaunty Jackalope using the latest Wine (1.0.1 from the repositories). EAC detects my drive, rips the audio track to wave (can see and play it in the directory). But, when using lame as an external compressor, I get this error:

The external compressor returned an error!

Options: "H:\Music\UNKN~QYS\1tmp1!542.wav"
"H:\Music\UNKN~QYS\1tmp1!542.mp3" -br 128000 -hq

File : H:\Music\Unknown Artist - Unknown Title\19 - Unknown Artist - Track19.wav


I think the problem is the wrong filename is sent to lame.exe (UNKN~QYS as a folder). Any idea how I can solve this? I would like to rip my audio cd's like i used to do in wintendo.

---

### Post by logos34 on 2009-05-01
> **DD0C said:**
> I just installed EAC on Jaunty Jackalope using the latest Wine (1.0.1 from the repositories). EAC detects my drive, rips the audio track to wave (can see and play it in the directory). But, when using lame as an external compressor, I get this error:

The external compressor returned an error!

Options: "H:\Music\UNKN~QYS\1tmp1!542.wav"
"H:\Music\UNKN~QYS\1tmp1!542.mp3" -br 128000 -hq

File : H:\Music\Unknown Artist - Unknown Title\19 - Unknown Artist - Track19.wav


I think the problem is the wrong filename is sent to lame.exe (UNKN~QYS as a folder). Any idea how I can solve this? I would like to rip my audio cd's like i used to do in wintendo.

maybe it's choking on invalid genre or the id3 tag settings. just a guess. You might want to post the "additional command-line options" line you're using, and what boxes you have checked at the bottom of that tab, as well as ID3 tab.  

[http://www.hydrogenaudio.org/forums/lofiversion/index.php/t40331.html](http://www.hydrogenaudio.org/forums/lofiversion/index.php/t40331.html)

---

### Post by DD0C on 2009-05-02
> **logos34 said:**
> maybe it's choking on invalid genre or the id3 tag settings. just a guess. You might want to post the "additional command-line options" line you're using, and what boxes you have checked at the bottom of that tab, as well as ID3 tab.  

[http://www.hydrogenaudio.org/forums/lofiversion/index.php/t40331.html](http://www.hydrogenaudio.org/forums/lofiversion/index.php/t40331.html)

Here are screenshots of the requested tabs:
[IMG]http://img301.imageshack.us/img301/2042/screenshotuod.png[/IMG]


[IMG]http://img395.imageshack.us/img395/9563/screenshot1d.png[/IMG]

[IMG]http://img301.imageshack.us/img301/7329/screenshot2c.png[/IMG]



Another thing I noticed: during ripping the filename of the wave file is Track02, when I get the error message, it's something like Ttmp1!542, when I click ok it changes back to Track02. I think this is normal, but anyway.. doesn't hurt if I mention it.

What I already tried (and didn't help):
- writing the wave file in a non dotted folder, something like /home/user/music
- clicking the first, second and fourth ticks in the ID3 tag
- moving lame.exe to another folder, also something like /home/user/music or something
- changing parameter passing scheme to user defined
- everything of the ID3 tag in the command line command instead of using the ID3 tagging from EAC

Btw: I followed the instructions on the Hydrogenaudio wiki . I used to use EAC some time ago under Intrepid or Hardy (don't remember) and everything worked that time. It's no drive problem or something. Besides, the wave is ripped.. just the encoding doesn't start.

If anyone can help me, please!

I'm using Jaunty and EAC 0.99 prebeta4

---

### Post by DD0C on 2009-05-02
Fixed. I removed EAC and reinstalled it, after that, everything worked.. with the SAME settings as stated before! Very strange..

---

### Post by logos34 on 2009-05-02
> **DD0C said:**
> Fixed. I removed EAC and reinstalled it, after that, everything worked.. with the SAME settings as stated before! Very strange..

I know what you mean--had a similar experience a year ago.  EAC would go all wonky on startup and feeze, thought it was the EAC Options>interface selection, but no...I reinstalled a couple of times, didn't work, even reinstalled different versions of wine--but nothing worked.  Turns out the culprit, IIRC, was in one of the config settings files.  After I deleted it everything a-ok.

---

### Post by s2n6 on 2009-05-04
t

---

### Post by l-x-l on 2009-05-15
> **logos34 said:**
> I know what you mean--had a similar experience a year ago.  EAC would go all wonky on startup and feeze, thought it was the EAC Options>interface selection, but no...I reinstalled a couple of times, didn't work, even reinstalled different versions of wine--but nothing worked.  Turns out the culprit, IIRC, was in one of the config settings files.  After I deleted it everything a-ok.

Having the same problem. What's IIRC? Where is it? So I can delete & see if it's causing my problem. Thx.

---

### Post by logos34 on 2009-05-15
> **l-x-l said:**
> What's IIRC? Where is it? So I can delete & see if it's causing my problem. Thx.

Not so fast, dude, that's my memory your talking about!  :lolflag:

'IIRC' = abbreviation for 'if I recall correctly'

---

### Post by l-x-l on 2009-05-15
LoL!! I've been using the net for a while now & never came across IIRC before. Guess I can't delete that after all. Thx anyway.

---

### Post by Naguz on 2009-07-15
I can't select the native interface. Eveything but the top alternative is greyed out. Have tried to set it to both win2k and xp in winecfg, and manually set the cd-rom to cd rom in winecfg too. It seems to be ripping OK, is there any chance of errors by using the "wrong" interface?

---

### Post by Naguz on 2009-07-16
I can't get lame encoding to work either. I was thinking it would work OK to point EAC to the win32 lame.exe, but it outputs "Can't init outfile", så i guess something is a bit off. Any tips? Setting this up on my moms computer, so it must be a one click procedure. Using a second program to encode the tracks is not really an option.

---

### Post by Leslie_K. on 2009-11-10
> **Naguz said:**
> I can't get lame encoding to work either. I was thinking it would work OK to point EAC to the win32 lame.exe, but it outputs "Can't init outfile", så i guess something is a bit off. Any tips? Setting this up on my moms computer, so it must be a one click procedure. Using a second program to encode the tracks is not really an option.

Running Ubuntu 9.10 with Wine 1.0.1 and [EAC 0.99 prebeta 5]("http://www.exactaudiocopy.de/en/index.php/resources/download/") which comes with FLAC 1.2.1 by default I managed to encode the ripped WAV file to FLAC. Then I downloaded [LAME 3.98.2]("http://rarewares.poskolio.com/lame3.98.2.zip") win32 binaries, extracted the lame.exe and lame.dll (I guess it's not needed) and using Applications->Wine->Browse C:\ Drive just created a the following directory: C:\Program Files\Exact Audio Copy\Lame plus I copied the two extracted files there. After starting up EAC via Applications->Wine->Programs->Exact Audio Copy I went to EAC->Compression Options and there I modified the options to:
```
[X] Use external program for compression
Parameter passing scheme: User Defined Encoder
Use file extension: .mp3
Program, including path, used for compression: C:\Program Files\Exact Audio Copy\LAME\LAME.EXE (Instead of browsing I just edited the path.)
Additional command-line options: --vbr-new %s %d
Bit rate: 320 kBit/s (It doesn't matter, by the way.)
[X] Delete WAV after compression
[ ] Use CRC check
[ ] Add ID3 tag
[X] Check for external programs return code
```
This way I managed to copy the tracks selected flawlessly.
Tell me if that helped your problem! (I guess you should give a try to the same versions of the software I downloaded - links provided.)
By the way, I didn't use predefined extraction path, so EAC always prompts me when copying tracks - maybe that also matters, but not sure?

---

### Post by mordak13 on 2010-05-21
Thanks for this info guys/ladys. I do audio trading online and most site require EAC rips to guarantee the quality is the best possible for archiving purposes and then we compress with FLAC. I have Windows 7 available but have been a linux exclusive user since 2004 and using Linux since 1998. I hate to use Windows if I can do it with Linux. I'm not to proud to use Wine when needed either. After all Wine Is Not an Emulator. ;-)

---

### Post by skralljt on 2011-02-24
The only two windows apps I really want to keep around are eac and foobar2000 in that order.  Easytag requires about three times the work to do the same stuff and linux rippers don't have the same functionality with accuraterip and just working without a bunch of horsesh*t.  
I have not had a problem with eac using default installs of wine and eac for over 2 years but I never encode using lame binaries, only the aotuv tuned vorbis encoder or flac.  If you are having trouble with eac's user defined encoder, you can always use it to just rip to .wav.  After all, that is what separates good rippers from mediocre rippers: How well can they turn a cd into a .wav file?  Once you have the .wav file just use a commandline encoder.  
If that sounds like too much work, both abcde and rubyripper perform admirably if you can figure out how to set them up correctly but that is a whole 'nother can of worms.

---

### Post by Ron O on 2011-03-02
I've used EAC for years in Windoze, and I just installed v.0.99pb5 in Ubuntu through Wine and let it put the EAC folder into wine program files, rather than try to decide which files in the folder I do not need. I expanded LAME 3.98.4 and put the entire folder into the EAC folder and pointed to lame.exe in EAC setup. Easy. And it works flawlessly- in fact it's WAY faster than it ever was in Windoze. 

EAC defaulted to "installed external ASPI interface" instead of win32, and since it works so well, I left it alone. I'm assuming it found the ASPI interface in Ubuntu? EAC is extracting wav.files at about 35x and it does an average CD at 192 bit rate in under 5 minutes. This is a SUPERB program, and thanks to the persistent work of the Wine developers, it runs great.

The only thing I miss is the error LEDs. They don't work in Ubuntu. In Windoze, if they lit up beyond the first row, you could see that EAC was re-sampling to get two checksums that match- one of the keys to it's accuracy. But I've run it enough before that I can tell by the track progress if it is resampling anyway. My last link to Windoze is finally gone. I could remove Windoze since I never use it, but I would rather use GParted to HUMILIATE it by cutting it's partition size down to the bare minimum.

---

### Post by skralljt on 2011-04-27
I have found that the red led error lights do light up.  I wish that my cd's weren't scratched enough for me to have noticed this!  The one problem I have with eac 1.0 beta 1 is that it isn't creating correct log files.  Rather, it creates a log file with only "ÿþE" in it which it did not do in previous versions on previous versions of ubuntu.  I guess I will email the author about this bug but not sure he'll care too much about wine users.  I have tried different settings like "English Only", checking and unchecking append checksum, and manually clicking on write log file.  They all yield the same goofy cyrillic characters or whatever they are.

---

### Post by micbelue425 on 2012-02-28
Do any of you guys use a Macbook with EAC 1.0b3? My drive doesn't seem to be recognized, but for EAC 0.95b4 it is recognized (will try 0.99pb5).

---

### Post by dun270 on 2012-12-19
You don't need EAC, Wine, or even Windows anymore to extract individual tracks from wav, ape, flac files with cue sheets.
Use flacon, at [https://code.google.com/p/flacon/](https://code.google.com/p/flacon/) or get it with apt-get:
  sudo add-apt-repository ppa:flacon
  sudo apt-get update
  sudo apt-get install flacon
It splits all wav, ape, flac to individual tracks with custom audio levels, and outputs files to mp3, flac, ogg, etc.
I may never see a WinXP screen again!

---

