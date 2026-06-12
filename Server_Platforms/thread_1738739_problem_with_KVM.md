---
title: "problem with KVM"
date: 2011-04-25
forum: Server Platforms
---

### Post by lui on 2011-04-25
I use Ubuntu server 10.04 LTS as virtualization platform.

Actually running kernel 2.6.32-31-server #61-Ubuntu S

root@jupiter:~# uname -a
> Linux jupiter 2.6.32-31-server #61-Ubuntu SMP Fri Apr 8 19:44:42 UTC
2011 x86_64 GNU/Linux

We have on running one virtual
> root@jupiter:~# virsh list --all
 Id Name                 State
----------------------------------
  1 kvmtik.4safety.cz    running


I run script for create virtual system wrote

> root@jupiter:~# make-hestia.4safety.cz.sh
2011-04-24 21:13:25,613 ERROR   : ubuntu-kvm already exists
Traceback (most recent call last):
  File "/usr/bin/vmbuilder", line 24, in <module>
    cli.main()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/contrib/cli.py", line
81, in main
    raise VMBuilderUserError('%s already exists' % destdir)
VMBuilder.exception.VMBuilderUserError: ubuntu-kvm already exists
/usr/local/bin/make-hestia.4safety.cz.sh: line 29:
--libvirt=qemu:///system: No such file or directory

I try restart libvirt 

> root@jupiter:~# /etc/init.d/libvirt-bin restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service libvirt-bin restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart
libvirt-bin
libvirt-bin start/running, process 25202

and syslog wrote

> root@jupiter:~# tail -f /var/log/syslog
Apr 24 21:17:01 jupiter CRON[25189]: (root) CMD (   cd / && run-parts
--report /etc/cron.hourly)
Apr 24 21:17:58 jupiter libvirtd: 21:17:58.089: warning :
qemudDispatchSignalEvent:385 : Shutting down on signal 15
Apr 24 21:17:58 jupiter libvirtd: 21:17:58.617: error :
udevStrToLong_ui:73 : Failed to convert '008' to unsigned int#012
Apr 24 21:17:59 jupiter kernel: [106086.771154] lo: Disabled Privacy
Extensions

Than for your help.

---

