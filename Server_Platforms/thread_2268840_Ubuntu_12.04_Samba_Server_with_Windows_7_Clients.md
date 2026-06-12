---
title: "Ubuntu 12.04 Samba Server with Windows 7 Clients"
date: 2015-03-11
forum: Server Platforms
---

### Post by cpatchett on 2015-03-11
Hello All,

I feel like I have searched for results to this problem until I am blue in the face, and I have yet to find any answers.  I am currently running Ubuntu Server 12.04, fully updated using apt.  It has the latest version of Samba server on it that I know to be available via apt.  I have rebuilt this server a few times trying different tests.  I have not changed many of the options at this point, it is pretty much a default install of Ubuntu and of Samba.  However, I am getting some really weird results.  I have a Windows 7 Pro desktop.  When trying to write files to a samba share on that server, I am getting very poor write speeds as well as the copy process just hangs ever so often, for a few seconds.  My Windows 7 machine has Teracopy installed, which is a third party file copy utility.  However, I get the same results using that as I do the standard windows explorer copy.  I am running a Gigabit, wired network.  However, the catch to the whole mess (I have tried as best I can to eliminate this) the Ubuntu server runs on a KVM Virtualized environment which uses NFS to connect to the NAS.  I have ran throughput utilities and I can write using scp to the drives with no problem.  I have narrowed this down as best I can to just be the Samba protocol and an issue between Windows 7 and Ubuntu.  Any suggestions would be a great help.  Thanks in advance.

---

### Post by volkswagner on 2015-03-12
You may need to run wireshark if there is no information in the logs.

---

