---
title: "BSOD on Windows XP Startup?"
date: 2011-06-05
forum: Virtualisation
---

### Post by Mazorak on 2011-06-05
So I've been running Natty for a couple of weeks now, and have been quite content with it. Anyways I downloaded the latest version of Virtualbox OSE from the software center, and proceeded to create a Windows XP VM via an iso file on my computer.

The entire setup goes perfectly without any error.
However, once XP is installed, I get a blue screen as soon as the windows logo pops up. Same thing happens with safe mode.

Any help on this would be appreciated!

---

### Post by papibe on 2011-06-05
Is your XP license OEM?

---

### Post by amauk on 2011-06-05
Most likely the virtual machine is emulating hardware that XP does not know how to handle
(XP is over 10 years old)

A quick google shows lots of virtualbox support threads about needing to downgrade the IDE controller that virtualbox emulates from PIIX4 to PIIX3 in order for XP to boot

---

### Post by Mazorak on 2011-06-05
@Papibe: It's not, actually.


> **amauk said:**
> Most likely the virtual machine is emulating hardware that XP does not know how to handle
(XP is over 10 years old)

A quick google shows lots of virtualbox support threads about needing to downgrade the IDE controller that virtualbox emulates from PIIX4 to PIIX3 in order for XP to boot

Yeah, I downgraded to PIIX3, still to no avail.

---

### Post by amauk on 2011-06-05
> **Mazorak said:**
> Yeah, I downgraded to PIIX3, still to no avail.Well, just twiddle about with the VM settings. If there's a lower option for something, change it

Says a lot about the age of an OS when VMs are emulating hardware out if it's scope...

---

### Post by Mazorak on 2011-06-05
I've spent an entire day fiddling with the settings, still does not work.

Anyways, this is the screen I'm getting.

[ATTACH]194285[/ATTACH]

---

### Post by amauk on 2011-06-05
After changing stuff, have you actually deleted and re-installed XP?
Just changing the settings may not do anything if the guest OS was installed with settings it doesn't like

---

### Post by Mazorak on 2011-06-05
> **amauk said:**
> After changing stuff, have you actually deleted and re-installed XP?
Just changing the settings may not do anything if the guest OS was installed with settings it doesn't like

Yeah I've probably reinstalled XP over 5 times now. Also, I think I reinstalled virtualbox a couple of times as well :/

---

### Post by amauk on 2011-06-05
Well, as I said, a quick google brings up all sorts of things about XP BSOD'ing under virtualbox

Maybe try virtualising vista or windows 7 instead

---

### Post by Mazorak on 2011-06-05
So after countless hours of frustration while desperately trying to tweak my Virtualbox settings, I came up with a solution (though some would disagree) :
 
1. Uninstalled Virtualbox
2. Installed VMware Player. Honestly, I did not encounter a single problem, and the overall experience was pleasant.
 
So my advice to you is: if virtualbox is giving you headaches, try VMware. 
 
Anyways, thanks amauk for trying to help.
Cheers.

---

### Post by fjgaude on 2011-06-05
> **Mazorak said:**
> So after countless hours of frustration while desperately trying to tweak my Virtualbox settings, I came up with a solution (though some would disagree) :
 
1. Uninstalled Virtualbox
2. Installed VMware Player. Honestly, I did not encounter a single problem, and the overall experience was pleasant.
 
So my advice to you is: if virtualbox is giving you headaches, try VMware. 
 
Anyways, thanks amauk for trying to help.
Cheers.

Yes, VMware Player 3.1.4 is a solid program working with 
WinXP and later additions of Ubuntu. Works for me.

---

