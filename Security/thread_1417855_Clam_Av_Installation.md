---
title: "Clam Av Installation"
date: 2010-02-27
forum: Security
---

### Post by Sutieday on 2010-02-27
I just really want to know if there is a way to install clam av through the terminal. I have tried manually installing it, but it doesn't really work. 

P.S. I just want Clam av to just keep my pc working at its best. I have been using windows for so long that I feel like just having an antivirus on my computer.

---

### Post by joberly on 2010-02-27
What method did you use to install it initially, and what exactly is going wrong ? Error messages during install? It won't run? We need more info!

---

### Post by 2hot6ft2 on 2010-02-27
> **Sutieday said:**
> I just really want to know if there is a way to install clam av through the terminal. I have tried manually installing it, but it doesn't really work. 

P.S. I just want Clam av to just keep my pc working at its best. I have been using windows for so long that I feel like just having an antivirus on my computer.
Sure
```
sudo apt-get install clamav
```
and if you want the GUI for it too use
```
sudo apt-get install clamav clamtk
```

---

### Post by Sutieday on 2010-03-01
Thanks! Your code worked. I don't really see a use for the antivirus since ubuntu rarely gets infected.

---

### Post by nannu68 on 2010-03-06
This is latest scan report after fresh updates of clamav. Does this mean i have viruses on system which need to be removed?

ClamTk, v3.08
Sat Mar 6 21:26:10 2010
ClamAV Signatures: 0
Infected files set to be quarantined.
Directories Scanned:
/root

Found 0 possible viruses (5 files scanned).

No viruses found.
-----------------------------------------------------------------------------

ClamTk, v3.08
Sat Mar 6 21:26:33 2010
ClamAV Signatures: 0
Infected files set to be quarantined.
Directories Scanned:
/root
/root/.hplip
/root/.gnome2
/root/.clamtk
/root/.gconfd
/root/.synaptic
/root/.synaptic/log
/root/.clamtk/history
/root/.gstreamer-0.10
/root/.config/gtk-2.0
/root/.clamtk/viruses
/root/.dbus/session-bus
/root/.clamtk/viruses/gdm.VIRUS.VIRUS.VIRUS.VIRUS.VIRUS.VIRUS.VIRUS.VIRUS.VIRUS.VIRUS/.fontconfig

Found 6 possible viruses (181 files scanned).

/root/.clamtk/viruses/gdm/ 0.Xservers
/root/.clamtk/viruses/gdm.VIRUS.V... 20.log
/root/.clamtk/viruses/gdm.VIRUS.V... 20.log
/root/.clamtk/viruses/gdm.VIRUS.V... 0.Xservers
/root/.clamtk/viruses/cache.VIRUS... etc
/root/.clamtk/viruses/cache.VIRUS... var
-----------------------------------------------------------------------------

---

### Post by uRock on 2010-03-06
Looks like they are probably just cookies.

---

### Post by liferocket on 2010-03-17
I tried installing ClamAV through the command line using the code below, and I also tried simply using the GUI Add/Remove application tool.  Both methods gave me the same error, "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." I tried playing with dpkg but I am not very Linux savy :(. advice please!

---

### Post by _h_ on 2010-03-17
> **liferocket said:**
> I tried installing ClamAV through the command line using the code below, and I also tried simply using the GUI Add/Remove application tool.  Both methods gave me the same error, "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." I tried playing with dpkg but I am not very Linux savy :(. advice please!

Try this:

[http://ubuntuforums.org/showpost.php?p=2322201&postcount=2](http://ubuntuforums.org/showpost.php?p=2322201&postcount=2)

---

### Post by liferocket on 2010-03-17
I thought I already some of that, but this time it worked!  Thx!
btw, i'm planning to install on a USB stick drive, so I have a bootable virus removal tool. Any important advice on that?

---

### Post by 2hot6ft2 on 2010-03-17
> **liferocket said:**
> I thought I already some of that, but this time it worked!  Thx!
btw, i'm planning to install on a USB stick drive, so I have a bootable virus removal tool. Any important advice on that?
Good luck trying to install 9.10 to a usb drive it didn't work for me. Kept dropping me to the initramfs prompt after the install anytime I had the hard drive in the machine. If the hard drive wasn't in the machine it would work fine but that defeated the whole purpose. I ended up installing 8.10 and upgrading to 9.04 then to 9.10. Now it works fine.

I removed my internal drive then doing the install, the upgrades and updates before putting the drive back in that way there was no way for it to install grub or anything else to the wrong place. It still has grub legacy but that's fine with me as long as it works.

---

### Post by xhalarin on 2010-03-17
> **liferocket said:**
> I thought I already some of that, but this time it worked!  Thx!
btw, i'm planning to install on a USB stick drive, so I have a bootable virus removal tool. Any important advice on that?

This topic really should be a thread of it's own but...

I have successfully set up 9.10 on a USB drive and it is working great across computers.  Here's a couple quick pointers:

[INDENT]- Undertaking a USB install is not for the feint of heart, you need to be comfortable spending hours troubleshooting and on the command line
- Use a big drive (8GB min, I have a 64GB Patriot Magnum that works really good)
- Do not use any of the USB persistence instructions or frameworks, they all cause problems and headaches in my experience, standard installer with special options works just fine[/INDENT]

I have been meaning to put together some detailed instructions for folks on this but haven't gotten to it.  There is a ton more that I have done to get mine running tip-top.  If you have any specific questions on the process, I will help however I can.  These forums definitely have been an incredible resource throughout the journey and I am very appreciative of all the help people have given on this topic over time.

---

