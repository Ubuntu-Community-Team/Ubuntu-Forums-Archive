---
title: "Diskless Ubuntu Server login"
date: 2010-11-24
forum: Server Platforms
---

### Post by i386DX on 2010-11-24
I used [this]("https://help.ubuntu.com/community/DisklessUbuntuHowto") howto to setup a PXE boot environment.

The server contains a LUbuntu 10.10-installation
the client is Ubuntu 10.10 Server
(I didn't mix up those two...)

So, everything is going fine; the client gets an ip-adres, and boots over PXE. The login-prompt is shown.
Problem: I can't login. It seems my users are deleted (better not copied). Of course the system (client) works fine when I boot the system from it's harddrive.

The only thing I can guess, there going something wrong with:
> 
mount -t nfs -onolock 192.168.1.2:/nfsroot /mnt
cp -ax /. /mnt/.
cp -ax /dev/. /mnt/dev/.


first of all, I had to use 'sudo mount' otherwise I get 'only root can do that'. To make sure I could write to /mnt I chmod'ed 777 it.

During the first copy-command, I get some errors (but most files are successfull copied). I'm not sure this is normal. Also the second copy-command gives errors.

[quote=Copy 1]
@ubuntu:/mnt$ cp -ax /. /mnt/.
cp: cannot access `/./root': Permission denied
cp: cannot create special file `/mnt/././lib/udev/devices/loop0': Operation not permitted
cp: cannot create special file `/mnt/././lib/udev/devices/net/tun': Operation not permitted
cp: cannot create special file `/mnt/././lib/udev/devices/ppp': Operation not permitted
cp: cannot open `/./lib/ufw/user.rules' for reading: Permission denied
cp: cannot open `/./lib/ufw/user6.rules' for reading: Permission denied
cp: cannot open `/./home/lionel/.nano_history' for reading: Permission denied
cp: cannot create hard link `/mnt/././bin/dnsdomainname' to `/mnt/././bin/domainname': Operation not permitted
cp: cannot create hard link `/mnt/././bin/nisdomainname' to `/mnt/././bin/domainname': Operation not permitted
cp: cannot create hard link `/mnt/././bin/bunzip2' to `/mnt/././bin/bzip2': Operation not permitted
cp: cannot create hard link `/mnt/././bin/gunzip' to `/mnt/././bin/uncompress': Operation not permitted
cp: cannot create hard link `/mnt/././bin/bzcat' to `/mnt/././bin/bzip2': Operation not permitted
cp: cannot create hard link `/mnt/././bin/ypdomainname' to `/mnt/././bin/domainname': Operation not permitted
cp: cannot create hard link `/mnt/././sbin/fsck.ext4' to `/mnt/././sbin/fsck.ext4dev': Operation not permitted
cp: cannot create hard link `/mnt/././sbin/e2label' to `/mnt/././sbin/tune2fs': Operation not permitted
cp: cannot create hard link `/mnt/././sbin/fsck.ext3' to `/mnt/././sbin/fsck.ext4dev': Operation not permitted
cp: cannot create hard link `/mnt/././sbin/ifup' to `/mnt/././sbin/ifquery': Operation not permitted
cp: cannot create hard link `/mnt/././sbin/mkfs.ext2' to `/mnt/././sbin/mke2fs': Operation not permitted
cp: cannot create hard link `/mnt/././sbin/e2fsck' to `/mnt/././sbin/fsck.ext4dev': Operation not permitted
cp: cannot create hard link `/mnt/././sbin/fsck.ext2' to `/mnt/././sbin/fsck.ext4dev': Operation not permitted
cp: cannot create hard link `/mnt/././sbin/mkfs.ext4dev' to `/mnt/././sbin/mke2fs': Operation not permitted
cp: cannot create hard link `/mnt/././sbin/mkfs.ext3' to `/mnt/././sbin/mke2fs': Operation not permitted
cp: cannot create hard link `/mnt/././sbin/mkfs.ext4' to `/mnt/././sbin/mke2fs': Operation not permitted
cp: cannot create hard link `/mnt/././sbin/ifdown' to `/mnt/././sbin/ifquery': Operation not permitted
cp: cannot open `/./var/lib/dpkg/triggers/Lock' for reading: Permission denied
cp: cannot open `/./var/lib/dpkg/lock' for reading: Permission denied
cp: cannot open `/./var/lib/ureadahead/var.run.pack' for reading: Permission denied
cp: cannot open `/./var/lib/ureadahead/pack' for reading: Permission denied
cp: cannot access `/./var/lib/sudo': Permission denied
cp: cannot open `/./var/lib/mlocate/mlocate.db' for reading: Permission denied
cp: cannot open `/./var/lib/apt/lists/lock' for reading: Permission denied
cp: cannot open `/./var/lib/urandom/random-seed' for reading: Permission denied
cp: cannot open `/./var/log/apt/term.log' for reading: Permission denied
cp: cannot open `/./var/log/installer/syslog' for reading: Permission denied
cp: cannot open `/./var/log/installer/cdebconf/templates.dat' for reading: Permission denied
cp: cannot open `/./var/log/installer/cdebconf/questions.dat' for reading: Permission denied
cp: cannot open `/./var/log/installer/partman' for reading: Permission denied
cp: cannot access `/./var/spool/cron/crontabs': Permission denied
cp: cannot access `/./var/spool/cron/atspool': Permission denied
cp: cannot access `/./var/spool/cron/atjobs': Permission denied
cp: cannot open `/./var/cache/debconf/passwords.dat' for reading: Permission denied
cp: cannot open `/./var/cache/apt/archives/lock' for reading: Permission denied
cp: cannot access `/./var/cache/ldconfig': Permission denied
cp: cannot access `/./lost+found': Permission denied
cp: cannot open `/./etc/security/opasswd' for reading: Permission denied
cp: cannot open `/./etc/sudoers.d/README' for reading: Permission denied
cp: cannot access `/./etc/chatscripts': Permission denied
cp: cannot open `/./etc/apparmor.d/cache/usr.sbin.tcpdump' for reading: Permission denied
cp: cannot open `/./etc/apparmor.d/cache/sbin.dhclient3' for reading: Permission denied
cp: cannot open `/./etc/ssh/ssh_host_dsa_key' for reading: Permission denied
cp: cannot open `/./etc/ssh/ssh_host_rsa_key' for reading: Permission denied
cp: cannot open `/./etc/shadow' for reading: Permission denied
cp: cannot open `/./etc/sudoers' for reading: Permission denied
cp: cannot open `/./etc/fuse.conf' for reading: Permission denied
cp: cannot open `/./etc/.pwd.lock' for reading: Permission denied
cp: cannot access `/./etc/ssl/private': Permission denied
cp: cannot open `/./etc/ufw/after6.rules' for reading: Permission denied
cp: cannot open `/./etc/ufw/before6.rules' for reading: Permission denied
cp: cannot open `/./etc/ufw/before.rules' for reading: Permission denied
cp: cannot open `/./etc/ufw/after.rules' for reading: Permission denied
cp: cannot open `/./etc/at.deny' for reading: Permission denied
cp: cannot open `/./etc/shadow-' for reading: Permission denied
cp: cannot open `/./etc/gshadow-' for reading: Permission denied
cp: cannot open `/./etc/gshadow' for reading: Permission denied
cp: cannot open `/./etc/apt/secring.gpg' for reading: Permission denied
cp: cannot open `/./etc/apt/trustdb.gpg' for reading: Permission denied
cp: cannot open `/./etc/group-' for reading: Permission denied
cp: cannot access `/./etc/ppp/peers': Permission denied
cp: cannot open `/./etc/ppp/pap-secrets' for reading: Permission denied
cp: cannot open `/./etc/ppp/chap-secrets' for reading: Permission denied
cp: cannot open `/./etc/passwd-' for reading: Permission denied
cp: cannot create hard link `/mnt/././usr/bin/perlthanks' to `/mnt/././usr/bin/perlbug': Operation not permitted
cp: cannot create hard link `/mnt/././usr/bin/lockfile-remove' to `/mnt/././usr/bin/lockfile-check': Operation not permitted
cp: cannot create hard link `/mnt/././usr/bin/mail-touchlock' to `/mnt/././usr/bin/mail-lock': Operation not permitted
cp: cannot create hard link `/mnt/././usr/bin/s2p' to `/mnt/././usr/bin/psed': Operation not permitted
cp: cannot create hard link `/mnt/././usr/bin/c2ph' to `/mnt/././usr/bin/pstruct': Operation not permitted
cp: cannot create hard link `/mnt/././usr/bin/sudo' to `/mnt/././usr/bin/sudoedit': Operation not permitted
cp: cannot create hard link `/mnt/././usr/bin/lockfile-create' to `/mnt/././usr/bin/lockfile-check': Operation not permitted
cp: cannot create hard link `/mnt/././usr/bin/perl' to `/mnt/././usr/bin/perl5.10.1': Operation not permitted
cp: cannot create hard link `/mnt/././usr/bin/mail-unlock' to `/mnt/././usr/bin/mail-lock': Operation not permitted
cp: cannot create hard link `/mnt/././usr/bin/lockfile-touch' to `/mnt/././usr/bin/lockfile-check': Operation not permitted


...
...
...
[/quote]

[quote=Copy 2]
@ubuntu:/mnt$ cp -ax /dev/. /mnt/dev/.
cp: cannot create special file `/mnt/dev/././fb0': Operation not permitted
cp: cannot create special file `/mnt/dev/././dri/card0': Operation not permitted
cp: cannot create special file `/mnt/dev/././dri/controlD64': Operation not permitted
cp: cannot create special file `/mnt/dev/././parport0': Operation not permitted
cp: cannot create special file `/mnt/dev/././lp0': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcsa6': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcs6': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcsa5': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcs5': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcsa3': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcs3': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcsa4': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcs4': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcsa2': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcs2': Operation not permitted
cp: cannot create special file `/mnt/dev/././agpgart': Operation not permitted
cp: cannot create special file `/mnt/dev/././autofs': Operation not permitted
cp: cannot create special file `/mnt/dev/././cpu/microcode': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcsa7': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcs7': Operation not permitted
cp: cannot create special file `/mnt/dev/././sdb1': Operation not permitted
cp: cannot create special file `/mnt/dev/././sda': Operation not permitted
cp: cannot create special file `/mnt/dev/././sdb': Operation not permitted
cp: cannot create special file `/mnt/dev/././sg1': Operation not permitted
cp: cannot create special file `/mnt/dev/././bsg/4:0:0:0': Operation not permitted
cp: cannot create special file `/mnt/dev/././bsg/5:0:0:0': Operation not permitted
cp: cannot create special file `/mnt/dev/././sg0': Operation not permitted
cp: cannot create special file `/mnt/dev/././btrfs-control': Operation not permitted
cp: cannot create special file `/mnt/dev/././network_throughput': Operation not permitted
cp: cannot create special file `/mnt/dev/././network_latency': Operation not permitted
cp: cannot create special file `/mnt/dev/././cpu_dma_latency': Operation not permitted
cp: cannot create special file `/mnt/dev/././mapper/control': Operation not permitted
cp: cannot create special file `/mnt/dev/././rtc0': Operation not permitted
cp: cannot create special file `/mnt/dev/././uinput': Operation not permitted
cp: cannot create special file `/mnt/dev/././psaux': Operation not permitted
cp: cannot create special file `/mnt/dev/././input/event2': Operation not permitted
cp: cannot create special file `/mnt/dev/././input/event1': Operation not permitted
cp: cannot create special file `/mnt/dev/././input/event0': Operation not permitted
cp: cannot create special file `/mnt/dev/././input/mice': Operation not permitted
cp: cannot create special file `/mnt/dev/././usbmon7': Operation not permitted
cp: cannot create special file `/mnt/dev/././usbmon6': Operation not permitted
cp: cannot create special file `/mnt/dev/././usbmon5': Operation not permitted
cp: cannot create special file `/mnt/dev/././usbmon4': Operation not permitted
cp: cannot create special file `/mnt/dev/././usbmon3': Operation not permitted
cp: cannot create special file `/mnt/dev/././usbmon2': Operation not permitted
cp: cannot create special file `/mnt/dev/././bus/usb/007/001': Operation not permitted
cp: cannot create special file `/mnt/dev/././bus/usb/006/001': Operation not permitted
cp: cannot create special file `/mnt/dev/././bus/usb/005/001': Operation not permitted
cp: cannot create special file `/mnt/dev/././bus/usb/004/001': Operation not permitted
cp: cannot create special file `/mnt/dev/././bus/usb/003/001': Operation not permitted
cp: cannot create special file `/mnt/dev/././bus/usb/002/003': Operation not permitted
cp: cannot create special file `/mnt/dev/././bus/usb/002/002': Operation not permitted
cp: cannot create special file `/mnt/dev/././bus/usb/002/001': Operation not permitted
cp: cannot create special file `/mnt/dev/././bus/usb/001/001': Operation not permitted
cp: cannot create special file `/mnt/dev/././usbmon1': Operation not permitted
cp: cannot create special file `/mnt/dev/././usbmon0': Operation not permitted
cp: cannot create special file `/mnt/dev/././net/tun': Operation not permitted
cp: cannot create special file `/mnt/dev/././ppp': Operation not permitted
cp: cannot create special file `/mnt/dev/././pktcdvd/control': Operation not permitted
cp: cannot create special file `/mnt/dev/././loop7': Operation not permitted
cp: cannot create special file `/mnt/dev/././loop6': Operation not permitted
cp: cannot create special file `/mnt/dev/././loop5': Operation not permitted
cp: cannot create special file `/mnt/dev/././loop4': Operation not permitted
cp: cannot create special file `/mnt/dev/././loop3': Operation not permitted
cp: cannot create special file `/mnt/dev/././loop2': Operation not permitted
cp: cannot create special file `/mnt/dev/././loop1': Operation not permitted
cp: cannot create special file `/mnt/dev/././loop0': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram15': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram14': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram13': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram12': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram11': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram10': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram9': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram8': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram7': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram6': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram5': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram4': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram3': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram2': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram1': Operation not permitted
cp: cannot create special file `/mnt/dev/././ram0': Operation not permitted
cp: cannot create special file `/mnt/dev/././ttyS1': Operation not permitted
cp: cannot create special file `/mnt/dev/././ttyS0': Operation not permitted
cp: cannot create special file `/mnt/dev/././ttyS3': Operation not permitted
cp: cannot create special file `/mnt/dev/././ttyS2': Operation not permitted
cp: cannot create special file `/mnt/dev/././hpet': Operation not permitted
cp: cannot create special file `/mnt/dev/././ptmx': Operation not permitted
cp: cannot create special file `/mnt/dev/././fuse': Operation not permitted
cp: cannot create special file `/mnt/dev/././ecryptfs': Operation not permitted
cp: cannot create special file `/mnt/dev/././snapshot': Operation not permitted
cp: cannot create special file `/mnt/dev/././mcelog': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty63': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty62': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty61': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty60': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty59': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty58': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty57': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty56': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty55': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty54': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty53': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty52': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty51': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty50': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty49': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty48': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty47': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty46': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty45': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty44': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty43': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty42': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty41': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty40': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty39': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty38': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty37': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty36': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty35': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty34': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty33': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty32': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty31': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty30': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty29': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty28': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty27': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty26': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty25': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty24': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty23': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty22': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty21': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty20': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty19': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty18': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty17': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty16': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty15': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty14': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty13': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty12': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty11': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty10': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty9': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty8': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty7': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty6': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty5': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty4': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty3': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty2': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty1': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcsa1': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcs1': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcsa': Operation not permitted
cp: cannot create special file `/mnt/dev/././vcs': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty0': Operation not permitted
cp: cannot create special file `/mnt/dev/././console': Operation not permitted
cp: cannot create special file `/mnt/dev/././tty': Operation not permitted
cp: cannot create special file `/mnt/dev/././oldmem': Operation not permitted
cp: cannot create special file `/mnt/dev/././kmsg': Operation not permitted
cp: cannot create special file `/mnt/dev/././urandom': Operation not permitted
cp: cannot create special file `/mnt/dev/././random': Operation not permitted
cp: cannot create special file `/mnt/dev/././full': Operation not permitted
cp: cannot create special file `/mnt/dev/././zero': Operation not permitted
cp: cannot create special file `/mnt/dev/././port': Operation not permitted
cp: cannot create special file `/mnt/dev/././null': Operation not permitted
cp: cannot create special file `/mnt/dev/././mem': Operation not permitted
cp: cannot create special file `/mnt/dev/././rfkill': Operation not permitted
cp: cannot create special file `/mnt/dev/././vga_arbiter': Operation not permitted

[/quote]


Anyone an idea what's going wrong?

---

### Post by spacejanitor on 2011-03-27
I'm in the exact same boat... anybody know why these operations are not permitted even when cp'ing with sudo?

---

