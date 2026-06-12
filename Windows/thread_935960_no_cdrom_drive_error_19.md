---
title: "no cdrom drive error 19"
date: 2008-10-02
forum: Windows
---

### Post by unisol on 2008-10-02
i have a amd 64 3800 with 2gb ram 250 gb hd, ati 9550 video card i have winxp home sp3. my problem is my cd and dvd drives dont show up in windows.i uninstalled and reinstalled the drivers but to no avail.i tried the ms registry cleaner, that didnt work. do you think this problem could be caused by sp3. when i try to install the drivers i get this message:Windows cannot start this hardware device because its configuration information (in the registry) is incomplete or damaged. (Code 19)

---

### Post by smoker on 2008-10-03
don't know if this may help, it is a fix for vista, but if you scroll down the page, there are options for XP,
[http://www.windowvistarepair.com/VistaBlog/known-vista-issues/dreaded-vista-error-code-39-code-31-code-32-and-code-19-60/](http://www.windowvistarepair.com/VistaBlog/known-vista-issues/dreaded-vista-error-code-39-code-31-code-32-and-code-19-60/)

best of luck

---

### Post by unisol on 2008-10-04
i tried that and a  few other things. im really starting to believe it is service pack 3 causing the  problem. it happened on my wifes computer, but i was able to fix the problem with MS guided help. no so on this computer. is it safe to uninstall sp3? when this problem started, i also have a new (don't know how it got there)partition in My Computer called INHOUSE. it  has bios, windows utils, burn, and other files in it. any idea?

---

### Post by smoker on 2008-10-04
hi, sorry that link didn't help. you can easily uninstall service pack 3 though, have a look here:
[http://support.microsoft.com/kb/950249](http://support.microsoft.com/kb/950249)

> i also have a new (don't know how it got there)partition in My Computer called INHOUSE. it has bios, windows utils, burn, and other files in it. any idea?

these don't belong to sp3, sound like they may belong to an 'oem' recovery partition, though i can't be sure (maybe it was a 'hidden' partition before you installed sp3),

best of luck

---

### Post by unisol on 2008-10-22
i uninstalled SP3 and that wasnt the problem. i have tried various patches and registry scripts and nothing helps. there are no upper and lower filters in the registry. when i try to reinstall the drivers i get this message:Windows cannot start this hardware device because its configuration information (in the registry) is incomplete or damaged. (Code 19) any ideas?

---

### Post by unisol on 2008-11-13
i found this on anMS forum and i thought i would like to share it. go to "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\IDE"

Once you're there, you should see multiple entries for your IDE drives. 
Check your CD-ROM drives. Check the entry directly below your CD-ROM drives 
to see if any of them have a property for the LowerFilter or UpperFilter. If 
so, delete the property. If you get a prompt saying you can't delete the 
property, you'll have to modify the permissions of the registry entry so that 
you're allowed to edit.

---

### Post by Viranh on 2008-11-13
I had this problem a year or so back. I deleted a registry key to fix it, but I don't remember well enough to be much help. The "upperfilter" and "lowerfilter" thing sounds somewhat familiar. I suppose you could always back everything up and reinstall. Sometimes phantom driver/registry problems are really hard to solve. Good luck.
Edit: it looks like you have it solved, I wasn't paying attention to who posted that.

---

