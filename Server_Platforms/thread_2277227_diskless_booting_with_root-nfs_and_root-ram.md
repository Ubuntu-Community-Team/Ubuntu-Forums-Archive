---
title: "diskless booting with root-nfs and root-ram"
date: 2015-05-07
forum: Server Platforms
---

### Post by priyans on 2015-05-07
Hi,

I've been setting up a diskless booting environment for my KVM test cluster. I know that it's possible to keep the root fs either on NFS volume or on local RAM.

I tried with the first option following this doc : [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto) . For that, I exported the /nfsroot over network and booted two hosts. So now my doubt is, when I cd in to /nfsroot directory on server, I don't see any separate files for these two clients but common vmlinuz and initrd. So where would be the local data from these two clients written to ? 

If it's written to RAM only, then what's the difference from using root fs on RAM method (by specifying [COLOR=#000000][FONT=Times New Roman]root=/dev/ram[/FONT][/COLOR] as boot parameter) ? I thought, if we are using nfs root option, then the clients would be writing data (at least delta files?) to the /nfsroot volume.

May be my logic is not correct, please help !

---

