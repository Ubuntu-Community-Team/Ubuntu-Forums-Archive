---
title: "Ubuntu 8.04 AMD64 Xen HVM Experience"
date: 2008-08-12
forum: Virtualisation
---

### Post by ecsezer on 2008-08-12
I just wanted to share my experience in running Xen and enabling HVM support.  Long story short I've failed and I hope to get an understanding on why that might be.

My system is a Dell Optiplex 755 which is a 64-bit machine with virtualization support.

I compiled xen from source and also compiled the 2.6.24-19-xen kernel.  I was able to boot into the system just fine.

Having the system up, I wanted to try virt-manager to create my DomU's.  However, I got the following error for which I haven't been able to find a satisfactory solution.

--------------------------------------------------------------
Unable to open connection to hypervisor URI 'xen:///':
<class 'libvirt.libvirtError'> virConnectOpenReadOnly() failed could not use Xen hypervisor entry /tmp/livirt_proxy_conn
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 332, in _open_thread
    self.vmm = libvirt.openReadOnly(self.uri)
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 144, in openReadOnly
    if ret is None:raise libvirtError('virConnectOpenReadOnly() failed')
libvirtError: virConnectOpenReadOnly() failed could not use Xen hypervisor entry /tmp/livirt_proxy_conn
----------------------------------------------------------------

After a day spent in the web, I decided I would stick with the command line and not use virt-manager.  My goal is to create a fully virtualized domU.  So I create a hvm configuration file and type in:
>> sudo xm create -c Ubuntu.hvm
Using config file "/etc/xen/Ubuntu.hvm".
Error: Kernel image does not exist: /usr/lib/xen/boot/hvmloader

Then I started looking at why I don't have hvmloader.  First of all, I'm unable to compile it from xen source code.  Apparently I need 'dev86' which I can't find in the repositories.  I read somewhere that bin86 would do as well, yet I still get the same compilation errors when trying to build hvmloader from xen source.

So I turned to the package manager versions.  I installed ubuntu-xen-server and voila, hvmloader was there under /usr/lib/boot/hvmloader.  So I restart the computer and for some reason the system is extremely slow.  After endless package manipilations I found out that xen-utils-3.2 seems to be the reason.  When I install xen-utils-3.1 (and the related 3.1 stuff) the system is running at a normal speed.  When I switch to xen-utils-3.2 the system comes to a crawl.  The problem is, when I remove xen-utils-3.2 and install 3.1, hvmloader is no longer there.

So I'm at a loss.  Is there anyone out there who's had success with using HVM guests in a Xen VMM using the amd64 kernel?  For me, the most critical thing would be to find out why my system slows down with xen-utils-3.2.  If I can get over that, I think the rest is working fine (except the virt-manager).

Cheers,

John

---

### Post by Ctrl+Alt+Del on 2008-08-22
In Xen 3.1 the hvmloader is part of the ioemu package, in 3.2 it was consolidated into xen-tools.

Wondering why your system is crawling under 3.2. running nicely here on my Opteron 64bit (Dell T105) running 8.04.1

I myself struggle with the problem of my hvm not booting after a succesfull install, but that's a different story

edit: oh and the virt-manager is simply broken, don't bother with it. I spend the better part of the day muddling through the python scripts with my very limited python skills and was not able to get any closer to a solution

---

