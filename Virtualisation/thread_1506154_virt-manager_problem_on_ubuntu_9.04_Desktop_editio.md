---
title: "virt-manager problem on ubuntu 9.04 Desktop edition"
date: 2010-06-10
forum: Virtualisation
---

### Post by tapas_mishra on 2010-06-10
Hi,
 I want to create Virtual Machines on my laptop.There is some error coming.I am describing step by step what I did

Ubuntu 9.04 on my Dell Laptop (Inspiron 1440)

**Step 1**
 
 Installed
```

apt-get install ubuntu-virt-server python-vm-builder
 libvirt-bin bridge-utils virt-manager 

```


**Step 2**
```

adduser $USER libvirtd

```

**Step 3**

```

virt-manager -c qemu

```

**Step 4**
I did got a GUI of virt-manager but 
with an error message 

```

Unable to open a connection to the libvirt management daemon.

Libvirt URI is: qemu

Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started

Unable to open connection to hypervisor URI 'qemu':
<class 'libvirt.libvirtError'> could not connect to qemu
None

```

**Step 5**

I checked 
```

dpkg -s libvirt-bin
Package: libvirt-bin
Status: install ok installed


```

Also checked if libvirtd is running
```

root@tapas-laptop:~# ps -el | grep libvirtd
5 S     0  2809     1  0  80   0 - 13269 poll   ?        00:00:02 libvirtd


```


So I ignored the error message in Step and clicked on close option.
Saw a GUI in which following was mentioned

```


Name             | ID | Status   |CPU usage|  CPU's | Memory usage
localhost(System) qemu Active(RO) 0.00%       2      0.00MB   and a small bar graph

```


**Step 6**


/etc/network/interfaces

```

auto br0
iface br0 inet static
        address 192.168.1.9
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.100.255
        gateway 192.168.1.100
        bridge_ports eth0
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.11
        dns-search local.domain.com
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off


```

Restarted network.

**Step 7**

Clicked on 

New button at the bottom of GUI which was working



**Step 8**

After this I tried to create a new Virtual Machine

upon choosing next the option of virtualization methods 

were greyed out (i.e. I could not select) both Paravirtualized and Fully Virtualization

there was an automatic selection on Paravirtualized (but as I mentioned it was greyed i.e. I could not select) )

CPU archictecture field here was greyed and hypervisor also 

**Step 9**

I clicked on Forward 

**Step 10**

OS Type (Selected Linux)

OS Variant (Selected RHEL 5)

and here the option

Local Install Media (greyed out)
Network Install Tree (HTTP,FTP or NFS) was by default selected
Network Boot     (greyed out)


**Step 11**

I created a local Apache on my laptop to host CentOS 5.5 image through apache.
This image was loop mounted in a folder so you can browse in that directory on Command prompt or 
[http://localhost/centos/](http://localhost/centos/)
was showing all the contents on DVD

**Step 12**

Clicked on Forward

Installation media URL [http://localhost/centos/](http://localhost/centos/)
Kickstart URL     (Left blank)
Kernel Parameters (Left blank)

**Step 13**

File Disk Image 

Location /var/lib/libvirt/images/centos.img

Size 6000 Mb

Ticked allocate entire virutal disk now. (In fact it was already ticked)

**Step 14**

Clicked Forward
and following error came

```

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 302, in forward
    if(self.validate(notebook.get_current_page()) != True):
  File "/usr/share/virt-manager/virtManager/create.py", line 1005, in validate
    vmmutil.build_default_pool(self._guest.conn)
  File "/usr/share/virt-manager/virtManager/util.py", line 54, in build_default_pool
    (DEFAULT_POOL_PATH, str(e)))
RuntimeError: Couldn't create default storage pool '/var/lib/libvirt/images': Could not define storage pool: operation virStoragePoolDefineXML forbidden for read only access

```

after this I could not proceed.

Can some one suggest some thing if any package or dependency is missing.

---

