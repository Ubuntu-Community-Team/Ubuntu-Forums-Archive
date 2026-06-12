---
title: "fai setup Problem"
date: 2008-02-19
forum: Server Platforms
---

### Post by lohchab on 2008-02-19
I am trying to configure fai in our department lab for installing
debian etch-r2(on clients) from a ubuntu (gutsy gibbon).
But i cant able to do it....
Can any body help me on this.

i had configured dhcp3-server,vsftp,pxe boot and a local ftp repositries for debian. which can install a debian system fully.
but i want to do it fully automatically. thats why i am using FAI(fully automatic installation).
here is the output for fai-setup:


user@myServer:~$ sudo fai-setup
Creating FAI nfsroot in /srv/fai/nfsroot/live/filesystem.dir.
By default it needs more than 330 MBytes disk space.
This may take a long time.
/srv/fai/nfsroot/live/filesystem.dir already exists. Removing /srv/fai/nfsroot/live/filesystem.dir
Creating base system using debootstrap version 1.0.7~gutsy1
Calling debootstrap etch /srv/fai/nfsroot/live/filesystem.dir [ftp://addres/to/debian/ftp/repo](ftp://addres/to/debian/ftp/repo)
Creating base.tgz
Upgrading /srv/fai/nfsroot/live/filesystem.dir
Making a key pair for cfengine, please wait, this could take a minute...
Writing private key to /var/lib/cfengine2/ppkeys/localhost.priv
Writing public key to /var/lib/cfengine2/ppkeys/localhost.pub
install_packages: reading config files from directory /etc/fai
***WARNING: These unknown packages are removed from the installation list: linux-image-generic live-initramfs
Adding additional packages to /srv/fai/nfsroot/live/filesystem.dir:
fai-nfsroot module-init-tools dhcp3-client ssh rdate lshw portmap bootpc rsync lftp rsh-client less dump reiserfsprogs ext2resize usbutils hwinfo psmisc pciutils hdparm smartmontools parted mdadm lvm2 dnsutils ntpdate dosfstools cvs jove xfsprogs xfsdump sysutils dialog discover mdetect console-tools console-common expect iproute udev subversion sysvinit upstart- cfengine2 libapt-pkg-perl grub lilo read-edid
install_packages: reading config files from directory /etc/fai
***WARNING: These unknown packages are removed from the installation list: linux-image-generic live-initramfs
Extracting templates from packages: 100%
Looking for keymap to install:
NONE
Looking for keymap to install:
NONE
Backing up any LVM2 metadata that may exist...done.
/sys/class/net/ is not available, persistent interface names not saved.
Checking available versions of rmt, updating links in /etc/alternatives ...
(You may modify the symlinks there yourself if desired - see `man ln'.)
Updating rmt (/usr/sbin/rmt) to point to /usr/sbin/rmt-dump.
Updating rmt.8.gz (/usr/share/man/man8/rmt.8.gz) to point to /usr/share/man/man8/rmt-dump.8.gz.
W: mdadm: failed to load MD subsystem.
Generating array device nodes... done.
Generating mdadm.conf... done (failed to scan arrays; /proc probably not mounted).
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
`/etc/fai/apt' -> `/srv/fai/nfsroot/live/filesystem.dir/etc/fai/apt'
`/etc/fai/apt/sources.list' -> `/srv/fai/nfsroot/live/filesystem.dir/etc/fai/apt/sources.list'
`/etc/fai/apt/sources.list~' -> `/srv/fai/nfsroot/live/filesystem.dir/etc/fai/apt/sources.list~'
`/etc/fai/fai.conf' -> `/srv/fai/nfsroot/live/filesystem.dir/etc/fai/fai.conf'
`/etc/fai/fai.conf~' -> `/srv/fai/nfsroot/live/filesystem.dir/etc/fai/fai.conf~'
`/etc/fai/make-fai-nfsroot.conf' -> `/srv/fai/nfsroot/live/filesystem.dir/etc/fai/make-fai-nfsroot.conf'
`/etc/fai/make-fai-nfsroot.conf~' -> `/srv/fai/nfsroot/live/filesystem.dir/etc/fai/make-fai-nfsroot.conf~'
`/etc/fai/menu.lst' -> `/srv/fai/nfsroot/live/filesystem.dir/etc/fai/menu.lst'
`/etc/fai/NFSROOT' -> `/srv/fai/nfsroot/live/filesystem.dir/etc/fai/NFSROOT'
`/etc/fai/NFSROOT~' -> `/srv/fai/nfsroot/live/filesystem.dir/etc/fai/NFSROOT~'
Shadow passwords are now on.
cp: cannot stat `/srv/fai/nfsroot/live/filesystem.dir/boot/vmlinuz-*': No such file or directory
Aborting
Removing `local diversion of /sbin/discover-modprobe to /sbin/discover-modprobe.distrib'



>>>>>>>>>>>>>>>>>>>>>>>>>>.
Here as i think line which are three ***ed are important.
But i cant manage to solve it.

Can any body help me on this.
Thnx in advance

---

