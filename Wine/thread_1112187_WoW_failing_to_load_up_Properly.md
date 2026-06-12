---
title: "WoW failing to load up Properly"
date: 2009-03-31
forum: Wine
---

### Post by SuperNapalm on 2009-03-31
Last thread was kinda hijacked so I'm reposting my problem in the hope I'll finally get some answers.

[B]Ubuntu 8.10
Wine 1.1.17 and 1.1.18[/B] (Problem occured in both versions)
Sapphire Radeon HD4670

Warcraft has been running pretty darn good since I finally made the full switch. However since last week I've gone to load it up via the desktop icon and nothing shows up (I've tried running from the exe driectly). The 'Starting World of Warcraft' thing displays on the taskbar then disappears and nothing comes up (and by nothing i mean stays at desktop and nothing appears to have been open at all). The System Monitor shows the Wow.exe process however...

Trying to start from a terminal I get this (I used an executable text file):
```
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:advapi:SetSecurityInfo stub
archive Data\enGB\patch-enGB.MPQ opened
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\lichking-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
archive Data\enGB\lichking-speech-enGB.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
```

It shows nothing else, just sits there, no slowdown or anything. System Monitor shows the process like the other method.

As far as I'm aware, after installing WoW there's been no additional installations of any kind other than the usual updates, so I'm quite puzzled as to why it suddenly isn't working.

---

### Post by darius779 on 2009-03-31
I'm also experiencing this problem as of today after a reboot. :(

---

### Post by SuperNapalm on 2009-04-02
Bump

Please help been unable to open it up for a week now...

---

### Post by SuperNapalm on 2009-04-02
Any help? Someone?

Even some brainstorming will help.

---

### Post by Brynster on 2009-04-02
try adding -opengl to you launch option

I could be trying to force directx which causes lots of issues. Also have you got/made sure the latest flgx ATi drivers are installed?

---

### Post by SuperNapalm on 2009-04-02
What I dont get is it has worked totally fine until like a week or so ago.
I've been running it in OpenGl whole time too.

---

### Post by hikaricore on 2009-04-02
> **SuperNapalm said:**
> What I dont get is it has worked totally fine until like a week or so ago.

Did you happen to install any updates on Ubuntu about a week or so ago, then reboot your system?
Often times you will need to reinstall any video drivers you've manually installed.

---

### Post by SuperNapalm on 2009-04-02
Ah, that's probably it, I'll go reinstall now...

---

### Post by robinsonbond007j on 2009-04-03
I just went from windows to linux. Was loving linux till I found out WoW isn't working for me either. I'm running a Nvidia 8600 gts. I can load the game and if I press a button or wait for 2-3 min. It will crash on me everytime. And I'm not sure if I'm running open GL or not. Still rather noobish. I just want to get back to lvling. And not have to do two partitions so I can just have one for wow in windows.

---

### Post by chips.4.u on 2009-04-03
> **hikaricore said:**
> Did you happen to install any updates on Ubuntu about a week or so ago, then reboot your system?
Often times you will need to reinstall any video drivers you've manually installed.

This solved my issue with Wine and WoW not working after restart.

---

