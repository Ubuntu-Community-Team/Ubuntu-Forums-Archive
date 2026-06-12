---
title: "Can't connect to Qemu/KVM monitor on headless box"
date: 2010-02-27
forum: Server Platforms
---

### Post by steve.st on 2010-02-27
Hi all,

I have KVM/Qemu/Libvirt setup on a remote headless box. I have a couple of VMs running and everything is fine.

Now I'd like to connect to the monitor to send some comments to Qemu, but I can't make it work. As the box is remote I don't have a GUI Qemu console, so I am trying to make it work using sockets.

The VM process is running with "-monitor unix:/var/run/libvirt/qemu/foo.monitor,server,nowait" and I have tried to connect using both "nc -U /var/run/libvirt/qemu/foo.monitor" and "socat - unix-connect:/var/run/libvirt/qemu/foo.monitor".

Neither works. strace shows nc/socat are blocking on connect() to the socket.

Any ideas?

Many thanks!

---

### Post by Insyte on 2010-04-01
The libvirt-bin process opens the monitor socket.  Stop it and you'll be able to connect.

    /etc/init.d/libvirt-bin stop

---

