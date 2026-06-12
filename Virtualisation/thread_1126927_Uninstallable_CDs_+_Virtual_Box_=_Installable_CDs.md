---
title: "Uninstallable CDs + Virtual Box = Installable CDs?"
date: 2009-04-15
forum: Virtualisation
---

### Post by DigiTan on 2009-04-15
I've been having game install problems on WinXP.  Basically, any software from CDs or DVDs is uninstallable (see screenshot below).  It happens while the installer tries to decompress .cab files.  The error message is very misleading.  It makes it sound like a media/network problem, but it's actually a flaw in the way cab files were designed (according to other sources).  It says file Retail~1.cab is the problem, but I assure everyone, other cab files will trigger this.

The #1 top remedy for this was to install the game on another computer, copy that directory to disk, and paste that directory onto the "sick" computer.  After checking out VirtualBox recently, I'm wondering if a virtual machine would count as "another computer" in that scenario.  I'm sure there was once a time where cab files **did** work on my system, so I think it should be possible.

Could a virtual machine solve my problem?  Or should I try decompressing the cab files in Ubuntu?


Just because these always get asked, I'll have to put this out there:
[list][*]It's not a scratched CD problem
[*]It's not a DVD drive problem
[*]Rebooting/Disk Cleanup won't fix it
[*]Manually copy-pasting it to the HDD won't fix it
[*]iso images and virtual CD drives are affected too
[*]WinRAR couldn't decompress it (maybe WinZip or Linux stuff?)
[*]Yes, the error is 2 away from 1337
[/list]

---

### Post by Dedoimedo on 2009-04-16
Did you try fixing the Windows?

See here:
[http://www.dougknox.com/xp/file_assoc.htm](http://www.dougknox.com/xp/file_assoc.htm)

And here:
[http://support.microsoft.com/?kbid=321444](http://support.microsoft.com/?kbid=321444)

Regards,
Dedoimedo

---

### Post by DigiTan on 2009-04-16
I'll try that second thing in a short while.  Truth be told, I'd rathter fix this at the source since I've never used a virtual machine before.

---

### Post by Perryg on 2009-04-16
Have you tried setting the Passthrough feature for the CD to on in the VBox setup?

---

### Post by kelvin spratt on 2009-04-16
When you install xp in vbox you get xp version depends on the disc so if you install Xp pro with sp3 that is what you get installed.
  Vbox bin only has 1 serious limitatition it does not play audio cds that it all you can do in xp you can do in vbox including virusess.
So if you have problems installing software it is normally a corrupted cd or xp setup that is at fault also remember to install vbox guest additions to your vbox Xp

---

### Post by DigiTan on 2009-04-16
> **Dedoimedo said:**
> Did you try fixing the Windows?

See here:
[http://www.dougknox.com/xp/file_assoc.htm](http://www.dougknox.com/xp/file_assoc.htm)

And here:
[http://support.microsoft.com/?kbid=321444](http://support.microsoft.com/?kbid=321444)

Regards,
Dedoimedo

Nah, these didn't fix it.  The first one ran fine, but I still get the error.  The second one: Instmsiw.exe said I had the wrong OS (and here I was thinking "XP" meant "XP").  I even tried that other .exe just to be sure I had the right link.

So far, I haven't even made a virtual machine yet.  I just looked at the starting dialogs.  If I have enough partition space to use VBox, I could try that right away.

---

### Post by Dedoimedo on 2009-04-17
If you have the original Windows CD, you can also run:

sfc /scannow

... in the run box, this will fix all broken files, dlls etc.

Cheers,
Dedoimedo

---

