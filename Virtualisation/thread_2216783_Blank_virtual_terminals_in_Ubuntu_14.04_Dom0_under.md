---
title: "Blank virtual terminals in Ubuntu 14.04 Dom0 under Xen 4.4 (UEFI)"
date: 2014-04-13
forum: Virtualisation
---

### Post by jwbrase on 2014-04-13
I have a newly built machine running Ubuntu 14.04. I've been working on getting Xen 4.4 set up on the machine. When I first installled Xen, it was booting via grub, and I was getting an error message "WARNING: no console will be available to OS". Upon boot, tty7 showed MATE display manager just fine (and X worked upon login), but the other virtual terminals all displayed blank black screens. Googling the error message revealed it to be related to booting Xen through Grub on a UEFI system, so I compiled the Xen EFI loader, dropped it into my EFI partition, and set up EFI to load Xen directly on boot. I no longer receive the error message, and the kernel does display some text output on boot (there is no splash screen when booting Xen directly from EFI, which I'm perfectly fine with), but once boot is complete I have the same problem as before: I get graphical output on tty7, but the other virtual terminals are completely blank.

I set up xen.cfg to boot Linux with the following command line:

```
vmlinuz-3.13.0-22-generic root=UUID=52e0c93e-56c1-47f1-9717-98e4161d71de ro  quiet splash crashkernel=384M-:128M crashkernel=38
```

From [this]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0CCwQFjAB&url=http%3A%2F%2Fwww-archive.xenproject.org%2Ffiles%2Fxensummit_4%2Fxensummit_linux_console_slides.pdf&ei=5TVLU439Eq6s2AXr5YGICg&usg=AFQjCNEQHh0s2Qh3Yyyd8a_gBye5KwQPIA") source, I made the wild guess that adding "xencons=xvc console=xvc0 console=tty1" might help, but that has not accomplished anything.

Virtual terminals work just fine in bare Ubuntu without Xen. The machine is using a Radeon R7 260X for the graphics adapter.

Can anyone provide any pointers on this?

EDIT: For some more detail, Google returns plenty of results on similar problems with virtual terminals on domU systems, and for serial console problems with dom0, but pretty much nothing on dom0 virtual terminals, other than cases where dom0 fails to load X, or fails to boot entirely. None of these, however, apply to my situation.

EDIT2: A quick "ps -A" under Xen reveals that getty is in fact operating on all six text consoles, despite the lack of visible output.

EDIT3: Curiouser and curiouser... Blindly typing my username and password on tty1, then switching back to X and running "ps -A" in gnome-terminal reveals that the console is receiving input: An instance of zsh starts on tty1 and runs my .zprofile, which is:

```
`echo $- | grep -qs i` && dialog --yesno "Use byobu? (No if starting X session)" 6 30 && exec byobu-launcher || clear && echo "Warning: bare console without byobu. No automatic session locking."
```

Hitting "enter" then causes an instance of screen to start on tty1. Hitting "right arrow, enter" causes nothing further to be launched. Both of these are exactly what I expect my .zprofile to do. This reveals that getty is receiving my username and password and that dialog is properly receiving the keystrokes fed to it.

---

### Post by maxinstuff2 on 2014-09-08
This is a bit old but I think I am having the same problem.

alt+f3 - f6 are all blank screens.

I am running kubuntu 14.04 (fully updated) and graphics adapter is an r9270x (similar to yours).
I think it has something to do with fglrx - with the open source drivers my virtual consoles display fine, but installing either version of fglrx from the repos seems to cause the screens to revert to blank screens. I also installed (and am currently running) the v14 beta drivers from the amd website which have the same issue.

A bit worrying - as the only way to recover a borked system is now recovery mode!

---

### Post by maxinstuff2 on 2014-09-15
I managed to solve this over the weekend.

Basically, I needed to do the following:
> Install the latest beta drivers (currently v14.6) from the AMD website.
> Run ```
sudo aticonfig --initital
``` to generate an xorg.conf file
> Restart into recovery mode - and fix the name of the file, which for some reason get's re-named to xorg.conf-yyyymmdd (or similar) after rebooting. Then reboot yet again.... only then will the proper drivers get used.

EDIT: Then I went into bios and set the graphics mode to VGA. **I believe this is what got my virtual consoles to work, rather than the newer drivers**
Now 3d is working fine and all virtual terminals are available.

As a note, I also had to re-do this process again as I use Steam and it failed to recognize the new graphics mode. I hade to run steam after installing the drivers, BEFORE rebooting, otherwise after the reboot it would not run. I guess this is a bug with Steam :/

---

