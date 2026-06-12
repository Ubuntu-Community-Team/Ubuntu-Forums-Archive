---
title: "Audio woes on Win98 VMWare machine"
date: 2008-01-09
forum: Virtualisation
---

### Post by wililupy on 2008-01-09
Hello, before I am shunned for asking this, I have tried everything already and still it is not working. I have installed OSS drivers, OSS kernel emulation, and even made my own OSS driver for my sound card, and still, it is not working. So, now for someone else to give me a hand.

I have an Audigy 2 ZS sound card that works like a champ in Ubuntu 7.10. I have also managed to install VMWare Server 1.04 with no hitches, other than no sound in any virtual machine. 

I started working with virtualization because some apps just don't run with wine. Sucks, oh well, I have since moved on. So I decided to try running them under windows virtual machines. Started with XP Pro, regular 32 bit version XP. I managed to get the software to install, installed VMWare Tools, and tried to get sound to work, nope. No Sound. I look in the Device Manager on windows, it says Unknown PCI Audio Device. I try installing drivers for my sound card, no worky. I tried reconfiguring VMWare server so it uses /dev/dsp, no joy. I force my sound card to use OSS drivers, still no Joy. I tell it Auto Detect, no joy. As you see, I get no joy from audio in Windows. So I think, lets try an older version, see what happens...
I install Windows 95, love how it doesn't see over 2gb, (fat 16, didn't think I would ever see that File system again) Installs no problem. Install VMWare tools, and once again, Unknown PCI Audio Device in Device Manager. I install Creative Soundblaster 16 through AWE-32 drivers, and no joy. I then try Windows 98. Finally, fat-32. Get to use the whole hard drive I set up, install VMWare tools, and wouldn't you guess it, NO AUDIO!! 
I have looked everywhere on the internet, translated god knows how many web pages, compiled, recompiled, installed, uninstalled and wrote OSS drivers. No matter what I do, my Virtual Machines have no Audio. I have also installed the Audigy Drivers on the VM's to no avail. The virtual systems know I have an audio device, but they can't access it becuase they windows drivers just aren't there. Is this an issue only with VMServer 1.04? Should I downgrade back to 1.03? I know that my OSS drivers work, becuase I still have audio in Ubuntu with them. Currently, I have put my system back the way it was when I first installed Ubuntu, using ALSA drivers for ubuntu and just running my apps in windows with no audio, but it does make running some games a little borish. 
Any help would be greatly appreciated. I need a little joy in my life.

Thanks in advance.

---

### Post by wililupy on 2008-01-09
Finally got audio to work. I needed to install an audio driver. After looking at the source code for vmware server, I found that it emulates an ensoniq sound card. I downloaded at win98 driver and boom, sound and midi and joystick now all work.

---

### Post by psyberdemon on 2008-01-18
where in gods name did you find that driver???

](*,)
](*,)
](*,)
](*,)

---

### Post by psyberdemon on 2008-01-18
this should help.

[http://www.vmware.com/support/gsx3/doc/vidsound_soundcfg_gsx.html](http://www.vmware.com/support/gsx3/doc/vidsound_soundcfg_gsx.html)

---

### Post by psyberdemon on 2008-01-18
this is the specific file you need : 

SBPCI_WebDrvsV5_12_01.exe


you can find it by taking the creative labs link above and searching the sound drivers for "Sound Blaster PCI 128" under Windows 98SE. make sure to specify "98SE" and not "98" or else the driver install will cause a BSOD

---

