---
title: "Restrict Windows 2000 from accessing Internet"
date: 2014-06-19
forum: Virtualisation
---

### Post by Tom_ZeCat on 2014-06-19
I have a laptop with Kubuntu 14.04 and Windows 7 under VirtualBox.  I need to run Microsoft Visual BASIC 6, an old development tool, which is not compatible with Windows 7.  I therefore plan to install Windows 2000 to run under VirtualBox thus enabling me to run VB 6.  I do not want to allow Win 2K to access the Internet.  It comes with no firewall, and I have my doubts that a firewall or antivirus software would work on it.  There's no need for it to access the net since VB 6 is the only thing I'll be running.  

When I look at my Win 7 install under VirtualBox in the VirtualBox Manager and I click on Network, I see "Adapter 1" and "Enable Network Adapter" which is checked and greyed out and it says "attach to: NAT".  There are also other choices there.  One of those choices is "not attached."  In my upcoming Win 2K install, if I choose that "not attached" will that thereby block Win 2K from ever accessing the Internet?  If not, how do I block it?  I need to permanently block it.  There's no reason for Win 2K to ever access the Internet.  That would be bad.  I'll be running it with no antivirus and no software firewall.  

In case you need to know why I'm running such an old OS and development tool, I need to rewrite some software that I wrote a long time ago in Visual BASIC 6.  I'll be rewriting it in C++ to run under Linux.  However, all Visual BASIC code is Linux incompatible.  I shudder at the thought of attempting to run Visual BASIC under WINE.

---

### Post by frankmorris2 on 2014-06-19
Hello,

When I choose "not attached", the virtual machine does not have an internet connection. It also prevents the machine to access your local network.

Your machine should be isolated. In some Windows versions, there will be an icon that says "cable unplugged".


Have a nice day.

---

### Post by Matthew_Smith on 2014-06-19
If you're not going to use the internet on Windows 2K, then I don't think firewalls matter, but if you don't want it to, then just go in your virtualbox settings and change the internet or disable WiFi in the virtual machine and host machine.

---

### Post by Tom_ZeCat on 2014-06-19
Okay, that's the info I need.  Thanks for the help.

---

