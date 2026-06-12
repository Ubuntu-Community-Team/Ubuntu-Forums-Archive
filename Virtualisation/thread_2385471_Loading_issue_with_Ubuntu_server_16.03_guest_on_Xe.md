---
title: "Loading issue with Ubuntu server 16.03 guest on Xen server 7.0"
date: 2018-02-20
forum: Virtualisation
---

### Post by sim085 on 2018-02-20
Hello, 

I have a couple of VMs installed on Xen server 7.0. All of these are Ubuntu server edition version 16.03. However one of these no longer wants to boot. After I start the grub loader comes up and when the time to wait elapses it tries to start but stops (Xen Center shows the VM as stopped).

I have looked over the internet but cannot understand how to resolve. I did manage to re-create the problem by installing a fresh version of Ubuntu server edition version 16.03.4 and then run the following commands:

```

sudo su
apt-get update
apt-get upgrade
apt-get dist-upgrade
shutdown now -r

```

That said I am not sure if it is just an update issue as I have tried not installing an updates on the VM giving me trouble and after leaving it on for some time, when I gave it shutdown now -h and tried to start again it showed the same symptoms again. 

Does anyone know how I can investigate this issue or what the problem might be?

---

### Post by sim085 on 2018-02-20
On second thought it could be related to updates. I have re-loaded this vm from an export I had done. I started it (booted successfully) and left it switched on. I then logged in on the VM from Xen Center console and I can see the following got printed on terminal:

```

[ OK ] Started ACPI event daemon.
[ OK ] Started ACPI event daemon.
[ OK ] Started ACPI event daemon.
[ OK ] Started ACPI event daemon.
       Stopping Network Time Syhnchronization...
[ OK ] Stopped Network Time Syhnchronization.
       Starting Network Time Syhnchronization...
[ OK ] Started Network Time Syhnchronization.
[ OK ] Started Trigger resolvconf update for networkd DNS.
[ OK ] Started ACPI event daemon.
[ OK ] Started ACPI event daemon.
       Stopping udev Kernel Device Manager...
[ OK ] Stopped udev Kernel Device Manager.
[ OK ] Started ACPI event daemon.
[ OK ] Started ACPI event daemon.
[ OK ] Started Daily apt upgrade and clean activities.

```

After these messages, if I do a restart VM does not come up again and I need to go back to a previous snapshot or import again. 

How can I update Ubuntu server edition running as guest on Xen then?

---

### Post by sim085 on 2018-02-21
Hello again,

What I found is that after the issue starts appearing the vm stays longer on grub screen (30s instead of 1s). I selected the option "Advance options for Ubuntu" and here I can see the following:

```

Ubuntu, with Linux 4.4.0-112-generic
Ubuntu, with Linux 4.4.0-112-generic (recovery mode)
Ubuntu, with Linux 4.4.0-21-generic
Ubuntu, with Linux 4.4.0-21-generic (recover mode)

```

If I select the first one "Ubuntu, with Linux 4.4.0-112-generic" the vm doesn't load. If I select the second one "Ubuntu, with Linux 4.4.0-21-generic" the vm loads up normally. 

So my question is; are these different kernels? Did "Ubuntu, with Linux 4.4.0-112-generic" come as part of an update (as I am assuming above)?

---

### Post by LHammonds on 2018-02-22
It looks like you have two kernels to boot from (which you always want to have at least 2 for this very reason).

Don't know why it isn't working for you though.  I have over a dozen Ubuntu Server 16.04.3 LTS servers running the latest kernel (4.4.0-112-generic) and patches.  I'm running on top of vmware's ESXi 6.0.0 though...not Xen Server.

Are you using VM guest extensions that comes with Ubuntu or drivers directly from XenServer?

For ESXi, I used to install vmware Tools from their ISO image but starting in Ubuntu 14.04, I could use the open-vm-tools.  In Ubuntu 16.04, open-vm-tools were automatically installed for me.

**EDIT:** Correction, they auto-upgraded themselves last night to 4.4.0-116-generic.  The ones running the new HWE platform are on 4.13.0-36-generic)

LHammonds

---

### Post by sim085 on 2018-02-22
Yes if I try an upgrade now I too get kernel 4.4.0-116-generic, however this one still fails. The only thing I have installed on these which is xen specific is the xen tools. I tried to re-install but still same issue. Really don't know where to look. I can go round the problem but can't understand what exactly is going wrong with the new kernel. 

Are there any logs which I can access (by booting through the bootable kernel) so I can know what is failing?


> **LHammonds said:**
> It looks like you have two kernels to boot from (which you always want to have at least 2 for this very reason).

Don't know why it isn't working for you though.  I have over a dozen Ubuntu Server 16.04.3 LTS servers running the latest kernel (4.4.0-112-generic) and patches.  I'm running on top of vmware's ESXi 6.0.0 though...not Xen Server.

Are you using VM guest extensions that comes with Ubuntu or drivers directly from XenServer?

For ESXi, I used to install vmware Tools from their ISO image but starting in Ubuntu 14.04, I could use the open-vm-tools.  In Ubuntu 16.04, open-vm-tools were automatically installed for me.

**EDIT:** Correction, they auto-upgraded themselves last night to 4.4.0-116-generic.  The ones running the new HWE platform are on 4.13.0-36-generic)

LHammonds

---

### Post by LHammonds on 2018-02-22
If you have active maintenance support from XenServer, check with them if there is a known issue with Xen7.0 and 4.4.0-112-generic kernel.  I wonder if this might be related to Spectre/Meltdown changes.  I don't know what kernel version those will be implemented in.

LHammonds

---

