---
title: "ltsp: fat client with motion -&gt; dropbox upload"
date: 2012-11-13
forum: Server Platforms
---

### Post by roberto99 on 2012-11-13
hi all

I would like to install motion ([http://manpages.ubuntu.com/manpages/precise/man1/motion.1.html](http://manpages.ubuntu.com/manpages/precise/man1/motion.1.html))  on my ltsp fat clients, which actually works well. What I dont know is how to upload the created files via dropbox. Can someone point me in the right direction?

thanks
Roberto

---

### Post by dannyboy79 on 2012-11-13
not sure what you are asking here. Don't you just have a dropbox folder you put the files in and they will automatically appear in the dropbox folder on the ltsp fat client? That's what dropbox does, keeps folders in sync.

---

### Post by roberto99 on 2012-11-13
I tried to install dropbox from within the fat client, but the user has no sufficient rights and I think it would get lost at reboot anyway. I tried to install from within the chroot, but that did not work. I installed it in the main (auto login) account on the server but you apparently can not inclued subfolders from other users accounts. I tried mount a nfs folder from the chroot for the fat client users to put the files somewhere within the files of the main account on the server so that its dropbox installation can upload it, but with no success...

---

### Post by dannyboy79 on 2012-11-13
WOW, i guess I first need to understand exactly what you want to accomplish. I am not familiar with motion or ltsp fat clients but I familiar with dropbox, NFS, SMB, etc etc. Can't you just share the folder you put the motion files in thru NFS and then mount them on your fat clients machines using NFS client mounts? Maybe somewhere within /mnt/?

---

### Post by roberto99 on 2012-11-13
thats what I tried from within the chroot. but the client dit not keep the mount in fstab. fstab was empty on the client.

---

### Post by dannyboy79 on 2012-11-13
and you followed this guide for NHF_HOME?
[https://help.ubuntu.com/community/UbuntuLTSP/FatClients#NFS_HOME](https://help.ubuntu.com/community/UbuntuLTSP/FatClients#NFS_HOME)

---

### Post by roberto99 on 2012-11-13
thanks dannyboy79

in context to which of the ways I mentioned should I try it? I mean, what should I do or see after doing this? Cause I cant see any difference after doing it. And, should I do this procedere from within the fat client's account on th server?

thanks
Roberto

---

### Post by dannyboy79 on 2012-11-13
what ever folders/files are within the /home folder on your server should now be in the /home/ folder on your fat clients.

---

### Post by roberto99 on 2012-11-13
it seems to work.... hold on!

it works, you are the man! 

I have been trying for hours and hours to find a solution the past 3 days. How can I reward you in here?

Thanks so much
Roberto

---

