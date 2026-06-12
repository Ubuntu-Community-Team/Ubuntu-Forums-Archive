---
title: "Help with dosemu please"
date: 2008-05-03
forum: Virtualisation
---

### Post by Michael Dooley on 2008-05-03
I had dosemu running in gutsy and it was performing fairly well with my CAD application. After upgrading to hardy via the Alternative CD and reinstalling dosemu from the ubuntu repository, I can't seem to get it running. I click on the DOS Emulator icon under System Tools but nothing happens. What can I do to get this thing up and running?

Thanks for reading this. I look forward to your response.

---

### Post by Michael Dooley on 2008-05-05
If I open a terminal window and type in either "dosemu" or "xdosemu" and press enter i get "LOWRAM mmap: Invalid arguement" and on the next line "Segmentation fault" then back to prompt.

What does this message point to? What can I do to get dosemu up and running?

Thanks for your time.

Edit: I went to the following URL:

[https://bugs.launchpad.net/ubuntu/+source/dosemu/+bug/216398](https://bugs.launchpad.net/ubuntu/+source/dosemu/+bug/216398)

and found a workaround first posted by Edward Mendelson and elaborated by others.

"sudo sysctl -w vm.mmap_min_addr=0" 

This enabled me to start dosemu. However, the next time I rebooted, dosemu did not start until I re-edited the etc/sysctl.conf file. 

This needs a little more in the way of a lasting solution. By the way, if I used the "/etc/init.d/propcps restart" command subsequent to setting the value to 0, the vm.mmap_min_addr value would be reset back to 65536 and dosemu would again be prevented from running.

---

### Post by randalls on 2008-05-05
> **Michael Dooley said:**
> If I open a terminal window and type in either "dosemu" or "xdosemu" and press enter i get "LOWRAM mmap: Invalid arguement" and on the next line "Segmentation fault" then back to prompt

There is a bug report on this ([Bug #217710 in dosemu]("https://bugs.launchpad.net/ubuntu/+source/dosemu/+bug/217710")). According to messages there this is caused by some new security features. You can reset them by setting vm.mmap_min_addr in /etc/sysctl.conf to 0. (You'll need to use sudo to edit this file.) Then reload the sysctl setting by typing 

sudo /etc/init.d/procps restart

in a terminal. DOSEMU will then run.

According to a message "Changing mmap_min_addr makes your system slightly less secure -- you will not be protected from potential kernel exploits that use NULL derefs."

---

### Post by Kenneth D. Gladden on 2008-05-08
Thanks for help

I reset vm.mmap_min_addr in /etc/sysctl.conf to 0.

This enabled starting all dos programs 

However

None of the dos programs can write to redricted
windows drives. 

any help would be appreciated

kdgladden

---

### Post by MaxDamage on 2008-06-13
By default, NTFS partitions are mounted belonging to root. To mount them as belonging to a specific user, use the "uid" and "gid" mount options.

[Mount documentation from the superb Gentoo Docs]("http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)#uid.2Cgid:_mount_as_.28user.2Cgroup.29")

P.S. The solution you used about that sysconfig option, also fixes some windows apps running under wine. :)

---

