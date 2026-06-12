---
title: "[SOLVED] Management of KVM"
date: 2008-04-18
forum: Virtualisation
---

### Post by Floffel on 2008-04-18
I set up a kvm virtual machine using virt-manager under an up to date hardy server.

Now I want to manage my virtual machines and make backups of them. Therefore I'm looking for a scriptable management solution.

In the [KVM Wiki there is a script like the one I like to have]("http://kvm.qumranet.com/kvmwiki/simple_shell_script_to_manage_your_virtual_machine_with_bridged_networking") - but it doesn't seem to be finnished nor do I get it to run.

Does anyone know a scriptable management solution like the graphical virt-manager to shutdown and start machines?

---

### Post by Floffel on 2008-04-19
After consulting the #kvm IRC Channel I was pointed to virsh. It is a management user interface for virtual machines and seems to do just what I wanted.

---

### Post by SuperBOB on 2008-04-20
You don't have to stop a VM to back it up.  You can use LVM2 snapshotting to back it up in real time.

---

