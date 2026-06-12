---
title: "Wide Screen Virtual Machine in VMware"
date: 2007-07-08
forum: Virtualisation
---

### Post by stormblue on 2007-07-08
I've got windows running in virtual machine and I want windows to go widescreen on my dell 1501.  Linux runs at 1280x800 and I'd like to get windows to run at this resolution or even bigger.  Any ideas on how to get started?

Thanks!

---

### Post by tgm4883 on 2007-07-08
You need to install the VMware utilities (Not sure if thats the right name) than comes with VMware Workstation.

---

### Post by stormblue on 2007-07-08
I've found VM utilities and VM tools.  I think tools is what I want.  Can anyone confirm this?

---

### Post by tgm4883 on 2007-07-08
Yea it's vmware tools

---

### Post by stormblue on 2007-07-08
I have them installed, and I looked at the properties in windows.  I'm not seeing anything that enables me to do wide screen in full screen mode under windows.  I tried adjusting the resolution in windows, but it doesn't have 1280x800.  Any more advice?  Thank you for the help so far.

---

### Post by stormblue on 2007-07-09
I found this [tutorial ]("http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1003")which may be helpful!

---

### Post by stormblue on 2007-07-09
I think this may be my problem when I try to go full screen, I get this error:

Unable to find an appropriate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.

Failed to switch to full screen SVGA mode.

any ideas?

---

### Post by stormblue on 2007-07-09
Issue Resolved!

---

### Post by tgm4883 on 2007-07-09
> **stormblue said:**
> Issue Resolved!

It's great that you got it resolved.  Could you post how and mark the thread resolved for others that may have the same problem

---

### Post by dewdman42 on 2007-07-17
Yes please.  I need to know the answer to this also

---

### Post by campioni on 2007-08-22
sure would have been useful to know this\\:D/

---

### Post by csharpy on 2007-11-26
Ouch, dead end thread. I just ran into this issue as well. Glad someone resolved it, gives me hope anyway :lolflag:

---

### Post by dpj23 on 2007-11-26
real quick here are you using player or workstation???

player may not allow you to adjust screen resolution, However, you can make these adjustments in workstation in a number of different ways...

---

### Post by csharpy on 2007-11-26
Neither, I'm using server

---

### Post by csharpy on 2007-11-29
I finally got around to figuring this out. What I wanted to do was run my guest Windows XP in wide-screen (1280x800) resolution to match that of my Ubuntu host. First I installed the VMWare Tools on the guest.

VMWare guest install instructions:
[http://www.vmware.com/support/ws55/doc/ws_newguest_tools_windows.html]("http://www.vmware.com/support/ws55/doc/ws_newguest_tools_windows.html")

Then I followed Petr's instructions, found on the VMWare forums, for modifying the guest registry for the new resolution.

Guest registry editing instructions:
[http://communities.vmware.com/message/77209#77209](http://communities.vmware.com/message/77209#77209)

After rebooting the guest OS, I was then able to select the new resolution from the windows display properties.

Good luck!

VMWare Server 1.0.4
Host: Ubuntu 7.10
Guest: Windows XP Professional SP2

---

