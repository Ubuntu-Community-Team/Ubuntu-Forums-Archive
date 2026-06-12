---
title: "Unable to connect to virtual machine"
date: 2009-10-16
forum: Server Platforms
---

### Post by karaluh on 2009-10-16
I'm settin gu vm host using this guide:
[https://help.ubuntu.com/9.04/serverguide/C/libvirt.html](https://help.ubuntu.com/9.04/serverguide/C/libvirt.html)

I've succesfully set up the virtual machine:
```
user1@server1:~$ sudo virsh -c qemu:///system list
Connecting to uri: qemu:///system
Identyfikator Nazwa                Stan
----------------------------------
  2 virtmachine          uruchamianie

```
But I'm unable to connect to it to install guest operating system:
```
user2@server2:~$ virt-viewer -c qemu+ssh:///server1 virtmachine
user2@localhost's password:
libvir: QEMU b&#322;&#261;d : serwer zamkn&#261;&#322; po&#322;&#261;czenie
unable to connect to libvirt qemu+ssh:///server1
```

The error translates as: "Server closed connection." I tried to google the error message, but didn't find any clues. Ssh key infrastructure works, I can log in to the remote vmhost machine (server1 - Jaunty) from my computer (server2 - Karmic) over ssh without password just fine. What do I do wrong?

---

