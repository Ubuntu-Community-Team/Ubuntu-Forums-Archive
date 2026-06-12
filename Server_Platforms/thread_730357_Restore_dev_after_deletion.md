---
title: "Restore /dev after deletion"
date: 2008-03-20
forum: Server Platforms
---

### Post by CyFreeze on 2008-03-20
I hope anyone can help me here.
I accidently erased a chrooted enviroment which had still some directories mounted. To be exactly /dev and /proc
Sure my system doesnt run without these two. As /proc is virtual i guess it will be recreated after restart. But the /dev is causing the problems. I cant recreate the files with MAKEDEV as long as /proc/devices is not crowded. Is it somehow possible to reinstall the devices without /proc or recreate /proc without restart? The server will hang on restart where i cant reach the box. Im currently on a rescue console and have so full access to server.

---

### Post by anindya_m on 2008-03-20
Hi. How could you access /dev and /proc from a chrooted environment? It should have trapped the shell to a particular directory.

---

### Post by CyFreeze on 2008-03-21
Both were mounted to their representatives inside the chroot. So as i erased the chroot from the file system it went through the main directories as well.

---

### Post by anindya_m on 2008-03-21
I understand. One way would be to boot from a live CD and try copying  /dev from the live CD to the root partition on the hard drive (at least some devices should be set up). See if you can boot from the hard drive after this. If you happen to have another identically configured machine you can try restoring the directories from there. I had a similar problem with /etc on  a server, but fortunately had the partition backed up.

---

### Post by koenn on 2008-03-21
I'm not sure you can just copy /dev : although the entries in /dev look and behave like files, they're not regular files. If you pass them through cp, the result might be regular files that won't work as pointers to hardware, which is what they actually should be. 

You say you used makedev. 
Did you try mknod ? makedev is probably a wrapper around mknod, so maybe you'll get the same (lack of) result, but it's worth a try.

eg to create /dev/hda you'd go
```

mknod /dev/hda b 3 0

```
I've only had to use such thing once, so i don' know all the details

this looks like a good intro :
[http://www.faqs.org/docs/linux_admin/x797.html](http://www.faqs.org/docs/linux_admin/x797.html)
[http://wiki.linuxquestions.org/wiki/Mknod](http://wiki.linuxquestions.org/wiki/Mknod)

I think you'll need at least /dev/console, /dev/loop  and the harddisk devices where your / filesystem lives to get a bootable and half-usable system.

Here's some more :
[http://www.faqs.org/docs/linux_admin/x822.html](http://www.faqs.org/docs/linux_admin/x822.html)


you should be able to get more major and minor numbers from 
[http://www.mjmwired.net/kernel/Documentation/devices.txt](http://www.mjmwired.net/kernel/Documentation/devices.txt)
or from your makedev conf file

Good luck, I think this is not going to be easy

---

### Post by CyFreeze on 2008-03-21
All these processes are depending on a running system so that /proc is mounted. The /proc/devices is needed.
I simply reinstalled the system now. Was not that bad as I had my system well structured. But I think this topic should be continued to help others in this dilemma. 

So can we create the /proc when the system is run on a livecd/rescue console?

---

### Post by koenn on 2008-03-21
I don't think you can just "create" a /proc filesystem. It's a virtual filesystem, the directories and files therein are representations of running processes - with process numbers for directories and 'files' containing info on the process in question.
They're represented as files so you can get info on processes with normal text and filesystem tools such as cat and find and ls ('everything is a file").

Since these proceses exist in the running kernel, it's enough to (re-)mount /proc ? I don't know and I'm not going to try :)

[http://www.faqs.org/docs/linux_network/x-087-2-iface.procfs.html](http://www.faqs.org/docs/linux_network/x-087-2-iface.procfs.html)

---

### Post by anindya_m on 2008-03-23
Hi. Remounting /proc is simple and is accomplished by a command like:
```
sudo mount -t proc proc dir/
```
Note that the device "proc" is an arbitrary word (however, the argument to -t isn't): fstab uses "proc" which makes sense since this will apprear as the device name in any error messages. You can safely try this on a running system; just choose some empty directory as a mount point.

> I'm not sure you can just copy /dev : although the entries in /dev look and behave like files, they're not regular files. If you pass them through cp, the result might be regular files that won't work as pointers to hardware, which is what they actually should be.

I agree: simply a cp over /dev wont work (try, for example, with /dev/zero, but kill it before it fills up your disk! ;)). What I had in mind was look up the dev directory from the live cd and create the corresponding entries with mknod, as suggested by koenn in the last post. However, this needs a script, and may be unnecessary as MAKEDEV should work after /proc is available (it is a simple script which loops over entries in /proc and uses mknod to make the actual device files).

So, to summarize, the steps could be:

1. Boot from a live cd.
2. chroot to the hard disk's / filesystem (making sure that all the commands below are available by mounting additional partitions, if necessary).
3. Mount the /proc filesystem as described above.
4. Finally run MAKEDEV.

---

