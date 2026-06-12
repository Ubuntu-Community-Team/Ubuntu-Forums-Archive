---
title: "Adobe CS4 Setup Unpacker"
date: 2010-11-04
forum: Wine
---

### Post by riku88 on 2010-11-04
Hello,
I've been trying to get my copy of CS4 to install on ubuntu lately, and i've run into one major problem. There's an unpacker .exe file that unpacks all the setup files to a designated folder (via 7zip standalone .exe unpacker, I believe)
The problem is, no matter what destination for the extraction I use, it always comes back with this error dialog:
[IMG]http://bb.xieke.com/files/Screenshot-7-Zip:%20Diagnostic%20messages.png[/IMG]
This shows up immediately after a percent-done dialog that never gets past 0.

Any idea what to do? 
Thanks in advance,
-Chris

---

### Post by lkjoel on 2010-11-05
> **riku88 said:**
> Hello,
I've been trying to get my copy of CS4 to install on ubuntu lately, and i've run into one major problem. There's an unpacker .exe file that unpacks all the setup files to a designated folder (via 7zip standalone .exe unpacker, I believe)
The problem is, no matter what destination for the extraction I use, it always comes back with this error dialog:
[IMG]http://bb.xieke.com/files/Screenshot-7-Zip:%20Diagnostic%20messages.png[/IMG]
This shows up immediately after a percent-done dialog that never gets past 0.

Any idea what to do? 
Thanks in advance,
-Chris
Try this in a Terminal window:
```
cd /home/chris/.gvfs/Adobe\ Photoshop\ CS4\ Extended.iso/
chmod +rwx ADBEPSHPCS4.exe
sudo !!
sudo chown chris ADBEOHSOCS4.exe
chmod +rwx ADBEPSHPCS4.exe
sudo !!
```
Could you show me the output of the commands in CODE tags? (Shown as "#")

---

### Post by riku88 on 2010-11-06
Thanks, I managed to unpack those files, but it turns out there's another unpacking thing inside. The files are Setup.exe, WinBootStrapper.msi, and WinBootstrapper.cab
When I run Setup.exe I get the generic Wine program error where it says the program "encountered a serious problem and needs to close."
I don't know what to do from here.
Any suggestions?

---

### Post by _outlawed_ on 2010-11-06
What version of Wine are you using, stable or development?

---

### Post by riku88 on 2010-11-06
Stable 1.2.1

---

### Post by _outlawed_ on 2010-11-06
Try the development version. I use Photoshop 7, and it bugs out in dev version but works fine in stable.

---

