---
title: "can't boot ubuntu in vmware...."
date: 2007-11-08
forum: Virtualisation
---

### Post by kushan_2001 on 2007-11-08
can't get ubuntu to load, keep getting the following error...
**Error:**
Operation on file "D:\ubuntu-nessie2\Ubuntu-nessie2.vmdk" failed.
If the file resides on a remote file system, please make sure your network connection and the server where this disk resides are functioning properly. If the file resides on removable media, reattach the media.
Choose Retry to attempt the operation again.
Choose Abort to terminate this session.
Choose Continue to forward the error to the guest operating system.

pls help...

____________________________________________________

---

### Post by kwlskwlguy on 2007-11-08
I'd try reinstalling Vmware server/player.

---

### Post by Delvien on 2007-11-08
> **kwlskwlguy said:**
> I'd try reinstalling Vmware server/player.

No, this is totally incorrect.

---

### Post by Delvien on 2007-11-08
If you have a networked or shared file that is linked to the VM, and you have deleted it or have disconnected the drive that it is connected to then your VM wont start or it will have errors.

Your vmdk looks like it was moved, move it back or use the "open an existing VM" option

---

### Post by kwlskwlguy on 2007-11-08
> **Delvien said:**
> No, this is totally incorrect.

Oh, I'm sorry, I hadn't realized.  I was only basing my answer on the lack of specificity in the orig question and my 3 or 4 years of  experience using Vmware Workstation, Player, Server, and now ESX.

A reinstall has solved my problems more than a few times, but I'll just leave this one to you Delvien, LOL, whatever.  A little courtesy goes a long way.


OK, Back to the Problem.
Which version of VMware are you using, and like the suave Delvien insinuated, is your D drive a Mapped Network Drive, or an External, or is it another drive/partition in your PC box?

---

