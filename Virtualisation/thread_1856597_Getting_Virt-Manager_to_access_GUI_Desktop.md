---
title: "Getting Virt-Manager to access GUI Desktop?"
date: 2011-10-08
forum: Virtualisation
---

### Post by nosmadar on 2011-10-08
I am experimenting with virtualization, the goal being getting off of Windows except for a virtual image (Quicken will probably never go "Linux").   

I've got a Core i5 box runing 10.4 LTS and I'm trying to use KVM - the Intel VM features are enabled. I managed to use Ubuntu VM Builder to get one image created  and running (Lucid). I have a separate laptop also on Lucid that I'm using for remote management (Virt-Manager).  However, much to my dismay, when I finally got Virt-Manager to connect to the VM process, the display was character cell, not GUI.

I realize that there may be other things I need to do to make this work as I want, like setting up VNC somewhere. But at this point the *Primary* thing I really want to validate is: Is even possible for a non-GUI server OS like Ubuntu Server to run the guest images which have GUI desktops and have the GUI desktops accessible?

Also can someone tell me if the JEOS images created using Ubuntu-vm-Builder are the issue because part of what was stripped form them was the GUI desktop components?

And last, I gather that Ubuntu development folks are abandoning JEOS and perhaps KVM even for Ubuntu Cloud?  In other words, will Ubuntu Cloud take the place of KVM or other virtualization software options?  

Thanks in Advance.

---

### Post by HermanAB on 2011-10-09
"Is even possible for a non-GUI server OS like Ubuntu Server to run the guest images which have GUI desktops and have the GUI desktops accessible?"
Yes, absolutely.  The VMs have nothing to do with the server display settings, or lack thereof.

And no, you don't need VNC if you run Win XP Pro with RDP.  if you run ordinary XP, then you need to install VNC server in the Windows VMs though since it doesn't have RDP. (RDP is a single user version of VNC that Microsoft licensed from Citrix, with the advantage that Citrix RDP is secure, whereas VNC is a serious security risk.)

Hope that helps!

---

### Post by nosmadar on 2011-11-15
I know it's been a while, but I wanted to clarify my configuration since I'm still stuck.
I have a box running 10.4.3 server and a laptop running Karmic. The idea is to use KVM on the server to host GUI VMs like other Ubuntu versions, but w/o installing X-Windows on the server.  So far I built one VM with JeOS and when I acccess it in Virt-manager it comes up as a text only window.  I found the following comment in the Ubuntu doc which has me concerned:
"The use case targeted when KVM was moved into main is "server virtualization". This means that even though KVM can be used to serve other purposes, it has been designed to be run on Ubuntu Server Edition to host non-graphical server operating systems"

I found documentation stating that there is a "-vnc" flag for the kvm command but it's not in the offical doc.

Can someone please clarify!

---

