---
title: "Can not get a terminal during install on Server"
date: 2013-02-15
forum: Virtualisation
---

### Post by Doug S on 2013-02-15
I have an Ubuntu Server 12.04.2. I am trying to install a virtual ubuntu server 12.04.2 on it. At this point the purpose is to learn. I am using the [Ubuntu server guide ]("https://help.ubuntu.com/12.04/serverguide/libvirt.html")as the main reference. I am stuck at the point of trying to somehow connect to a terminal to continue with installation after the virt-install command. I have been reading the various "man" pages attempting to determine what to do. 
 
kvm is using one cpu at 100%, and has been for about 7 hours now. I assume waiting for me to continue with the installation. Some, perhaps, relevant information:```
doug@s15:~/iso$ kvm-ok
INFO: /dev/kvm exists
KVM acceleration can be used
doug@s15:~/iso$ virsh vncdisplay 2
:0
doug@s15:~/iso$ sudo netstat -plnt | grep kvm
[sudo] password for doug:
tcp        0      0 127.0.0.1:5900          0.0.0.0:*               LISTEN      7606/kvm
```O.K. so I know that my host is listening on port 5900 for a vnc connection, but I also think that is not what I want. However, I have not been able to figure out what other "--graphics" option I should use, keeping in mind that I do not have any GUI on my host. Regardless, I did try virt-viewer, but it just says "Cannot open display", not surprising since I think it needs a GUI also.
 
My best guess, at this point, it that I should be launching "virt-install" with "--graphics none" and somehow later on connecting to some serial terminal. Or better still, don't bother with the --noautoconsole option that is in the server guide. So I tried that, and supposedly end up in a console, but it doesn't work. (Although kvm is no longer using 100% of 1 cpu and kvm is no longer listening on port 5900).
 
Can someone point me in the right direction?
 
For reference, the last attempt command:```
sudo virt-install -n virt32_01 -r 128 --disk path=/var/lib/libvirt/images/virt32_01.img,bus=virtio,size=12 -c ubuntu-12.04.2-server-i386.iso --accelerate --network network=default,model=virtio -v
```

---

### Post by Doug S on 2013-02-16
O.K., I was (finallly) able to proceed by: Installing a VNC viewer program on my windows vista LapTop; Changing the virt-install command to (scroll right to see the highlighted change):```
sudo virt-install -n virt32_01 -r 128 --disk path=/var/lib/libvirt/images/virt32_01.img,bus=virtio,size=12 -c ubuntu-12.04.2-server-i386.iso --accelerate --network network=default,model=virtio --connect=qemu:///system [COLOR=red]--graphics vnc,listen=0.0.0.0[/COLOR] --noautoconsole -v
```This doesn't change my inital post question: Is there a way on a non-GUI server without involving other computers?

---

### Post by Doug S on 2013-02-24
Bump.

---

