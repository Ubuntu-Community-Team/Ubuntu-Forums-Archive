---
title: "Unable to access Bitdefender Gui from Unity bar"
date: 2011-10-25
forum: Security
---

### Post by DanglingPointer on 2011-10-25
I installed Bitdefender a couple of days ago on Ubuntu 11.10.  I was able to see the GUI then, run update and even do a full scan.  But since then I have been unable to access the gui again.  Each time I click on the icon on the unity bar it says...

"Only one instance of this program may run at any given time"

If I log off or restart and try and access Bitdefender, a pop-up says it is loading the engine and another pop-up appears with tips, but that is it.  No gui.

Does anyone here have had the same problem and been able to recover from it?

---

### Post by DanglingPointer on 2011-10-26
No one here have any ideas?  Help please!

BUMP

---

### Post by _Diego_ on 2011-10-27
Same issue here and I don't know what to do to resolve it.

---

### Post by DanglingPointer on 2011-10-27
> **_Diego_ said:**
> Same issue here and I don't know what to do to resolve it.

Hopefully someone here has sorted it... One more BUMP!

If no one knows, we may need to fix this ourselves...  I'll give it another few days... hopefully someone responds.  I'm just too busy to figure it out.  
If no one knows how to get this going with no problems, I'm likely going to recursively scour the whole filesystem and remove every bit of Bitdefender.  Fark it!  I'll install ClamAV.

---

### Post by OpSecShellshock on 2011-10-28
Have you tried accessing it from Dash? Hit the Super key, type in the first few letters, and click on it when it comes up in the list, just to see what happens. I've had some other applications that didn't open quite properly from the launcher but worked from Dash. Sounds like the initial problem is that it was still running even when you'd closed out of it, but that might be by design. Also, check the developer's site. It may not have been tested on 11.10 yet.

---

### Post by _Diego_ on 2011-10-28
This is the discussion on Bitdefender forum:
[http://forum.bitdefender.com/index.php?s=&showtopic=30005&view=findpost&p=124695]("http://forum.bitdefender.com/index.php?s=&showtopic=30005&view=findpost&p=124695")

They suggest this procedure:

"Please run as root:

# rm /opt/BitDefender-scanner/var/lib/scan/bdcore.so
# ln -s /opt/BitDefender-scanner/var/lib/scan/bdcore.so.linux-x86_64 /opt/BitDefender-scanner/var/lib/scan/bdcore.so

"

---

### Post by Starfleet on 2011-10-28
Also don't allow it to run continuously in the background with the drop zone showing on the desktop in Unity. It doesn't work properly and you cannot access the settings controls in most 11.10 installations once hyou have done this. Don't ask me how I know this! It sounds as if that is what has happened. It appears to crash when you ask it to open. Remember, you don't really need a virus scanner running in the background in Ubuntu. Just run it before you do anything important to make sure you haven't picked up a Windows virus to pass onto others.

---

### Post by OpSecShellshock on 2011-10-28
It's not so much that you don't need one, it's that the one you need doesn't exist. Which operationally pretty much amounts to the same thing, I guess.

---

### Post by steelmachine on 2011-12-19
This should fix it, did for me, found this on another forum (Bitdefender forum).

In terminal:

sudo bash

rm /opt/BitDefender-scanner/var/lib/scan/bdcore.so

cat /opt/BitDefender-scanner/var/lib/scan/versions.dat.* |awk '/bdcore.so.linux/{print $3}'|while read bdcore_so;do touch /opt/BitDefender-scanner/var/lib/scan/$bdcore_so;bdscan --update;ln -s /opt/BitDefender-scanner/var/lib/scan/$bdcore_so /opt/BitDefender-scanner/var/lib/scan/bdcore.so;done

---

