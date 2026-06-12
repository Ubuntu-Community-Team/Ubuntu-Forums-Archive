---
title: "Trouble Installing guest using libvirt"
date: 2010-08-02
forum: Virtualisation
---

### Post by QuinnHarris on 2010-08-02
I am unable to use virt-install or virt-manager to create a kvm guest.

I try the following
**sudo virt-install --connect qemu:///system -n xpsp2 -r 512 -f windows.qcow2 -s 12 -c /dev/cdrom --vnc --noautoconsole --os-type windows --os-variant winxp**

*and get this output*

Starting install...
Creating storage file win 100% |=========================|  12 GB    00:00     
ERROR    could not remove profile for 'libvirt-210d0515-2a42-7f79-29ea-4d10685f007b'
Domain installation may not have been
 successful.  If it was, you can restart your domain
 by running 'virsh start xpsp2'; otherwise, please
 restart your installation.
ERROR    could not remove profile for 'libvirt-210d0515-2a42-7f79-29ea-4d10685f007b'
Traceback (most recent call last):
  File "/usr/bin/virt-install", line 943, in <module>
    main()
  File "/usr/bin/virt-install", line 839, in main
    start_time, guest.start_install)
  File "/usr/bin/virt-install", line 894, in do_install
    dom = install_func(conscb, progresscb, wait=(not wait))
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 660, in start_install
    return self._do_install(consolecb, meter, removeOld, wait)
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 758, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 1097, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: could not remove profile for 'libvirt-210d0515-2a42-7f79-29ea-4d10685f007b'

*The libvirt daemon produces this output*
**sudo /usr/sbin/libvirtd -v**
14:49:29.898: error : qemudDomainLookupByName:3017 : Domain not found: no domain with matching name 'xpsp2'
14:49:30.249: error : qemudDomainLookupByUUID:2992 : Domain not found: no domain with matching uuid '210d0515-2a42-7f79-29ea-4d10685f007b'
14:49:30.277: error : qemudDomainLookupByName:3017 : Domain not found: no domain with matching name 'xpsp2'
14:49:30.509: error : qemudReadLogOutput:1347 : internal error Process exited while reading console log output
14:49:30.509: error : qemudWaitForMonitor:1536 : internal error unable to start guest: libvir: Security Labeling error : error calling aa_change_profile()

libvir: error : internal error '/usr/lib/libvirt/virt-aa-helper -R -u libvirt-210d0515-2a42-7f79-29ea-4d10685f007b' exited with non-zero status 1 and signal 0: virt-aa-helper: error: profile does not exist
libvir: Security Labeling error : could not remove profile for 'libvirt-210d0515-2a42-7f79-29ea-4d10685f007b'


*And the log file*
**cat /var/log/libvirt/qemu/xpsp2.log**
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin HOME=/home/quinn USER=root LOGNAME=root QEMU_AUDIO_DRV=none /usr/bin/kvm -S -M pc-0.12 -enable-kvm -m 512 -smp 1 -name xpsp2 -uuid 210d0515-2a42-7f79-29ea-4d10685f007b -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/xpsp2.monitor,server,nowait -monitor chardev:monitor -localtime -no-reboot -boot d -drive file=/var/log/libvirt/qemu/windows.qcow2,if=ide,index=0,format=raw -drive file=/dev/cdrom,if=ide,media=cdrom,index=2 -net nic,macaddr=52:54:00:1c:c5:46,vlan=0,name=nic.0 -net tap,fd=42,vlan=0,name=tap.0 -chardev pty,id=serial0 -serial chardev:serial0 -parallel none -usb -usbdevice tablet -vnc 127.0.0.1:0 -k en-us -vga cirrus 
libvir: Security Labeling error : error calling aa_change_profile()


I am new to libvirt but I doesn't make sense it would try and use virt-aa-helper to remove a profile that hasn't been created yet.  If I run the command again the profile UUID does change.

Any ideas,
Thanks

---

### Post by nutznboltz on 2011-03-03
deleted

---

