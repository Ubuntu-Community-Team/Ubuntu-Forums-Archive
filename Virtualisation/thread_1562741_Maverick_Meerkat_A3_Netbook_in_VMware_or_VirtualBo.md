---
title: "Maverick Meerkat A3 Netbook in VMware or VirtualBox"
date: 2010-08-28
forum: Virtualisation
---

### Post by Jim_in_Omaha on 2010-08-28
I have been trying to test out the new Netbook edition in both VMware and Virtualbox. What happens is it will boot up to the purple screen and there are no icons. Although if I force a power down it will come up with the options screen to shutdown, hibernate, suspend, etc.

I have tried dozens of different settings to no avail....

Any body have luck with this yet??

---

### Post by Jim_in_Omaha on 2010-08-29
I found this:
[http://ubuntuforums.org/showthread.php?t=1557925]("http://ubuntuforums.org/showthread.php?t=1557925")

---

### Post by nerohc on 2010-09-06
That was helpful. Thank you.
I tried to enable 3d acceleration in virtualbox settings, and put 128mb for video too. It has 1gb RAM. It still happens the same. Should I install any non-free driver?

---

### Post by dcstar on 2010-09-11
Boot up into the netroot recovery mode and install the **ubuntu-desktop** package and then remove the **ubuntu-netbook-default-settings** package.

Then you will get a system that boots to a normal Gnome screen.

---

