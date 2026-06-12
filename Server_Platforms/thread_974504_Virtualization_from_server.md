---
title: "Virtualization from server"
date: 2008-11-07
forum: Server Platforms
---

### Post by technosinner on 2008-11-07
This may be a strange question, but I have a 8.04 Server I use for web host testing and file server.  I wanted to know if it's possible at all to use this server as a virtual box?  What I mean is run the VM from the server but connect from another desktop.

I already use Virtualbox on my desktop but I'd like to use the server's resources rather than my desktop.

I've looked at VMWare ESXi but that's overkill for my needs, and by far.  I don't need a complete virtual solution, just a test VM.

Any ideas how I could do this?

Tks!
ts

---

### Post by Thirtysixway on 2008-11-07
Well vmware sounds like what you want.  There is other virtualization software available such as qemu, but I'm not sure if it's what you're looking for.

VMWare has remote access and web access, and runs the machine remotely.

---

### Post by phillik747 on 2008-11-07
I would look into vmware.  I have run vmware 1.0.7 and 2.  Once I upgraded to vmware 2 and had nothing but problems with it on a x86_64 server so I reinstalled my server to i386 and it seems to be working fine now.  There are howto's on running a headless Virtualbox but it seemed to complicated for what I needed. However I really liked vmware 1.0.7; I should have never upgraded. :( 

Some really good tutorials are here [http://www.howtoforge.com/howtos/virtualization]("http://www.howtoforge.com/howtos/virtualization") and on this forum.

---

### Post by windependence on 2008-11-07
Phillik747 is correct. 2.0 has not proven to be a great product. 

VMware server really is not the best solution for a production environment. ESXi runs directly on the hardware with no host OS and is MUCH faster and with a smaller footprint uses much less resources. ESXi can ONLY be managed from a remote PC not from the server itself other than to set the IP and networking information. It is a great product and would probably be the best solution for what you want to do.

-Tim

VMware Channel Partner

---

### Post by FrostyFlames on 2008-11-08
You can install VirtualBox and run the whole thing in command line code and use remote desktop to connect to the VM.

[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server)

---

### Post by technosinner on 2008-11-11
Thanks guys, I'll look into these!

---

