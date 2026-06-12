---
title: "Virtualization"
date: 2014-03-31
forum: Virtualisation
---

### Post by thault on 2014-03-31
I'm currently running Ubuntu 12.04 server LTS. I am looking at running a virtual CentOS server that will run OwnCloud. I'm relatively new to virtualization. Any suggestions?

---

### Post by 1clue on 2014-03-31
QEMU or KVM, instal it and let it go.  You can see the console via X or from a tool like virt-manager, and probably a bunch of other options.

You could also theoretically donate your video card to that VM and it would work in spite of the host not having a gui.  I know this should be possible but have yet to try it.

---

### Post by thault on 2014-04-01
> **1clue said:**
> QEMU or KVM, instal it and let it go.  You can see the console via X or from a tool like virt-manager, and probably a bunch of other options.

You could also theoretically donate your video card to that VM and it would work in spite of the host not having a gui.  I know this should be possible but have yet to try it.

Any good guides on installing and using KVM?

---

### Post by slickymaster on 2014-04-01
> **thault said:**
> Any good guides on installing and using KVM?

[Linux-KVM - HOWTO]("http://www.linux-kvm.org/page/HOWTO")
[Quick Start Guide for installing and running KVM]("http://pic.dhe.ibm.com/infocenter/lnxinfo/v3r0m0/topic/liaai.kvminstall/kvminstall_pdf.pdf")

---

### Post by Lars Noodén on 2014-04-01
Installing is not hard.  It's part of the Qemu suite.

[https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

Here's one example of using it:

```

   qemu-img create -f qcow2 tahr.test.qcow2.img 5g

   qemu-system-i386 --enable-kvm -hda tahr.test.qcow2.img -m 1024 \
	-cdrom trusty-server-i386.iso -boot d

```

Then boot from the installed hard disk.

```

   qemu-system-i386 --enable-kvm -hda tahr.test.qcow2.img -m 1024 \
	-boot c

```

It is also possible to forward local ports to the VM.  This forwards
port 1234 on the local host to port 22 on the VM:
```

   qemu-system-i386 --enable-kvm -net user,hostfwd=tcp::1234-:22 \
	-net nic -hda tahr.test.qcow2.img -m 1024 -boot c

```

Then you can ssh to localhost on port 1234 and get to your guest.

---

### Post by thault on 2014-04-01
By installing KVM on the server, how do I go about using virt-manager on a CLI server. Do I need to X11 forward over ssh?

---

### Post by thault on 2014-04-02
I guess what I'm looking for is the command I need to run in order to initialize the program to x11 port forward.

---

### Post by 1clue on 2014-04-02
I don't use one.  Your remote host needs to allow X11 forwarding, /etc/ssh/sshd_config search on [B]X11
[/B]
Other than that, I do this:
[B]
ssh -X remotebox
firefox &
[/B]
And that's all it takes.

---

