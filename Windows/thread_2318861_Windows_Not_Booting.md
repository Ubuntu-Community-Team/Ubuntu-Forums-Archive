---
title: "Windows Not Booting"
date: 2016-03-30
forum: Windows
---

### Post by Shadius on 2016-03-30
Hi all,

I've got an Acer running Windows Vista.  Recently, it has been unable to boot into the desktop.  It just displays a black screen with the mouse pointer.  I've tried "Repair Your Computer" and running a CHKDSK on the C: drive, but it still doesn't boot.  I think the laptop died when it was installing Windows Update and when I powered it up, it was unable to boot into the desktop.  Any help is appreciated.  This is my only Windows computer and it has a lot of data on it.  What else can I try? Thanks in advance.

---

### Post by westie457 on 2016-03-30
While in 'Repair Your Computer' are you able to do a system restore?

---

### Post by Shadius on 2016-03-30
It says "No restore points have been created on your computer's system disk.  To create a restore point open [COLOR="#0000CD"]System Protection[/COLOR]."  Upon clicking "System Protection" a dialogue box pops up saying, "Your computer is running in a limited diagnostic state.  If you use System Restore in this limited state, you cannot undo the restore operation.  Help topics are not available in this state."  

So it seems I'm not able to go back to a restore point. :(

---

### Post by westie457 on 2016-03-30
With no restore points set it won't work.
Next idea, try booting into 'Safe Mode with Networking'. If the screen goes to a default resolution open Device Manager to try and roll-back the Graphics driver then try updating the Graphics driver rebooting where necessary.

---

### Post by Shadius on 2016-03-30
I can't understand how there's no restore points.  There should be a few.  I never turned off Restore Points.  Anyway, I tried to boot into ***Safe Mode with Networking*** and it loaded to the same black screen with the mouse pointer.

---

### Post by westie457 on 2016-03-30
I have to go off-line now for a while.
What happens with the Graphics if you try booting a Live DVD/USB?
Will get back to this later.

---

### Post by Shadius on 2016-03-30
I will try booting into a Live Ubuntu DVD and report back what happens.  Appreciate the help so far.

---

### Post by Shadius on 2016-03-30
I was able to use the Ubuntu LiveCD.  Graphics are fine.

---

### Post by westie457 on 2016-03-31
Hi Shadius
Well at least the LiveCD proves the graphics card works. It is now likely the windows driver is corrupted.

How to fix it? 
In the Repair Windows CMD prompt type 'sfc /SCANNOW'  hit Enter and wait for it to finish.

Found this possible fix here. [https://social.technet.microsoft.com/Forums/windows/en-US/04d2d42d-9fb0-49ba-8d39-4ac934c3783c/black-screen-white-mouse-pointer?forum=itprovistadesktopu](https://social.technet.microsoft.com/Forums/windows/en-US/04d2d42d-9fb0-49ba-8d39-4ac934c3783c/black-screen-white-mouse-pointer?forum=itprovistadesktopu)

---

### Post by Shadius on 2016-03-31
> **westie457 said:**
> Hi Shadius
Well at least the LiveCD proves the graphics card works. It is now likely the windows driver is corrupted.

How to fix it? 
In the Repair Windows CMD prompt type 'sfc /SCANNOW'  hit Enter and wait for it to finish.

Found this possible fix here. [https://social.technet.microsoft.com/Forums/windows/en-US/04d2d42d-9fb0-49ba-8d39-4ac934c3783c/black-screen-white-mouse-pointer?forum=itprovistadesktopu](https://social.technet.microsoft.com/Forums/windows/en-US/04d2d42d-9fb0-49ba-8d39-4ac934c3783c/black-screen-white-mouse-pointer?forum=itprovistadesktopu)

Westie457,

I input "sfc /SCANNOW" from the CMD and I get this:

[B]Beginning system scan.  The process will take some time.  

There is a system repair pending which requires reboot to complete.  Restart Windows and run sfc again.[/B]  

I restart and run sfc again, but it tells me the same thing.

---

### Post by westie457 on 2016-03-31
[http://www.kapilarya.com/there-is-system-repair-pending-which-requires-reboot-to-complete](http://www.kapilarya.com/there-is-system-repair-pending-which-requires-reboot-to-complete)

Two possible chances to force 'sfc /scannow' to run, try them in the order given in the link.

---

### Post by Shadius on 2016-04-01
> **westie457 said:**
> [http://www.kapilarya.com/there-is-system-repair-pending-which-requires-reboot-to-complete](http://www.kapilarya.com/there-is-system-repair-pending-which-requires-reboot-to-complete)

Two possible chances to force 'sfc /scannow' to run, try them in the order given in the link.

Trying **"dism.exe /image:C:\ /cleanup-image /revertpendingactions** gives me 'dism.exe' is not recognized as an internal or external command, operable program or batch file.

Tried the Registry Editor but there is not RebootPending key. 

I'm at a total loss with this. :'(

---

### Post by westie457 on 2016-04-01
Hi Shadius,
I am learning as we go through this trying to fix w/out resorting to a reinstall or factory reset.
If not already done back-up your data and all downloaded program installation files if you still have them.
Reinstalling is the last resort.

In the meantime here is a suggestion on how to get dism.exe recognised.

[http://www.myonestopforum.com/viewtopic.php?t=3880&p=4117](http://www.myonestopforum.com/viewtopic.php?t=3880&p=4117)

Also on another forum there is this. [http://www.techsupportforum.com/forums/f217/solved-and-quot-0xc0000034-and-quot-when-vista-boots-655227.html](http://www.techsupportforum.com/forums/f217/solved-and-quot-0xc0000034-and-quot-when-vista-boots-655227.html) follow the link in post #13

---

### Post by Shadius on 2016-04-10
Tried it.  Didn't work.  Looks like it's dead.

---

### Post by westie457 on 2016-04-11
Unfortunately it is looking that way.
Have been looking for ways to do a non-destructive reinstall of vista.

This looks to be a comprehensive guide (mostly for Win 7) [https://www.winhelp.us/non-destructive-reinstall-of-windows-7.html](https://www.winhelp.us/non-destructive-reinstall-of-windows-7.html)

Good luck

---

### Post by Shadius on 2016-04-17
Thanks for the help anyway westie.  I really appreciate it.  I'm just gonna try to get my files off the hard drive and that'll be that.

---

