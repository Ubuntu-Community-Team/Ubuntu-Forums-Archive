---
title: "libvirt error when using vnc"
date: 2010-03-14
forum: Server Platforms
---

### Post by ginbuntu on 2010-03-14
Hi, I am trying to create a guest OS on Ubuntu server 9.04  witht his command
 
```

sysadm@ubuntu:~$ sudo virt-install -n jboss2 -r 2048 --vcpus=4 --os-type=linux --nonsparse -w bridge:br0 --accelerate --vnc --noautoconsole --vncport=5906 -f /dev/sdb1 -c /VMs/cd-images/ubuntu-8.04.4-server-amd64.iso 


Starting install...
internal error unable to start guest: char device redirected to /dev/pts/1
char device redirected to /dev/pts/3
inet_listen: bind(ipv4,127.0.0.1,5906): Cannot assign requested address
inet_listen: FAILED

Domain installation may not have been
 successful.  If it was, you can restart your domain
 by running 'virsh start jboss2'; otherwise, please
 restart your installation.
ERROR    internal error unable to start guest: char device redirected to /dev/pts/1
char device redirected to /dev/pts/3
inet_listen: bind(ipv4,127.0.0.1,5906): Cannot assign requested address
inet_listen: FAILED
Traceback (most recent call last):
  File "/usr/bin/virt-install", line 709, in <module>
    main()
  File "/usr/bin/virt-install", line 642, in main
    dom = guest.start_install(conscb, progresscb, wait=(not wait))
  File "/usr/lib/python2.6/dist-packages/virtinst/Guest.py", line 926, in start_install
    return self._do_install(consolecb, meter, removeOld, wait)
  File "/usr/lib/python2.6/dist-packages/virtinst/Guest.py", line 966, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 973, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error unable to start guest: char device redirected to /dev/pts/1
char device redirected to /dev/pts/3
inet_listen: bind(ipv4,127.0.0.1,5906): Cannot assign requested address
inet_listen: FAILED

sysadm@ubuntu:~$

```
as you can see it, gives an error. however if I remove the --vnc option, it works fine.
```

sysadm@ubuntu:~$ sudo virt-install -n jboss2 -r 2048 --vcpus=4 --os-type=linux --nonsparse -w bridge:br0 --accelerate  --noautoconsole -f /dev/sdb1 -c /VMs/cd-images/ubuntu-8.04.4-server-amd64.iso 


Starting install...
Creating domain...                                                 0 B 00:01 
/usr/lib/python2.6/dist-packages/virtinst/Guest.py:1086: DeprecationWarning: integer argument expected, got float
  for ignore in range(1, (5 / .25)): # 5 seconds, .25 second sleeps
Domain installation still in progress. You can reconnect to 
the console to complete the installation process.
sysadm@ubuntu:~$

```
But then I can not connect to the console. 

Can some one help me with this problem. thanks in advance

---

### Post by Cosma on 2010-03-14
Try to remove just "--vncport" to let it take the next free one or check with "lsof -i" if there is already someone running on port 5906.

---

### Post by ginbuntu on 2010-03-14
I tried that already and I also disabled apparmor

---

