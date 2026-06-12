---
title: "Need help setting up Wireless in Ubuntu Studio"
date: 2010-10-31
forum: Ubuntu Studio
---

### Post by fumfumfum on 2010-10-31
Hi, I recently switched over to Ubuntu Studio on my Compaq Presario V6500 laptop but I can't pick up any wireless signals and the little orange light never turns blue.

After reading another thread I and ran the following commands:

$ iwlist scanning
result:
> josh@ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

vboxnet0  Interface doesn't support scanning.


and

$ sudo lspci | grep Ethernet
result:
> josh@ubuntu:~$ sudo lspci | grep Ethernet
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)


Can anybody please help? I can't find any wireless drivers online for this laptop that are supported by Linux and I really need wireless access for my studies.

You've probably figured that I'm a Linux noob, but if you guys just tell me what to do then I'm sure I can follow along.

Thanks
Josh.

---

### Post by mango42 on 2010-11-01
Well, I'm a perennial Linux 'noob' (I start afresh with each new version!) but I've also hit this 'problem' and discovered that it is necessary in 'Studio' to load the required networking modules oneself as they apparently conflict with the real time kernel.

Go into your distro DVD, go to /pool/ (can't remember the exact sub-directory) and look for a .deb file called **nm-applet** - try installing it and there will be some error messages calling for other packages/dependencies - make a note of these and find them on the distro, load them, load nm-applet et voila, you'll (most probably!) have net access.

Maybe in your version, you could do all this automagically through Synaptic?

HTH

.

---

### Post by fumfumfum on 2010-11-01
Thanks mango!

I couldn't fine "nm-applet" but I did find "network-manager" and "network-manager-applet" which I assumed were the same thing.

They wouldn't install off the disc because I apparently had the same versions in a software channel already.

So I ran "$ sudo apt-get install network-manager"

I reset and it seems to have installed so now I get the little blue light on my wireless toggle.

However when I bring up the network administration window there is nothing in the wireless or wired tabs. Do I need to input the SSID of available networks directly before I can connect?

---

### Post by mango42 on 2010-11-02
I'm not to be relied on here but ISTR that **nm-applet** is vital for some reason but yes, if your wifi is recognised (eg: wlan0 or whatever active) in network tools, you could try manually entering an SSID. As I said, it all seems to work automagically when nm-applet is present (check if it's on the system monitor processes tab?).

Then there's the old command line route of sudo ifconfig wlanx, iwconfig ditto, dhclient and wotnot - at least that way you can see what's going on or not, as the case may be!

HTH ;-)

---

