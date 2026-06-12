---
title: "Host OS Shortcut Keys do not work While VMWare Workstation is Running."
date: 2008-04-28
forum: Virtualisation
---

### Post by davinci0212 on 2008-04-28
I installed Hardy from a clean installation and VMWare Workstation 6.x. I had some trouble installing VMWare, and found a workaround here:

[http://ubuntuforums.org/showthread.php?t=770716](http://ubuntuforums.org/showthread.php?t=770716)

My problem is that when I am running a Guest OS in fullscreen, I lose control of the keyboard shortcuts on the Host OS. For example, I cannot alt-tab, ctrl+alt+D, ctrl+alt+L, etc. All the desktop effects are not available as well. When I close VMware, I still have the same problem until I restart X or the computer. 

Any ideas? Let me know if I can provide more information. 

Thanks!!!!

---

### Post by davinci0212 on 2008-04-28
Also, this problem doesn't happen when I am in "windowed mode" (i.e. not full screen). I have VMware tools installed on the guest OS, but the Host OS is reporting that it's out of date. I'll update VMware tools and report on if that made a difference.

---

### Post by davinci0212 on 2008-04-28
> **davinci0212 said:**
> Also, this problem doesn't happen when I am in "windowed mode" (i.e. not full screen). I have VMware tools installed on the guest OS, but the Host OS is reporting that it's out of date. I'll update VMware tools and report on if that made a difference.

No luck, same problem. :(

---

### Post by davinci0212 on 2008-05-01
Anyone? I have had bad luck getting people to answer my questions so far on this forum :-(

---

### Post by davinci0212 on 2008-05-01
> **davinci0212 said:**
> Also, this problem doesn't happen when I am in "windowed mode" (i.e. not full screen). I have VMware tools installed on the guest OS, but the Host OS is reporting that it's out of date. I'll update VMware tools and report on if that made a difference.

This problem is now happening in "windowed mode" as well. Sometimes it gets so bad that when I open an application on the host OS, pressing any key will immediately terminate that app. 

Help please!!!!

---

### Post by davinci0212 on 2008-05-02
Yay! I actually figured the solution out on my own. Hopefully I'll get to the point where I can give back regularly to this community rather than take :-) Maybe someone can actually make use of this. 

Fix for losing control of VM:

1. Open VMware Workstation
2. Edit | User Preferences | Input Tab
3. Uncheck "Grab when cursor enters window", "Ungrab when cursor leaves window", and "hide cursos on ungrab". 
4. Click Hot Keys Tab
5. Select "Ctrl+Alt"
6. Click close. 

That's it! No more lockups or lost of the Host OS shortcuts. You do lose the ability to move out of the guest OS into the host OS without pressing Ctrl+Alt, but that key combination is fine with me.

---

### Post by jboyers on 2008-06-25
This solution also resolved (in a roundabout way) a different problem I was having.  Sometimes, I would thought I was in an application on the VM Windows XP guest and hit ctrl-z to undo a mistake.  However, I would find that I was on the VMWare Server app itself and accidentally suspend the guest image.  By unchecking the items under Cursor, as you suggested, I stay in the image until I decide via Ctrl-Alt to get out.  Thanks so much!!

---

### Post by kakyoism on 2008-07-01
thank god1
i've been having the same problem, and no one tried to answered my posts.
and it's still there1111
u can see that my exclamation point is gone still111

no shift or control

sorry, ur solution didn't work for me.

---

