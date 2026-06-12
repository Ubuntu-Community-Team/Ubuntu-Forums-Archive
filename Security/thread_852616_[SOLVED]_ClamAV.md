---
title: "[SOLVED] ClamAV"
date: 2008-07-07
forum: Security
---

### Post by Powerman2442 on 2008-07-07
I have installed ClamAV from "sudo apt-get update" -- "sudo apt-get install clamav". Now that I have it installed I can't find it anywhere. In Applications or System.

I also tried installing it via the Synaptic Package Manager and was having the same issues. I know Ubuntu doesn't need an AV program, but I was told that it may be a good idea to scan for viruses so I don't become a hub for infecting other PCs. 

Plus I dual-boot Vista and Ubuntu so I am not sure if a virus on Ubuntu's partition could effect my Windows partition. 

Thanks,
Powerman2442

---

### Post by ProbablyX on 2008-07-07
clamav is just the engine of the antivirus system. You might want a GUI for it, for instance "clamtk".

Theres more info here:
[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html](http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html)

---

### Post by dentaku65 on 2008-07-07
Install it as daemon and resident scan
```
sudo apt-get install clamav-daemon clamav-freshclam
```

---

### Post by Powerman2442 on 2008-07-08
> **ProbablyX said:**
> clamav is just the engine of the antivirus system. You might want a GUI for it, for instance "clamtk".

Theres more info here:
[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html](http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html)

Okay, thanks.

dentaku65 - Thanks as well.

Edit: Okay I have it and the GUI for it installed and running (under clamtk), but I can't update it because I need to be root. How do I open terminal as root to open clamtk with? I thought it was "su -", but I tried that and got this...

derek@derek-laptop:~$ su -
Password: 
su: Authentication failure

Another Edit: I wasn't thinking, but I just opened up a "Root Terminal" and opened clamtk and it let me use the update feature. 

I also think that the Update Manager for Ubuntu updated it before I even had to. Cause it said 1 update available and I checked and it was an update for clamtk. After updating via the Update Manager it didn't tell me my virus database was over 180 and some odd days old.

---

### Post by ProbablyX on 2008-07-08
> **Powerman2442 said:**
> Okay, thanks.

dentaku65 - Thanks as well.

Edit: Okay I have it and the GUI for it installed and running (under clamtk), but I can't update it because I need to be root. How do I open terminal as root to open clamtk with? I thought it was "su -", but I tried that and got this...

derek@derek-laptop:~$ su -
Password: 
su: Authentication failure

Another Edit: I wasn't thinking, but I just opened up a "Root Terminal" and opened clamtk and it let me use the update feature. 

I also think that the Update Manager for Ubuntu updated it before I even had to. Cause it said 1 update available and I checked and it was an update for clamtk. After updating via the Update Manager it didn't tell me my virus database was over 180 and some odd days old.

:) You can also run a program in root mode by typing
>  sudo appname 

like sudo clamtk
Then enter your password to authenticate.
The "su" command is locked in ubuntu for saftey reasons, you must use sudo as above. :)

---

### Post by Titan8990 on 2008-07-08
For a GUI program like that you would want to do:

gksudo GUIPROGRAM

Using sudo give the program your administrative privledges while gksudo will give it roots. In rare casses using sudo to open GUI programs can cause some major issues (according my Ubuntu book).

You are unable to use "su" because you have not unlocked the root account by assigning it a password.

---

### Post by Zoom78 on 2008-07-16
> **ProbablyX said:**
> clamav is just the engine of the antivirus system. You might want a GUI for it, for instance "clamtk".

Theres more info here:
[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html](http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html)

even though it's not as advanced as the windows programs clamtk seems good :)

---

