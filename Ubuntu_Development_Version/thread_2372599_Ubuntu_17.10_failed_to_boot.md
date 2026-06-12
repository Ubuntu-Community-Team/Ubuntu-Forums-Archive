---
title: "Ubuntu 17.10 failed to boot"
date: 2017-09-26
forum: Ubuntu Development Version
---

### Post by lammert-nijhof on 2017-09-26
I used Ubuntu 17.10 in Virtualbox since June and updated the system each day. I noticed today, that the update of yesterday 25-9 did break the system. It did halt or loop during the boot process, black screen and no disk or network activity. Today I tried the daily build (for some reasons) they had two builds on one day and also that one (the most recent one of the two) stopped during the boot process. It is the first time, since I started using betas in 2011, that a beta has so been f**ked up. Tomorrow I will try again with the latest daily build. Just to be complete in my rant, the betas from Xubutu, Lubuntu and Ubuntu Mate work without any problem, so maybe it is related to Wayland??
Anybody knows what is happening?

I really like those three. For me Lubuntu did not change, since I used it on a 384MB PIII laptop and I love that consistency. I hate the bling bling of many distros, but Lubuntu should have a little bit more, maybe another fusion of distros would be nice; Lubuntu and Peppermint. Xubuntu is also very consistent. In using it, I understand again, why it was my main distro during the introduction of Unity. I liked Unity, but it did not support my video hardware in 2011. Ubuntu Mate brings back my memory of 2010, but it also has that Unity look and feel, so probably I will use it instead of Ubuntu after October. The main reason is that the 3D for Virtualbox is working in Ubuntu Mate (like in L- and Xubuntu) and it never did work in Ubuntu 16.04, 17.10 or Ubuntu Gnome 17.04.

---

### Post by ventrical on 2017-09-27
I think it is gdm3 and kernel 4.13.x-x.

There are bugs file against the kernel and gdm3.

Here is one such example: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1718713](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1718713)

regards..

---

### Post by ventrical on 2017-09-27
lammert,

Could you check you see which kernel you have?

```


uname -a

```

thanks

If it's 4.14.n-n then I have same network probs as you with that kernel.

regards..

---

### Post by lammert-nijhof on 2017-09-27
I can't check the kernel anymore, the system did not boot and I deleted the VM to try a clean install Wednesday. All Ubuntu distros used the same kernels, sometimes with a day of delay, the others have 4.13.0-11 and Lubuntu has 4.13.0-12, but that one has been installed 26-9.

I've seen that bug report and I had more or less the same symptoms.

---

### Post by makitso on 2017-09-27
I have this problem with Ubuntu 17.10 giving a black screen during the boot process in VirtualBox.  Its after the splash and its on the login page.  If I hit the space bar and then type in my password I get by it.  Or, boot with the previous kernel.

Update:  Today's update to kernel 4.13.0-12 fixed this problem.

---

### Post by rrnbtter on 2017-09-27
Greetings,
I can't run a VM with 4.13.0-12 because that kernel won't load my Wifi chip. VM stops with no network error.   With 4.13.0.11 everything including VM works fine. I usually wait out kernel problems and keep a couple of fallback's.

---

### Post by lammert-nijhof on 2017-10-02
I have downloaded the official last beta and the boot problem is solved. The Beta looks beautiful, but too often I click on the first Icon, if I want to select applications from the Dash. The handling of 3D acceleration in Virtualbox has been improved. If it is enabled, it does not show the Wayland session anymore in the login menu. The remaining problem I have, that the desktop freezes looking at YouTube videos in Firefox with 3D enabled in Virtualbox. You have to power off the VM to get out of that situation. A pity because Xubuntu, Lubuntu and Ubuntu Mate all work perfectly well. Like in 2011, when the HW video stack of Unity did not work for my PC, I might have to use an alternative distro for half a year, since I'm moving all my work to VMs.

---

