---
title: "KVM Remote Manager or web Based Manager"
date: 2020-05-27
forum: Virtualisation
---

### Post by rupok on 2020-05-27
Hello There,

Is there any active "KVM Manager" project for Ubuntu 18.04 or higher version?

I'm planing to install KVM in Ubuntu 18.04 headless server. So I want to manage the KVM from remote (my machine) machine, or from web console of the KVM machine.
Is there any solution?

---

### Post by slickymaster on 2020-05-27
Thread moved to **Virtualisation** for a better fit

---

### Post by TheFu on 2020-05-27
I use **virt-manager**. It runs on any workstation with ssh access to the KVM host.  Both need libvirt and group permissions. No need for any root/sudo access for anything related to creating, running, shutting down or removing a VM.

Youtube has videos for virt-manager.  Sometimes it is call VMM.  The program name is virt-manager. If the management workstation is separate from the KVM host, setup ssh. That ssh connection is all that is needed.

Let me look for my presentation about this stuff.   ...

On the "server" (hadar)
[LIST=1]
[*]```
sudo apt install openssh-server  kvm qemu-system   bridge-utils fail2ban
```
[*]Ensure your userid is a member of libvirtd
[*]Create a bridge manually in netplan. The host needs to have a static IP.
[/LIST]


On the "workstation" (regulus)
[LIST=1]
[*]```
sudo apt install ssh virt-manager  fail2ban
```
[*]Ensure your userid is a member of libvirtd
[*]Setup ssh authentication between the client and the server - ssh-keygen and ssh-copy-id
[*]Verify the ssh connection to the server (key-based makes life easier)
[/LIST]

Run virt-manager, connect to the KVM host.  My connection string looks like this: 
```
qemu+ssh://thefu@hadar/system
```

The GUI console access isn't the most efficient, so I use **ssh** 95% of the time and **x2go** the other 5%.  But if networking is broken for the guestOS, the console is the only way to connect.  That can be through virt-manager or virsh.

virt-manger has been around and working well since at least 2010.  I'm running it on a 20.04 workstation (actually a desktop VM) connecting to a 16.04 KVM-host.  The "workstation" runs on that 16.04 KVM-host, btw, but connections to 2 other KVM hosts work fine too from the same virt-manager.

---

### Post by rupok on 2020-05-31
Thanks a lot for this information. It was really helpful.

---

