---
title: "Problem with vmbuilder on oneiric"
date: 2011-10-16
forum: Virtualisation
---

### Post by pyuill on 2011-10-16
I attempted to create a vm with python-vm-builder under 11.10 x64 but I keep getting the same failure no matter what suite, flavour or other option I choose. Any idea what I am doing wrong?
Thanks, Peter

peter@nimes:~$ sudo vmbuilder kvm ubuntu --suite oneiric --flavour virtual -o --libvirt qemu:///system --hostname vm1 --mirror [http://mirror.internode.on.net/pub/ubuntu/ubuntu](http://mirror.internode.on.net/pub/ubuntu/ubuntu)
2011-10-17 07:26:28,455 INFO    : Calling hook: preflight_check
2011-10-17 07:26:28,462 INFO    : Calling hook: set_defaults
2011-10-17 07:26:28,462 INFO    : Calling hook: bootstrap
2011-10-17 07:32:10,028 INFO    : Calling hook: configure_os
2011-10-17 07:32:34,477 INFO    : 
2011-10-17 07:32:34,478 INFO    : Current default time zone: 'Etc/UTC'
2011-10-17 07:32:34,481 INFO    : Local time is now:      Sun Oct 16 20:32:34 UTC 2011.
2011-10-17 07:32:34,481 INFO    : Universal Time is now:  Sun Oct 16 20:32:34 UTC 2011.
2011-10-17 07:32:34,481 INFO    : 
2011-10-17 07:32:46,448 INFO    : umount: /tmp/tmplvaN8e/dev: device is busy.
2011-10-17 07:32:46,448 INFO    :         (In some cases useful info about processes that use
2011-10-17 07:32:46,448 INFO    :          the device is found by lsof(8) or fuser(1))
2011-10-17 07:32:46,448 INFO    : Cleaning up
2011-10-17 07:32:46,448 ERROR   : Process (['umount', '/tmp/tmplvaN8e/dev']) returned 1. stdout: , stderr: umount: /tmp/tmplvaN8e/dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

Traceback (most recent call last):
  File "/usr/bin/vmbuilder", line 24, in <module>
    cli.main()
  File "/usr/lib/python2.7/dist-packages/VMBuilder/contrib/cli.py", line 216, in main
    distro.build_chroot()
  File "/usr/lib/python2.7/dist-packages/VMBuilder/distro.py", line 84, in build_chroot
    self.call_hooks('configure_os')
  File "/usr/lib/python2.7/dist-packages/VMBuilder/distro.py", line 67, in call_hooks
    call_hooks(self, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/VMBuilder/util.py", line 165, in call_hooks
    getattr(context, func, log_no_such_method)(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/VMBuilder/plugins/ubuntu/distro.py", line 155, in configure_os
    self.suite.unmount_dev()
  File "/usr/lib/python2.7/dist-packages/VMBuilder/plugins/ubuntu/dapper.py", line 118, in unmount_dev
    run_cmd('umount', '%s/dev' % self.context.chroot_dir)
  File "/usr/lib/python2.7/dist-packages/VMBuilder/util.py", line 120, in run_cmd
    raise VMBuilderException, "Process (%s) returned %d. stdout: %s, stderr: %s" % (args.__repr__(), status, mystdout.buf, mystderr.buf)
VMBuilder.exception.VMBuilderException: Process (['umount', '/tmp/tmplvaN8e/dev']) returned 1. stdout: , stderr: umount: /tmp/tmplvaN8e/dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

---

### Post by PhENTZ on 2011-11-02
I got the same problem.
It seems to be related to [https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/726790](https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/726790)
I posted a comment.

---

