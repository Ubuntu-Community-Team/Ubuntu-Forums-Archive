---
title: "What could we propose PP, in order to avoid the &quot;Black Screen&quot;"
date: 2011-10-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-18
I've been working via PM with some of the interesting cases of "Black Screen" after update or during fresh install of Oneiric CD. I am documenting what I find. At some point, developers should try to address such issues, to try to develop better strategies for PP. 

**Causes for "Black Screen" found so far:** ("Black" may refer to a completely black screen, to a "Blank" screen for non-native English speakers (might be white) or to a standard boot console screen (for those that have never seem one). It goes through all levels from monitor being off to the lack of a GUI, basically. Reports are hard to understand. 

**1)** Fail to load Plymouth graphic mode due to BIOS or VGA particularity.  May be black, pink, purple, square pattern, etc. Corrupted video anyway.  User can't switch to VT. Rare. User has to disable quiet, splash on grub.

**2)** Standard (but mysterious) incompatibility of Grub and PC, the cases in which noacpi, noapic, nolapic allow boot.

**3)** EFI based system upgrades with standard method (unaware of what EFI  is, or of the 
need for special procedures). Monitor will generally turn off  after a while. MACs, some Lenovo, some HP basically.

**4)** Corrupted / Uninstalled grub: Gets a Kernel error, sometimes visible. Some users can switch to VT. For others, their keyboards (specially  USB) stop working. Users can't explain how grub got corrupted.

**5)** Wrong /run, /run/lock, /var  structure. For some reason, I have found users with /run and /run/lock, but with no /var/run and /var/lock as soft links to the /run equivalents. DBUS errors flood dmesg. Mostly all daemons fail. Boot  proceeds (below Plymouth purple screen) a while until panic. Some users, with disabled Plymouth (or in which Plymouth fails) manage to see the console errors and unrelated message in screen (battery problem, network-manager waiting for connection, modem-manager resetting, etc) but X won't be loaded at this point, there will be no prompt in this VT. 

**6)** Boot OK. The simple lack of proper (or properly installed) video drivers makes X not load. 

**7)** Wrong ownership of $HOME and ~/.Xauthority.

**8)** Lightdm not installed, GDM not configured properly.

**9)** Lightdm installed, but with wrong settings (addressed)

**10)** And the new one, that really impressed me: Right after selecting the language for installation on the CD/USB standard or Alternate CD, the screen goes black with blinking cursor. Impossible to switch VTs or to understand what is going on.  
(see video posted by user: [http://www.youtube.com/watch?v=dNN5Ame0nTc](http://www.youtube.com/watch?v=dNN5Ame0nTc)) 

The solution?? Start memtest, interrupt memtest and enter setup again. I can't understand why, but it works.
b) Remove CMOS battery for a while and try again (or short jumper 1, of course)
Curiosity: BIOS was reset to default values many times, computer turned on/off and memories do pass the memtest.

Opinion: Few (if any) of them are exclusive to Oneiric. Many will happen again with PP. There probably are more causes we haven't been able to document so far. We must be able to see errors as they happen on users PCs. They must be able to see some text in order to get help / report anything. I haven't looked at code yet, but I've been told that Plymouth store initial programs outputs and later send them to log structure. I believe it would be better if if would simply redirect stdout  to another VT. In many cases, user would at least be able to switch to the output VT and report what he see as the error, thus being able to properly report / ask for help.

---

### Post by el_koraco on 2011-10-18
> a) Start memtest, interrupt memtest and enter setup again. I can't understand why, but it works.

I had Plymouth freeze or if I disabled it, I had the boot hang on the last Upstart line. If I started via recovery, then did anything, like mount the fs and go to a root shell, and continue boot, I'd get to tty7, which, with no DM, was blank, but I could switch to tty1-6 and do the normal thing. Weird. That was with the netinstall and with another Grub loading Oneiric, but still, weird.

---

### Post by effenberg0x0 on 2011-10-18
[ATTACH]204744[/ATTACH]
]Either Plymouth has some incompatibility with your VGA Card, 
your GRUB or /dev/sda(n) sectors got corrupted or it is not 
compatible to your current BIOS settings, your PC has a (U)EFI
BIOS that demands non-standard procedures, your /var is empty
or is a broken link to other directory, you have a problem with 
your video drivers or haven't installed them, your home directory
is not owned by you and your default group, or you have no 
permission to write and read to/from it, or you have installed GDM
and is trying to launch lightdm, or you have installed lightdm but
the installation is wrong, or you have no proper setup of Compiz and 
Unity packages. [COLOR=Red]What would you like to do?
[/COLOR]
[LIST]
[*][COLOR=Red]Open sectors for Hex editing[/COLOR]
[*][COLOR=Red]Read and debug BIOS via DMI[/COLOR]
[*][COLOR=Red]lol[/COLOR]
[/LIST]

---

### Post by ventrical on 2011-10-18
Yes.. always check the BIOS settings. I have had problems on some towers when the On Board Lan chip was enabled. Also disabling legacy USB during install helped. And also with onnboard sound and making sure that the OnBoard Video was <disabled> some PCs will panic if this option is set to auto and you have an AGP  or PCI card installed.

  A real good fix (when all else fails) is to disable onboard LAN and stick in a D-Link PCI card if you got one laying around. And then there are other settings with newer BIOSes that have to be configed correctly.

  Another trick is to install onto a known good system and then pull the hdd or pendrive and stick it into the PC you would like to have working. works about 99 percent of the time. I know .. some people do not have the luxury of having an extra desktop laying around. They are so cheap now you can get a good p-4 laying on the side of the road.

With laptops, pull the hdd and install directly to a USB drive  from the CD .. etc... working with Ubuntu provides a lot of alternatives.

regards,

ventrical

---

### Post by buzzmandt on 2011-10-18
I tried for 3 days and many burns and packs after packs of cigarettes to install on a friends machine about a year ago.... I couldn't find anything wrong but it would just hang and then black screen.....

Turned out to be a bios setting, something about a memory hole.  I think it was set to yes and i changed it to no or something like that...... 

but damn talk about obscure.

---

### Post by madjr on 2011-10-18
when you refer to "black screen", do you also mean **Unbootable** ?

---

### Post by MAFoElffen on 2011-10-18
> **effenberg0x0 said:**
> I've been working via PM with some of the interesting cases of "Black Screen" after update or during fresh install of Oneiric CD. I am documenting what I find. At some point, developers should try to address such issues, to try to develop better strategies for PP. 

**Causes for "Black Screen" found so far:** ("Black" may refer to a completely black screen, to a "Blank" screen for non-native English speakers (might be white) or to a standard boot console screen (for those that have never seem one). It goes through all levels from monitor being off to the lack of a GUI, basically. Reports are hard to understand. 

**1)** Fail to load Plymouth graphic mode due to BIOS or VGA particularity.  May be black, pink, purple, square pattern, etc. Corrupted video anyway.  User can't switch to VT. Rare. User has to disable quiet, splash on grub.

**2)** Standard (but mysterious) incompatibility of Grub and PC, the cases in which noacpi, noapic, nolapic allow boot.

**3)** EFI based system upgrades with standard method (unaware of what EFI  is, or of the 
need for special procedures). Monitor will generally turn off  after a while. MACs, some Lenovo, some HP basically.

**4)** Corrupted / Uninstalled grub: Gets a Kernel error, sometimes visible. Some users can switch to VT. For others, their keyboards (specially  USB) stop working. Users can't explain how grub got corrupted.

**5)** Wrong /run, /run/lock, /var  structure. For some reason, I have found users with /run and /run/lock, but with no /var/run and /var/lock as soft links to the /run equivalents. DBUS errors flood dmesg. Mostly all daemons fail. Boot  proceeds (below Plymouth purple screen) a while until panic. Some users, with disabled Plymouth (or in which Plymouth fails) manage to see the console errors and unrelated message in screen (battery problem, network-manager waiting for connection, modem-manager resetting, etc) but X won't be loaded at this point, there will be no prompt in this VT. 

**6)** Boot OK. The simple lack of proper (or properly installed) video drivers makes X not load. 

**7)** Wrong ownership of $HOME and ~/.Xauthority.

**8)** Lightdm not installed, GDM not configured properly.

**9)** Lightdm installed, but with wrong settings (addressed)

**10)** And the new one, that really impressed me: Right after selecting the language for installation on the CD/USB standard or Alternate CD, the screen goes black with blinking cursor. Impossible to switch VTs or to understand what is going on. The solution? 

a) Start memtest, interrupt memtest and enter setup again. I can't understand why, but it works.
b) Remove CMOS battery for a while and try again (or short jumper 1, of course)
Curiosity: BIOS was reset to default values many times, computer turned on/off and memories do pass the memtest.

Opinion: Few (if any) of them are exclusive to Oneiric. Many will happen again with PP. There probably are more causes we haven't been able to document so far. We must be able to see errors as they happen on users PCs. They must be able to see some text in order to get help / report anything. I haven't looked at code yet, but I've been told that Plymouth store initial programs outputs and later send them to log structure. I believe it would be better if if would simply redirect stdout  to another VT. In many cases, user would at least be able to switch to the output VT and report what he see as the error, thus being able to properly report / ask for help.
We (effen & I) were just talking about this on PM... LOL.

I've been helping users with these problems since before natty.  I reseached it.  I started a sticky on this back in June and have actively supported it since.  It started with just kms issues (grub, kernel, xorg...) That support soon just blew out the sides and had to include everything that effects graphics and then some.  It just went to all layers of the operating system.

The problem there it that a black screen could meean a "lot" of things, as effen pointed out.

Efffen discussed helping user's and the patience it took... LOL.  I had some with natty that could not follow any type of direction, but would not give up on their (sometimes self-created) problem... Enough so that I created 3 custom natty LiveCD's with hardcoded boot options and install scripting for the big 3 (nvidia, ATI, Intel).  Heck, I had 1 user try for 2 weeks saying he wastry to boot from the CD's, but was actually trying to run things off the CD's from Windows!

I would really like to see some of these things taken care of.  I think I have some ideas on some.  They sort of split off on 2 branches though.

The Distribution upgrade- When have we been asked or given the chance as testers to see what problems there would be to do a distribution upgrade from the soon-to-be past release, to the pre-release- to see what's going to get broke?  Shouldn't we do that? (LTS is next)

The installation process.  We here are afirly verse with this porcess, idosyncracies of "our" equipment... know what bugs are out there... and automatically go about our business manually fixing and tweaking our boxes.  New user? Well...  They install, reboot, blackscreen, panic.  The fixes are know by us, the dev's, etc... the installer does a probe for hardware and sets variables for the process.  Can't they set up the logic to either temporarily set a variable to do the first reboot into a working screen or the same to install a working driver for their hardware?

---

### Post by MAFoElffen on 2011-10-18
> **madjr said:**
> when you refer to "black screen", do you also mean **Unbootable** ?
New users don't know the difference in that... That's why the first part of my sticky has a trouble shooting flowchart from grub>Kernel>xorg/desktop.

EDIT- One more is the suspend-resume > reboot... On some new mobo's it ends up with the BIOS cmos cuurpted and can't find any of the disks or devices.

---

### Post by ventrical on 2011-10-18
> **MAFoElffen said:**
> We (effen & I) were just talking about this on PM... LOL.

I've been helping users with these problems since before natty.  I reseached it.  I started a sticky on this back in June and have actively supported it since.  It started with just kms issues (grub, kernel, xorg...) That support soon just blew out the sides and had to include everything that effects graphics and then some.  It just went to all layers of the operating system.

The problem there it that a black screen could meean a "lot" of things, as effen pointed out.

Efffen discussed helping user's and the patience it took... LOL.  I had some with natty that could not follow any type of direction, but would not give up on their (sometimes self-created) problem... Enough so that I created 3 custom natty LiveCD's with hardcoded boot options and install scripting for the big 3 (nvidia, ATI, Intel).  Heck, I had 1 user try for 2 weeks saying he wastry to boot from the CD's, but was actually trying to run things off the CD's from Windows!

I would really like to see some of these things taken care of.  I think I have some ideas on some.  They sort of split off on 2 branches though.

The Distribution upgrade- When have we been asked or given the chance as testers to see what problems there would be to do a distribution upgrade from the soon-to-be past release, to the pre-release- to see what's going to get broke?  Shouldn't we do that? (LTS is next)

The installation process.  We here are afirly verse with this porcess, idosyncracies of "our" equipment... know what bugs are out there... and automatically go about our business manually fixing and tweaking our boxes.  New user? Well...  They install, reboot, blackscreen, panic.  The fixes are know by us, the dev's, etc... the installer does a probe for hardware and sets variables for the process.  Can't they set up the logic to either temporarily set a variable to do the first reboot into a working screen or the same to install a working driver for their hardware?


 I have been helping people with these problems since before Linux ! 

:)

---

### Post by ventrical on 2011-10-18
> **buzzmandt said:**
> I tried for 3 days and many burns and packs after packs of cigarettes to install on a friends machine about a year ago.... I couldn't find anything wrong but it would just hang and then black screen.....

Turned out to be a bios setting, something about a memory hole.  I think it was set to yes and i changed it to no or something like that...... 

but damn talk about obscure.


yep .. video shadow mem is another.

another is ddr memory.  and trying to match that . For the most part  all frequencies will work on a mixed array but some 333MHz will not match with 266 or 444 .. etc...The Soya, Gigabyte, Via, SiS boards can be touchy at certain revisions.

With Dell Mobos, now those ones are touchy , even though Dell has had advertisments featuring the Ubuntu system, Dell and Toshiba MoBos have a tendency to get these 'satic lock_ups' with non-proprietary PCI cards (or non-approved by Dell). basically what this mean is that  a segment of memeory will lock_up in the sleep state. The way to remedy this is to remove the PCI card and then replace it, Especially with older adapter cards.

  And then there is still card-creep. Yup .. even in 2011 .. still , the PCI cards wil ever so slightly creep out of there sockets due to heat/on/off.. etc..  and that should give you an A20 error.

Oh yah .. disable plug'n'play in BIOS. If your BIOS had plug 'n play , you know it was designed for MS and some of those undocumented interrupt vectors will only work with a proprietary driver. Pure greed if you ask me.

---

### Post by effenberg0x0 on 2011-10-18
> **madjr said:**
> when you refer to "black screen", do you also mean **Unbootable** ?

Hey madjr. I've come to the conclusion that it generally means anything that is not colorful and fun. Users can't tell at what stage their PC is: BIOS, Grub, Boot, Console. Most of these are considered Black Screen.

Just so you see I'm not kidding, I had a user that didn't knew the possibility of reboot, only power on or poweroff. I replaced "sudo reboot now" for "remove PC power cable (the thick black one) from outlet, count to 5 and reinsert".

---

### Post by effenberg0x0 on 2011-10-18
@MAFoElffen, 

One thing that bothers me is that, as far as I can remember, you could take a sheet of paper, write "Nvidia Quadro" on it, stick into a slot and boot stuff like Dapper, Edgy. It would launch a X session in VGA mode. I had a crappy laptop back then with SiS Chipset / VGA which couldn't run any of the cool things, but I had a VGA mode without any tweaking.

Two last versions of Ubuntu were a bit of a change for me and, being stuck with some professional problems, I never studied them as much as I should have. But, as I look a little into the workings of the current desktop, I see there should be a fallback mode.

```

start on ((filesystem
           and runlevel [!06]
           and started dbus
           and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
                or stopped udev-fallback-graphics))
          or runlevel PREVLEVEL=S)

stop on runlevel [016]

emits login-session-start
emits desktop-session-start
emits desktop-shutdown
```

Has anyone seen a fallback mode? I have not.

Regards,
Effenberg

---

### Post by cariboo on 2011-10-19
At one point several releases back there was a failsafe X mode in the recovery menu, but that is no longer available, it might be time to urge the Xorg developers to bring it back.

That being said, there were still people that ran into the black screen of death, and even failsafe X didn't work for them.

---

### Post by MAFoElffen on 2011-10-19
> **effenberg0x0 said:**
> @MAFoElffen, 

One thing that bothers me is that, as far as I can remember, you could take a sheet of paper, write "Nvidia Quadro" on it, stick into a slot and boot stuff like Dapper, Edgy. It would launch a X session in VGA mode. I had a crappy laptop back then with SiS Chipset / VGA which couldn't run any of the cool things, but I had a VGA mode without any tweaking.

Two last versions of Ubuntu were a bit of a change for me and, being stuck with some professional problems, I never studied them as much as I should have. But, as I look a little into the workings of the current desktop, I see there should be a fallback mode.

```

start on ((filesystem
           and runlevel [!06]
           and started dbus
           and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
                or stopped udev-fallback-graphics))
          or runlevel PREVLEVEL=S)

stop on runlevel [016]

emits login-session-start
emits desktop-session-start
emits desktop-shutdown
```Has anyone seen a fallback mode? I have not.

Regards,
Effenberg
I'm still thinking since then they added nore on KMS... Just from looking through over 100 xorg logs since June on Natty and Onierics since August, the current fall-back seems to be KMS is left on and for drivers, if it can't find one, then it tries the nouveau first then the VESA... 

If you set a vga=788 (set to a  Linux VESA mode of 800x600) and/or a nouveau.modeset=0 (turn off and do not try the nouveau driver) , then even new nvidia cards boot into VESA using a default driver.  

As cariboo907 said- 
> At one point several releases back there was a failsafe X mode in the  recovery menu, but that is no longer available, it might be time to urge  the Xorg developers to bring it backI really miss telling people to go to that recovery option, boot... install their driver...

---

### Post by ranch hand on 2011-10-19
> **effenberg0x0 said:**
> Hey madjr. I've come to the conclusion that it generally means anything that is not colorful and fun. Users can't tell at what stage their PC is: BIOS, Grub, Boot, Console. Most of these are considered Black Screen.

Just so you see I'm not kidding, I had a user that didn't knew the possibility of reboot, only power on or poweroff. I replaced "sudo reboot now" for "remove PC power cable (the thick black one) from outlet, count to 5 and reinsert".
That is why we have to have a splash screen.  Very important.

---

### Post by PaulInBHC on 2011-10-19
With prior releases and an old Radeon 7000 card, I had black screen, no cursor, no signal detected flashes on monitor and no activity on HDD light. You sit there a while and no noises or anything happens. That's what I consider a black screen.

---

### Post by seeker5528 on 2011-10-21
> **buzzmandt said:**
> Turned out to be a bios setting, something about a memory hole.  I think it was set to yes and i changed it to no or something like that...... 

but damn talk about obscure.

If it was the 'OS/2' memory hole thing, then it should only be enable if you have 'OS/2', that's the only thing that comes to mind of the top of my head. Having said that, don't know why it would be an issue to have the memory hole enabled.

Later, Seeker

---

### Post by effenberg0x0 on 2011-10-21
> **buzzmandt said:**
> I tried for 3 days and many burns and packs  after packs of cigarettes to install on a friends machine about a year  ago.... I couldn't find anything wrong but it would just hang and then  black screen.....

Turned out to be a bios setting, something about a memory hole.  I think  it was set to yes and i changed it to no or something like that...... 

but damn talk about obscure.

I can understand how Linux can destroy one lungs :) As soon as things get complicated, I practically eat a couple packs.

I have this option in my BIOS ("Memory Hole Remapping"). Makes no difference to boot with or without. AFAIK, it is only relevant in older motherboard, to allow for more than 3GB of RAM. In my case, on or off I still see the same amount of RAM (16GB) on 64Bit Kernel.

And this setting is known to produce BSOD in W7, not Linux. See standard google search, all mentions are regarding W7 issues. BIOS reports more RAM than W7 Home can handle. W7 users must use ForceEnable PAE.

[http://www.google.com/search?client=ubuntu&channel=fs&q=memory+hole+remapping&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=memory+hole+remapping&ie=utf-8&oe=utf-8)

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-10-21
> **PaulInBHC said:**
> With prior releases and an old Radeon 7000 card, I had black screen, no cursor, no signal detected flashes on monitor and no activity on HDD light. You sit there a while and no noises or anything happens. That's what I consider a black screen.

Probably an  issue in the support for standard vbe 2.0/3.0 or e(ddc) 1/2. Linux probably follow standards while the proprietary card has a slightly different implementation.

Regards,
Effenberg

---

### Post by PaulInBHC on 2011-10-25
Black screen, press tab and enter?

[http://ubuntuforums.org/showthread.php?p=11394049#post11394049](http://ubuntuforums.org/showthread.php?p=11394049#post11394049)

---

### Post by effenberg0x0 on 2011-10-26
It's a good tip. If grub is loaded, but not visible, one can try such things. Sometimes I find myself in a black VT, login and sudo reboot without seeing a single character. On slow buffered ssh sessions too... It sucks, but it's a way out. The only problem would be the more than 100 other situations in which it wouldn't help lol :)

Ex of what occupies a part of my day: Why does some users get a kernel panic (supposedly: there's no video, one can't see why the boot is stalled) no matter what they try on BIOS and grub parameters, using modern PCs, and the only workaround known is to start a memtest, exit the memtest immediately, and then go for a kernel option? Why do other users can only get grub to work after reseting BIOS with jumper 1 (or removing motherboard battery), even after loading BIOS defaults? Why does some PCs seem to only accept to boot via USB if you change the other HDD/ODD priority order (even if booting from USB is set as the first priority device for boot)? How come a modern VGA can not be compatible with vbe 2.0/3.0, even if it says it supports it to specs?

I've been documenting these problems for a while now. Not only with issues seen in this forum, but other forums and onsite implementations. While there are some obvious problems (plymouth, bad disks, etc), I can tell there are probably more than 50 undocumented situations that *seem to be* related to (standard) hardware. There's a guy flowcharting these things. It's a huge flow.

---

