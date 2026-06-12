---
title: "Black screen with only cursor"
date: 2024-08-16
forum: Ubuntu Development Version
---

### Post by Peturrr on 2024-08-16
I run 24.10 for a while already, and today after doing a apt-get upgrade and rebooting I am now greeted by a weird startup melody and a black screen with only my cursor.

I can't seem to switch to console and also when disabling wayland in gdm3 config, I still get this black screen, rendering my desktop unusable. 

I am using latest Nvidia drivers (running a GTX 4070 Ti Super). Not sure what happened here?

---

### Post by vhaarr+launchpad on 2024-08-17
Same here, you need to downgrade gnome-shell to [https://launchpad.net/ubuntu/+source/gnome-shell/46.4-1ubuntu1](https://launchpad.net/ubuntu/+source/gnome-shell/46.4-1ubuntu1) and probably mutter from 15 to 14.

That's what I did at least. There's like 10+ packages you need to manually downgrade using dpkg or whatever.

---

### Post by Claus7 on 2024-08-17
Hello,

installing today's iso I was also greeted with this nice melody, yet things were crisp and nice. Installation took place under virtualbox.

Regards!

---

### Post by jbicha on 2024-08-19
Could one of you affected by the issue file a bug for it?

---

### Post by mdrda on 2024-08-19
Same here. RTX 4090, nvidia-driver-550. The problem is there is nothing unusual in the logs. Xorg, syslog, gdm.  By switching to Xfce the login screen appears, screen goes black after login. Will try the above mentioned workaround.
Some more observations:
- have been running Oriole builds with no issues, upgrading every day, on the day when the build with login sound was introduced the graphics broke - could it identify the bad commit?
- driver itself looks running without issues, nvidia-smi command is showing Xorg and Gdm well loaded in VRAM when the screen is black and only mouse pointer is visible
- size of the pointer looks normal, so likely not a wrong resolution problem
- changes in Xorg.conf don't make any difference
- changing the default nomodeset=1 to 0 under modprobe.d nvidia config causes X crash
- changing Wayland to enabled in gdm config changes the behavior to no-signal to monitor

---

### Post by jbicha on 2024-08-19
Well that was basically the day when gnome-shell was updated from 45 to 46. However, there are several related packages in that upgrade so it's a little complex to try downgrading.

---

### Post by majercak on 2024-08-20
Did you have any luck with that issue? I'm also looking into fixing it, but still nothing so far

---

### Post by Peturrr on 2024-08-20
> **jbicha said:**
> Could one of you affected by the issue file a bug for it?

Yes, will do. Can you point me to where I should do that? Launchpad Gnome-Shell?

---

### Post by jbicha on 2024-08-20
In this particular case, this is my recommendation:

File the bug at [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+filebug?no-redirect](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+filebug?no-redirect)

Make a note of the Launchpad bug number that is assigned. Then, on your affected system:

Install the broken gnome-shell updates if they aren't already installed.

Run this command using the Launchpad bug number instead of BUGNUMBER.

```

apport-collect BUGNUMBER

```

Normally, you could just run ubuntu-bug gnome-shell to avoid needing to do the apport-collect step, but the problem here is that you aren't able to run your web browser on the affected system to finish filing the bug.

---

### Post by slalancette on 2024-08-20
Hello, same here. I used shift-key on startup to get to Grub menu and select previous kernel image so I can use my computer.  The automatically updated one, 6.8.0-40 didn't boot. It says I/O error dev sda, sector 88152992.


Some info:
sebas@sebas2:~$ uname -a
Linux sebas2 6.5.0-44-generic #44~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue Jun 18 14:36:16 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
sebas@sebas2:~$ apt list --installed | grep -e linux-image -e linux-headers -e linux-modules


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


linux-headers-5.15.0-118-generic/jammy-updates,jammy-security,now 5.15.0-118.128 amd64 [installed,automatic]
linux-headers-5.15.0-118/jammy-updates,jammy-updates,jammy-security,jammy-security,now 5.15.0-118.128 all [installed,automatic]
linux-headers-6.5.0-44-generic/jammy-updates,jammy-security,now 6.5.0-44.44~22.04.1 amd64 [installed,automatic]
linux-headers-6.8.0-40-generic/jammy-updates,jammy-security,now 6.8.0-40.40~22.04.3 amd64 [installed,automatic]
linux-headers-generic-hwe-22.04/jammy-updates,jammy-security,now 6.8.0-40.40~22.04.3 amd64 [installed,automatic]
linux-headers-generic/jammy-security,now 5.15.0.118.118 amd64 [installed,upgradable to: 5.15.0.119.119]
linux-image-5.15.0-118-generic/jammy-updates,jammy-security,now 5.15.0-118.128 amd64 [installed,automatic]
linux-image-6.5.0-44-generic/jammy-updates,jammy-security,now 6.5.0-44.44~22.04.1 amd64 [installed,automatic]
linux-image-6.8.0-40-generic/jammy-updates,jammy-security,now 6.8.0-40.40~22.04.3 amd64 [installed,automatic]
linux-image-generic-hwe-22.04/jammy-updates,jammy-security,now 6.8.0-40.40~22.04.3 amd64 [installed,automatic]
linux-image-generic/jammy-security,now 5.15.0.118.118 amd64 [installed,upgradable to: 5.15.0.119.119]
linux-modules-5.15.0-118-generic/jammy-updates,jammy-security,now 5.15.0-118.128 amd64 [installed,automatic]
linux-modules-6.5.0-44-generic/jammy-updates,jammy-security,now 6.5.0-44.44~22.04.1 amd64 [installed,automatic]
linux-modules-6.8.0-40-generic/jammy-updates,jammy-security,now 6.8.0-40.40~22.04.3 amd64 [installed,automatic]
linux-modules-extra-5.15.0-118-generic/jammy-updates,jammy-security,now 5.15.0-118.128 amd64 [installed,automatic]
linux-modules-extra-6.5.0-44-generic/jammy-updates,jammy-security,now 6.5.0-44.44~22.04.1 amd64 [installed,automatic]
linux-modules-extra-6.8.0-40-generic/jammy-updates,jammy-security,now 6.8.0-40.40~22.04.3 amd64 [installed,automatic]

---

### Post by Peturrr on 2024-08-21
Interesting, when I select a previous kernel, I boot normally into Gnome.... So is it some kernel issue or so? I am now reinstalling my Nvidia driver for this kernel (6.8.0-31) to see if it then also boots.

-
Hmm, that fails immediately after boot, with the same black screen. So it might be a Nvidia Driver vs Gnome incompatibility or so. I'll make a bug report, since there is not much else I can figure out.

---

### Post by Peturrr on 2024-08-21
I added a bug report, following the instructions by @jbicha 

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/2077530](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/2077530)

Please add your own experience to that bugreport if you are also suffering from this.

---

### Post by mdrda on 2024-08-21
Yeah, same experience. When removing Nvidia drivers, all good.  Tested with the latest new open drivers.  nvidia-driver-560-open (560.28.03-0ubuntu0~gpu24.10.1) .
Same thing. Black screen with a mouse cursor. Doesn't look like a kernel or driver issue.

One interesting fact: if I connect to the running session via RDP client from a different machine (RDP server provided by Gnome desktop sharing) , I'm getting the same black screen. Looks like there is just a single flaw in there - Gnome is just not rendering things on the canvas :-)  Quite important flaw though ;-)

---

### Post by mdrda on 2024-08-26
Fixed after today's upgrade. All good.

---

### Post by IanW on 2024-08-29
Kubuntu has it now. :(

UPDATE - Fixed by removing the proprietary Nvidia drivers

---

