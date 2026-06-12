---
title: "kvm qemu virt-install serial passthrough issues"
date: 2011-01-16
forum: Virtualisation
---

### Post by stokkeland on 2011-01-16
It took a while to discover this - I believe it is a bug, but I am not enough of a lx/vm geek to know where to start filing a bug report, so I am posting this here hoping to help others and if someone can verify that it is a bug they can file it, hopefully. 

running ubuntu lucid server - 2.6.32-27-server #49-Ubuntu SMP
fully updated as of today I believe - some perhaps related versions```
kvm 1:84+dfsg-0ubuntu16+0.12.3+noroms+0ubuntu9.3
libvirt-bin 0.7.5-5ubuntu27.8
qemu-kvm 0.12.3+noroms-0ubuntu9.3
virt-manager 0.8.2-2ubuntu8
virtinst 0.500.1-2ubuntu6.1
```I had a hard time finding much on my issue, the goal was to get a serial port passthrough from host to guest, win-xp

This was my command and error (guest name xp-tracker):```
# virt-install -n xp-tracker -r 512 --disk path=/var/vm/xp-tracker/xp-tracker_sys --network bridge=br0 --vnc --vnclisten=0.0.0.0 --noautoconsole --serial=dev,PATH=/dev/ttyS0 --os-type windows --os-variant winxp --import

Starting install...
Guest installation complete... restarting guest.
ERROR    monitor socket did not show up.: Connection refused
Domain installation may not have been
 successful.  If it was, you can restart your domain
 by running 'virsh start xp-tracker'; otherwise, please
 restart your installation.
ERROR    monitor socket did not show up.: Connection refused
Traceback (most recent call last):
  File "/usr/bin/virt-install", line 943, in <module>
    main()
  File "/usr/bin/virt-install", line 859, in main
    dom.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 300, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: monitor socket did not show up.: Connection refused
``` i found all kinds of info out there related to apparmor issues - that wasn't the case - what I found was that when issuing that command, the scripts or something forces the data to lower case, so when doing virsh dumpxml yI saw this```
    <serial type='dev'>
      <source path='/dev/ttys0'/>
      <target port='0'/>
    </serial>
``` which I did not catch until hours of monkeywork - that ttys0 was with a lowercase S - after editing the xml and doing a define, it now works fine...

hopefully this post helps someone else find and fix -  I have no clue if it is ubuntu specific..  if someone wants to file a bug report and need more info from me feel free to ask, as long as it is something I can get from a production state of the system :)

---

