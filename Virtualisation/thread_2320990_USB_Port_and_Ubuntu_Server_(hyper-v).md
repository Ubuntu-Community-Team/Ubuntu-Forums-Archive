---
title: "USB Port and Ubuntu Server (hyper-v)"
date: 2016-04-19
forum: Virtualisation
---

### Post by wagner3 on 2016-04-19
Hi all,

I'm running a virtual ubuntu machine (Ubuntu 12.04) using Hyper V, on a Windows 2008 R2 host.

I need to use a Usb modem in this ubuntu virtual machine. I read some answers regarding this but can't find a way to do this.

Is there a way to do this without having to install a USB-IP solution? Can I just plug the modem on the host and somehow access trough the virtual machine?

Thanks a lot, all answers will be great appreciated.

---

### Post by MAFoElffen on 2016-04-19
A few ways....

Windows Guest to remote Windows Guest Host...
With using Hyper-V, set your VM internal in the OS to allow remote connection in the System properties. In your VM Guest Host (machine your are connecting from) start a remote desktop connection. At the panel where you see "connect" as an option, to the right of that button will be a link that says "options". Select that link.

The panel that will open will let you select local machine resource options that will be joined to that remote desktop connection. One of the options will be to allow use of the local USB ports... You will need to boot or reboot the VM guest from that connection for it to see a locally attached device, through that local port. Sadly, it doesn't work for everything, but allows "some" local access and resource mapping.

Linux Guest to remote Linux Guest Host
VNC to VNC, or Spice-to-Spice doing the same. 

Linux Guest to Windows Guest Host
VNC to VNC compatible app doing the same.

Like I said, with Hyper-v, is limited... and what is gong to bring it close is the connection between (RDP, Spice or VNC) and how the app on the remote connection maps the local resources. The closest it's going to get is the Win-to-Win with RDP (hyper-v's native ties) and anything else, you would be trying to replicate that.

Personally, I have hyper-v here... but use some of my other Virtual Hosts to host most of my VM's. Hyper-V does what it does, but has it's limits. And what it does do, is not always convenient or easy.

---

