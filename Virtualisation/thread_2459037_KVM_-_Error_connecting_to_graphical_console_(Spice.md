---
title: "KVM - Error connecting to graphical console (SpiceClientGtk)"
date: 2021-03-09
forum: Virtualisation
---

### Post by Alan5127 on 2021-03-09
Hi All,

I have a new install of Ubuntu Server 20.04.2 LTS setup and running KVM.

Everything *seems* to be fine with the server.

I have then installed 'virt-manager' on my Ubuntu 18.04 LTS Desktop machine, and successfully connected to the KVM Server.

I have tried to create a new VM (Debian Stretch) from the Virtual Machine Manager (virt-manager), but each time I am getting the same issue which is that I cannot see the VM Console.


The error I am getting is:
> Error connecting to graphical console:
Error opening Spice console, SpiceClientGtk missing


I have checked that 'SpiceClientGtk' is installed on the Ubuntu Server by entering:

```
sudo apt install gir1.2-spiceclientgtk-3.0 --dry-run
```

which returns:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gir1.2-spiceclientgtk-3.0 is already the newest version (0.37-2fakesync1).
gir1.2-spiceclientgtk-3.0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

so I believe that is correctly installed.  For what it was worth, I also installed it on my Desktop, but that made no difference either.



I also tried connecting using 'virt-viewer'.

I entered this on my desktop:

```
virt-viewer --connect qemu+ssh://username@172.25.25.3/system VMName
```

I don't have keys setup (yet) so I am expecting to get asked for the password, which I am (a number of times, but apparently that is expected).  The 'virt-viewer' application opens, and sits with the message:

> Connected to graphic server


The VM is definitely running (at least according to the host):

```
$ virsh list

 Id   Name         State
----------------------------------------
 1    VMName   running


```


Any suggestions on what to try or do next?

Thanks,

Alan.

---

### Post by TheFu on 2021-03-09
Setup ssh-keys already.

On the client system:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote
```
That's it.

Verify the keys are working:
```
ssh userid@remote
```

On the client machine, you must have **virt-manager** and spice-client-...... (really long package name) installed and your userid should be in the *libvirtd* group on the KVM server.
There are other settings inside the VM that are needed, but I think the defaults are for SPICE to be used since 18.04.  You can change that to VNC or VMVGA, if you like in the VM settings.  On a non-desktop, SPICE isn't exactly useful.  Heck, on a non-desktop, just use ssh directly. That is much more efficient.
Until today, I never tried to connect to a server using spice. It never made any sense to try.

---

### Post by Alan5127 on 2021-03-09
Hi TheFu,

Adding the SSH keys fixed the problem.

No idea  why - I appreciate it is more convenient, but not sure why it works that  way, and not by typing the password, but regardless, it is working  now.T

Thanks!

Alan.

---

