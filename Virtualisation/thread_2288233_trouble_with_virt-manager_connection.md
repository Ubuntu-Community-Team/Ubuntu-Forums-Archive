---
title: "trouble with virt-manager connection"
date: 2015-07-25
forum: Virtualisation
---

### Post by ruslan7 on 2015-07-25
Hi all!
I don't have a lot of experience of ubuntu. I have a test-lab. In my test lab i have a server ubuntu 14.04 and desktop(vm) ubuntu 15.04. On both machines i created a user "eadmin" and add him to "libvirt" group. I used this link [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) as manual to install kvm. But i can't connect to server from desktop use virt-manager. 
I've tried to conncet 
sudo virt-manager -c qemu+ssh://eadmin@192.168.1.51
sudo virt-manager -c qemu+tcp://eadmin192.168.1.51/system
But get an error. Message bellow.
"Internal error: no QEMU URI path given, try to qemu:///system
Libvirt URI is: qemu+ssh://eadmin@192.168.1.51
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 1050, in _open_thread
    self._backend.open(self._do_creds_password)
  File "/usr/share/virt-manager/virtinst/connection.py", line 158, in open
    open_flags)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 105, in openAuth
    if ret is None:raise libvirtError('virConnectOpenAuth() failed')
libvirtError: internal error: no QEMU URI path given, try qemu:///system"


My server ubuntu 14.04
addr:192.168.1.51/24
Linux nd01 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
libvirtd (libvirt) 1.2.2
qemu-kvm  2.0.0+dfsg-2ubuntu1.14

My desktop(vm) Ubuntu 15.04-desktop
addr:192.168.1.35
Linux desktop1504 3.19.0-23-generic #24-Ubuntu SMP Tue Jul 7 18:52:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
virt-manager   1:1.0.1-5ubuntu1

How should i do to connect my server use virt-manager from desktop?
Thank's for the answers
Best regard Ruslan.

---

### Post by TheFu on 2015-07-25
Did you setup ssh first?
That is the first step for any networked Unix system - ssh - install the client and the server on both sides, then get key-based authentication working.

BTW - ssh is the first thing I install on any system - 64-way Superdome or Raspberry Pi - both run openssh-server.

---

### Post by ruslan7 on 2015-07-27
TheFu thank's for your advice. 
Yes, i had installed ssh before. Trouble is the libvirtd.conf. Libvirt-bin doesn't listen port 16509. 
My setings in /etc/libvirt/libvirtd.conf
listen_tcp = 1
tcp_port = "16509"
listen_addr = "192.168.1.51"
unix_sock_group = "libvirtd"
unix_sock_ro_perms = "0777"
unix_sock_rw_perms = "0770"
auth_unix_ro = "none"
auth_unix_rw = "none"
I 've read that after configuration libvirtd.conf i have to add options "-l" into /etc/default/libvirt-bin, option libvirtd_opts="-d". But after that service libvirt-bin can't start. 
sudo service libvirt-bin start
libvirt-bin stop/post-start, (post-start) process 2014

---

### Post by TheFu on 2015-07-27
I have **NEVER** touched those options.  Always use automatic ssh tunnels for the remote stuff. It "just works", assuming ssh is already working between the machines.  The only trick to getting userid@remote to work is that "userid" be in the libvirtd group on the 'remote" system.  Besides that, normal ssh_config stuff and ~/.ssh/config settings "just work".

I would guess the only reason for those settings would be if SPICE was used without any TLS.

---

