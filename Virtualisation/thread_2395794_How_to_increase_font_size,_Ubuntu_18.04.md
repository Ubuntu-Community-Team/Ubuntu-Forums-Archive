---
title: "How to increase font size, Ubuntu 18.04"
date: 2018-07-07
forum: Virtualisation
---

### Post by satimis on 2018-07-07
Hi all,

Host - Ubuntu 16.04 gnome desktop
Guest - Ubuntu 18.04 gnome desktop
KVM

I have installed "Unity control center"

Unity control center -> Displays
Unknown display
(please see attached screenshot_unknown_display.png)

What shall I do?  Install "gnome-tweaks" or "unity-tweak-tool" ?

Please advise.  Thanks

Regards
satimis

---

### Post by PaulW2U on 2018-07-07
> **satimis said:**
> What shall I do?  Install "gnome-tweaks" or "unity-tweak-tool" ?
If you're not running Unity in Ubuntu 18.04 then you don't need the "Unity Control Center" as you already have "gnome-control-center" installed. It's the "Settings" application.
Install only the applications/utilities for the Ubuntu version that you want to tweak.
So, if you have Ubuntu 18.04 (GNOME Shell) running in KVM then install "gnome-tweaks".

---

### Post by satimis on 2018-07-07
> **PaulW2U said:**
> If you're not running Unity in Ubuntu 18.04 then you don't need the "Unity Control Center" as you already have "gnome-control-center" installed. It's the "Settings" application.
Install only the applications/utilities for the Ubuntu version that you want to tweak.
So, if you have Ubuntu 18.04 (GNOME Shell) running in KVM then install "gnome-tweaks".

Thanks

I have gnome-tweaks installed.

To increase the font size of the top menu I have to change "Scaling Factor" from 1.00 to 1.60.  What is its function?

satimis

---

### Post by PaulW2U on 2018-07-07
> **satimis said:**
> To increase the font size of the top menu I have to change "Scaling Factor" from 1.00 to 1.60.  What is its function?
I'm new to kvm myself and I'm too seeing things that I did not expect to. I've previously been a Virtualbox user.

I think "Scaling Factor" is not **changing** the font size but increasing or decreasing the **displayed** font size. I don't know whether you have stumbled on a kvm bug or not as I only use VMs to test ISOs and replicate issues when answering support questions. I don't ever plan to use Ubuntu in a VM on a permanent basis.

In my regular installation of Ubuntu I don't need to use "Scaling Factor" to change the Window Title font as it seems to change as expected.

---

### Post by satimis on 2018-07-07
> **PaulW2U said:**
> I'm new to kvm myself and I'm too seeing things that I did not expect to. I've previously been a Virtualbox user.

I think "Scaling Factor" is not **changing** the font size but increasing or decreasing the **displayed** font size. 
Ok, thanks.  Hoping that other folks on the forum can help.

> 
I don't know whether you have stumbled on a kvm bug or not as I only use VMs to test ISOs and replicate issues when answering support questions. I don't ever plan to use Ubuntu in a VM on a permanent basis.


I'm running both KVM and VirtualBox here.  Both of them are installed on SSD.  I have about 60~70 VMs/Guests installed, all for testing.  Both KVM and VirtualBox are having bugs.

I'm prepared to test "Tensorflow", the Open Source AI.  It is because the 1TB SSD running VirturalBox is nearly full therefore I created several Ubuntu 18.04 guests on KVM ready to start my test.

Regards
satimis

---

