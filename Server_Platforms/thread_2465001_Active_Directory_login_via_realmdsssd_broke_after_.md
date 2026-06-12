---
title: "Active Directory login via realmd/sssd broke after updating to 2.2.3-3ubuntu0.6"
date: 2021-07-18
forum: Server Platforms
---

### Post by Gholam on 2021-07-18
I've got a number of Ubuntu 20.04 LTS servers joined to Windows Active Directory via this procedure: [https://www.server-world.info/en/note?os=Ubuntu_20.04&p=realmd](https://www.server-world.info/en/note?os=Ubuntu_20.04&p=realmd)

Apologies if I'm doing something obviously dumb, as most of my time is spent in Windows servers, and I only occasionally dabble with Linux.

Over this weekend, I ran a round of updates (simple sudo apt upgrade, then reboot), and all of them lost the ability to log in via AD accounts. I restored a couple from backup, and they returned to operation. Looking at the list of packages that are candidates to be upgraded in a restored server, I found the following:

```
alsa-ucm-conf/focal-updates 1.2.2-1ubuntu0.8 all [upgradable from: 1.2.2-1ubuntu0.7]
apt-transport-https/focal-updates 2.0.6 all [upgradable from: 2.0.5]
apt-utils/focal-updates 2.0.6 amd64 [upgradable from: 2.0.5]
apt/focal-updates 2.0.6 amd64 [upgradable from: 2.0.5]
cloud-init/focal-updates 21.2-3-g899bfaa9-0ubuntu2~20.04.1 all [upgradable from: 21.1-19-gbad84ad4-0ubuntu1~20.04.2]
initramfs-tools-bin/focal-updates 0.136ubuntu6.6 amd64 [upgradable from: 0.136ubuntu6.5]
initramfs-tools-core/focal-updates 0.136ubuntu6.6 all [upgradable from: 0.136ubuntu6.5]
initramfs-tools/focal-updates 0.136ubuntu6.6 all [upgradable from: 0.136ubuntu6.5]
libapt-pkg6.0/focal-updates 2.0.6 amd64 [upgradable from: 2.0.5]
libipa-hbac0/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
libnss-sss/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
libnss-systemd/focal-updates 245.4-4ubuntu3.7 amd64 [upgradable from: 245.4-4ubuntu3.6]
libpam-sss/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
libpam-systemd/focal-updates 245.4-4ubuntu3.7 amd64 [upgradable from: 245.4-4ubuntu3.6]
libprocps8/focal-updates 2:3.3.16-1ubuntu2.2 amd64 [upgradable from: 2:3.3.16-1ubuntu2.1]
libsmbclient/focal-updates 2:4.11.6+dfsg-0ubuntu1.9 amd64 [upgradable from: 2:4.11.6+dfsg-0ubuntu1.8]
libsss-certmap0/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
libsss-idmap0/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
libsss-nss-idmap0/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
libsss-sudo/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
libsystemd0/focal-updates 245.4-4ubuntu3.7 amd64 [upgradable from: 245.4-4ubuntu3.6]
libudev1/focal-updates 245.4-4ubuntu3.7 amd64 [upgradable from: 245.4-4ubuntu3.6]
libwbclient0/focal-updates 2:4.11.6+dfsg-0ubuntu1.9 amd64 [upgradable from: 2:4.11.6+dfsg-0ubuntu1.8]
libxml2/focal 2.9.12+dfsg-0+ubuntu20.04.1+deb.sury.org+1 amd64 [upgradable from: 2.9.10+dfsg-5+ubuntu20.04.1+deb.sury.org+3]
linux-base/focal-updates 4.5ubuntu3.6 all [upgradable from: 4.5ubuntu3.1]
linux-firmware/focal-updates 1.187.15 all [upgradable from: 1.187.14]
nfs-common/focal-updates 1:1.3.4-2.5ubuntu3.4 amd64 [upgradable from: 1:1.3.4-2.5ubuntu3.3]
php-common/focal 2:84+ubuntu20.04.1+deb.sury.org+1 all [upgradable from: 2:82+ubuntu20.04.1+deb.sury.org+1]
php-mbstring/focal 2:8.0+84+ubuntu20.04.1+deb.sury.org+1 all [upgradable from: 2:8.0+82+ubuntu20.04.1+deb.sury.org+1]
php7.2/focal 7.2.34-23+ubuntu20.04.1+deb.sury.org+1 all [upgradable from: 7.2.34-22+ubuntu20.04.1+deb.sury.org+1]
procps/focal-updates 2:3.3.16-1ubuntu2.2 amd64 [upgradable from: 2:3.3.16-1ubuntu2.1]
python3-samba/focal-updates 2:4.11.6+dfsg-0ubuntu1.9 amd64 [upgradable from: 2:4.11.6+dfsg-0ubuntu1.8]
python3-sss/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
samba-common-bin/focal-updates 2:4.11.6+dfsg-0ubuntu1.9 amd64 [upgradable from: 2:4.11.6+dfsg-0ubuntu1.8]
samba-common/focal-updates 2:4.11.6+dfsg-0ubuntu1.9 all [upgradable from: 2:4.11.6+dfsg-0ubuntu1.8]
samba-dsdb-modules/focal-updates 2:4.11.6+dfsg-0ubuntu1.9 amd64 [upgradable from: 2:4.11.6+dfsg-0ubuntu1.8]
samba-libs/focal-updates 2:4.11.6+dfsg-0ubuntu1.9 amd64 [upgradable from: 2:4.11.6+dfsg-0ubuntu1.8]
sssd-ad-common/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
sssd-ad/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
sssd-common/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
sssd-ipa/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
sssd-krb5-common/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
sssd-krb5/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
sssd-ldap/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
sssd-proxy/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
sssd-tools/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
sssd/focal-updates 2.2.3-3ubuntu0.6 amd64 [upgradable from: 2.2.3-3ubuntu0.4]
systemd-sysv/focal-updates 245.4-4ubuntu3.7 amd64 [upgradable from: 245.4-4ubuntu3.6]
systemd-timesyncd/focal-updates 245.4-4ubuntu3.7 amd64 [upgradable from: 245.4-4ubuntu3.6]
systemd/focal-updates 245.4-4ubuntu3.7 amd64 [upgradable from: 245.4-4ubuntu3.6]
ubuntu-advantage-tools/focal-updates 27.1~20.04.1 amd64 [upgradable from: 27.0.2~20.04.1]
udev/focal-updates 245.4-4ubuntu3.7 amd64 [upgradable from: 245.4-4ubuntu3.6]

```
However, trying to manually downgrade sssd to 2.2.3-3ubuntu0.4, I got an error:

```
sudo apt install sssd=2.2.3-3ubuntu0.4   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '2.2.3-3ubuntu0.4' for 'sssd' was not found
```

apt policy sssd showed me this:

```
sssd:
  Installed: 2.2.3-3ubuntu0.6
  Candidate: 2.2.3-3ubuntu0.6
  Version table:
 *** 2.2.3-3ubuntu0.6 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.2.3-3ubuntu0.1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/main amd64 Packages
     2.2.3-3 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal/main amd64 Packages
```

So running the following got me back online:
```
sudo apt install sssd=2.2.3-3ubuntu0.1 sssd-ad=2.2.3-3ubuntu0.1 python3-sss=2.2.3-3ubuntu0.1 sssd-common=2.2.3-3ubuntu0.1 sssd-ipa=2.2.3-3ubuntu0.1 sssd-krb5=2.2.3-3ubuntu0.1 sssd-ldap=2.2.3-3ubuntu0.1 sssd-proxy=2.2.3-3ubuntu0.1 libsss-idmap0=2.2.3-3ubuntu0.1 sssd-ad-common=2.2.3-3ubuntu0.1 sssd-krb5-common=2.2.3-3ubuntu0.1 libipa-hbac0=2.2.3-3ubuntu0.1 -y --allow-downgrades

```
However, next time I update the servers, I imagine sssd will break again. Looking at /var/log/auth.log on a machine that is running sssd-2.2.3-3ubuntu0.6, I can see this:

```
Jul 18 05:43:00 server sshd[88633]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.187.1  user=aduser
Jul 18 05:43:00 server sshd[88633]: pam_sss(sshd:auth): authentication success; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.187.1 user=aduser
Jul 18 05:43:00 server sshd[88633]: pam_sss(sshd:account): Access denied for user aduser: 6 (Permission denied)
Jul 18 05:43:00 server sshd[88633]: Failed password for aduser from 192.168.187.1 port 53472 ssh2
Jul 18 05:43:00 server sshd[88633]: fatal: Access denied for user aduser by PAM account configuration [preauth]

```
If I tail all the logs under /var/log (tail -f /var/log/*.log) while trying to log in over SSH with an AD account, I get a few more messages, but nothing helpful:

==> /var/log/auth.log <==
```
Jul 18 05:51:22 server sshd[88935]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.187.1  user=aduser

```
==> /var/log/kern.log <==
```
Jul 18 05:51:22 server kernel: [187280.438839] kauditd_printk_skb: 10 callbacks suppressed
Jul 18 05:51:22 server kernel: [187280.438840] audit: type=1400 audit(1626587482.535:2027): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/proc/88935/cmdline" pid=951 comm="sssd_pam" requested_mask="r" denied_mask="r" fsuid=0 ouid=0


```==> /var/log/auth.log <==
```
Jul 18 05:51:22 server sshd[88935]: pam_sss(sshd:auth): authentication success; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.187.1 user=aduser

```
==> /var/log/kern.log <==
```
Jul 18 05:51:22 server kernel: [187280.529942] audit: type=1400 audit(1626587482.627:2028): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/run/samba/gencache.tdb" pid=88940 comm="gpo_child" requested_mask="wrc" denied_mask="wrc" fsuid=0 ouid=0
Jul 18 05:51:22 server kernel: [187280.529945] audit: type=1400 audit(1626587482.627:2029): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/run/samba/gencache.tdb" pid=88940 comm="gpo_child" requested_mask="wk" denied_mask="wk" fsuid=0 ouid=0
Jul 18 05:51:22 server kernel: [187280.550266] audit: type=1400 audit(1626587482.647:2030): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/dev/urandom" pid=88940 comm="gpo_child" requested_mask="wc" denied_mask="wc" fsuid=0 ouid=0
Jul 18 05:51:22 server kernel: [187280.556980] audit: type=1400 audit(1626587482.655:2031): apparmor="ALLOWED" operation="mknod" profile="/usr/sbin/sssd" name="/var/lib/sss/gpo_cache/domain.local/Policies/{D2D135E5-A470-43B5-9B21-2209724FB46A}/GPT.INI0taiqo" pid=88940 comm="gpo_child" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
Jul 18 05:51:22 server kernel: [187280.556999] audit: type=1400 audit(1626587482.655:2032): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/var/lib/sss/gpo_cache/domain.local/Policies/{D2D135E5-A470-43B5-9B21-2209724FB46A}/GPT.INI0taiqo" pid=88940 comm="gpo_child" requested_mask="wrc" denied_mask="wrc" fsuid=0 ouid=0
Jul 18 05:51:22 server kernel: [187280.557021] audit: type=1400 audit(1626587482.655:2033): apparmor="ALLOWED" operation="chmod" profile="/usr/sbin/sssd" name="/var/lib/sss/gpo_cache/domain.local/Policies/{D2D135E5-A470-43B5-9B21-2209724FB46A}/GPT.INI0taiqo" pid=88940 comm="gpo_child" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Jul 18 05:51:22 server kernel: [187280.557032] audit: type=1400 audit(1626587482.655:2034): apparmor="ALLOWED" operation="rename_src" profile="/usr/sbin/sssd" name="/var/lib/sss/gpo_cache/domain.local/Policies/{D2D135E5-A470-43B5-9B21-2209724FB46A}/GPT.INI0taiqo" pid=88940 comm="gpo_child" requested_mask="wrd" denied_mask="wrd" fsuid=0 ouid=0
Jul 18 05:51:22 server kernel: [187280.557035] audit: type=1400 audit(1626587482.655:2035): apparmor="ALLOWED" operation="rename_dest" profile="/usr/sbin/sssd" name="/var/lib/sss/gpo_cache/domain.local/Policies/{D2D135E5-A470-43B5-9B21-2209724FB46A}/GPT.INI" pid=88940 comm="gpo_child" requested_mask="wc" denied_mask="wc" fsuid=0 ouid=0
Jul 18 05:51:22 server kernel: [187280.557418] audit: type=1400 audit(1626587482.655:2036): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/var/lib/sss/gpo_cache/domain.local/Policies/{D2D135E5-A470-43B5-9B21-2209724FB46A}/GPT.INI" pid=88940 comm="gpo_child" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

```
==> /var/log/auth.log <==
```
Jul 18 05:51:22 server sshd[88935]: pam_sss(sshd:account): Access denied for user aduser: 6 (Permission denied)
Jul 18 05:51:22 server sshd[88935]: Failed password for aduser from 192.168.187.1 port 51729 ssh2
Jul 18 05:51:22 server sshd[88935]: fatal: Access denied for user aduser by PAM account configuration [preauth]

```

Where should I look to get more information on these failures in order to get AD integration working with the current and future versions of sssd?

Edit: never mind, found this: [https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/1934997](https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/1934997)

---

### Post by ajgreeny on 2021-07-18
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

