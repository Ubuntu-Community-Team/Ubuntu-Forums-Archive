---
title: "[SOLVED] Ubuntu JeOS, exactly like a full Server but optimised?"
date: 2008-10-29
forum: Server Platforms
---

### Post by batfastad on 2008-10-29
Hi everyone

I'm looking into getting a dedicated server to run our intranet database and mail server.
However rather than getting 2 separate servers, I thought it might make sense to virtualise them both onto 1 server.

So I take it this is where JeOS comes in?

The mail server I was looking to install was the Zimbra Collaboration Suite, which is fully compatible with Ubuntu Server 8.04

Does that also mean it will work fine under JeOS in a VMWare virtual machine?

So anything that runs under Ubuntu 8.04, will run under JeOS. It's just JeOS is optimised to running as a VM?

Thanks, Ben

---

### Post by batfastad on 2008-11-02
Hi guys
Anyone got any info on this?

Is JeOS 32bit or 64bit?

Thanks, B

---

### Post by Thirtysixway on 2008-11-02
JeOS is the server version, but it's made to work better in things like VMWare as a guest machine.  It doesn't come with a lot of the default packages and drivers that ubuntu-server comes with (simple things like wget for example).

Anything that runs under 8.04 will also work on JeOS, it just may require some dependent packages to be installed.  But aptitude or apt-get should take care of it.

---

### Post by batfastad on 2008-11-02
Ok that's really cool. A great idea to slim Ubuntu Server down for VM use, looks like I'll be needing that soon!

Final Q... so is JeOS 32 or 64bit?
Or does it not really work like that in a VM? I guess it could just take on the architecture of the host machine running VMWare Server

Thanks, B

---

### Post by eighto2 on 2008-11-03
I believe it is both, it just depends on what server cd you install from... I've been using the 32bit on on a mysql server runs great!

---

### Post by batfastad on 2008-11-03
Oh right ok, I did see that you can install it straight from the Server CD with "Install a minimal virtual machine"

But I was actually looking through the product info at [http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos) and the CD images at [http://cdimage.ubuntu.com/jeos/releases/](http://cdimage.ubuntu.com/jeos/releases/) and there doesn't seem to be any mention of a different releases of 32 and 64bit versions

The reason I ask is that I was thinking of getting a dedicated server so our remote users get improved speeds when accessing our mail server and intranet DB (currently both hosted over our ADSL connection).

The dedicated server we were looking at is fully 64bit architecture in hardware, but the VM environment given is Debian Etch 4.0 32bit with VMWare server.
So I was wondering whether to install a 32bit or 64bit version of Ubuntu as a VM. Since the host OS is 32bit, but the server hardware supports 64bit

Thanks, B

---

### Post by eighto2 on 2008-11-03
You CAN run a 64bit guest on a 32bit host, only if your cpu(s) are VT enabled (an intel technology Vmware uses for running 64 bits guests) and your bios must also support this technology

---

