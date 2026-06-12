---
title: "Can login with public key but forgot user password"
date: 2010-08-26
forum: Security
---

### Post by juergenD on 2010-08-26
Hi,
I have a problem with my ubuntu account. I am running 4 virtual machines, based on jeos-8.04 and I am using a public key authentication to login to my account (via ssh). This is not the problem, I have the key and the passphrase. But when I am logged in, I can't sudo, because I forgot the password for the accout.
Is there any way to fix this? There are no other users defined. 
Thanks in advance for any help.
Juergen

---

### Post by spjackson on 2010-08-26
If you reboot and select recovery mode from the grub menu, you can get a root shell, and then you can change your password with
```

passwd username

```Perhaps there's a method without using recovery mode, but I am not aware of one.

---

### Post by juergenD on 2010-08-26
But how can I access the boot sequence? These are virtual machines.

---

### Post by souki on 2010-08-26
What kind of virtualization ?

if you can access your guest/disk from the host, you can copy your ssh-key to /root/.ssh/authorized_keys, or change /etc/shadow, or change /etc/sudoers
if the guest is on a virtual disk, you have to find howto mount it from the host

---

### Post by juergenD on 2010-08-26
I am using kvm. I have 4 virtual machines running, based on jeos-8.04. The host is ubuntu server 8.04. I can access every virtual machine and the host via ssh/public key. 
But i cannot [sudo] (host and virtual) because I forgot the password, which is the same for all virtual machines and the host.
The virtual machines, are image files in my home directory.

---

### Post by souki on 2010-08-26
you have to mount the kvm disk image,
maybe like this : [http://equivocation.org/node/107](http://equivocation.org/node/107)

---

### Post by juergenD on 2010-08-27
Many thanks for your help. With your instructions I was able to mount the image file of my virtual machines and inject a new password into the /etc/shadow file. I can start the virtual machines again next week and let you know if it works.  Thanks a lot and best regards Juergen

---

