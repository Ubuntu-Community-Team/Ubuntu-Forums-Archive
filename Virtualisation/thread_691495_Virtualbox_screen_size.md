---
title: "Virtualbox screen size"
date: 2008-02-08
forum: Virtualisation
---

### Post by Benbow on 2008-02-08
I have just started running xp in virtualbox. The actual screen size is less than one quarter of the normal screen (about the same size as this thread box I'm posting in).
Can I increase this or is it normal?

---

### Post by PhoenixP3K on 2008-02-08
> **Benbow said:**
> I have just started running xp in virtualbox. The actual screen size is less than one quarter of the normal screen (about the same size as this thread box I'm posting in).
Can I increase this or is it normal?

Inside Windows XP you can change the resolution. By default it's set at 800x600. If you need it bigger you must change the resolution INSIDE Windows. 

Right click on the Desktop, go on Proprieties.

---

### Post by p_quarles on 2008-02-08
Moved to Virtualization.

Getting the best resolution in Virtualbox usually requires that you install the "Guest Extras" package. This can be done from the "Device" menu in the virtual machine's window.

---

### Post by Ubeaut on 2008-06-09
There's a new, simple solution to this problem since VirtualBox 1.6.2.

Check out my post at:

[http://ubuntuforums.org/showthread.php?p=5145028#post5145028](http://ubuntuforums.org/showthread.php?p=5145028#post5145028)

.

---

### Post by rleck on 2010-10-02
Install the Guest Extras, as advised, have a look at Ubeaut's good (but aging) advice. Here's my update to Ubeaut's 2 cents, from section 9.6.2 of the virtualbox help manual, currently VirtualBox version 3.2.8

VBoxManage setextradata global GUI/MaxGuestResolution any

will remove all limits on guest resolutions.

VBoxManage setextradata global GUI/MaxGuestResolution >width,height<

manually specifies a maximum resolution.

VBoxManage setextradata global GUI/MaxGuestResolution auto

restores the default settings. Note that these settings apply globally to all guest systems, not just to a single machine.

---

### Post by SeijiSensei on 2010-10-02
I like "seamless" mode which is available from the Guest Extensions.  Usually I start VB on a second desktop, then kick the Windows guest into seamless mode.  I have the Windows panel configured to occupy the top of the screen, so I can use it by moving my mouse to the top edge, or bring up the KDE panel by bringing my mouse to the bottom.

Running the guest in full-screen mode with the Linux and Windows NVIDIA drivers both installed and the Guest Extensions, I have no trouble making Windows run at 1280x720 or 1920x1080.

---

