---
title: "[SOLVED] KVM, vnc, putty tunnel"
date: 2008-04-05
forum: Virtualisation
---

### Post by mbeach on 2008-04-05
Hi,
I'm playing with Hardy and KVM.  I've got a virtual machine running [mykvm.img], after following 
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

I start "mykvm" with the command:
qemu -no-acpi -m 384 -vnc :10 mykvm.img

From the localhost I can use a VNC viewer to view "mykvm" KVM by connecting to localhost:5910

I also have an ssh-server running on localhost (the Hardy box).  From a machine outside the network, I can ssh in to this machine (port forwarded through the routers).  Using putty from a windows machine from outside the lan, I am also able to tunnel to the localhost:5900 using vnc viewer  (using the tunnels in putty). 

That's all good.  What I was hoping to do next is vnc to the KVM machine available on localhost:5910 by tunneling from the windows machine outside the lan in a similar manner, however, I just get a timed out connection when I try.  I'm quite certain my tunnel on the Putty side is setup correctly.

Where do I look for log entries which would tell me if the request is even getting through to the Hardy machine?  Does the KVM vnc server have a configuration setting that would prevent me from viewing it via a forwarded port?  Which file would that be in?

Any pointers are welcomed, Thank you,
mb.

---

### Post by mbeach on 2008-04-05
Nevermind - works as expected.  Just need to spell 'localhost' correctly.

---

