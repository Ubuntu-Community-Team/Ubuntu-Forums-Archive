---
title: "Wow...nothing works"
date: 2009-01-28
forum: Wine
---

### Post by rpeals1 on 2009-01-28
So i'm fairly annoyed at this point and i've been searching the past 3 days trying to fix this. I'm running the newest version of xubuntu and the newest version of wine. Just changed from ubuntu to xubuntu because ubuntu was using like 50% of my cpu just sitting there. Only thing i use my pc for is internet and wow. Wow worked fine with ubuntu after setting opengl and all that noise, except i ran like 4 fps in cities and lag was awful. so i switched to the lighter operating system hoping that using less than 80% of my cpu power while wow is up would make it run better.

wellll, i wouldn't know if it ran better. Now with xubuntu, it wont work at all. Wow is installed and whatever and i've patched it up to 3.0.1. Now this is where the big issue comes in. I can't flippin download it. the blizzard downloader has been up for the past 2 days trying to download this damn patch and its at 75 percent. so over 30 hours of downloading and i'm at 2gbs out of 2.6gbs. I used mirrors for the other patches but of course thats not working for this either. This patch comes as a .zip file unlike all the others. so i extract the file from the .zip to my WOW folder and try to run it. Doesn't work of course and here's the error message:

 The file "Interface\GLUES\COMMON\GLUES-WOW-BCLOGO.BLP" in archive "C:\Program Files\World of Warcraft\Data\enUS\patch-enUS.MPQ" could not be opened, because an error 2 occurred. If this problem persists, please contact Blizzard Technical Support. (MPQFile::OpenFromArchive)
 To check this installation for problems, click the "Repair" button. The Repair tool can automatically fix many update errors.

The repair button obviously doesn't work and i never expected it to at this point. I'm running in opengl mode and still doens't work. 

So i tried downloading TBC because if i remember right it has this patch in it. So boot up that WOW installer, ultra fail of course. error message is:

Failed to read information from the Internet. Please close all applications and try again

So everything was going fine, until this stupid patch. Now wow has gone into auto-fail mode and nothing is working. I'm running all nvidia hooplah and everything should work fine because it has before just with ubuntu not xubuntu. Maybe i should just keep downloading this patch and maybe it'll be done by next week or something? If anyone can help make this work that would own. if you need any more info about my pc ask.

---

### Post by RaiCoss on 2009-01-28
> **rpeals1 said:**
> So i'm fairly annoyed at this point and i've been searching the past 3 days trying to fix this. I'm running the newest version of xubuntu and the newest version of wine. Just changed from ubuntu to xubuntu because ubuntu was using like 50% of my cpu just sitting there. Only thing i use my pc for is internet and wow. Wow worked fine with ubuntu after setting opengl and all that noise, except i ran like 4 fps in cities and lag was awful. so i switched to the lighter operating system hoping that using less than 80% of my cpu power while wow is up would make it run better.

wellll, i wouldn't know if it ran better. Now with xubuntu, it wont work at all. Wow is installed and whatever and i've patched it up to 3.0.1. Now this is where the big issue comes in. I can't flippin download it. the blizzard downloader has been up for the past 2 days trying to download this damn patch and its at 75 percent. so over 30 hours of downloading and i'm at 2gbs out of 2.6gbs. I used mirrors for the other patches but of course thats not working for this either. This patch comes as a .zip file unlike all the others. so i extract the file from the .zip to my WOW folder and try to run it. Doesn't work of course and here's the error message:

 The file "Interface\GLUES\COMMON\GLUES-WOW-BCLOGO.BLP" in archive "C:\Program Files\World of Warcraft\Data\enUS\patch-enUS.MPQ" could not be opened, because an error 2 occurred. If this problem persists, please contact Blizzard Technical Support. (MPQFile::OpenFromArchive)
 To check this installation for problems, click the "Repair" button. The Repair tool can automatically fix many update errors.

The repair button obviously doesn't work and i never expected it to at this point. I'm running in opengl mode and still doens't work. 

So i tried downloading TBC because if i remember right it has this patch in it. So boot up that WOW installer, ultra fail of course. error message is:

Failed to read information from the Internet. Please close all applications and try again

So everything was going fine, until this stupid patch. Now wow has gone into auto-fail mode and nothing is working. I'm running all nvidia hooplah and everything should work fine because it has before just with ubuntu not xubuntu. Maybe i should just keep downloading this patch and maybe it'll be done by next week or something? If anyone can help make this work that would own. if you need any more info about my pc ask.

That's ridiculously slow, what graphics card have you got??

---

### Post by rpeals1 on 2009-01-28
So I opened wow through the terminal. It does same thing i does everytime, login in and it tells you to restart for patch. restart and downloader opens and begins download. I'll just copy and paste from start up until error.

raymond@raymond-desktop:~$ wine '/home/raymond/.wine/dosdevices/c:/Program Files/World of Warcraft/Wow.exe'
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
fixme:powrprof:DllMain (0x7cca0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cca0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ebc8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x142578,0x142478): stub
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x33e98c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d88c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33cafc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d88c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec1c,0x00000000), stub!

:/ i dunno what all this means lol. Xubuntu runs so much better than ubuntu and from first startup seemed to belong on this pc more than ubuntu. but if wow won't work it will just be a big fail. any help is hugely appreciated if you need anymore information ask.

---

### Post by RaiCoss on 2009-01-28
> **rpeals1 said:**
> So I opened wow through the terminal. It does same thing i does everytime, login in and it tells you to restart for patch. restart and downloader opens and begins download. I'll just copy and paste from start up until error.

raymond@raymond-desktop:~$ wine '/home/raymond/.wine/dosdevices/c:/Program Files/World of Warcraft/Wow.exe'
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
fixme:powrprof:DllMain (0x7cca0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cca0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ebc8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x142578,0x142478): stub
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x33e98c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d88c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33cafc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d88c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec1c,0x00000000), stub!

:/ i dunno what all this means lol. Xubuntu runs so much better than ubuntu and from first startup seemed to belong on this pc more than ubuntu. but if wow won't work it will just be a big fail. any help is hugely appreciated if you need anymore information ask.

Well ok, I'll ask again, what graphics card do you have?

---

### Post by Cope57 on 2009-01-28
Application database for [World of Warcraft]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922") for WINE.

If you do happen to get it to work, let everyone know...

---

### Post by RaiCoss on 2009-01-28
> **Cope57 said:**
> Application database for [World of Warcraft]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922") for WINE.

If you do happen to get it to work, let everyone know...

Yeah I've already looked on WINEHQ, this seems to be a new problem, and isn't listed anywhere on there ;)

---

### Post by rpeals1 on 2009-01-28
I dunno what my graphics card is. Based on price and where i got this pc probably integraded poop. probably explains alot. but still, i want it to work on xubuntu, and i don't think this is a video problem. and yea i'm definantly going to need a video card.

---

### Post by RaiCoss on 2009-01-28
> **rpeals1 said:**
> I dunno what my graphics card is. Based on price and where i got this pc probably integraded poop. probably explains alot. but still, i want it to work on xubuntu, and i don't think this is a video problem. and yea i'm definantly going to need a video card.

................Ok well that dosen't really help, are you using Aol??

Whats your ISP?

---

### Post by rpeals1 on 2009-01-28
ISP is cox. cable internet.The downloader downloaded this same patch in like 15 minutes or less with ubuntu. maybe i should just switch back to ubuntu

---

### Post by Marshal0505 on 2009-01-28
> **rpeals1 said:**
> I dunno what my graphics card is. Based on price and where i got this pc probably integraded poop. probably explains alot. but still, i want it to work on xubuntu, and i don't think this is a video problem. and yea i'm definantly going to need a video card.

"I'm on an acer aspire ast180. Nvidia chipset. Nvidia Geforce 6100 Nforce 405." Is what i found on your earlier post [http://ubuntuforums.org/showthread.php?p=6058531#post6058531](http://ubuntuforums.org/showthread.php?p=6058531#post6058531).

Which is very similar to my old pc , except my card was a 7800GTX.
I was never fully satisfied with WoW performance.Even havin similar performance to what you described.
Makes me wonder you might just need more raw power to run WoW decently.Although some tweaking might help you.

You could try closing X and use a script to launch WoW, it might give you that bit extra.

---

### Post by reiki on 2009-01-28
WoW works SPLENDIDLY in Wine. I've been running it in Wine for a long time. WotLK and all. I get no lag in cities or on raids. If you have integrated graphics you have no business running WoW. I have never called anyone an idiot, but you know... if the shoe fits.... may as well wear it.

Do not blame the OS for the shortcomings of your system when you try to do things your system doesn't have the hardware to pull off. 

I have an old Pentium D 930, 4GB of memory, and a 512MB NVidia 7300GT. So it's not like I have some brand new, monster machine. 

WoW is fine if you have the hardware for it.

---

### Post by RaiCoss on 2009-01-28
> **rpeals1 said:**
> ISP is cox. cable internet.The downloader downloaded this same patch in like 15 minutes or less with ubuntu. maybe i should just switch back to ubuntu

I wouldn't I'm using Ubuntu 8.10 and having EXACTLY the same problem!!

And a tip to break the download/patch cycle. When it's downloaded the patch but dosen't run the patcher, reset the machine and then let it repatch, and repeat, the ultra slow download speed I don't have much of a clue about, it's either Blizzard glitching or purposely throttling download speeds, or your ISP punishing you because the patcher uses P2P, you could try disable P2P sharing in the downloader options, apart from that I'm stumped:-?

---

### Post by RaiCoss on 2009-01-28
> **reiki said:**
> WoW works SPLENDIDLY in Wine. I've been running it in Wine for a long time. WotLK and all. I get no lag in cities or on raids. If you have integrated graphics you have no business running WoW. I have never called anyone an idiot, but you know... if the shoe fits.... may as well wear it.

Do not blame the OS for the shortcomings of your system when you try to do things your system doesn't have the hardware to pull off. 

I have an old Pentium D 930, 4GB of memory, and a 512MB NVidia 7300GT. So it's not like I have some brand new, monster machine. 

WoW is fine if you have the hardware for it.

Yeah I'm aware it works perfectly in WINE, its just a problem that seems to have arisen in the past couple of days.

And reiki or whatever your name is. Your machine is pretty powerful, so maybe you should stop playing the "It works PERFECTLY on my old machine", the guy isn't an idiot for using intergrated ¬¬

---

### Post by rpeals1 on 2009-01-28
yea marshall ty u for getting that. it's not intergrated its that geforce 6100. and reiki...ur so nice.

---

### Post by RaiCoss on 2009-01-28
> **rpeals1 said:**
> yea marshall ty u for getting that. it's not intergrated its that geforce 6100. and reiki...ur so nice.

6100 is an intergrated chip as far as I know, but that shouldn't matter, i got great perfoormance outta an old 5700 so ya'know;)

At the moment I get a pretty rock steady 60FPS with 4XAA on an 8600GT, and used to get about 25 on the 5700 so I doubt its the GPU, anyway has anyone found any kinda clue why the download is so S-L-O-W??

---

### Post by sgx on 2009-01-28
> **rpeals1 said:**
> I dunno what my graphics card is. Based on price and where i got this pc probably integraded poop. probably explains alot. but still, i want it to work on xubuntu, and i don't think this is a video problem. and yea i'm definantly going to need a video card.
On any linux with synaptic, it is fairly easy to go into synaptic, and remove all the apps you dont' use, the system files are largely the same,
in the varous distros/versions, so leave those alone, but Open Office, Gimp, redundant multitudes of audio/video/printing/spell-checking/console/text apps can all be uninstalled, making  for a faster system. On a new install, I usually do this in about
5 passes, taking notes what I delete, logging out after each major set of changes, one for OOG, one for graphics apps, one for text apps, etc etc.
Once, deleting a certain screensaver bombed my system, so be safe!

If you have a separate /home partition, you can save lots of config time,
re-using your net and eyecandy prefs by not formatting that partition, an option in the custom partitioning section om most distros, hence no fear  of long post reinstall config rituals, as you perfect your system to your needs.
I have read that wine apps work best when started before any web-browsing session, and have seen evidence that is true, so as you work through this,
start wow, or the app you test, first, after a reboot. Is your screen DPI setting, or default video resolution changed during your tests?

Cheers:)

---

### Post by rpeals1 on 2009-01-28
lol yeaaa the DL speed is the issue. i just wanna playyy i'm used to lag in cities by now.

---

### Post by RaiCoss on 2009-01-28
> **rpeals1 said:**
> lol yeaaa the DL speed is the issue. i just wanna playyy i'm used to lag in cities by now.

Ugh, by the time I sort this out, my subscription will be finished ¬¬

---

### Post by rpeals1 on 2009-01-28
reinstalling wow and wine to see if that helps

---

### Post by RaiCoss on 2009-01-28
> **rpeals1 said:**
> reinstalling wow and wine to see if that helps

Fair enough, but I've aready done that three times ¬¬

Anddddddddd you where saying about lag in cities and low FPS, do you edit the config.wtf file so that WoW runs in OpenGL mode instead of DRU DirectX?

---

### Post by rpeals1 on 2009-01-28
yeaaa i was running in opengl

---

### Post by RaiCoss on 2009-01-28
> **rpeals1 said:**
> yeaaa i was running in opengl

Then I don't have a clue why you run so slowly. Like I said before I get a pretty steady 60FPS, even on a puny 2GHZ Sempron :-k

---

### Post by rpeals1 on 2009-01-28
yea and this was running on all low settings. worked alot better on vista honestly :/. i hated vista though.

---

### Post by RaiCoss on 2009-01-28
lol............i get 130+ on all low xDDDDDDD

---

### Post by rpeals1 on 2009-01-29
soooo i put ubuntu back on my pc, dled the newest wine and what not had all the same probs. then i downgraded my wine back to 1.1.10 and everything works fine. blizz downloader works much faster, still slow but normal blizz downloader slow. so try downgrading?

---

### Post by RaiCoss on 2009-01-29
> **rpeals1 said:**
> soooo i put ubuntu back on my pc, dled the newest wine and what not had all the same probs. then i downgraded my wine back to 1.1.10 and everything works fine. blizz downloader works much faster, still slow but normal blizz downloader slow. so try downgrading?

Mines working fine now, just gotta download the 3GB patch :-?

---

