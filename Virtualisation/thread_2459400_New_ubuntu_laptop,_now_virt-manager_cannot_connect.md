---
title: "New ubuntu laptop, now virt-manager cannot connect."
date: 2021-03-18
forum: Virtualisation
---

### Post by Heeter on 2021-03-18
Hi all,

I have a current mature host ubuntu server with only kvm installed on a "bare metal" Dell blade server. I have 2 guest ubuntu vms running on it.

I justrecently replaced my laptop, My old one I used to connect to server using virtmanager, but I cannot figure out how to get virtmanager to connect on my new laptop.

I can still connect using ssh to all 3.

I would like to get virtmanager to connect, but every ip I use it says cannot connect.

I must admit it has been so long ago that I don't really remember how to create a new connection???

Oh well, anyway guidance would be greatly appreciated

PS** libvirtd is running on host server

Regards

---

### Post by TheFu on 2021-03-18
Setup ssh-keys between the client and server.  That's 2 commands, both run on the client machine.
```
$ ssh-keygen -t ed25519     
$ ssh-copy-id {userid}@remoteIP
```

On the KVM server, verify that your userid is a member of the libvirtd group. Use 'id' to do that.

---

### Post by Heeter on 2021-03-18
> **TheFu said:**
> Setup ssh-keys between the client and server.  That's 2 commands, both run on the client machine.
```
$ ssh-keygen -t ed25519     
$ ssh-copy-id {userid}@remoteIP
```

On the KVM server, verify that your userid is a member of the libvirtd group. Use 'id' to do that.

Great Thank you TheFu

Thats what it was complaining about ssh.

Going to try that right away!!!

---

### Post by Heeter on 2021-03-18
Thank you TheFU

Virt-manager now connected to the kvm server

Regards

---

### Post by TheFu on 2021-03-18
Please use the "Thread Tools" button near the top to mark this thread SOLVED. Help out the community.

---

### Post by Heeter on 2021-03-18
Done

---

