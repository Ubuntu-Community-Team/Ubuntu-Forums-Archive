---
title: "VirtualBox had incompatible problem on Ubuntu 13.04 64bits"
date: 2013-08-24
forum: Virtualisation
---

### Post by anderlew on 2013-08-24
Hello everyone.
Several weeks ago. I can use VirtualBox on my ubuntu correctly(Still on ubuntu 13.04 64bits). I don't known which update made this incompatible problem with virtualbox.
When I start the virtualbox service, I got this error message '[ 3488.347958] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[COLOR=#ff0000][ 3614.728633] vboxdrv: Unknown symbol mcount (err 0)[/COLOR]'.
I try to used the official VirtualBox and open source version from repository. The problem are still happened.
I also google it and no answer. Anyone known how to resolve this problem. Thank you.


OS: Ubuntu 13.04 64bits
Kernel: 3.8.0-30-generic
Virtualbox: virutalbox-4.2(ubuntu repository version), virtualbox 4.2.16(Official version)

---

### Post by anderlew on 2013-08-25
Nobody had the same problem as me? I known one of my friends he using ubuntu 13.04 also, and virtualbox working correctly. But he used ubuntu 32bits.
Could you tell me which ubuntu(32bits or 64 bits) and virtualbox version are you using. 
Thank you.

---

### Post by ibjsb4 on 2013-08-25
> **anderlew said:**
> Could you tell me which ubuntu(32bits or 64 bits) and virtualbox version are you using. 

32bit and always download vBox from the VirtualBox site.  I have been doing this for a few years and problems are rare for me.

And I only run LTS versions (12.04).

---

### Post by anderlew on 2013-08-26
> **ibjsb4 said:**
> 32bit and always download vBox from the VirtualBox site.  I have been doing this for a few years and problems are rare for me.

And I only run LTS versions (12.04).

Thank you, [COLOR=#000000]ibjsb4[/COLOR].
Does any other friend also met the same problem as me.
I'm so lock got this problem. Do I need create a bug for ubuntu developer?

---

### Post by SeijiSensei on 2013-08-26
I believe that whether you can run 64-bit guests on top of a 64-bit host depends on features of the CPU and BIOS.

However, you might try this first.  Use "sudo apt-get purge virtualbox*" to remove any existing repository versions.  Next visit [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) and follow the instructions for "Debian-based" systems.  Even though it does not appear in the list, on a 13.04 machine you should add the line

```
deb http://download.virtualbox.org/virtualbox/debian raring contrib
```

to /etc/apt/sources.list.  Follow the instructions to download and install Oracle's public key, then use apt-get to install VB as described on the Downloads page.  This method ensures that your installation of VB will be kept up-to-date automatically using the same system Ubuntu uses to update all the other software on your system.

---

### Post by TheFu on 2013-08-26
No help on this specific topic, but I'll put forth a different option ... 

I stopped using virtualbox on Linux systems a few years ago - the stability was crap back then on my hardware.

Switched from Xen to KVM-based virtualization. KVM has always worked. ALWAYS, when Xen, virtualbox, proxmox, ESXi and a few others refused to work.  These days, running **KVM** with libvirt provides a way to get great desktop audio and GPU performance by using the **Spice** remote desktop - no more slow VNC stuff needed. It will never be as fast as VirtualBox desktop-on-desktop graphics, but it is very close. I've seen streaming video work with Spice.  The key is to use **virt-manager** to setup the VMs - virt-manager is a GUI app that anyone used to VMware Player or VirtualBox will quickly understand.

Less and less do we need to use software created by corporations known to be hostile towards F/LOSS.

Anyway, I hope you find a solution that meets your needs. There isn't a one-size fits everyone solution yet.

---

### Post by SeijiSensei on 2013-08-26
> Less and less do we need to use software created by corporations known to be hostile towards F/LOSS.


While Oracle indeed bought VirtualBox as part of its purchase of Sun, it looks to me like the original developers still largely run the show.  (For instance, the website hasn't changed in years.)  The only proprietary features of VB are things like USB integration which cannot be freely distributed because they require a license from usb.org.

Running VirtualBox on a Windows or Linux desktop machine is bog-simple.  In the desktop setting, using ordinary applications, I don't find performance to be an issue.  If I were running a server that supports multiple virtual machines, I'd opt for a different solution like Xen or KVM. My [Linode]("http://www.linode.com/") VMs are all on the Xen platform.  However for desktop users who, like me, occasionally need to run Windows or try things out in a CentOS or Ubuntu Server instance, I have no complaints about VirtualBox.

I do use PostgreSQL partly because I don't trust Oracle when it comes to SQL databases.  I don't think they give a damn about VB; it was just something that came along when they bought Sun.  MySQL posed a bigger threat to their core business, which is a reason to avoid it, though I think Postgres is the bigger threat when it comes to enterprises.  I started using Postgres when I needed a database I could distribute freely to clients; at the time both MySQL and the now-departed msql had restrictive licenses.  RedHat included PG, and so did I.  Now I can't imagine using anything else.

---

### Post by TheFu on 2013-08-26
> **SeijiSensei said:**
> While Oracle indeed bought VirtualBox as part of its purchase of Sun, it looks to me like the original developers still largely run the show.  (For instance, the website hasn't changed in years.)  The only proprietary features of VB are things like USB integration which cannot be freely distributed because they require a license from usb.org.

Running VirtualBox on a Windows or Linux desktop machine is bog-simple.  In the desktop setting, using ordinary applications, I don't find performance to be an issue.  If I were running a server that supports multiple virtual machines, I'd opt for a different solution like Xen or KVM. My [Linode]("http://www.linode.com/") VMs are all on the Xen platform.  However for desktop users who, like me, occasionally need to run Windows or try things out in a CentOS or Ubuntu Server instance, I have no complaints about VirtualBox.

I do use PostgreSQL partly because I don't trust Oracle when it comes to SQL databases.  I don't think they give a damn about VB; it was just something that came along when they bought Sun.  MySQL posed a bigger threat to their core business, which is a reason to avoid it, though I think Postgres is the bigger threat when it comes to enterprises.  I started using Postgres when I needed a database I could distribute freely to clients; at the time both MySQL and the now-departed msql had restrictive licenses.  RedHat included PG, and so did I.  Now I can't imagine using anything else.

As usual, we agree on almost everything ... except I've not had the same luck with virtualbox on Linux.  50% of the machines I've tried it on would crash the hostOS - complete lockup.  OTOH, that was 3+ yrs ago.  For the last 2 yrs, Mom's PC has been using VirtualBox on Linux and while it isn't as clean an implementation as KVM, it has been stable for Mom.  I've been using VirtualBox on Windows for about 4 yrs - multi-week stability was an issue until Win7 came out and had 6 months of use - since that time, vbox with Windows as the hostOS has caused ZERO stability issues here - we're talking months between reboots ... or whenever the monthly patches from MS are released.

Xen is fine, provided someone else is running the hostOS. 4 yrs of experience doing that here on a few different HW platforms.

DBs - I prefer pg, choose to use whatever DB the developers use and if that is MySQL, use MariaDB instead.  Just brought up a Redmine instance today. They "support" pg, but they develop on MySQL.  I try to **never fight the developers** - having been one commercially.

These days, I avoid anything that says "oracle" if possible, but EMC and VMware have proven to be much worse to me and my clients. Sometimes, we have to pick the least evil solution. ;(

---

### Post by anderlew on 2013-08-26
> **SeijiSensei said:**
> I believe that whether you can run 64-bit guests on top of a 64-bit host depends on features of the CPU and BIOS.

However, you might try this first.  Use "sudo apt-get purge virtualbox*" to remove any existing repository versions.  Next visit [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) and follow the instructions for "Debian-based" systems.  Even though it does not appear in the list, on a 13.04 machine you should add the line

```
deb http://download.virtualbox.org/virtualbox/debian raring contrib
```

to /etc/apt/sources.list.  Follow the instructions to download and install Oracle's public key, then use apt-get to install VB as described on the Downloads page.  This method ensures that your installation of VB will be kept up-to-date automatically using the same system Ubuntu uses to update all the other software on your system.

Thanks for you reply. I do it before and not useful. I just try to do it by your instructions again and it still can't working.
I will try to use KVM recently. because I red a news about 'Oracle will stop to developing VirtualBox'.

---

### Post by anderlew on 2013-08-26
> **TheFu said:**
> No help on this specific topic, but I'll put forth a different option ... 

I stopped using virtualbox on Linux systems a few years ago - the stability was crap back then on my hardware.

Switched from Xen to KVM-based virtualization. KVM has always worked. ALWAYS, when Xen, virtualbox, proxmox, ESXi and a few others refused to work.  These days, running **KVM** with libvirt provides a way to get great desktop audio and GPU performance by using the **Spice** remote desktop - no more slow VNC stuff needed. It will never be as fast as VirtualBox desktop-on-desktop graphics, but it is very close. I've seen streaming video work with Spice.  The key is to use **virt-manager** to setup the VMs - virt-manager is a GUI app that anyone used to VMware Player or VirtualBox will quickly understand.

Less and less do we need to use software created by corporations known to be hostile towards F/LOSS.

Anyway, I hope you find a solution that meets your needs. There isn't a one-size fits everyone solution yet.

Thanks for your help. I will try to use kvm, vmware or other products instead of virtualbox.

---

### Post by alexey4 on 2013-09-02
Check your GCC version. It must be at least 4.6
If not, install using apt-get.

---

### Post by PJ_Dawson on 2013-09-06
When you created the VM, you selected Ubuntu(64-bit) correct?  otherwise the VM will be configured with an i386 processor, if i'm not mistaken.  

To be perfectly honest I've never really noticed a difference in performance between 32 and 64 bit applications, 32 bit has always worked fine for me.

I have 3 separate ubuntu servers, all on VM's in VirtualBox.  Two are running server-12.04-32 bit  and one is running 12.04-desktop-32 bit.

---

