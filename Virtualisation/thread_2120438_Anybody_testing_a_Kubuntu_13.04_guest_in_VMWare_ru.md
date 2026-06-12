---
title: "Anybody testing a Kubuntu 13.04 guest in VMWare running on a Windows Host?"
date: 2013-02-26
forum: Virtualisation
---

### Post by mparillo on 2013-02-26
If so, could you see if you can confirm my bug report:
[https://bugs.kde.org/show_bug.cgi?id=311974](https://bugs.kde.org/show_bug.cgi?id=311974)

---

### Post by meteorrock on 2013-02-26
I am running ubuntu with gnome 3+ as my guest OS. Before I was using unity. No bugs in Vmware here. Check your onboard mouse settings in your ubuntu guest OS. I suspect its an user error since I have seen this bug on mouse controls on other desktops besides that  KDE desktop being reported on the internet. Got the kernel 3.7.6 upgraded here, which is your ubuntu 13.04. It works fine. 

Using Windows 7 Host here. Vmware workstation 9.0 .

Make sure you got Vmware tools uploaded into your guest OS. That helps with that mouse bug others are reporting all over the net. It will give you full functions for your guest OS. You will have to click inside of your guest OS window for control of your mouse inputs and functions. 

Here is the code for that VMware tools if you do not have it installed already. Open up your terminal. 

```
sudo apt-get install open-vm-tools
```
```
sudo apt-get install open-vm-dkms
```
```
sudo apt-get install open-vm-toolbox
```

Hope that helps. If this is not the issue, let others know you got VMware tools installed correctly in your menu settings of VMware and they can pinpoint it further for you.

---

### Post by mparillo on 2013-02-26
Thanks, I am running VMWare Player 5.0.1 build-894247 and I am pretty sure I have VMWare Tools installed. I have:
```
                                                                                              
mparillo@ubuntu:~$ vmware-toolbox-cmd -v
9.2.2.18018 (build-893683)
mparillo@ubuntu:~$

```

---

### Post by meteorrock on 2013-03-09
Yeah, It loads up after modifying the desktop in Vmware to KDE on Ubuntu, I could not get the stock "Kubuntu" to install through VMware either as an .iso only. Tried that with my Vmware over the last few days.  Something is messed up in the splash-screen, it just hangs there, could be that "lightdm" configuration that comes with KDE for the splash. It works fine though applying the  KDE plasma desktop here though for ubuntu 13.04 stock. I had to use the terminal to apply the desktop on a bare ubuntu build, and reboot into the log-in screen for ubuntu and choose the KDE desktop environment. 


So if you want ubuntu with KDE download and install the ubuntu as a stock .iso and manually install kde as a desktop through the terminal. It will give you the option to start in KDE at the log in screen of ubuntu with Vmware. "Lightdm" works though in vmware on installation for the KDE desktop through the terminal. Weird bug. 

Using Vmware workstation 9.0.1 as of this moment.  Linux kernel 3.8.2 on my ubuntu-kde remix build. Don't go with my kernels, they sure don't feel "stable" . Might revert back to 3.7.6.

---

### Post by mparillo on 2013-03-11
You might be facing this bug:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1153035](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1153035)

I think I did, but I was able to install an earlier Daily Build, but still no luck on using my mouse to reveal the Panel once I set it to auto-hide.

---

### Post by mparillo on 2013-04-26
I just added this to my [bug report]("https://bugs.kde.org/show_bug.cgi?id=311974"):

[COLOR=#2E3436][FONT=Open Sans]This appears to be only when the Panel is at the bottom.
When I read this:
 [/FONT][/COLOR][http://irclogs.ubuntu.com/2013/04/26/%23kubuntu.html#t10:34](http://irclogs.ubuntu.com/2013/04/26/%23kubuntu.html#t10:34)
[COLOR=#2E3436][FONT=Open Sans]I changed the screen edge to left, top, and right.
In all cases, I could use the mouse to reveal the Panel, except for when the Panel is at the bottom.[/FONT][/COLOR]

---

