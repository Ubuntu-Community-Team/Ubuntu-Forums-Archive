---
title: "Virtualbox in Trusty problems"
date: 2014-08-16
forum: Virtualisation
---

### Post by cscj01 on 2014-08-16
I upgraded from 12.04.5 x64 to 14.04.1 x64.  Although my Vbox kernel module was generated, and I could launch my XP VM, the screen is not being managed correctly.  For example, when I launch the VM, the screen comes up and odd characters appear before the XP logon screen.  When I login, the screen is drawn very slowly, and the icons on the start bar do not show descriptions when I mouse over them.  If I click on the Start button, only part of the menu shows.  If I move my mouse pointer over that menu, it will eventually fill in.  If I try to move an open window, trails of the window are left on the screen.  There are many other issues.  My version of Virtualbox is 4.3.10, the one supplied in Trusty.  My vbox-install.log only contains one entry```
/etc/init.d/vboxdrv: 334: /etc/init.d/vboxdrv: /usr/share/virtualbox/src/vboxhost/build_in_tmp: not found
```The problem with this is the only folder in /usr/share/virtualbox is nls.

I have removed and reinstalled Virtualbox to no avail.  The modules installed are
[LIST]
[*]virtualbox
[*]virtualbox-qt
[*]virtualbox-guest-additions.iso
[*]virtualbox-dkms
[*]
[/LIST]
I also installed virtualbox-extension-pack (for 4.3.10) from the Virtualbox web site.

Is there a known problem, or what am I missing?

---

### Post by howefield on 2014-08-16
Thread moved to the "*Virtualisation*" forum.

---

### Post by ajgreeny on 2014-08-16
I would suggest you use the latest version of VBox 4.3.14 from Oracle [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) by scrolling down on that page to the **Debian-based Linux distributions** section and adding the repos to your software sources as shown there.  You should also add the same version of the guest-additions which is also available from that Oracle site.

---

### Post by cscj01 on 2014-08-16
> **ajgreeny said:**
> I would suggest you use the latest version of VBox 4.3.14 from Oracle [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) by scrolling down on that page to the **Debian-based Linux distributions** section and adding the repos to your software sources as shown there.  You should also add the same version of the guest-additions which is also available from that Oracle site.

Removed Virtualbox 4.3.10 and insstalled 4.3.14.  Updated the extension pack.  Same problem.

---

### Post by ajgreeny on 2014-08-16
Let's see if you are in all the right groups for VB to run properly and allow sharing of folders etc etc.
Run command **groups** in terminal and report back the output.  It should contain **vboxusers**

---

### Post by cscj01 on 2014-08-16
Yes, I am a member of vboxusers as well as vboxsf and many others.

I too have 128 MB for Graphics and 2 GB for Memory.  My Display in Preferences was initially set to Automatic, but I have set my display in preferences to None and have entered many different resolutions.  Some seem to work better than others, but they all have the same problems: trails, partial windows, slow response.

---

### Post by ajgreeny on 2014-08-17
In that case I am baffled; sorry.

---

### Post by SeijiSensei on 2014-08-17
Try turning off 3D acceleration for the VM in Settings if it is enabled.

---

### Post by cscj01 on 2014-08-17
I just noticed the following in my Vbox.log:```
00:00:00.328990 Guest OS type: 'WindowsXP'
00:00:00.330544 crCtlSubmit failed -37
00:00:00.349679 fHMForced=true - 64-bit guest
```My XP is 32 bit, and I have set Version on the Basic Tab of Settings = Windows XP (32 bit).  Could this be causing my problem?  If so, what is making Virtualbox force a 64 bit VM?

Edit:  My Ubuntu host is 64 bit.

---

### Post by cscj01 on 2014-08-17
> **SeijiSensei said:**
> Try turning off 3D acceleration for the VM in Settings if it is enabled.

Did not have it enabled, although I have tried it both ways.  Seems to make no difference.

---

### Post by ajgreeny on 2014-08-17
My XP is also 32 bit running fine in Xubuntu 12.04 64bit, and it works very well, as did yours in 12.04, so I wonder if it is a 14.04 problem with VBox and XP.

---

### Post by TheFu on 2014-08-17
I could imagine that Oracle stopped testing XP in vbox for 14.04 and later as support for XP ended prior to the release.  Newer isn't always better.

I know - not an answer, just a thought.

---

### Post by cscj01 on 2014-08-22
I have a thread on the Virtualbox forums about this at [https://forums.virtualbox.org/viewtopic.php?f=7&t=62993]("https://forums.virtualbox.org/viewtopic.php?f=7&t=62993")

If I get this resolved, I'll post it here.

---

### Post by fidelis2 on 2014-08-28
Very similar problem here:

My new Xubuntu 14.04 (64 bit) installation runs Virtualbox (from the   software centre), but a Win7 (x64) and a Win8 (x64) guest won't like my   host's USB(3) ports, no matter if I set in Virtualbox "use USB1" or  "use  USB2" mode for the guest. Expansion pack and vbox user group is  set.
Both guests see the Canon MP printer connected to an USB port and   install the driver, but report a problem with the USB port and so a   complete communication with the printer fails, hence no printing   possible that way.

However, a WinXP (32bit) guest can fully communicate with the very same   printer on a USB3 port, if I set in Virtualbox "use USB1" for the  guest.  The other option "use USB2" does end with the same error as Win7  and  Win8 guests do.

Maybe this is helpful to other readers, too?

(Full story here in the printer thread: [http://ubuntuforums.org/showthread.php?t=2241234&p=13110108#post13110108](http://ubuntuforums.org/showthread.php?t=2241234&p=13110108#post13110108) )

---

### Post by cscj01 on 2014-08-30
Well, the folks over at Virtualbox suggested I create another XP VM.  I did that, and it ran fine.  They did not have any other ideas, so I do not know why my old VM did not work correctly.  I used the same virtual disk and configured it the same as my original XP VM.

With that, I'll mark this thread as solved.  Thanks to all for your assistance.

---

