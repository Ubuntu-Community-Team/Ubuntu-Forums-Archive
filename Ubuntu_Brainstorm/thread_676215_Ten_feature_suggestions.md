---
title: "Ten feature suggestions"
date: 2008-01-23
forum: Ubuntu Brainstorm
---

### Post by Game_boy on 2008-01-23
**1. Custom Distributions**

Basically I want Revisor. There are numerous uses, from helping new users get a custom experience with little effort to feeling like you know something about how a system works. Preferably you could customise packages safely and customise some of the install and log-on screens.

**2. Easier Virtualisation**

As of now it is impossible to install and configure a full home virtualisation solution on Ubuntu without using the terminal and understanding how virtualisation, network bridges and sandboxes function. Canonical could select a set of virtualisation packages and configure them with scripts automatically upon install. A GUI could then give the option to boot an ISO on your disk or a bootloader on another partition.

**3. Windows binaries suggest an installation of Wine**

For new users who don't "get" why their programs don't work, clicking on EXE, MSI and BAT files should suggest an (unsupported) installation of Wine. This does not mean double-click should launch these binaries (security risk) but users should at least know that it is possible to use them.
[B]
4. Concise promotional video[/B]

When explaining about Ubuntu to friends, I am often stuck for ideas that will fit into their Windows-shaped heads. I would love (and indeed the marketing team would very much benefit from) a 2-minute video that sums up the major advantages of using Ubuntu, not over other Linux distros but over Windows and Mac OS X in general terms. The graphics would use Compiz and show the most polished Ubuntu applications, and the voiceover would speak in general terms of performance, freedom and security.
[B]
5. Edit system files by sudo dialog in Nautilus[/B]

Linux often requires configuration files to be edited by hand, and it is hard for a new user to know how to use the terminal, so I propose whenever one tries to edit protected files in Nautilus, an Update Manager styled password box appears to let one do so without cryptic permission errors.
[B]
6. Unified Live Ubuntu[/B]

Using a combination of loopmounted installs, partition managers, Ubiquity and virtualisation, this is what I want to appear to a new and interested user:

1. User downloads a small Ubuntu Installer (of whatever type of system binary, such as .exe).

2. Ubuntu Installer gives friendly welcome screen and asks for computer type and K/Ubuntu preference. It then downloads the relevant ISO in the background .

3. Ubuntu.exe gives a LiveCD view of Ubuntu, but in a window like virtualisation. This can be exited like a LiveCD or if the user clicks install a nested Ubiquity would appear.

4. Ubiquity gives all relevant options including partioning. If partionining cannot be done while the host OS is booted, perhaps the computer could restart at this point.

5. On boot, a GRUB menu with Ubuntu and the other OSs is given, i.e. the loopmounted install has been turned into a real partition in the background by the installer.

6. You now have a dual-boot system with no CD burning and none of the downsides of Wubi. The person is oblivious to the various applications used to achieve this.
[B]
7. Two system themes[/B]

I am not happy with the art team. In every meeting i have checked, they appear to vote for more delays and more meetings each time, despite having no other work to do. The theme has not changed significantly since Warty.

I therefore want to give them some serious work. I propose that Ubuntu develops two themes at a time: one standard and one composited. The composited would be enabled by default and take advantage of all of the eye candy Compiz can provide, while the standard is clean and professional. I want this because we need to make Compiz a more integral part of the system while having a pure GNOME alternative and also standardising the pretty themes which people get and then upset their system due to incompatibilities.

**8. Integrated Backup Solution**

I want Time Machine on Ubuntu, with quite simple functionality but a pretty, Compiz-enabled front end. Currently, while scripts that do this are availible, the average Ubuntu user is not aware that automatic backups could be scheduled nd has no ideac how to retrieve them if neccesary even if a script is running. I therefore propose an enabled-by-default backup program.
[B]
9. System Monitor by default[/B]

New users are unaware how to kill processes. This can be fixed by permanently adding System Monitor to the top bar. I am not pandering to Windows users by suggesting a Ctrl+Alt+Del shortcut, however.
[B]
10. MIDI files prompt installation of a sensible MIDI stack [/B]

Unlike other audio formats, Ubuntu does not suggest or have pre-installed a MIDI software stack. Timidity has no good GUI interface by default and its default sound patches sound bad when playing files designed and tested against the Windows MIDI stack (Sorry, current state of the world.) I want a back-end installed that defaults to an existing Ubuntu media player and has a better set of sound patches.

---

### Post by smartboyathome on 2008-01-24
1. Try Reconstructor or UCK.
2. I would say that Virtualbox would be the best candadite to build this off of. If only it was fully open source. :(
3. That would probably be pretty easy to do if you just create a new (simple) application to be run when an EXE is run and be replaced by WINE when it is installed.
4. Try making one. I don't think that Canonical has the money to make big videos like this.
5. This will be able to happen soon, just wait for PolicyKit to be integrated.
6. The flaw in this is in steps 3 and 4. Nothing can be done to the computer while it is booted up to windows, and it can't reboot because nothing would be loaded. Also, virtualization cannot do all functions (such as 3D effects) so a lot of people would be disapointed that it couldn't be witnessed without dualbooting.
7. While I sort of agree with this, the fact that only a subset of stuff that compiz has is even enabled with the default version makes it not really feel the need for this. I would say have it as an option, but not default. Also, it isn't the art team that delayed it, it was Canonical. Read [this thread]("http://ubuntuforums.org/showthread.php?t=665874&highlight=theme") for more info.
8. TimeVault would need more polish in order to be included in Ubuntu imo. But I do think that Ubuntu needs a backup program.
9. It may be a good idea, but hardly anything is on the panel already. If that got on there, maybe it could be in a drawer with a few other useful things (like xkill, perhaps?).
10. You will probably have to make it yourself, as there are more important things to worry about right now (like hardware support).

---

### Post by pacsum on 2008-01-24
Ubuntu should have at least one graphic interface for all you can do on the terminal. Erasing junk/temp files,...

---

### Post by smartboyathome on 2008-01-24
> **pacsum said:**
> Ubuntu should have at least one graphic interface for all you can do on the terminal. Erasing junk/temp files,...

If it did, then there would be too many programs included in Ubuntu. Also, keep the junk/temp files to the corresponding topic, please. :KS

---

