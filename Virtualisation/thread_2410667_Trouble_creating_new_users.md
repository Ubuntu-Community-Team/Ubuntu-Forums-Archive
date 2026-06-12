---
title: "Trouble creating new users"
date: 2019-01-18
forum: Virtualisation
---

### Post by m-knichel on 2019-01-18
I have a VM (Virtualbox) running 18.04 with LTSP.  I want the users home directories to be on the bare metal not in the VM so I created /homes on bare metal and used vboxsf to mount it into the VM (created a shared folder in VB).  When I tried to create a new user I get an error about Protocol Error.  /homes on bare metal and in VM is owned by root with same perms as /home on both.  What am I missing? or doing wrong?

```
sudo adduser -home /homes/test3 test3
Adding user `test3' ...
Adding new group `test3' (1003) ...
Adding new user `test3' (1003) with group `test3' ...
Creating home directory `/homes/test3' ...
Stopped: Couldn't create home directory `/homes/test3': Protocol error.


Removing directory `/homes/test3' ...
Removing user `test3' ...
Removing group `test3' ...
groupdel: group 'test3' does not exist
adduser: `groupdel test3' returned error code 6. Exiting.

```

---

### Post by howefield on 2019-01-18
Thread moved to the "*Virtualisation*" forum.

---

### Post by SeijiSensei on 2019-01-19
I believe the shared folders feature in VB relies on CIFS to mount directories from the host machine. (Using CIFS enables this feature to work across platforms.) The mounted directories may not have the full panoply of *nix primitives required.  That could be what "protocol error" means in this context.

---

### Post by SeijiSensei on 2019-01-19
Here's a solution that might work using NFS.

[https://help.ubuntu.com/stable/serverguide/network-file-system.html](https://help.ubuntu.com/stable/serverguide/network-file-system.html)

Install nfs-kernel-server on the host, then edit /etc/exports to share directories on the host via NFS.  Use the bridged-adapter method to set up networking for the virtual machine.  Now both the VM and the host will have IP addresses within the same subnet.  

In the virtual machine, install nfs-common to enable NFS client services.  Now you should be able to issue a mount command in the VM like this:

```
sudo mount ip.addr.of.host:/home /home
```

to mount the directory /home on the host as /home in the virtual machine.  For safety sake, use

```
sudo mv /home /home.old
sudo mkdir /home
sudo mount ip.addr.of.host:/home /home

```

to preserve whatever is in /home already.

I have a machine set up as a server in my home office.  I store everything there and export /home with NFS.  Makes it easy to mount any shared directory on either Linux VM hosts or VM guests.  (I run both NFS and Samba so I can mount /home on Linux or Windows.)

---

### Post by two4two on 2019-01-28
Thanks SeijiSensei.  I will experiment with that.  I was coming to the idea that vbox VMs can't create symlinks on vbox shared folders.  There is no problem doing it inside the VM, but to try to do it on a file system outside the VM (a shared folder) couldn't work.  What's more, after all my experimenting I broke my VM and so had to restore a snapshot.  Not a problem, but I didn't have any other ideas until I saw your post.

---

