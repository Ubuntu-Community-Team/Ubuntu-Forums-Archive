---
title: "remote console from a Mac with KVM"
date: 2008-12-31
forum: Virtualisation
---

### Post by eldaria on 2008-12-31
Hi I run a Ubuntu server version 8.10, and I'm setting up KVM, but before I do that I would like to know if it is possible to do remote management of the virtual machines from a Mac OSX? like with VNC or similar.
The reason is that I use my Apple for everyday stuff, and would like to be able to connect to the remote console of the virtual machines.
I know I can SSH to the host, but since I have no GUI on the host, I can not use the virt-viewer application, Or is there a way to do this?
I understtod that virt-viewer uses VNC, but can I use any VNC client to connect remotely?

---

### Post by kaivalagi on 2008-12-31
> **eldaria said:**
> Hi I run a Ubuntu server version 8.10, and I'm setting up KVM, but before I do that I would like to know if it is possible to do remote management of the virtual machines from a Mac OSX? like with VNC or similar.
The reason is that I use my Apple for everyday stuff, and would like to be able to connect to the remote console of the virtual machines.
I know I can SSH to the host, but since I have no GUI on the host, I can not use the virt-viewer application, Or is there a way to do this?
I understtod that virt-viewer uses VNC, but can I use any VNC client to connect remotely?

As KVM uses VNC to provide a "remote desktop" locally there should be no reason why you can't access the same vnc edsktop from another machine on your LAN.

I haven't done it myself but it must be feasible.

Get KVM up and running with a guest OS first, then try connecting with vnc to the remote ip and port for KVM, when it's running.

I recommend using the virt-manager / libvirt packages to setup the VM, it will spit out xml config files to here: ~/.libvirt/qemu/ which should help a little.
[COLOR="Blue"]
Edit: Just found this little Q & A from [here]("http://edin.no-ip.com/content/libvirt-kvm-debian-mini-howto"):

[I]**Q. **I hope to connect my client with VNC from a remote host, how to do so?
**A. **The default VNC setup of a newly created virtual client will bind to localhost only (127.0.0.1), therefore you can't access it though public network. In order to change this behavior, edit the domain configuration file, e.g. /etc/libvirt/qemu/demo.xml, search for the <graphics> section, and update it based on your needs (e.g. edit it as <graphics type='vnc' port='-1' listen='0.0.0.0'/>, where port='-1' means it will search for a free port above 5900 automatically, port='0' means port 5900, port='1' means port 5901, and so on).[/I][/COLOR]

---

### Post by eldaria on 2008-12-31
Thanks, 

I will go ahead and set it all up. :-)

Regards,
Brian Levinsen

---

### Post by kaivalagi on 2008-12-31
Let us know how you get on, it would be useful to know exactly how to get it working for remote access

Cheers

---

### Post by eldaria on 2008-12-31
Sure thing. :-)

---

### Post by eldaria on 2009-01-03
Ok I got a Guest environment setup.

But it was not possible to use the built in vnc client in Mac OSX to connect to the guest.

So I installed tighvnc from Macports[http://www.macports.org/]("http://www.macports.org/"), and now I can connect.

It is a bit strange, I have used the built in vnc client many times to connect to other vnc servers, for example Kubuntu desktop sharing.

---

### Post by kaivalagi on 2009-01-03
What did you end up setting the kvm xml file up like? did you just set the vnc ip to all zeroes like in the article?

Good that you got it working anyway!

---

### Post by eldaria on 2009-01-03
Yes, I just set Zeroes, Originaly I used the eth0 IP, but figured the Zeroes were easier.

---

