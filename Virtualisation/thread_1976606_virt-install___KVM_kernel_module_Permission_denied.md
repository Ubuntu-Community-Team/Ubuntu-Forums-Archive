---
title: "virt-install  : KVM kernel module: Permission denied"
date: 2012-05-09
forum: Virtualisation
---

### Post by lostinspace2011 on 2012-05-09
I am trying to install Windows as a guest on 12.4 using the following command:

```
virt-install -d --connect qemu:///system -n vista -r 512 -f windows.qcow2 -s 12 -c /home/alex/windows-vista.iso --vnc --noautoconsole --os-type windows --os-variant vista

```which fails with the following error:

```
libvirtError: internal error Process exited while reading console log output: char device redirected to /dev/pts/4
Could not access KVM kernel module: Permission denied
failed to initialize KVM: Permission denied
No accelerator found!

[Wed, 09 May 2012 12:30:44 virt-install 12040] DEBUG (cli:449) Domain installation does not appear to have been successful.
If it was, you can restart your domain by running:
  virsh --connect qemu:///system start vista
otherwise, please restart your installation.
Domain installation does not appear to have been successful.
If it was, you can restart your domain by running:
  virsh --connect qemu:///system start vista
otherwise, please restart your installation.
```Looking online suggests a problem with permissions on /dev/kvm. On a clean installation of the host using ubuntu 12.4 permissions are set to root:root. I added my own user and root to the kvm and libvirtd groups and changed permissions on /dev/kvm to root:kvm, however this did not resolve the problem. 

Any suggestions on what I can do to get this resolved.

Thanks in advance

---

### Post by lostinspace2011 on 2012-05-09
As it turns out I had the kvm and kvm-intel modules loaded before changing the permissions. Unloading both modules using rmmod, and then running the virt-install command again seemed to have solved my problem. 

What is strange though is that virt-install did not reload the modules ? I am new to using kvm, so it may be normal. 

Should virt-install load the kvm module ?

---

### Post by augustl on 2012-05-30
I can confirm that reloading kvm-intel solved the problem for me.

When I loaded the module, I was not in the kvm or libvirtd group. I added my user to those groups and relogged, but kvm-intel seems to only read these group things when it loads, or something like that.

---

### Post by mirela666 on 2013-03-07
Maybe you have installed both kvm and qemu-kvm packages, I had same problem untill I uninstalled kvm and left qemu only.

---

### Post by ibanez89 on 2013-04-15
> **mirela666 said:**
> Maybe you have installed both kvm and qemu-kvm packages, I had same problem untill I uninstalled kvm and left qemu only.

Same problem and same solution, many tx for your help :)

---

### Post by sirius2x on 2013-05-31
lot of thank's
helped for me
[LEFT][COLOR=#223355][FONT=helvetica][] - [COLOR=#76797C]**[/COLOR][COLOR=#76797C]**[/COLOR][/FONT][/COLOR][/LEFT]

---

