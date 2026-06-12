---
title: "How far does DELL customize Ubuntu on its machines (if at all)?"
date: 2020-11-19
forum: Ubuntu, Linux and OS Chat
---

### Post by divinours on 2020-11-19
Hi,
I've just ordered a DELL laptop with Ubuntu. I won't receive it until a few weeks but I'm already considering setup options. Does anyone know if there is an added value to the distribution that comes preinstalled by DELL, compared to a vanilla Ubuntu install ? Does DELL tweak any settings, include custom drivers, or add daemons to optimize battery life, thermals and such? I'm tempted to try Pop OS (which is Ubuntu-based and plays nice out-of-the-box with HiDPI screens and iGPU/dGPU combos), but would not want to lose out on any of the DELL tweaks, if they make using the laptop a better experience... 
Any experience from DELL users ? Thanks !
Benjamin

---

### Post by EuclideanCoffee on 2020-11-19
Check out its OEM repository for details. They make adjustments to kernel and patches to hardware.

[URL="https://linux.dell.com/repo/hardware/"]https://linux.dell.com/repo/hardware/

[/URL]My main Debian machine runs on Dell hardware. I run another Ubuntu device that runs on very old HP. Dell is far superior.

---

### Post by CatKiller on 2020-11-19
It depends on the model.

If there's anything that needs to be done to make the machine work well in the state they sell it, then they'll do that. They have a repository for that software. 

They also upstream those changes, partly to be a good open source citizen, and partly because that means they don't need to keep maintaining it indefinitely themselves when there are other people that want to do it for them.

They also don't want to have to do scores of tweaks and patches in the first place, so they pick already Linux-friendly components to start from.

The Ubuntu installer is also capable of applying hardware-dependent tweaks based on the results from Canonical's testing facility. Those also get upstreamed.

I've been running standard Ubuntu installs (I wanted Cinnamon, and then I wanted KDE) on my 2015 Dell laptop throughout, with no problems.

---

### Post by sdsurfer on 2020-11-20
Not much, although there is still underlying Dell hardware management software. A couple years ago I had a Dell precision tower ordered with Ubuntu. It came with 16.04 installed a full two years after 18.04 was released. So yeah, it's almost like "send it with an empty drive, I'll do it myself."

By "underlying software" I mean, a few times, once during startup and once during work with the O.S. opened, I got pop up notices for BIOS/Dell firmware updates. They obviously didn't come from Ubuntu. No big deal, they updated fine.

---

### Post by grahammechanical on 2020-11-20
Would you break the guarantee if you installed another OS over the one supplied by the retailer?

Regards

---

### Post by divinours on 2020-11-24
Thank you all for the answers. Good point about the warranty: the laptop is paid for by my employer and comes with a 5-year warranty period which I should probably try to keep intact :-\", especially considering my previous experiences with Dell (admittedly from a long time ago, I hope QC has become better...). I'll ask Dell about it. If I'm allowed to change distros, I'll probably give Pop OS a try...

---

### Post by mm28690 on 2021-10-13
Is this repository applicable to all Dell machines - Latitude/XPS, Desktops?

---

### Post by mm28690 on 2021-10-13
> **CatKiller said:**
> It depends on the model.

If there's anything that needs to be done to make the machine work well in the state they sell it, then they'll do that. They have a repository for that software. 

Do you by chance have any idea where(link) to get the machine specific distro?

---

### Post by Tadaen_Sylvermane on 2021-10-13
> [COLOR=#000000]the laptop is paid for by my employer

Without knowing the arrangement here my first statement would be not to bother checking with Dell. Check with your employer as technically it is their machine, not yours. Even if you can do your work from another OS or whatever doesn't give you authority to change things on a machine that you do not personally own.[/COLOR]

---

### Post by dirtydog01 on 2021-11-28
Thanks for the links.

---

