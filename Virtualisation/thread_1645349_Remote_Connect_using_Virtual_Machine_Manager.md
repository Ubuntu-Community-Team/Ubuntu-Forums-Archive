---
title: "Remote Connect using Virtual Machine Manager?"
date: 2010-12-14
forum: Virtualisation
---

### Post by flickerfly on 2010-12-14
I'd like to make a connection to my remote virtualization server, but Virtual Machine Manager seems to require me to connect as root. Using Ubuntu, I'd like to avoid having to set a root password on the server. This would be inconsistent with my other machines and I find myself in agreement with the policy that Ubuntu has in this area.

How can I connect to my virt server? I put username@server in for the server name and this looked like it was going to work, but it doesn't have proper permissions (can't do sudo?).

I'm so close...

---

### Post by flickerfly on 2010-12-14
Oh, I figured out my permission issue. In studying to figure out the problem using virsh instead, I found the solution to both. For others who may need this...

On the remove server add the user to the libvirtd group.

```
sudo usermod -G libvirtd -a username
```

Then when putting the hostname into the connection dialog, do it in ssh form like this "username@hostname".

I haven't yet run this through it's paces, so I may still have other problems.

---

### Post by beeny on 2012-11-13
For reference, this is the exception raised by VMM in case the user used for establishing the connection isn't part of the libvirtd group. Notice the 'virConnectOpenAuth() failed' near the end: 

```

Unable to connect to libvirt:

End of file while reading data: : Input/output error

Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started

Libvirt URI is: xen+ssh://madave@york.madave.nl/

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 1185, in _open_thread
    self.vmm = self._try_open()
  File "/usr/share/virt-manager/virtManager/connection.py", line 1167, in _try_open
    flags)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 102, in openAuth
    if ret is None:raise libvirtError('virConnectOpenAuth() failed')
libvirtError: End of file while reading data: : Input/output error

```

---

### Post by wildmanne39 on 2012-11-13
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

