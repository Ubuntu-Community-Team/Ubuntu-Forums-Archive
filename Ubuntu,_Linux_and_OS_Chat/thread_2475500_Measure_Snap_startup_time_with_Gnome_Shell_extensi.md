---
title: "Measure Snap startup time with Gnome Shell extension."
date: 2022-05-29
forum: Ubuntu, Linux and OS Chat
---

### Post by Dennis N on 2022-05-29
There is now a gnome-shell extension that reveals startup time of applications. It was mentioned in the Ubuntu blog May 26. After installing the extension, I measured Firefox snap in a VM of Ubuntu 22.04. First, after installing the extension, I did a power off of the VM. Then power on. Next, started Firefox snap and recorded the time (a popup).

Firefox Snap startup time: 5.052 seconds.
Close Firefox and open again: 1.532 seconds.

Did the same test a Firefox Flatpak in a separate VM of Ubuntu 22.04 on same host. Same procedure.

Firefox Flatpak startup time: 2.791 seconds.
Close Firefox and open again: 1.751 seconds.

It's not the same each time. I repeated for the Flatpak, and the initial statup time was slightly different: 3.512 sec.

Host cpu: intel core i3-4150. Haswell (circa 2014) - 2 cores to the VM.

---

### Post by DuckHook on 2022-05-29
You might find this reassuring: [https://www.omgubuntu.co.uk/2022/05/ubuntu-making-firefox-snap-app-faster](https://www.omgubuntu.co.uk/2022/05/ubuntu-making-firefox-snap-app-faster)

It's good to know the devs are aware of the issues and are working on fixes.

My experience has varied from the tolerable to the intolerable: On my new blazingly fast machine with NVME SSDs, the first start is reasonable and under 5 seconds. On my older HDD&#8209;based 8GB DDR3 RAM machine, it takes an intolerable 35 seconds.

---

### Post by poorguy on 2022-06-02
I'll admit that 22.04 Ubuntu and 22.04 Ubuntu Official flavors have taken a bit of getting used to when compared to previous versions.

Apparently I'm getting used to 22.04 Ubuntu and 22.04 Ubuntu Official flavors because the initial slowness of the Snaps opening after a system restart no longer seems to be as annoying as it was originally.

I'll keep chugging along with  22.04 Ubuntu and 22.04 Ubuntu Official flavors and see how it progresses with time as it really ain't that bad imo.

---

### Post by DuckHook on 2022-06-02
> **poorguy said:**
> …it really ain't that bad imo.
I'm *very* happy with Focal. I've had to work around a few things like Firefox, but that's just a minor irritant. Other than such irritants, my overall experience has been great. That's been the case with Ubuntu and me for years. As much as I complain about some things in Ubuntu, I have no plans to change distros or flavours.

I suspect that my experiences are reflected in most Ubuntu users.

I might change my mind after upgrading Mrs DH, but I'm waiting for the first point release before chancing that.

---

### Post by poorguy on 2022-06-03
I use 20.04 Ubuntu as one of my daily drivers and I've no complaints.

I like 22.04 Lubuntu may not be perfect but it's okay.

Probably best to wait for the first point release.

---

