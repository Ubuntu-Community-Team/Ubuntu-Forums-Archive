---
title: "Cannot ssh into LXC Ubuntu instance from host"
date: 2024-08-19
forum: Virtualisation
---

### Post by guitgentlygeeps on 2024-08-19
Hi,

I have created an instance from image Ubuntu:24.04. The container spins up fine and contains an ip address of 10.10.10.79. On my Ubuntu 22.04 host, my lxd adapter, lxdbr0 is at 10.10.10.1. I can ping from my host to the container and I can ping from my container to my host. I can ssh from my host to my container and easily create a ssh key pair and ssh into my host from the container with a key. I set this key pair up using ssh-copy-id with no problems. The frustrating problem is that I cannot ssh into my container as root or as a user account that I created for the container. I've edited /etc/ssh/sshd_config and set PermitRootLogin yes and tried various edits of typical parameters in this file all to no avail. The error that I get when attempting to ssh in is: 

$ ssh root@10.10.10.79
root@10.10.10.79: Permission denied (publickey).

I get the same error when attempting to a (non-root) guest account.

I've seen multiple posts of this but everyone suggests solving by editing sshd_config but this doesn't work in my case.

Does anyone have any insight into this. Thanks so much in advance.

Cheers.

---

### Post by TheFu on 2024-08-19
Did you put the public key into /root/.ssh/  correctly?
I know you won't listen, but logging in directly as root is not usual for Ubuntu systems, even containers.  If you use lxd to create the container, the "ubuntu" account is created for sudo needs.

You can use an **lxc exec** from the lxc host, btw to directly connect into the container as root, if you like.
```
$ lxc exec {container-name}  /bin/bash
```
I just tested that and it worked. Got a root shell inside the container.

Is your LXD networking configured for NAT, hostonly, or bridged?  I only use bridged and don't have this issue.

---

### Post by guitgentlygeeps on 2024-08-20
Hey thanks for the response. I hear what you're saying about the root login issue. Two things about that:
1.) I have many times successfully done a root login with Ubuntu on various real HW machines.
2.) As I stated in my post, I created a non-root account and still couldn't login via ssh.

And yes, I use lxc exec to get a root login or just start the container with the --console parameter.
I'd like to try to get my public key to the container and try what you've suggested but how to get the file from my host to the container?
Again, I appreciate your response!

Also, my network is configured as bridged.

---

### Post by currentshaft on 2024-08-20
126

---

### Post by guitgentlygeeps on 2024-08-20
Thanks. When I try that it appears that ssh on the host is trying all of the host private keys but since I have no public key on the instance it fails. It appears it's what TheFu stated. If I can get my public key to the instance, it might work. But it's also curious that I can just ssh as root into a ubuntu distro on a pi, or odroid or seemingly any hardware but not an lxc container.

---

### Post by guitgentlygeeps on 2024-08-20
Hey TheFu. I used the following command on my container u1:
lxc file push ~/.ssh/id_rsa.pub u1/root/.ssh/
Then logged into my instance lxc exec u1 bash
Once in I got into /root/.ssh and executed the command: cat id_rsa.pub >> authorized_keys

Once I did all of this I'm now able to ssh into my instance. Thank you! I still would like to know why the container acts differently than a HW installed ubuntu distro with respect to root login.
For instance, it would be nice to be able to just use ssh-copy-id from my host to accomplish this task.

---

