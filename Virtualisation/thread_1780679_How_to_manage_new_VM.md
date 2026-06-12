---
title: "How to manage new VM"
date: 2011-06-12
forum: Virtualisation
---

### Post by raz230 on 2011-06-12
Hello,
I have an Ubuntu 64b 11.04 Server install setup with KVM on Dell hardware. I have setup a virtual machine using "virt-install --prompt" and followed all the basic prompts.

The vm seems to be running, I listed it here:

rob@lvmhost:~$ virsh list
 Id Name                 State
----------------------------------
  3 vm0                  running

The host OS is a server OS with no GUI.  I can't use virt-manager because I don't have a windowing system running in this machine.  My Guest OS is Ubuntu Desktop 11.04 just for testing - I called it *vm0*

I've tried pointing VNC at the host-server IP address and that was a no-go.  I've read that you need to use virt-manager from another machine.  Ideally I'd like to use a web interface like Proxmox has or VNC on the machine itself.  

How do I get at this instance?

---

### Post by Jake.Debord on 2011-06-14
If you wanted to use virtualbox you could use Phpvirtualbox:

[http://code.google.com/p/phpvirtualbox/](http://code.google.com/p/phpvirtualbox/)

Sounds like something you may be interested in. I have never used KVM they may have something similar but I do not know.

---

### Post by stephanhughson on 2011-06-14
You should be able to connect using VNC.

I'd do:

virsh list --all

which would give me a list of the names of the virtual servers.


Next:

virsh vncdisplay name_of_server
200.200.200.200:0

The 200.200.200.200 is an example IP. You'll get something like that.

For the bit on the end...

:0 = the normal VNC port
:1 = the normal VNC port + 1
:2 = +2 etc...


When you're using a VNC client, it will translate that to 5900, 5901, 5902 etc.


In the virtual server's XML, you'll need to have a mention of VNC somewhere. e.g.

<graphics type='vnc' port='-1' autoport='yes' listen='200.200.200.200'/>

You can edit the XML with the "virsh edit" command.


You can use netstat to check if the VNC port is listening and whether or not it's only listening on 127.0.0.1 or not. There are configuration files in /etc/libvirt/ that you might need to check, but the virtual server's XML is important too.


It might just be easier for you to install Proxmox, which will give you an easier interface. You'll still be using KVM, you'll be using Debian which Ubuntu is based on and you'll have easier access to some of the slightly harder functions.

Don't give up, KVM is excellent :p

---

### Post by dragonslayr on 2011-07-18
Do you have another linux machine with a gui in the building? If so, install virt-manger on that desktop, then you can do it remotely..


File>add connection>over ssh

---

