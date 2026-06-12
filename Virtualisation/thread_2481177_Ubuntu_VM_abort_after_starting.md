---
title: "Ubuntu VM abort after starting"
date: 2022-11-21
forum: Virtualisation
---

### Post by satimis on 2022-11-21
Hi all,

Host - Ubuntu 22.04
Guest/VM Ubuntu 22.04 Win 10
Oracle VirtualBox

Hi all,


Just add a new MSI GeForce GTX 1650 Super Gaming X graphic card

1)
Ubuntu 22.04 VM can be started but after playing a while abort automatically. 

2)
Win 10 VM won't abort but the max resolution I can set 1600x1200
The PC is connected to a 4K display

Please advise how to fix the problem?

If it is the driver problem please advise where can I download the correct driver and how to install it.

[B]No problem on the Host is found up to now
[/B]
Thanks in advance.

Regards

---

### Post by &amp;KyT$0P# on 2022-11-21
What version of VirtualBox are you using?

> **satimis said:**
> 2)
Win 10 VM won't abort but the max resolution I can set 1600x1200

How are you determining this is the max?
Does this VM have installed the version of Guest Additions that matches the VirtualBox version?

---

### Post by satimis on 2022-11-21
> **halogen2 said:**
> What version of VirtualBox are you using?



How are you determining this is the max?
Does this VM have installed the version of Guest Additions that matches the VirtualBox version?
Hi,

Thanks for your advice.

There are no other resolutions available for selecting

Guest Additions has been installed before.

I tried to update it but I can't find```

File Machine View Input Devices Help

```

On the top of the Windows 10 VM window

Regards

---

### Post by &amp;KyT$0P# on 2022-11-21
> **satimis said:**
> There are no other resolutions available for selecting

Where are you selecting?

The normal way to change the resolution of a VirtualBox VM is to have installed Guest Additions to match the host version of VirtualBox, then just resize the VM's window just like you would resize any other program's window and Guest Additions will change the VM's resolution to exactly fit the window.

> **satimis said:**
> I tried to update it but I can't find```

File Machine View Input Devices Help

```

On the top of the Windows 10 VM window

Check the setting for that: Oracle VM VirtualBox manager, select the VM, click Settings button, this is configurable under "User Interface".

---

### Post by satimis on 2022-11-21
> **halogen2 said:**
> Where are you selecting?

The normal way to change the resolution of a VirtualBox VM is to have installed Guest Additions to match the host version of VirtualBox, then just resize the VM's window just like you would resize any other program's window and Guest Additions will change the VM's resolution to exactly fit the window.
I did it after starting Win 10

Settings -> System -> Display
Display resolution
[1600 x1200] (max)

on the right bottom-bar corner
-> ^ -> Oracle VirtualBox Guest Addition 6.1.3....
click it without response

I can't run it again

On Linux VM I select screen solution after starting the VM

> 
Check the setting for that: Oracle VM VirtualBox manager, select the VM, click Settings button, this is configurable under "User Interface".
Settings -> User Interface
(check)  Show in Full-screen/Seamless
(check)  Show at Top of Screen

Also tried (uncheck) Show at Top of Screen

I can't only check 'Show at Top of Screen"

All without result to display those items

Regards

[B][COLOR="#FF0000"]
Edit
===[/COLOR][/B]
**Note that the main menu bar is hidden in scaled mode. You can access it by pressing Host+Home.**

Please refer to attached screenshot

Hitting Host+HOME without response

---

### Post by &amp;KyT$0P# on 2022-11-22
At the very top of User Interface settings, there are buttons for whether to display each of the menus on the top of the VM window, and a checkbox to the right of all those which I would assume is for the entire menu bar.  Is that checkbox checked?

If you can't get the menu bar showing, and if you have the status bar on the bottom of the VM window showing the virtual optical drive icon, you could try right-clicking that > "Choose a disk file...", and browse to [FONT=Courier New]/usr/share/virtualbox/VBoxGuestAdditions.iso[/FONT]

---

### Post by satimis on 2022-11-22
> **halogen2 said:**
> At the very top of User Interface settings, there are buttons for whether to display each of the menus on the top of the VM window, and a checkbox to the right of all those which I would assume is for the entire menu bar.  Is that checkbox checked?

If you can't get the menu bar showing, and if you have the status bar on the bottom of the VM window showing the virtual optical drive icon, you could try right-clicking that > "Choose a disk file...", and browse to [FONT=Courier New]/usr/share/virtualbox/VBoxGuestAdditions.iso[/FONT]
Please refer to the screenshot attached.  Thanks

Regards

---

### Post by satimis on 2022-11-22
Further to my previous posting

It should look like the screenshots attached

Right-Ctrl + C

switching between them

I took the screenshots on my spare PC

Regards

---

### Post by &amp;KyT$0P# on 2022-11-22
> **satimis said:**
> Please refer to the screenshot attached.  Thanks

The checkbox to show the menu bar is unchecked.  It's very tiny on your screenshot (to the right of "Help", just before that grey bar at the very right of the window).  Also, you seem not to have the Devices menu selected to be shown (click the "Devices" text to make it look pressed in same as "File", "Machine", and "Help").

---

### Post by satimis on 2022-11-22
> **halogen2 said:**
> The checkbox to show the menu bar is unchecked.  It's very tiny on your screenshot (to the right of "Help", just before that grey bar at the very right of the window).  Also, you seem not to have the Devices menu selected to be shown (click the "Devices" text to make it look pressed in same as "File", "Machine", and "Help").
Performed steps as advised.  Please refer to screenshots attached.

Now
Right-Ctrl + C  
working

But displaying only 2 items - Devices Help
Not showing;
File - Machine - View - Input -Devices - Debug - Help

Regards

---

