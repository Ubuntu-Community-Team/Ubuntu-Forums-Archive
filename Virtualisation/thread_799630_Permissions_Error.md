---
title: "Permissions Error"
date: 2008-05-19
forum: Virtualisation
---

### Post by Skeet on 2008-05-19
When I try to run my virtual os (windows xp pro), its started to come up with an error saying I don't have permissions to use the file. It only started doing it since i restarted.

I've tried chowning the folder and the file inside (the big one), and it still doesn't seem to want to open.

How can I get around this? :confused:

---

### Post by Skeet on 2008-05-19
Can anyone please help me? :(

---

### Post by bradmkjr on 2008-05-19
Could you post the output of ls -l for the "Virtual Machine" Directory, it maybe a chmod issue. I had some weirdness on my 7.10 Ubuntu Server with 1.0.4 VMware server. I frantically chown and chmod a ton of files all over the place and finally got it working, not sure the exact files which worked, but the directory list may offer some clues.

Thanks,
Bradford Knowlton
[http://x86Virtualization.com](http://x86Virtualization.com)

---

### Post by Skeet on 2008-05-19
```
total 1584520
-rw------- 1 root     root        1474560 2008-05-19 18:27 autoinst.flp
-rw-r--r-- 1 root     root         406260 2008-05-19 22:22 vmware-0.log
-rw-r--r-- 1 root     root         105947 2008-05-19 23:41 vmware.log
-rw------- 1 root     root           8684 2008-05-19 23:41 Windows XP Professional.nvram
-rw------- 1 root     root     1408761856 2008-05-19 23:41 Windows XP Professional-s001.vmdk
-rw------- 1 root     root       60358656 2008-05-19 23:41 Windows XP Professional-s002.vmdk
-rw------- 1 root     root      149618688 2008-05-19 23:41 Windows XP Professional-s003.vmdk
-rw------- 1 root     root         393216 2008-05-19 23:41 Windows XP Professional-s004.vmdk
-rw------- 1 root     root          65536 2008-05-19 23:41 Windows XP Professional-s005.vmdk
-rw------- 1 root     root            646 2008-05-19 23:40 Windows XP Professional.vmdk
-rw------- 1 root     root              0 2008-05-19 18:27 Windows XP Professional.vmsd
-rwxrwxrwx 1 sjcurran sjcurran       2167 2008-05-19 23:40 Windows XP Professional.vmx
-rw------- 1 root     root            278 2008-05-19 18:27 Windows XP Professional.vmxf
```

Hope thats right. Thanks for the quick reply.

---

### Post by Skeet on 2008-05-19
As you can see i've changed the permissions of the main file, I wasn't sure whether it was necessary to change the others too.

---

### Post by bradmkjr on 2008-05-19
Thank you for post the information.

If this is a production server, please be careful with the following commands, but if this is a test system enjoy the following advice:

If I'm reading it correctly, the disk image is owned by root, which means that only root would have access to the hard drive images.

You need to find out which user is running the vmware server application. I would assume you standard login user.

sudo chown -R sjcurran:sjcurran "/var/lib/vmware/Virtual Machines"

This would change owner of all files in the virtual machine directory to sjcurran, group sjcurran. This must be run as sudo, since the current owner is root.

Let me know if this makes a difference, you could also run chmod in a similar manner.

Good Luck,
Bradford Knowlton
[http://x86Virtualization.com/](http://x86Virtualization.com/)

---

### Post by Skeet on 2008-05-19
It worked, thanks very much for that. I thought it was a case of changing each file inside that folder independently, but that little command made it alot easier. Thank you so much :)

---

