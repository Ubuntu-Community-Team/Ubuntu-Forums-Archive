---
title: "Secret of Monkey Island Special Edition"
date: 2009-07-15
forum: Wine
---

### Post by xenogia on 2009-07-15
Hey Guys,

Just wondering if anyone has tested Monkey Island Special Edition on Wine as of yet.  I am considering purchasing it but wondering if any of you guys have tested it.  Just incase the purchase becomes defunct at my end.

---

### Post by brupje on 2009-07-16
I tested it. Won't work for me, at all. See [http://appdb.winehq.org/objectManager.php?sClass=application&iId=10023](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10023)

---

### Post by binbash on 2009-07-17
I can't get it working too.

---

### Post by Dwarf007 on 2009-07-17
Hi,

1) install at least wine 1.1.23
you'll find the deb packages here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

2) install winetricks (see [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks))
and do the following: 

$ wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
$ sh winetricks vcrun2005sp1 vcrun2005

maybe you don't need that but I performed this step cause of issues with msvcp80.dll and msvcr80.dll.

now you can start SMI:SE in theory.
It worked for me, except that my computer does not seem powerfull enough. Therefore I have the choice between:
- either the sound but no vertex shader (no graphics)
- either very very laggy graphics and no sound (which I also gave up)

I hope I'll find a solution different to buying a more powerfull PC :-(

Hope it works for you guys!
Enjoy,
-- 
Daniel

---

### Post by compholio on 2009-07-17
> **Dwarf007 said:**
> ...
now you can start SMI:SE in theory.
It worked for me, except that my computer does not seem powerfull enough. Therefore I have the choice between:
- either the sound but no vertex shader (no graphics)
- either very very laggy graphics and no sound (which I also gave up)
...

I don't have any sound when I try the game, how is your sound setup?

---

### Post by Dwarf007 on 2009-07-18
> **compholio said:**
> I don't have any sound when I try the game, how is your sound setup?

ALSA is selected in winecfg.
But I must say that I didn't do anything special for the sound.

---

### Post by Dwarf007 on 2009-07-18
[Instructions on how to play!]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17211&iTestingId=42656")

Enjoy!

---

### Post by compholio on 2009-07-18
> **Dwarf007 said:**
> ALSA is selected in winecfg.
But I must say that I didn't do anything special for the sound.

Hmmm, what settings do you have under DirectSound on the audio tab?  This is really bizarre, because absolutely everything else I run under Wine the sound works great.

---

### Post by compholio on 2009-07-18
> **compholio said:**
> Hmmm, what settings do you have under DirectSound on the audio tab?  This is really bizarre, because absolutely everything else I run under Wine the sound works great.

Well, I have no idea why - but starting with a fresh registry fixed it.  I did all sorts of things (like import a fresh registry on top of my existing one) and the only thing that worked was to actually have a fresh registry.  So, there must be some registry key that, if it exists, will make it so the audio doesn't work.

Update:
The registry key responsible is the one corresponding to the "Default Sample Rate" in winecfg.  If this value is not set to 44100 then there will be no audio.

---

### Post by fettuohi on 2009-07-24
I have the same problem with sound and I have a HDA Intel sound card. I can't sound in MI:SE no matter what I do.

Regards

André

---

### Post by N_L on 2010-05-15
I'm gonna bump this thread if I may, because I'm having problems with this game.

I installed it fine but I can't run it at all. I browse to it's location and when I run mise.exe with wine it starts loading(in start bar) and nothing happens.

Im on 10.4 ubuntu and installed with winetricks  vcrun2005&sp1, dx9d and some other stuff probably. Running office sucessfully.

Any thoughts of what I should try?

Also I tried installing xact but  I get this:
sha1sum mismatch! Rename /home/nolimit/.winetrickscache/./directx_feb2010_redist.exe and try again.

---

### Post by Cyclingrelf on 2011-01-12
Bumpety bump. I'm wondering if anyone can help me?

I'm trying to run Secret of Monkey Island special edition in Steam on wine with Ubuntu Maverick Meerkat. I can install steam and use it to install the game (after it installs directx), apparently with no problems, but when I try to run the game, a window opens saying "Preparing to launch The Secret of Monkey Island: Special Edition". This closes and then a blank window opens, which is initally white. There is an audible "clunk" from the speakers, the white rectangle shrinks slightly into the top right corner, leaving a black border on the left and bottom. At the bottom right, a Steam logo apears saying "Access the Steam Community while playing". And then nothing else happens. No visuals appear at all and no more sound beyond the original clunk. Sometimes, it then crashes completely with an error saying "The program MISE.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience." It doesn't always do this, sometimes it just sits there blankly until I close it down.

**Hardware**
Compaq Evo N610c laptop.
Intel Pentium 4 processor
1GB RAM
30 GB ATA hard disk
ATI Radeon Mobility M7 LW graphics chip
Intel Corporation 82801CA/CAM AC'97 Audio Controller

**Software**
Ubuntu 10.10 Maverick Meerkat
Wine 1.3
wine 1.3-gecko
winetricks
Steam 

I used winetricks to install d3dx9, vcrun2008, vcrun2008sp1 and xta

Wine is configured to Windows 2000, ALSA driver, hardware acceleration: emulation, Default sample rate 44100 Default bits per sample 16

I tried using the terminal to run wine MISE.exe, but with the same effect as already described, and no error messages in the terminal, so nothing to help me there.

I'd be grateful if anyone can help. I'm stuck! :confused:

---

### Post by user2037 on 2013-04-23
I too can't run it even after installing the mentioned dependency DLL's. It bombs with "Program Error" and "The program MISE.exe has encountered a serious problem...". 

EDIT: Running WINE 1.5.28

> 
fixme:win:EnumDisplayDevicesW ((null),0,0x33c014,0x00000000), stub!
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
err:ole:CoGetClassObject class {03219e78-5bc3-44d1-b92e-f63d89cc6526} not registered
err:ole:CoGetClassObject no class object {03219e78-5bc3-44d1-b92e-f63d89cc6526} could be created for context 0x1
wine: Unhandled page fault on read access to 0x00000000 at address 0x441192 (thread 005f), starting debugger...


---

### Post by Bucky Ball on 2013-04-23
[B][I]Thread Closed

Reason:[/I][/B] Necromancy. Old thread put to bed. 

@ user2037: You will greatly improve your chances of help if you start a new thread rather than resurrecting this one. It hasn't seen any action for two years and lots can change in that time. If a thread hasn't had a post in a year please post a new one with a descriptive title and outlining your problem. Good luck.

---

