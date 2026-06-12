---
title: "VM recommendations"
date: 2014-02-20
forum: Virtualisation
---

### Post by AmbiguousOutlier on 2014-02-20
Hello, I want to run a variety of VMs running on a remote headless host, being accessed via slow atom client. I tried KVM and I liked the client side tools, however it's very slow and unworkable. I've then tried VirtualBox using RemoteBox on the client, and all though this is a lot quicker than KVM, I can't get it to display full screen seamlessly even with the extensions installed. I've also tried using remote desktop viewer on the VirtualBox VM and the performance was similar to KVM.

Even according to [this](http://virt.kernelnewbies.org/TechComparison); if my main concern is performance and no lag then VirtualBox is really my only option. 

I use citrix at work and the performance of this is very fast and almost unnoticeable but I don't want to spend $500 for a license, so my question is what other tools are there to view VMs?

---

### Post by TheFu on 2014-02-20
KVM performs just as well as any other VM technology here. Perhaps you just didn't tune it?
My daily use ubuntu desktop runs in a private cloud under KVM.  I've used ESXi, Xen, VirtualBox and openvz previously.
I've found that using NX instead of rdp or vnc makes all the difference, but there are a few other VM tuning setup things that must be done too. [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)

---

### Post by AmbiguousOutlier on 2014-02-20
Are you using spice? I couldn't get that working and you blog doesn't seem to be responding.

---

### Post by TheFu on 2014-02-20
> **AmbiguousOutlier said:**
> Are you using spice? I couldn't get that working and you blog doesn't seem to be responding.

Tried spice but found NX to be better. I only run LTS releases and in 2012, spice wasn't quite ready for daily use. Also had issues with keyboard mapping. It is probably much better now - for LAN use. I'd only use it over a real VPN outside the LAN.

Seems some content filters are blocking my blog. Can't figure out why, since there isn't anything nasty or even controversial there. Noticed this from a foreign country then again last week across town at a local business.  Just filtering just HTTP, not any other ports. Anyway, I can only suggest that your network is filtering for some reason. I'd love to know which filter service is doing this - have not been able to determine it from this side.

---

### Post by ajgreeny on 2014-02-20
Depending on what VMs you are trying to run, the problem of lack of full screen even with VBox-guest-additions installed may be the guest's fault.

At the moment it seems that the daily .ISO files of *ubuntu 14.04 will not run full screen in Vbox, whereas any other version is fine.

---

### Post by CharlesA on 2014-02-20
I was running VMs headless with Vbox for ages with no problems. I did use the native remote access tools instead of that VRPD crap though.

Regular RDP for Windows, NX for Linux.

---

### Post by AmbiguousOutlier on 2014-02-28
My experiences so far are;

I've created the VM's on both VirtualBox and KVM and to be honest once they are set up I see no one being better than the other, so I'm hosting my VM's using KVM currently on a Debian headless box. 

I'm using virt-manager to manage my KVM from my ubuntu client. Using the default KVM machine viewer and Ubuntu's remote desktop viewer; both very slow and unworkable for day to day use (I couldn't figure out how to install spice).

I've tried to use this NX protocol, however google keeps returning me to Nomachine. I have set this up and on the whole is very workable, however there is a bug where by occasionally the window focus freezes and I'm unable to switch windows. This means I have to force the machine off and restart it. This is a known bug with no resolution. 

Is there a way to use NX with KVM, FreeNX is currently being used with Nomachine and when this works is very fast.

---

### Post by CharlesA on 2014-02-28
Huh, I haven't experienced that bug with the version of NoMachine's NX that I am using.

Which version are you using 4.x or 3.x? I'm still using 3.x.

---

### Post by TheFu on 2014-02-28
I had that bug about a year ago for a week. Figured out a work-around. Sorry, can't remember what it was now and didn't take any notes. It was something on the client-side.  

I'm also using the NoMachine 3.x client ... .deb and Win7 x64 versions - happily.  Can't wait for the Android version, so I can't travel with just a tablet.
Never tried the NoMachine server - didn't like the limitations and FreeNX sorta "just works" and has for about 3-4 yrs. Think I first used it on a 8.04 system.

Consoles on KVM suck. About the only thing I do on the console is find the IP address and make certain that sshd is running. After that, everything is managed through ssh and ansible-playbooks. I'm working on a **First 5 Minutes on a New Server** article to explain what I do immediately after a new box is put on my network.

---

### Post by CharlesA on 2014-02-28
> **TheFu said:**
> 
Consoles on KVM suck. About the only thing I do on the console is find the IP address and make certain that sshd is running. After that, everything is managed through ssh and ansible-playbooks. I'm working on a **First 5 Minutes on a New Server** article to explain what I do immediately after a new box is put on my network.

+1. I'm running proxmox, so I'm using ye ole Java VNC viewer to connect to the console and it isn't fun, but it does get the job done.

---

