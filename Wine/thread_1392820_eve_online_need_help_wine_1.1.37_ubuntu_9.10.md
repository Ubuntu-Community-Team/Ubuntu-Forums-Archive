---
title: "eve online need help wine 1.1.37 ubuntu 9.10"
date: 2010-01-28
forum: Wine
---

### Post by panterus on 2010-01-28
ive been trying to get eve online running for the last 5 days on ubuntu 9.10 and wine 1.1.37 (the latest stuff so i hear) but i keep getting exceptions with the direct 3d cross to opengl im not sure exactly what is happening because im new to linux systems but id appreciate any help. if anyone has gotten this to work please explain how.:p

i have heard there may be an issue with running in 9.10 specifically but  it seems that some people have gotten it to work but im not sure how. some of the detail on the eve forums suggest changing the parameters in the regedit under currentuser\\wine\\direct3d but when i look all thats there is direct sound is this maybe part of the problem?

---

### Post by beastrace91 on 2010-01-30
Have you tried this: > Ubuntu-9.10 has a known problem starting Eve-Online. This is a known issue specific to Ubuntu-9.10, and is not a problem with Wine. The workaround includes editting the prefs.ini file found in the Eve Online program folder. Edit "bitsCancelled=1" to "bitsCancelled=0".

This short script will also automate this function at Eve startup runtime:

perl -pi -e 's/bitsCancelled=1/bitsCancelled=0/' "$HOME/.wine/drive_c/users/$USER/Local Settings/Application Data/CCP/EVE/c_program_files_ccp_eve_tranquility/settings/prefs.ini" && wine explorer /desktop=0,1680x1050 "C:\Program Files\CCP\EVE\eve.exe" &

 Here is another using sed instead:

sed -i -e '/bitsCancelled/ s/1/0/' prefs.ini && wine explorer /desktop=0,1680x1050 "C:\Program Files\CCP\EVE\eve.exe" &

Thanks to N3o and Ilya Konovalovfor creating these scripts from the work-around I found along with others on the Eve Online Linux forums.

 

UPDATE: you need to adjust the path's in the script to your installation and use the scripts to start eve. If you edit prefs.ini by hand, you must do it every time you plan to start EVE.

Regards,
~Jeff

---

### Post by Artemis3 on 2010-01-31
Actually thats the lame workaround. The problem is the kernel, do not use 2.6.31. So [go here](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and install the latest 2.6.32 (.7 atm).

All you need to do is click 3 files: linux-headers (i386 or amd64), linux-headers all, and linux-image (i386 or amd64), then reboot.

---

