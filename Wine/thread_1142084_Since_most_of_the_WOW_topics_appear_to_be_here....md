---
title: "Since most of the WOW topics appear to be here..."
date: 2009-04-28
forum: Wine
---

### Post by Clydtsdk-Rivendare on 2009-04-28
Anyone else having problems with applying patch 3.1.1a? I can't use Blizzard's downloader (I'm not sure why) and when I try to use a patch mirror, when I try to apply the patch I get the message "Waiting for files to close" even though everything appears to be closed.

So... yeah. I can't play WOW now. Just when I was starting to get good at it...

Any help here?](*,)

EDIT: The issue ITT has changed. See the second page [#11-20]

---

### Post by Clydtsdk-Rivendare on 2009-04-29
BUMP since the problem still has not resolved itself.

Here's a pic.

---

### Post by garythegoth on 2009-04-29
I just installed it today. Worked perfectly apart from being slow downloading the last patch. 
Did you update to WINE 1.1.20?
The 1.0.1 release in the repos is next to pointless now.

---

### Post by Clydtsdk-Rivendare on 2009-04-29
> **garythegoth said:**
> I just installed it today. Worked perfectly apart from being slow downloading the last patch. 
Did you update to WINE 1.1.20?
The 1.0.1 release in the repos is next to pointless now.

I thought I did. Lemme check.

thanks.:popcorn:

EDIT: just checked, I have 1.1.19.... hm.

And the result is.... *drumroll*

...WOW won't start up at all. I'll poke around and see what I can do before complaining about it tho.

---

### Post by garythegoth on 2009-04-29
> **Clydtsdk-Rivendare said:**
> I thought I did. Lemme check.

thanks.:popcorn:

EDIT: just checked, I have 1.1.19.... hm.

Still no better?

---

### Post by Clydtsdk-Rivendare on 2009-04-30
BUMPing since I royally messed up and then fixed wine.

The patch applied fine but WOW still thinks I need to patch it...

EDIT: Here's a shot

EDIT 2: Removed screen shot as it's no longer relevant

---

### Post by Clydtsdk-Rivendare on 2009-05-01
BUMP...

Can't figure WOW out, it still thinks I need to patch it. Mebbe I should wait til 3.1.2?...

---

### Post by johnl on 2009-05-01
Hi,

I had a similar problem;  when I ran the Launcher from the WoW game folder, it did something (looked like a quick repair?) and then the game ran fine.  If you have't tried running the Launcher, I would try that; if that doesn't work, try the repair tool.

---

### Post by Clydtsdk-Rivendare on 2009-05-01
Tried both of those.

Now I went and reinstalled WOW, but can't get TBC/WOTLK to reinstall....

---

### Post by Bios Element on 2009-05-01
Try installing WoW to it's own prefix.
[http://bioselement.com/blog/2009/01/03/wine-world-of-warcraft/](http://bioselement.com/blog/2009/01/03/wine-world-of-warcraft/)

---

### Post by Clydtsdk-Rivendare on 2009-05-01
@Bios: I'll take a look at that, thanks.

On another note, I got TBC to work using this thread:

[http://ubuntuforums.org/showthread.php?t=1064891](http://ubuntuforums.org/showthread.php?t=1064891)

However, I did its WOTLK stuff and got the error

" No installer data could be found. If this problem persists, please contact Blizzard Technical Support."

EDIT:

And fixed that as well. WOTLK is installing as I speak... type.

EDIT2:

Everything is reinstalled, re-patched but WOW still refuses to admit it. My day wasn't a total waste though, I figured out how to mass-DL patches via torrent.

Nerd score +1.

EDIT3: Have a couple screenshots. I log into WOW, get hit with the "Patch Required" screen, then hit ENTER and get the second error.

I'm really frustrated guyz.

---

### Post by Clydtsdk-Rivendare on 2009-05-02
bumping

Still haven't got the issue resolved.

>_____________________________________________<

EDIT

```
wine "/home/klabnik/.wine/drive_c/Program Files/World of Warcraft/Wow.exe"
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
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
fixme:win:EnumDisplayDevicesW ((null),0,0x39edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebd0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f584,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f578,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5dc,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32_FLOAT
fixme:win:EnumDisplayDevicesW ((null),0,0x39f140,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39deec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df24,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39dee0,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37404084) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000


```

My internet is fine BTW.

---

### Post by Clydtsdk-Rivendare on 2009-05-04
BUMP

Still tired of this "Patch Required" BS.

---

### Post by Dimarchi on 2009-05-05
Where are the patches located, actually? If those screenshots are of any indication, there are *way* less of them than really should be. Have you moved them somewhere else ( I wouldn't recommend that...copy yes, but no moving...less trouble when WoW crashes, corrupts your install, and you need to use Repair.exe)?

It *does* look like you have patched correctly judging from the second screenshot. Have you tried opening either Launcher.exe or Repair.exe first? Permission problem?

---

### Post by Clydtsdk-Rivendare on 2009-05-09
> **Dimarchi said:**
> Where are the patches located, actually? If those screenshots are of any indication, there are *way* less of them than really should be. Have you moved them somewhere else ( I wouldn't recommend that...copy yes, but no moving...less trouble when WoW crashes, corrupts your install, and you need to use Repair.exe)?

It *does* look like you have patched correctly judging from the second screenshot. Have you tried opening either Launcher.exe or Repair.exe first? Permission problem?

Ack, just when I've left the topic for dead... 

I did move the patches so they were all in the same place, I've used Launcher.exe and I'm pretty sure I tried Repair.exe though I'll look at that again.

EDIT:

Interesting.... I can't seem to find Repair.exe. And it seems I'm not the only one.

[http://forums.worldofwarcraft.com/thread.html?topicId=14697590372&sid=1](http://forums.worldofwarcraft.com/thread.html?topicId=14697590372&sid=1)

---

