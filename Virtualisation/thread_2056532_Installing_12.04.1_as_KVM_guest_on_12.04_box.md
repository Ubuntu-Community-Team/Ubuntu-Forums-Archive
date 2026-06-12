---
title: "Installing 12.04.1 as KVM guest on 12.04 box"
date: 2012-09-11
forum: Virtualisation
---

### Post by RHAnthony on 2012-09-11
I am trying to install a KVM guest using the following command:

```
virt-install --name="SFTP" --ram="1024" --vcpus="1" --nographics --accelerate --os-type="linux" --network="bridge:br0" --disk="path=/mnt/overland/vmstorage/SFTP.dsk,size=50" --cdrom="/mnt/overland/vmstorage/Install-Media/ubuntu-12.04.1-server-amd64.iso"
```


My problem is that when I run this command, I get the following on the screen:

```
root@DR-SRV2:~# ./virt-install.command.sh

Starting install...
Creating domain...                                                                                                                                                            |    0 B     00:01
Connected to domain SFTP
Escape character is ^]


```

... and then it just hangs forever.  ^] gets me out, but nothing else that I can find, gets a response.


I have a few KVM guests (CentOS) up and running, so I know it works and I didn't have this issue with those.  However those were installed with the *--location* option and an install root URL, and the *--extra-args="console=ttyS0"* option as well.  Do I need something like that for the .iso install to give me a working prompt as well?

---

