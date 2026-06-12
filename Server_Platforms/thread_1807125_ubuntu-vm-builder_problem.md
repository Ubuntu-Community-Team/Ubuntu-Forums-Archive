---
title: "ubuntu-vm-builder problem"
date: 2011-07-18
forum: Server Platforms
---

### Post by Pechy on 2011-07-18
Hello,
I'm having some troubles with ubuntu-vm-builder. When I try to build new virtual machine, it throws some errors and I don't know why.

```

root@ubuntu:/home/vm/VMBuilder-0.12.4# ubuntu-vm-builder kvm natty --addpkg openssh-server --ip 10.1.0.180 --mask 255.255.255.224 --net 10.1.0.160 --bcast 10.1.0.191 --gw 10.1.0.190 --dns 10.1.0.254
Traceback (most recent call last):
  File "/usr/bin/ubuntu-vm-builder", line 24, in <module>
    uvb.main()
  File "/usr/local/lib/python2.7/dist-packages/VMBuilder/contrib/cli.py", line 62, in main
    hypervisor, distro = self.handle_args(optparser, sys.argv[1:])
  File "/usr/local/lib/python2.7/dist-packages/VMBuilder/contrib/cli.py", line 288, in handle_args
    distro = VMBuilder.get_distro('ubuntu')()
  File "/usr/local/lib/python2.7/dist-packages/VMBuilder/distro.py", line 74, in __init__
    super(Distro, self).__init__()
  File "/usr/local/lib/python2.7/dist-packages/VMBuilder/distro.py", line 31, in __init__
    self.plugins = [plugin_class(self) for plugin_class in self.plugin_classes]
  File "/usr/local/lib/python2.7/dist-packages/VMBuilder/plugins/__init__.py", line 46, in __init__
    self.register_options()
  File "/usr/local/lib/python2.7/dist-packages/VMBuilder/plugins/network/__init__.py", line 70, in register_options
    domainname = '.'.join(socket.gethostbyname_ex(socket.gethostname())[0].split('.')[1:]) or "defaultdomain"
socket.gaierror: [Errno -2] Name or service not known

```

When I try normal vmbuilder, it throws the same error.
Can anyone pls help me? I got stuck. :confused:
Thanks for any advices.

---

### Post by Pechy on 2011-07-19
Nobody knows? :confused:

---

### Post by Maesto on 2012-05-24
Please have a look if your Server is able to resolve its FQDN ( hostname -f)

---

