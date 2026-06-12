---
title: "Ms office install help- tried everything"
date: 2011-04-17
forum: Wine
---

### Post by kristina_h on 2011-04-17
I am trying to install MSOffice using Wine from a disk. My first attempt involved installing it from Wine directly. I installed wine1.2.2, set the overrides suggested by various other forums, ran the setup.exe with wine from the terminal, and sure enough the Windows-style installation began. However, after a while of loading, the installer informed me that an error occurred and quit. 

My next attempt was to install PlayOnLinux. I chose the Office option, led it to the office disk, and after barely a second it told me that the install was completed successfully without ever launching the Windows msoffice installer. 

I tried uninstalling and reinstalling both programs. Now, when I try to configure wine, the GUI takes almost two minutes to launch, giving me the following error:

```
err:process:_wine_kernel_init boot event wait timed out
```I know that I am a linux novice. However, I feel like the problem might  be some lurking leftover installation files from previous attempts. I  don't know how to start with a clean slate. Does anyone have any  suggestions?

---

### Post by ajgreeny on 2011-04-17
If I were you, and for the easiest way, as you are a new user, I would try synaptic to "Completely remove" wine, then in nautilus hit Ctrl+H to show all hidden files and folders, and remove the hidden /home/username/.wine folder which is where all the programs' configurations are kept for things you've installed with wine.

You may even find that the second part of this is all that is needed and may not need to uninstall wine itself.

---

