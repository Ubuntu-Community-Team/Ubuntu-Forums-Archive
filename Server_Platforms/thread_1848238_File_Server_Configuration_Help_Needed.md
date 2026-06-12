---
title: "File Server Configuration Help Needed"
date: 2011-09-22
forum: Server Platforms
---

### Post by Enforcer83 on 2011-09-22
[SIZE="3"]**The current situation:**[/SIZE]
I have a desktop computer running Windows 7 that is sharing several drives over the network with other Windows 7 machines as well as streaming to my XBOX 360.  My desktop has come due for its yearly cleaning (read reformatting).  Instead of reformatting to Windows and dual booting Ubuntu, I have decided to convert it completely to Ubuntu for a couple of reasons, namely, running a small web server and file server.  I get the web server configuration, for the most part and anything I don't I will ask about, but the file server section is a little sketchy.

[SIZE="3"]**The proposed configuration:**[/SIZE]
My system will have the following proposed partitions, included are the corresponding sizes of each partition (please comment on partion sizes if too small):

/boot (200MB)
/     (everything that is not defined as a seperate partition; 20GB)
/home (LVM; as big as I have storage for, currently close to 4TB)

[SIZE="3"]**The issue:**[/SIZE]
With the LVM, I noticed in several posts after Googling LVM, that Windows won't recognize it.  How do I configure my system so that I get the storage setup I want, 1 network drive of expandable size, and yet still be able to see the drive on a Windows machine?

I do not wish to convert the other machines over to Ubuntu as I have programs that do not run in Ubuntu or the Wine emulator.

---

### Post by Lars Noodén on 2011-09-22
> **Enforcer83 said:**
>  ...yet still be able to see the drive on a Windows machine?


That would be with [Samba](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html).

---

### Post by Enforcer83 on 2011-10-04
Thank you.  I appreciate your time.

Sortly after I posted I read the Samba section in the server guide and had an "ah ha" moment.

---

