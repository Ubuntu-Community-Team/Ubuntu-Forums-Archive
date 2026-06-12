---
title: "ubuntu 12.04 fglrx gnome3"
date: 2011-11-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by pulpo69 on 2011-11-27
I'm on ubuntu 11.10 using gnome-shell and fglrx (ati) driver.
I simply like the the gnome-shell much more than unity and the fglrx-driver
worked better for me than the radeon one.
I use ubuntu from the beginning and don't want to change the distribution.
In oneiric I've the problem that gnome don't plays well with the fglrx driver. I saw that in 12.04 is a newer version this driver.
Has anyone tried this driver and gnome shell?
Is fglrx and gnome no o.k.?
Thanks in advance for every hint or advice.

---

### Post by BC59 on 2011-11-27
Well I used the ATI driver and in the Gnome 3 part of Ubuntu 11.10 but I noticed instability. I installed the newer version ATI Radeon Linux Display Drivers 11.11, manually from here:

[http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html](http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html)

I noticed a big difference, but still the flickering was not gone.

After this installed LinuxMint 12 (was then RC) and with this driver everything worked perfectly.

The problem is that Mint for me is boring so I returned to Ubuntu 11.10 and to Unity, which finally I prefer over Gnome 3.

With the manually installed driver I experienced a crash when the kernel was updated, which is normal, so I decided to use the Canonical offered proprietary driver and everything works super now.

---

### Post by Harry33 on 2011-11-27
> **BC59 said:**
> 
...
The problem is that Mint for me is boring so I returned to Ubuntu 11.10 and to Unity, which finally I prefer over Gnome 3.
...


About this sentence ...
Gnome 3 is the desktop environment (DE) common to Unity and Gnome-shell. They are both shells working on Gnome 3 and on the Gimp Tool Kit 3 (GTK+3).
Also Gnome-panel of the Ubuntu 11.10 and 12.04 (dev) is a shell working on Gnome 3 DE.

---

### Post by pulpo69 on 2011-11-27
the problem seems to be solved (for now in 11.10). i installed the xorg-edgers ppa (which includes the newest fglrx-drver) and
the ricotz ppa for the newest gnome. And the problems are gone.
No more unreadable panels with strange cölors, everything seems to work fine.

---

### Post by BC59 on 2011-11-27
> **Harry33 said:**
> About this sentence ...
Gnome 3 is the desktop environment (DE) common to Unity and Gnome-shell. They are both shells working on Gnome 3 and on the Gimp Tool Kit 3 (GTK+3).
Also Gnome-panel of the Ubuntu 11.10 and 12.04 (dev) is a shell working on Gnome 3 DE.

I'm sure in Canonical they are not informed about this, because in the logon screen they give you to select between Ubuntu and Gnome.

---

### Post by Harry33 on 2011-11-28
> **BC59 said:**
> I'm sure in Canonical they are not informed about this, because in the logon screen they give you to select between Ubuntu and Gnome.

Actually those session names describe the default shell environments.
Ubuntu means Unity (default to Ubuntu).
Gnome means Gnome-shell (default to vanilla Gnome).

---

### Post by paul555 on 2011-12-10
I also have the same issue with fglrx and gnome shell. pulpo69 after you installed these ppas you got everything working ok? I see they have unstable packages.

---

