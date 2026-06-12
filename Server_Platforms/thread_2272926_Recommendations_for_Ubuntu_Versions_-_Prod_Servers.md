---
title: "Recommendations for Ubuntu Versions - Prod Servers, Need Remote Desktop"
date: 2015-04-09
forum: Server Platforms
---

### Post by bsntech on 2015-04-09
Seeking recommendations for the version of Ubuntu that should be installed.

This will be for production servers that will have a large range of services for web - apache, proftp, dovecot, exim4, mysql, spamassassin, clamav, csf, virtualbox (host-only).

Recently upgraded to Ubuntu 14.04 but do not like the fact that Compiz is taking a huge chunk of CPU.  It has tripled the average CPU usage one eight-core servers with 16 GB of memory.

The main requirement is the ability to remote desktop into them - even if no one is logged in.  I made a lot of custom changes several years ago and have continued to just do the typical upgrade - but it is time to probably start a fully clean install from all of the upgrades and to get rid of Compiz/Unity.

Looking for a low footprint OS (minimum space usage) but also the ability to do the remote desktop capabilities.  The Ubuntu GNOME seems to be hitting my attention, but what do others think?

---

### Post by TheFu on 2015-04-09
* Servers don't have a desktop. Learn it. Know it. Love it.
* 14.04 Server is a fine LTS release.  No desktop, no compiz. No bloat.
* If you demand a remote desktop, don't use Unity.  Go with something lite, but I suspect setting up and using a pure WM will be too much effort - try xfce or lxde.  Use x2go for the client/server remote desktop.  There are how-tos all over the place.  x2go has a PPA for 14.04.
* Get over your remote desktop needs, if you want to be a server admin.  ssh is all we need ... plus a DevOps tool like ansible.
* Don't touch gnome3.
* Don't install proftp - [plain FTP should have died out in 1990]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp"). Use sftp instead.
* Mysql - use mariaDB, the non-Oracle alternative.
* Virtualbox is a toy for playing with virtual machines. For production use KVM (preferred) or Xen for servers and extremely stable situations. On a client machine, load up virt-manager to manage the VMs.  If you will have more than a few physical servers, take a look at proxmox - if more than 20-50 physical servers - look at openstack for upto 20K physical servers.

* And as long as you asked, dump apache for nginx, unless you really need the "kitchen sink" of apache.

You did ask for "recommendations." ;)

Did I mention - forget remote desktops? Do not load a desktop distro on a server.

If you'd like to become more comfortable with Linux/Unix, some directed learning will open the world to you [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) and explain why point-n-click is inefficient. Just the first 5 links there.

---

### Post by bsntech on 2015-04-09
Appreciate the response back, TheFu.

I'm installing a minimal version of Ubuntu currently - just for testing and will then install the necessary requirements.

The main reason for the remote desktop capabilities is to control and manage the virtual machines that would be running on them.  All of the VMs I have now use VirtualBox, which I've used for many years and it works pretty well.  I do everything else via ssh.

ProFTP - I have it set to require SSL/TLS with a certificate.  

MySQL vs MariaDB - any real reason to change from MySQL?  Sure, it is operated by Oracle now, but is that a reason to change?

Certainly appreciate the recommendations.

---

### Post by TheFu on 2015-04-09
Lots of opinion follows ... 

> **bsntech said:**
> I'm installing a minimal version of Ubuntu currently - just for testing and will then install the necessary requirements.
Should fit in about 4G - which is still 4x too large, IMHO.

> **bsntech said:**
> 
The main reason for the remote desktop capabilities is to control and manage the virtual machines that would be running on them.  All of the VMs I have now use VirtualBox, which I've used for many years and it works pretty well.  I do everything else via ssh.
virt-manager removes that requirement. Switch to KVM and you'll drop all the extra stuff you have with a GUI for virtualbox. It isn't hard - *vboxmanage export*.  Plus KVM is faster than any of the other alternatives for HVM solutions - even the commercial options. The only trick is linux bridging - besides that, virt-manager is the GUI you want - just run securely from anywhere thanks to ssh tunnels (automatic). virt-manager provides a remote console too. You can find my KVM+virt-manager presentation with a search. On the same LAN, you might try a SPICE remote desktop, if you need more performance. I use x2go myself - prefer the NX protocol for 2-3x performance over VNC/RDP options and ssh for key-based tunnel security.

> **bsntech said:**
> ProFTP - I have it set to require SSL/TLS with a certificate.  
Clients can choose NOT to use encryption with FTPS ... use sftp. It is proven and works. sftp has extra options to lock down users and is almost trivial to chroot. If you want everyone in the world to have access, use http.  Plus FTP is hell on firewalls. The add-on FTP servers have had histories of backdoors or bugs, so I'd rather avoid them.

> **bsntech said:**
> MySQL vs MariaDB - any real reason to change from MySQL?  Sure, it is operated by Oracle now, but is that a reason to change?
I take it you've never been burned by Oracle?  Either you can wait for that to happen or you can be proactive and switch to BETTER technology on your schedule, not theirs. Let there be no mistake, KVM, mariadb ARE better technologies .... IMHO.  Really, I'd go with postgresql over even mariadb, if you can, but that is a larger change.

> **bsntech said:**
> Certainly appreciate the recommendations.
As you can see, I'm full of "opinion." ;)  Hopefully others will chime in to refute what I've written and provide a different viewpoint. 
Only you can decide if I've made a case or not.

---

### Post by volkswagner on 2015-04-09
+1 for KVM and ssh -X user@server virt-manager.

You won't regret the small time investment.

KVM is the closest thing you'll find vs running on real hardware.

As stated, with this approach you can keep your server lean without a desktop environment.
Keep your GUI's in your VM's.

Here are some links I used to get my setup working.
[https://vpsboard.com/topic/248-install-and-configure-kvm-to-your-dedicated-server/](https://vpsboard.com/topic/248-install-and-configure-kvm-to-your-dedicated-server/)
[http://wiki.libvirt.org/page/Networking#Host_configuration](http://wiki.libvirt.org/page/Networking#Host_configuration) I used for setting up the bridge.

After running through the tutorial, here are some commands I ran to get X forwarding and virt-manager working.

```
aptitude install libgtk2.0-bin policykit-1  --without-recommends
aptitude install virt-viewer --without-recommends
aptitude install ntfs-3g policykit-1-gnome qemu  --without-recommends
apt-get install xauth
```

---

### Post by TheFu on 2015-04-09
> **volkswagner said:**
> +1 for KVM and ssh -X user@server virt-manager.

Actually - this is NOT what I recommend.

virt-manage can run on any Linux desktop anywhere in the world.  It will use ssh to connect to libvirtd running on the hypervisor and can manage 95% of the stuff you need a hypervisor to manage.  To be clear - virt-manager HAS SSH BUILT-IN - it isn't something you have to manually tunnel yourself.

No need for any gui tools, including virt-manager, on the VM host.

So - if you like, you can run it inside a VM-guest from any client you have. For that, I'd use x2go ... OTOH, why bother if you already have a Linux desktop?  It is only if you have a Windows/OSX dekstop where the remote into virt-manager makes sense and X/Windows is highly non-secure, so use x2go instead.

If you have a linux desktop - install virt-manager and ssh on it. Then let virt-manager handle the remote connection to the VM host running KVM+libvirtd (no GUI necessary on the server all all).

BTW - I've used all these methods. Generally, I manage VMs from a chromebook running ubuntu with virt-manager on it.
Here's a diagram: [http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization](http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization) - ignore the freenx/nomachine stuff - that is x2go now and completely optional.

---

### Post by bsntech on 2015-04-09
Very much appreciate the responses.

The minimal install of Ubuntu turned out to be only a gig with nothing else loaded.  Going to check and see if I can find your KVM article for the host computer.  The VMs are all going to be overhauled anyways, so I won't need to import.  What about easily making copies of those VMs to use it as another system?  With VirtualBox, it was simple to issue one command to change the GUID to duplicate to a 'new' VM.

MariaDB - does it support all of the same PHP functions and everything that MySQL does?  And does it do master-master replication (replication in both directions)?

---

### Post by TheFu on 2015-04-09
You can treat VMs under KVM just like physical hosts.  You can migrate from virtualbox to kvm in many, many, different ways. Your choice.  With KVM, you can "live-migrate" running VMs between KVM servers. Or you can shutdown the VM, export the XML settings (virsh dumpxml) and copy the virtualHDD file(s) to a different box (assuming you don't use LVM passthru.  That is sorta THE reason for using VMs - any VMs, right?  If you want to live-migration, you'll want shared storage or a SAN.

KVM is extremely flexible - especially with storage.  Networking isn't really part of KVM - you can use openvswitch which can do almost anything.  For 10G networking, openvswitch is recommended. For 1G networking, I don't find it worth the hassle.  Setup your bridges manually outside KVM and don't trust the libvirt bridges.  

You'll have to google for those mariadb answers - my understanding is API compatibility - so you can use mysql clients/libraries to connect to mariadb servers.  The mariaDB team are the guys who created mysql.  I've dropped in mariadb as a 100% replacement for mysql a few times, but generally use postgresql on new projects.

---

