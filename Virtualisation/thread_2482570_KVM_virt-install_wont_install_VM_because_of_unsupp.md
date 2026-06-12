---
title: "KVM virt-install wont install VM because of unsupported configuration"
date: 2023-01-04
forum: Virtualisation
---

### Post by kingslavcho on 2023-01-04
Hi friends,
Ii have a problem with my ubuntu server on which i installed kvm and  virt-install so i can run a VM. I tried to install an Ubuntu VM with the  following command showed below in the code but i get an error of  unsupported configuration.. I am also trying to install it on the home  directory (partition is made there - partitions showed below in the picture) because i have a special place assigned for my VMs as showed  below.. Can you tell me how can i resolve this issue?
Just to be clear, the installation is not successful.

 Thank you

```


kingdev@devpc:/home/kvmimages/ubuntu1$ sudo virt-install --name ubuntu-guest --os-variant ubuntu22.0 4 --vcpus 2 --ram 2048 --location http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/ --n etwork bridge-virbro, model=virtio --graphics vnc --disk path=/home/kvmimages/ubuntu1/ 
WARNING Graphics requested but DISPLAY is not set. Not running virt-viewer. 
WARNING No console to launch for the guest, defaulting to --wait -1 

Starting install... 
Retrieving 'linux' 
Retrieving 'initrd.gz' 
11 MB 00:00:10 49 MB 00:00:50 
ERROR unsupported configuration: storage type 'dir' requires use of storage format 'fat' 
Domain installation does not appear to have been successful. 
If it was, you can restart your domain by running: 
virsh --connect qemu:///system start ubuntu-guest 
otherwise, please restart your installation.
```

Paritions in ubuntu server:[URL="https://freeimage.host/i/HASCSTl"]

[IMG][/URL][[IMG]https://iili.io/HASCSTl.png[/IMG]]("https://freeimage.host/")[/IMG][URL="https://freeimage.host/i/HASCSTl"]
[/URL]

---

### Post by Doug S on 2023-01-04
I assume these are typos, but you have the same on your [askubuntu]("https://askubuntu.com/questions/1448611/kvm-virt-install-wont-install-vm-because-of-unsupported-configuration") version of the same question:

```
sudo virt-install --name ubuntu-guest --os-variant [COLOR="#FF0000"]ubuntu22.0 4[/COLOR] --vcpus 2 --ram 2048 --location http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/ [COLOR="#FF0000"]--n etwork[/COLOR] bridge-virbro, model=virtio --graphics vnc --disk path=/home/kvmimages/ubuntu1/ 
```

I assume you meant:

```
sudo virt-install --name ubuntu-guest --os-variant [COLOR="#FF0000"]ubuntu22.04[/COLOR] --vcpus 2 --ram 2048 --location http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/ [COLOR="#FF0000"]--network[/COLOR] bridge-virbro, model=virtio --graphics vnc --disk path=/home/kvmimages/ubuntu1/ 
```

I am not an expert, but use this for graphics:

```
--video=vmvga --graphics vnc,listen=0.0.0.0 --noautoconsole
```

I don't know about your other issues.

---

### Post by MAFoElffen on 2023-01-04
Here is what I adapted from your startup to create a successful run on mine:
```

sudo virt-install --name ubuntu-guest \
    --os-variant ubuntu20.04 \
    --vcpus 2 --ram 2048 \
    --location http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/ \
    --network default \
    --video=vmvga \
    --graphics vnc,listen=0.0.0.0 \
    --noautoconsole  \
    --disk path=/data/KVM-VM/[COLOR=#ff0000]test.qcow2[/COLOR]

```
Note that the error you reported, said that the resulting path to storage was a directory, which it tried to write to, and couldn't, because a directory is not a disk storage file... Listen to the error. If you create a VM disk file and name it in --disk, it should kick off fine... Mine did. I created test.cow2 and pointed it in the --disk def.
```

mafoelffen@Mikes-B460M:~$ sudo virt-install --name ubuntu-guest --os-variant ubuntu20.04 --vcpus 2 --ram 2048 --location http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/ --network default --video=vmvga --graphics vnc,listen=0.0.0.0 --noautoconsole  --disk path=/data/KVM-VM/test.qcow2

Starting install...
Retrieving 'linux'                                                                                                                                    | 9.1 MB  00:00:05 ... 
Retrieving 'initrd.gz'                                                                                                                                |  47 MB  00:00:08 ... 
Creating domain...                                                                                                                                    |    0 B  00:00:00     

Domain is still running. Installation may be in progress.
You can reconnect to the console to complete the installation process.
mafoelffen@Mikes-B460M:~$ virsh list
 Id   Name                 State
------------------------------------
 1    lunar-lander-01-01   running
 2    ubuntu-guest         running

```

---

