---
title: "sharing files in virtualbox"
date: 2007-11-04
forum: Virtualisation
---

### Post by Mets on 2007-11-04
Hi, I'm trying to share files between a Windows Vista host and Ubuntu 7.04 guest using VirtualBox.  I have searched the forums and I have found how to do the reverse (share files with a windows guest and an Ubuntu host) but those obviously don't work in my case.  Can anybody help me out?  I'd like to be able to do both read and write if it is possible.

Thanks!

---

### Post by Exonimus on 2007-11-04
virtualbox has a nice 'shared folders' option. You might have to install the guest additions, I can't remember. 

First, (install guest additions if needed) go to the 'devices' menu(once your ubuntu guest system has started). click 'shared folders' go to 'machine folders' and click the 'add new folder' icon. select a folder(on your host) to share. Now, in your ubuntu guest, go to the console and type: ```
 mount -t vboxsf share mount_point
``` and rename the 'share' to whatever folder you have shared

edit: yup, you need guest additions. (go to the 'devices' tab, click install guest additions, and it''ll probably launch. If not, the guest additions will still be mounted as a cd drive, and you'll need to launch it yourself)

hope this works. Good luck!

---

### Post by Mets on 2007-11-07
Thanks for the reply.  It worked great.  I had to manually create a folder /media/cdrive but it worked.  I used the command ```
sudo mount -t vboxsf cdrive /media/cdrive
``` and I got my entire C:\ under Ubuntu.  The only problem is that it is read only.  Is there a way to make it writable?

Edit
After reading this ([http://forums.virtualbox.org/viewtopic.php?p=9455#9455](http://forums.virtualbox.org/viewtopic.php?p=9455#9455)) I figured out that "mount_point" actually needed to be a folder in Ubuntu, sorry about that

---

### Post by Mets on 2007-11-11
bump

---

### Post by KillerKiwi on 2007-11-12
You can use a samba share on the host machine

---

### Post by iamsickofschool on 2010-09-03
Really? I didnt know Vista used samba... (Sarcasm intended)

---

