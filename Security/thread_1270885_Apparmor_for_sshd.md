---
title: "Apparmor for sshd"
date: 2009-09-20
forum: Security
---

### Post by Windows_ on 2009-09-20
Hello!

First:

I have the default /etc/apparmor.d/usr.sbin.sshd file on my ubuntu server.
But when I turn it on, I can't able make ssh connection to my server.

Second:

I've switched on the complain mode and then have made logprof. The lines below were added:

1) sys_resource
2) /etc/default/locale
3) /proc/1039/oom_adj (i've added the /proc/*/oom_adj. Is it OK?)
4) /proc/filesystems (is it normal for sshd?)
5) /var/run/motd 

I have some uncertainty for the first line, third and fourth.
Is anybody have tried to tune the sshd apparmor?
Can anybode consult me?

---

### Post by Sporkman on 2009-09-21
This is the usr.dbin.sshd I've built so far (not yet complete):

#include <tunables/global>

/usr/sbin/sshd flags=(complain) {
  #include <abstractions/base>

  capability setgid,
  capability setuid,
  capability sys_chroot,
  capability dac_override,
  network inet,
  network inet6,
  
  /dev/pts rw,
  /dev/tty rw,
  /etc/default/locale r,
  /etc/environment r,
  /etc/gai.conf r,
  /etc/hosts r,
  /etc/hosts.allow r,
  /etc/host.conf r,
  /etc/hosts.deny r,
  /etc/localtime r,
  /etc/nsswitch.conf r,
  /etc/passwd r,
  /etc/protocols r,
  /etc/resolv.conf r,
  /etc/security/limits.conf r,
  /etc/security/pam_env.conf r,
  /etc/security/pam_env.conf r,
  /etc/shadow r,
  /etc/ssh/moduli r,
  /etc/ssh/ssh_host_dsa_key r,
  /etc/ssh/ssh_host_rsa_key r,
  /etc/ssh/sshd_config r,
  /lib/ld-*.so rix,
  /proc/[0-9]*/fd/ r,
  /proc/[0-9]*/mounts r,
  /proc/[0-9]*/oom_adj rw,
  /usr/sbin/sshd mrix,
  /var/run/motd r,
  /var/run/sshd.pid w,
  /var/run/utmp krw,
}


...unfortunately, with this I run into this when giving it a spin:

[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/341205](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/341205)

---

