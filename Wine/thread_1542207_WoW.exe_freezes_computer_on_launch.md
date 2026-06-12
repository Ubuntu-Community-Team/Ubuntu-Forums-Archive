---
title: "WoW.exe freezes computer on launch"
date: 2010-07-30
forum: Wine
---

### Post by amorella on 2010-07-30
I am using Ubuntu 10.04 Lucid and Wine 1.1.42, with WoW set to run in XP. 
launcher.exe works perfectly normal but lauching directly into wow.exe or lauch via the Laucher freezes my computer (mouse still moves and any music playing will continue, but nothing new can be done)...and I have to restart. 

I originally installed Ubuntu, wine and wow and got it to work (not sure what I did), but I messed up by install by playing around with some video settings and reformatted, reinstalled ubuntu off the same disk and pasted the wow folder into my virtual C drive (exactly the same backup of the wow folder that worked before).  

The WoW I am using is an up to date version that is copied from a computer running XP.  

This freeze happens when I launch directly through wine.  When I launch through the terminal I get the following:
[INDENT]xx@xx-pc:~$ wine "C:\Program Files\WoW\Wow.exe"
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\enUS\patch-enUS-3.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\patch-3.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x192ee20,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192eb0c,0x00000000), stub!
fixme:reg:GetNativeSystemInfo (0x33fd9c) using GetSystemInfo()
[/INDENT]
[INDENT]Then  a wow critical error (#132) pops up:
[INDENT]"This application has encountered a critical error:"

ERROR #132 (0x85100084) Fatal Exception
Program:    C:\Program Files\WoW\Wow.exe 
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:FFFFFFFF
[/INDENT][/INDENT]
I'm not sure if it's relevant, but opening wow.exe to view in Archive Manager result in the followings error message:

[INDENT]An error occurred while loading the archive.
Command line output 

Archive:  /home/xx/.wine/dosdevices/c:/Program Files/WoW/Wow.exe
[/home/xx/.wine/dosdevices/c:/Program Files/WoW/Wow.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/xx/.wine/dosdevices/c:/Program Files/WoW/Wow.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/xx/.wine/dosdevices/c:/Program Files/WoW/Wow.exe or
          /home/xx/.wine/dosdevices/c:/Program Files/WoW/Wow.exe.zip, and cannot find /home/xx/.wine/dosdevices/c:/Program Files/WoW/Wow.exe.ZIP, period.
[/INDENT]I have searched forums and found that a common suggested solution is to add SET gxApi “*opengl*” to the Config.wtf file, and this has not worked for me.  

Paste from terminal for video driver:
[INDENT]xx@xx-pc:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)

[/INDENT]System info @ [http://img267.imageshack.us/img267/3323/systeminfo.png](http://img267.imageshack.us/img267/3323/systeminfo.png)

Please let me know if I need to give any more info, btw I'm a newbie @ linux (going on 2weeks now) so please give detailed instructions.  Thanks for any help in advance! :D

---

### Post by Iowan on 2010-07-30
Moved to Wine.

---

### Post by DrMelon on 2010-07-30
Instead of copypasting the WoW folder, I suggest you download the WoW installer and install it fresh - the copy-pasted one will not have generated the nessecary registry entries in the Windows registry.

---

### Post by hikaricore on 2010-07-30
> **DrMelon said:**
> Instead of copypasting the WoW folder, I suggest you download the WoW installer and install it fresh - the copy-pasted one will not have generated the nessecary registry entries in the Windows registry.

World of Warcraft doesn't require registry entries...
The only time it ever uses the registry is to locate the install path which is set when you launch the game.

---

### Post by asdfoo on 2010-07-30
install the most recent version of Wine (1.3.0) and make sure you have the most recent ubuntu updates installed as there was a kernel bug affecting blizzard products. (I think the most recent 2.6.35 includes the fix)

---

### Post by cwwilson721 on 2010-07-31
I would also delete the WTF folder (Remember to launch WoW with the '-opengl' tag, and make sure the shortcut you use points to the "WoW.exe" file, and not Launcher.exe. After you get WoW running, you MIGHT be able to switch it back to Launcher.exe.).

Removing the WTF folder will make WoW reconstruct all the various video/audio settings for your current hardware. There could very well be a conflict in there between the Win system you copied from and the Ubuntu one you are trying to run it on. By the error in the OP, it's some kind of hardware flub. The differences could be enough to cause the errors

Let us know

---

### Post by hikaricore on 2010-08-01
I personally do not suggest ever using Launcher.exe it just ends up causing more problems and serves no purpose.

---

### Post by cwwilson721 on 2010-08-01
If it's working, it lets me know of news and patches.And gives me more time to find my freakin' Authenticator.

---

### Post by amorella on 2010-08-03
so I deleted the WTF folder completely and opened wow.exe with Wine.  And it worked!  :)

But...(yes there's usually a but), it was obiously meant to launch fullscreen (default settings) but ubuntu didn't let it (not sure if that's normal), and it went kind of out of wack.  i.e. to "accept" the agreement I had to click about 2cm below the button (mouse not aligned on screen) and the thing was pretty gittery.  So in one hit, which was a bad idea, I adjusted the resolution and changed it to windowed mode...crashed instantly.  So I try to relaunch, and it's the same story as before.  Deleting the WTF no longer makes it launch :(

I'm currently replacing the WoW folder with a backup on the external.  And I'm hoping doing that +deleting that wtf folder will let it launch again.  I'll update you

---

### Post by amorella on 2010-08-03
So I replaced the WoW folder again, excluding WTF, interface and a "WBD" or "WDB" folder (can't remember the exact name).  And same story as before with the mouse being off and screen resolution changing to be massive.  I was able to change the resolution without it crashing, but the mouse didn't fix no matter what resolution.  I'd been logged in about 2min when the whole game went a grey colour and stopped responding.  Nothing else froze.  I force quit (right click on taskbar, then selected force quit when it said it wasn't responding), then restarted the game.  It won't open now, more critical errors.

---

### Post by hikaricore on 2010-08-03
Disable desktop effects... that's the only thing that would cause it to go grey and is more than likely causing your issue in the first place.

---

### Post by cwwilson721 on 2010-08-03
Install compiz-fusion-icon, set to metacity, and reload the desktop (All by rt clicking on the icon in the tray)

---

### Post by amorella on 2010-08-10
I'm sad to say it was more trouble than it was worth.  Now running wow on windows 7.  Thanks for all your help!  It was much appreciated.  Ciao

---

### Post by hikaricore on 2010-08-10
> **amorella said:**
> I'm sad to say it was more trouble than it was worth.  Now running wow on windows 7.  Thanks for all your help!  It was much appreciated.  Ciao

Eggs + 1 Basket

In the future you probably should consider the possibility that software might not run on an operating system it was not intended to.
That said World of Warcraft runs perfectly fine on my 8600GT, I can't imagine your newer hardware would have any trouble provided you followed instructions.

---

