---
title: "WARNING: XP Activation in VirtualBox Disables Original XP"
date: 2008-01-29
forum: Virtualisation
---

### Post by rosegarden78 on 2008-01-29
A word to the wise: Choose carefully among virtual PC programs for there is no turning back.  VirtualBox is recommended as it is open source and unlikely to demand money.  I must share with you my experience.  I activated my "new" XP installation inside VirtualBox and used Windows Update to get current.

Then I booted into my real XP and guess what!  Windows Update refused to update my real system.  Three failed attempts to solve this left me with one alternative: Erase original XP because  it is security risk if not patched with current updates.  The good news is Ubuntu likes having the whole disk to itself.  And I like that XP is faster in virtual mode and networks automatically with Ubuntu desktop.

So don't activate XP or Vista in a virtual PC unless you want to disable your original installation and plan to use the program forever.

EDIT: I still ran into problems transferring a VDI file to a different user.  I changed the XML path but all I got was NTLDR failed to boot.  Be careful with your virtual PC file and don't move it between different user paths.  Read documentation carefully before making backup of home folder or .virtualbox folder.

---

### Post by an.echte.trilingue on 2008-01-29
I ran into the same problem with vmware.  The solution is pretty straight forward: just download the wga crack widely available on sites such as the pirate bay, and run it.

However, I am not sure of the legality of this...  Anybody know?

---

### Post by Vadi on 2008-01-29
Um, this is a bit obvious here. You need **two** licenses of Windows if you're using **two** copies.

If you decide to 'transfer' the license to the other, the first get it's license disabled. And vice versa.

I think that you're forgetting that you don't own Windows. Just the license to use it. Wake up, buddy!

---

### Post by an.echte.trilingue on 2008-01-29
It's not so obvious, actually.

I may have misunderstood the parent, but I am using one single installation of XP installed on the same computer, on the same hard drive partition, running on the same processor, just sometimes I run it natively and sometimes I run it from within Linux.  You can read more about the technique [here]("http://ubuntuforums.org/showthread.php?t=380699").

I see nothing against this in the windows TOS, but I am not a lawyer.

---

### Post by Vadi on 2008-01-29
I hope this is the right EULA:

[http://www.microsoft.com/windowsxp/home/eula.mspx](http://www.microsoft.com/windowsxp/home/eula.mspx)

And hey look, they made it easy. First paragraph:

> 1.1 Installation and use. You may install, use, access, display and run **one copy of the Software on a single computer**, such as a workstation, terminal or other device ("Workstation Computer"). The Software may not be used by more than one processor at any one time on any single Workstation Computer.

---

### Post by kyphi on 2008-01-29
You can install as many instances of Windows on Virtual Box as takes your fancy.

What you can NOT do is update each of them because then they become totally separate and seemingly "real" installations.

Why update the VirtualBox operating systems anyway?  When you close them they are gone.

---

### Post by JoshuaRL on 2008-01-29
But isn't what he trying to do different than that?  He's trying to run his XP partition through VirtualBox.  That's different than a normal Virtual instance of XP.  It runs off of all the settings, files, and apps from the XP partition.

But I agree with the solution.  I would say to never update through VirtualBox.  If it says you need to update and you have the time to, do it the "official" way.  Boot into XP, run the updates, and then go back to Ubuntu and VirtualBox.  That would probably keep any issues to the minimum.

---

### Post by jakornblum on 2008-04-04
OK here's what's going on from what I understand.  He's running a dual-boot of XP and Ubuntu.  He's also trying to virtualize the already existing version of XP from within Ubuntu.  So that's ONE copy of XP, it's just being accessed natively sometimes and virtually through VMWare (or equivalent) at other times.  This should not violate the EULA (There's only one copy of XP).  If you want to get around the reactivation issues that can occur with virtualization, follow this guide:
[http://ubuntuforums.org/showthread.php?p=4644845](http://ubuntuforums.org/showthread.php?p=4644845)
Good luck!

---

### Post by theozzlives on 2008-12-21
> **jakornblum said:**
> OK here's what's going on from what I understand.  He's running a dual-boot of XP and Ubuntu.  He's also trying to virtualize the already existing version of XP from within Ubuntu.  So that's ONE copy of XP, it's just being accessed natively sometimes and virtually through VMWare (or equivalent) at other times.  This should not violate the EULA (There's only one copy of XP).  If you want to get around the reactivation issues that can occur with virtualization, follow this guide:
[http://ubuntuforums.org/showthread.php?p=4644845](http://ubuntuforums.org/showthread.php?p=4644845)
Good luck!

You're actually using 2 CPUs and Hard Drives... a REAL one and a VIRTUAL one, you need two licences.

---

### Post by jimmy the saint on 2008-12-21
> **theozzlives said:**
> You're actually using 2 CPUs and Hard Drives... a REAL one and a VIRTUAL one, you need two licences.

I disagree.  The quoted paragraph said that one installation could not be accessed by more than one process or AT THE SAME TIME.  There is ONE installation ONE harddrive in ONE machine being accessed by ONE processor at a time.  He shouldn't need two licenses (in my insignificant opinion) technically, but I am sure that updating the wga tool to make this work is low on M$s list of todos.

---

### Post by stinger30au on 2008-12-21
you can update date anytime you like with patches, its called [autopatcher]("http://www.autopatcher.com/")

---

### Post by PilotJLR on 2008-12-21
> **jimmy the saint said:**
> I disagree.  The quoted paragraph said that one installation could not be accessed by more than one process or AT THE SAME TIME.  There is ONE installation ONE harddrive in ONE machine being accessed by ONE processor at a time.  He shouldn't need two licenses (in my insignificant opinion) technically, but I am sure that updating the wga tool to make this work is low on M$s list of todos.

Depends on the type of license. With OEM Windows (likely what the OP is using), the license lives and dies on the hardware, be it virtual or physical. Not transferable in any way. The 3 activation limit is just MS showing a little flexibility... they could limit it to 1 activation, if they wanted, and see be consistent with the OEM eula.

---

