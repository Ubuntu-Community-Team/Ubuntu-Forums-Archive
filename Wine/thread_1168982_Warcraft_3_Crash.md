---
title: "Warcraft 3 Crash"
date: 2009-05-24
forum: Wine
---

### Post by zeroo on 2009-05-24
So I'm running Warcraft 3 under wine, and everything runs fine except for that fact that after 15 minutes it just crashes. 
It says:
FATAL ERROR!
The instruction at '0x7DD2FC34' referenced memory at '0x00b5c6E4'
The memory could not be 'read'.

Press OK to terminate the application.


Any ideas on whats going on?

---

### Post by khelben1979 on 2009-05-24
Are you using it with the -opelgl parameter? You can also try to see if your screensaver messes it up too. Maybe turn it off?

If your computer is suffering from bad ventilation inside it can also be that it get's too hot inside. What hardware configuration do you have?

(Time for me to finally get some sleep, back again later..)

---

### Post by zeroo on 2009-05-24
Yeah, I used regedit so it launched with opengl every time. Screen saver is off anyway.  I have a Radeon 4870, if that makes any difference and this is what terminal says. 

fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f650,0x00000000), stub!
wine w3l.exe -window
zero@zero-desktop:~/Desktop/Warcraft$ err:ole:CoCreateInstance apartment not initialised
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f650,0x00000000), stub!
fixme:secur32:schan_InitializeSecurityContextW Using hardcoded "NORMAL" priority
fixme:secur32:schan_QueryContextAttributesA Unhandled attribute 0x53

---

### Post by NightMKoder on 2009-05-24
Video card driver & wine version?

---

### Post by zeroo on 2009-05-24
Wine Version: 1.1.22
Video Driver: ATI/AMD proprietary FGLRX graphics driver

---

### Post by NightMKoder on 2009-05-25
I remember for ATI you need to disable some extension to get more stability/fps:

> 
# Open the registry editor and navigate to the following key

HKEY_CURRENT_USER\Software\Wine\
# Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
#

Right-click on the wine folder and select [NEW] then [KEY]
#

Replace the text New Key #1 with OpenGL
#

Right-click in the right hand pane and select [NEW] then [String Value]
#

Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
# Then double click anywhere on the line, a dialog box will open.
#

In the value field type GL_ARB_vertex_buffer_object

Please note that after using this tweak, the icon pictures may misplace themselves. For example, the icon for "gold" will look like and icon for an orb. 


See if that helps. Otherwise...blame your drivers.

---

### Post by zeroo on 2009-05-25
So I used the exception thing and it seemed to have made it run longer then usual, yet still the crash.
When it crashes terminal comes out with this:
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7abae518

---

### Post by personjerry on 2009-05-28
bump

my wciii runs for a while, then same crash as post right above (obviously mem location differs but same error code). doesn't seem to happen if not on bnet. had error before the mentioned ati card tweak, which did nothing.

same card, drivers, wine version.

---

### Post by Troll_the_Great on 2009-05-29
I had the same problem, but I managed to fix it by using an older version of wine (1.03) without the -opengl at the end. 
   Anyway, I hope the wine developers will soon solve the problem with the 1.23 patch.
Cheers!

---

### Post by personjerry on 2009-05-29
do you mean 1.0rc-3?

that didn't work for me

---

### Post by zeroo on 2009-05-29
If you have the same card and drivers as I do,  I'm beginning to think its the drivers we have. 
Still it would be nice to know some sort of fix, since crashing during every dota game is getting annoying.  

Anyone?

---

### Post by racerraul on 2009-05-30
I have W3 ROC\TFT 1.23 working with Wine 1.1.22...

But are unable to connect to LAN games... we can see them, from each others computers, but connection fails.  I was able to fix this with Windows by setting up rules in the firewalls for port 6112-6119, but I dont have any firewalls setup with Ubuntu... all the machines are running Intrepid.

Any ideas?  from what I have researched, it looks like I am in need of a Wine patch\hack for 1.1.22

---

### Post by EvilTchnlgy on 2009-05-30
I am having the same problem on 9.0.4 with a geforece 8800 gt with the proprietary nvidia drivers.

---

### Post by BoneSmash on 2009-05-30
This crash most likely has nothing to do with your graphics, it's these two errors that cause the crash:
fixme:secur32:schan_InitializeSecurityContextW Using hardcoded "NORMAL" priority
fixme:secur32:schan_QueryContextAttributesA Unhandled attribute 0x53

The reason some older versions of Wine work is because in one of the recent development builds secur32:schan_InitializeSecurityContextW got stubbed but never implemented, so it crashes.

It is possible this isn't the reason for your crash, but most likely this is the culprit.

---

### Post by EvilTchnlgy on 2009-05-30
I just downloaded an old version of wine to see if my system presents the same error in versions that are known to work properly to isolate the cause of the problem. The patched version of wine is installing now and I'll report back.

---

### Post by personjerry on 2009-05-30
i'm not actually sure if the 1.0rc3 works or not, the lag is ridiculous (i think it may have to do with my processor partly, whenever I play some 3-d wine game the first 1000 frames or so are extremely slow and then it works well, but the frames may go by very slowly) even though other apps work well during this time

using a AM3 quad-core 3.0ghz phenom II processor

---

### Post by EvilTchnlgy on 2009-05-30
Well I didn't actually get that far... I tried compiling a few versions of wine but kept getting 
```
error: called object &#8216;pFT_MulFix&#8217; is not a function
```
that was on my clipboard but I know there was alot mroe code that it spit out after my failed make install.
I hate to hijack the thread a little but from what I've read this issue stems from a change in freetype. If anyone has info on how to get past this I was planning on seeing what the most recent version of wine will run wc3 without this error is.

---

### Post by personjerry on 2009-06-01
I've tried 1.13, 1.0-rc3, and 1.23 (with -opengl) and they did not work.

---

### Post by personjerry on 2009-06-02
On the other hand, they (at least 1.23) works without -opengl, but is ridiculously slow (frames don't update well)

---

### Post by personjerry on 2009-06-03
uh bump.

---

### Post by sarunasm on 2009-06-04
when i connect to battle.net within 1 minute i get 

Fatal error

program:    war3.exe
exception: 0xc0000005 (ACCESS_VIOLATION) at
0073:7DC0DC0DBE4

The instruction as 0x7DC0DBE4 referenced memory at 0x31F3C17C
The memory could not be read

Pres OK to terminate application.



Ubuntu 9.04 wine 1.1.22 nvidia 8600gts

Any ideas? :(

---

### Post by personjerry on 2009-06-04
does that happen even if you join a game before the error?

---

### Post by sarunasm on 2009-06-05
If i join a game no errors.but if i stay in chat or i looking for games where to join after aprox 30 sec i geting error
this error with warcraft 3 patch 1.23

---

### Post by personjerry on 2009-06-08
Imo that's a different (albeit similar) bug

---

### Post by shae on 2009-06-08
Perhaps you could give my repo a try for wine.  I use it to play WC3 all the time.  Eventually I will also add the snoopy WC hosting utility as well.

[https://launchpad.net/~starfall87/+archive/ppa](https://launchpad.net/~starfall87/+archive/ppa)

I am currently using wine 1.1.21 + githacks + a patch to fix minimization in OpenGL mode.
Just install the keyring package and refresh your sources. Then you can install wine from my repo, though you may need to force the version in synaptic.

---

### Post by personjerry on 2009-06-11
didn't work. This is how I managed to play warcraft: I used virtualbox

---

### Post by stev47 on 2009-06-13
I've had the same problem.
It is not a wine problem. I tried various versions and hacks and nothing worked.

It seems to be introduced by fglrx version 8.602 (Catalyst 9.4).
Installing version 8.593 (Catalyst 9.3) solved the problem for me.

Greetings

---

### Post by wowsushi on 2009-06-13
I am having a similar problem. 
 I am trying to install wow on ubuntu 9.04x64.
I have installed wine 1.1.23 and have succesfully downloaded and pached wow all the way to the current patch level.
I can start the wow launcher, but when i hit PLAY or start WoW.exe through Wine WOW crashes.
The program never really starts since it has not produced a config.wtf file.

My log from wine looks like this:
Wine WoW.exe -opengl

fixme:advapi:SetSecurityInfo stub  archive
Data\enGB\patch-enGB.MPQ opened archive  
Data\patch.MPQ opened archive  
Data\enGB\patch-enGB-2.MPQ opened archive 
Data\patch-2.MPQ opened archive 
 Data\expansion.MPQ opened archive 
Data\lichking.MPQ opened archive 
 Data\common.MPQ opened archive  
Data\common-2.MPQ opened archive  
Data\enGB\locale-enGB.MPQ opened archive  
Data\enGB\speech-enGB.MPQ opened archive  
Data\enGB\expansion-locale-enGB.MPQ opened archive 
 Data\enGB\lichking-locale-enGB.MPQ opened archive 
 Data\enGB\expansion-speech-enGB.MPQ opened archive  
Data\enGB\lichking-speech-enGB.MPQ opened  
fixme:win:EnumDisplayDevicesW ((null),0,0x39edac,0x00000000), stub! 

The wow log says:
This application has encountered a critical error:
ERROR #132 (0x85100084) Fatal Exception
Program: C:\Programmer\World of Warcraft\WoW.exe Exception: 0xC0000005 (ACCESS_VIOLATION) at 0023:7CD9396A 

The instruction at xxxxxxxxx referenced memory at yyyyyyy. The memory could not be read.

 Can anyone tell me what the problem seems to be, and how to fix it?

---

### Post by ge0ffrey on 2009-08-01
I got the same problem: I can join battlenet and start searching for a game, but if it takes longer then 30 seconds it crashes (otherwise it doesn't and the game plays fine).

The 1.0 version of wine didn't have this problem.

---

### Post by ge0ffrey on 2009-08-01
Vote for the bug in wine:
[http://bugs.winehq.org/show_bug.cgi?id=18997](http://bugs.winehq.org/show_bug.cgi?id=18997)

---

### Post by freackout on 2009-11-07
> **personjerry said:**
> do you mean 1.0rc-3?

that didn't work for me

WORKS FOR ME ***********(nvidia with compiz effects on and twinview 2*24" monitors) + high defenition on runescape too though thats javascript************** wish i could give you a screenshot but dunno how to put it here without link.
set it up 4 my son he likes wow linch king (3)

dont forget the opengl parameter.......
wine wow.exe -opengl (ie:- wine /pathto/install.exe -opengl)

i used copy cd's to hard drive method in the link bellow, dont forget the hidden mounting of the cd-rom its on the link.
something like sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/WoW DVD/

HERE'S THE TRICKY BIT........
(plz DONT go hitting play/ect in wow box after 1st & 2nd cd if you want all 3 cd's, it stumped me for a bit it will crash, wait then close the dialog between inserting (installing all 3). example you could mount cd1 install it,wait then close the program, unmount insert second disk mount repeat process ect close unmout then run from wine menu it will get further updates on the final stage only. (not needing updates between cd's).

NOTE *****************NOTE its a bug also in wine 1.4 so...
it needed wine 1.2, downgrading from 1.4 (thats only for world of warcraft) then upgrade if you wish after the install of wow but not essential.
 
[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

if you manage ok also see winetricks [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
this will give you loads of extra stuff for wine.

---

