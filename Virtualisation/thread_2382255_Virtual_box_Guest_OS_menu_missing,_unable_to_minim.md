---
title: "Virtual box Guest OS menu missing, unable to minimize"
date: 2018-01-11
forum: Virtualisation
---

### Post by wrongusername2 on 2018-01-11
Hi 
    Guest OS in Virtual box does not behave well with host os. 
**VirtualBox Graphical User Interface Version 5.0.40_Ubuntu r115130**
HostOS: Ubuntu 16.04GuestOS: Win7

Problems are    
1) Guest OS does not always show top menu where devices and other items are located. 
2) Guest OS shows Launch bar and Top bar of Host os.
3) Only way to minimize Guest OS is to Shut down Guest OS.

Keyboard Integration: CHECKED
Mouse Integration: CHECKED


I have installed extension pack of Host**(VNC 5.0.40r115)**, and also installed Guest installed for Guest OS.
See the attached files.

Whole interaction is seems to be buggy. 
Please let me know if this is normal behavior or can be improved.






Thanks

---

### Post by cruzer001 on 2018-01-12
> **wrongusername2 said:**
> Whole interaction is seems to be buggy. 
Please let me know if this is normal behavior or can be improved.

I prefer going to the site and loading the latest version.  Maybe that would help in your case, 5.0 is a bit dated.

I think #2 is a setting problem as that is the way I have mine set up (both guest/host panels on top/not running unity).

---

### Post by wrongusername2 on 2018-01-12
Thanks for responding. Newer VB is 5.2.4 and mine is 5.0. I will upgrade later.

I found following work around

>>>>[COLOR=#000000] Guest OS shows Launch bar and Top bar of Host os.[/COLOR]
To make *Launch bar* and *Top bar* of HostOS dissapear from Guest OS, **click on 'Show Desktop' icon** in *Launch bar. *Now the whole screen will be taken up by HostOS.
Then in order to go to GuestOS, click on *VirtualBoox* icon in *Launch Bar*. This will take us to Guest OS. Now  whole screen will be taken up by GuestOS.
 
>>>[COLOR=#000000] Guest OS does not always show top menu where devices and other items are located. 
[/COLOR]Click on ALT+TAB. This shows Launch Bar. Click on ** 'Show Desktop' icon. **Now you will see both *Launch bar* and *Top bar* of HostOS  inside Guest OS
Hover the mouse at the top, this will bring up Menubar for Guest Os. Use the Menubar to minimize Guest OS

Not best of the solution but seems consistent.

Thanks

---

### Post by cruzer001 on 2018-01-12
Yep, keep playing around with the options till you hit on the one you really like.

See ya

---

### Post by wrongusername2 on 2018-01-13
I found a much easier way of transferring control from **GuestOS to HostOS and vicevera**. This method uses ALT+TAB for everything. Ignore the menu shown at the top of GuestOS.  

**1)** Disable *Keyboard integration* as shown below. Means when you are in GuestOS and press ALT+TAB, HostOS will capture the keystroke, not the GuestOS.	'R-click on VM' -> 'User Interface' -> Input -> 'Keyboard'  (UNCHECK)

**2)** If you want to go from HostOS to Guest-OS, do the following
	-Press Alt+TAB
	-Click 'Virtual Box' Icon
	-Then select the 'VM window' belonging to GuestOS
	-Now you should see the Guest OS in full screen mode


**3)** If you want to go from Guest-OS to HostOS, do the following
	-Do not look for top menu bar.
	-Press Alt+TAB
	      Host-OS will capture the key stroke and will show the* application-bar*
	-Click 'Show Desktop' icon 
	-Now you will see HostOS


**What is the drawback of this method?**
   ALT+TAB will not apply to GuestOS. Means when you are in GuestOS and press ALT+TAB, HostOS will capture the keystroke.

---

