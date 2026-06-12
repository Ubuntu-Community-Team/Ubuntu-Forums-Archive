---
title: "Setting up permissions for shared folder on a ViralBox VM."
date: 2015-12-13
forum: Virtualisation
---

### Post by hackarre on 2015-12-13
I'm currently running Ubuntu Server 14.04 and wanted to create a virtual machine (another Ubuntu Server) to run transmission on it. 

I installed virtualbox and edited /etc/fstab to auto mount a share that links to a folder in one of the external hard drives attached to the computer. I have access to the share and can create and edit files. 

I want this share to contain the folders that transmission is gonna download to but in order for transmission to work, it's user "debian-transmission" needs read and write permissions to the folders. Without those transmission is gonna through the error: "Error: Permissions denied.." as soon as it starts to download a file.
So I need the debian-user (on the guest machine) to be able to read an write on a shared folder that is mounted on the host. 

I've tried to chown debian-transmission:"user" "folder" on the root guest and giving it chmod 775 permissions without success. Whenever I do that, the permissions show as run by root in the host machine.

I also tried creating a debian-transmission user on my host (main) machine with the same uid as the guest user, and give it the same permissions. All without luck. I also added the debian-transmission user to both main accounts groups with usermod -aG.

All of these made me try a different approach an tried the same thing on a samba share and I'm encountering the same problems.


I am starting to get frustrated :mad:, probably missing something obvious. I guess I could make transmission run under the root account as it seems to be able to access the folder, but I don't really wanna do that.


Thank you!

---

### Post by howefield on 2015-12-13
Thread moved to the "*Virtualisation*" forum.

---

### Post by SeijiSensei on 2015-12-13
Is there a reason not to grant that folder 777 permissions?

---

### Post by hackarre on 2015-12-13
> **SeijiSensei said:**
> Is there a reason not to grant that folder 777 permissions?


Also tried it without success.

---

### Post by damien27 on 2015-12-14
You cant, you need the "Guest Additions CD" and there is no ubuntu version, just install a ssh server on one off the computers and do it that way. Its even faster.

---

### Post by QIII on 2015-12-14
Guest Additions most certainly can be installed on an Ubuntu guest.  What gave you the impression that it could not?

---

### Post by hackarre on 2015-12-15
> **damien27 said:**
> You cant, you need the "Guest Additions CD" and there is no ubuntu version, just install a ssh server on one off the computers and do it that way. Its even faster.

"Guest Additions CD" needs to be installed in order to share folder between host and guest, It's installed.

---

