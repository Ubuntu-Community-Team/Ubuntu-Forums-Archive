---
title: "KVM on Server"
date: 2019-02-02
forum: Virtualisation
---

### Post by sniper8752 on 2019-02-02
I would like to install virtual machines on my server, and am looking at this tutorial: [https://linuxconfig.org/how-to-create-and-manage-kvm-virtual-machines-from-cli](https://linuxconfig.org/how-to-create-and-manage-kvm-virtual-machines-from-cli).  Is [COLOR=#000000][FONT=&quot]virt-viewer required?  If not, how would I set the IP?  I'd like to avoid a GUI, if possible. [/FONT][/COLOR]

---

### Post by TheFu on 2019-02-03
No. You don't need to use virt-viewer. You can connect to the console using **virsh**.

Are you aware that **virt-manager** works from remote systems over an ssh tunnel to the KVM host?  No GUI code needed on the KVM host, but your desktop/client machine can use the virt-manager tool to access the console for each VM.

Or you can ssh into the VM host and use virsh, if you like. I use it for tweaking some settings to which virt-manager doesn't provide access.

If I installed/created more than 1 VM a month, I'd want to automate it too.

---

