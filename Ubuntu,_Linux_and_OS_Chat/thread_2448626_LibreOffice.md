---
title: "LibreOffice"
date: 2020-08-10
forum: Ubuntu, Linux and OS Chat
---

### Post by mickee384 on 2020-08-10
why does ubuntu always have LibreOffice vers 1.6.4.4 installed? Mine is at 7.0, but it always seems to be there.

---

### Post by Dennis N on 2020-08-10
It depends on the source. Ubuntu 20.04 repository will provide 6.4.4.4, while Snap = 6.4.5.2, and Flatpak = 7.0.0.3

---

### Post by The Cog on 2020-08-11
And [https://www.libreoffice.org/download/download/](https://www.libreoffice.org/download/download/) offers 7.0.0.3 .deb packages. It's best to uninstall your existing version first. I find synaptic the best tool for doing that - there are many packages to remove.

---

### Post by ping-wu on 2020-08-11
I have recently found the best way to run LibreOffice 7.0 is to use the appimage.

---

### Post by TheFu on 2020-08-11
> **ping-wu said:**
> I have recently found the best way to run LibreOffice 7.0 is to use the appimage.

But that 
[LIST]
[*]doesn't integrate with the OS patches
[*]requires manual updates
[*]newer isn't always better
[*]includes all he other issues using self-contained packages (slow, bloated, often constrained without local control, doesn't always work)
[/LIST]

For people like me, the version of libreoffice on 16.04 is what I want on all releases. Newer versions change some things, not always for the better.

For LTS releases, businesses don't want change. We want the same version, just with security updates only.  That's different from what a home user or developer may want.  Often those users think that newer is better, always.  They typically load a new Linux OS every 6 months.

To each their own. Whatever meets your needs best.

---

### Post by slickymaster on 2020-08-11
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by zebra2 on 2020-08-11
The OP may be confusing "build" with "version". Other than that, I am more interested in file compatibility mode than anything else. Right now everything seems to work fine with my on the job spreadsheets (Windows). I keep everything compatible at work. That seems to be the trick for me. It seems to me that it is the corporate user not so much the home user that has the big interest in office software.Without compatibility I need a VM, dual boot, or a second system. Right now everything is groovy (yes, pun intended).

---

### Post by ping-wu on 2020-08-11
Oops.  What I meant to say is "I have recently found the best way to run LibreOffice 7.0 is to use the appimage", *along with the existing Ubuntu 20.04 built*.  The two LibreOffice versions have their own .config folders and seem to be happily running independent of each other without any conflict.  At lease so far.

Even with the 7.0 version, I am still not able to turn on OpenCL (I have installed the Vulkan driver).  I am running Ubuntu 20.04.1 on Ryzen 7 + Ryzen 580.

---

### Post by mickee384 on 2020-08-16
I'm actually referring to 1.6.4.4 installed along side 7.0.0.3
[IMG]https://1.bp.blogspot.com/-Wih3t0Nx5v0/XzmD3qBm6XI/AAAAAAAA8CI/9xHJtdfRRakHtYj8_GNwQIV7BZPO1hmLwCLcBGAsYHQ/s640/libre_offoce.jpg[/IMG]

---

### Post by deadflowr on 2020-08-17
> I'm actually referring to 1.6.4.4 installed along side 7.0.0.3
Depends on where each is installed from,
You can have the apt version (from either the repos or PPA) the snap version, the flatpak version, and the appimage version all installed at once side by side (by side by side).
Edit: I also forgot you can also have a source built version installed too.
(And maybe the Windows version through Wine, if possible)

Bottom line is there are many ways to have multiple version of packages installed at the same time.

---

