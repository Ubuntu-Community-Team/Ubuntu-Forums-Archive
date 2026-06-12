---
title: "Stripped down server for QEMU KVM"
date: 2020-02-15
forum: Server Platforms
---

### Post by LHammonds on 2020-02-15
Has anyone compiled a list of packages that are safe to remove from a standard install for the purpose of running the machine as a KVM host?

LHammonds

---

### Post by TheFu on 2020-02-16
I haven't.  Ubuntu Server is pretty bloated.  I've removed a number of packages just to see them added back by Canonical's default use of --install-recommended in apt and apt-get.  Everyone has a different level of comfort with stripped down installs.  Things that I think are completely useless are mandatory for others and vice versa.   nano is useless.  bridge-utils, cron, at, rdiff-backup, rsync, ssh-server and postfix are mandatory.   libvirt is mandatory to me, but KVM purists might want to manually create and run their VMs.  I don't want systemd-resolv* or resolvconf or dnsmasq on the system, but Canonical thinks one of those is mandatory and will often put them all back.  Don't get me started about Canonical's automatic daily package repo update scripts.

I suppose, if this were something I needed, a minimal server install using the alternate installer is where I'd begin.  Might check out what MAAS installs, but with all the Juju, lxd, zfs stuff, I'd bet that would be 2x the number of packages actually needed.

Just depends.

---

### Post by LHammonds on 2020-02-25
My initial jump into KVM will be with a standard install of Ubuntu Server 18.04.4 LTS but I will eventually look at what packages are installed that can be removed and automate the process.

Here is a list of the 506 packages installed by default (OpenSSH is a must):

```
accountsservice/bionic,now 0.6.45-1ubuntu1 amd64 [installed]
acl/bionic,now 2.2.52-3build1 amd64 [installed]
acpid/bionic,now 1:2.0.28-1ubuntu1 amd64 [installed]
adduser/bionic,bionic,now 3.116ubuntu1 all [installed]
amd64-microcode/bionic-updates,bionic-security,now 3.20191021.1+really3.20181128.1~ubuntu0.18.04.1 amd64 [installed,automatic]
apparmor/bionic-updates,bionic-security,now 2.12-4ubuntu5.1 amd64 [installed]
apport/bionic-updates,bionic-updates,now 2.20.9-0ubuntu7.11 all [installed]
apport-symptoms/bionic,bionic,now 0.20 all [installed]
apt/bionic-updates,now 1.6.12 amd64 [installed]
apt-utils/bionic-updates,now 1.6.12 amd64 [installed]
at/bionic,now 3.1.20-3.1ubuntu2 amd64 [installed]
base-files/bionic-updates,now 10.1ubuntu2.8 amd64 [installed]
base-passwd/bionic,now 3.5.44 amd64 [installed,automatic]
bash/bionic-updates,now 4.4.18-2ubuntu1.2 amd64 [installed]
bash-completion/bionic,bionic,now 1:2.8-1ubuntu1 all [installed]
bc/bionic,now 1.07.1-2 amd64 [installed]
bcache-tools/bionic,now 1.0.8-2build1 amd64 [installed]
bind9-host/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
bsdmainutils/bionic,now 11.1.2ubuntu1 amd64 [installed]
bsdutils/bionic-updates,now 1:2.31.1-0.4ubuntu3.5 amd64 [installed]
btrfs-progs/bionic,now 4.15.1-1build1 amd64 [installed]
btrfs-tools/bionic,now 4.15.1-1build1 amd64 [installed]
busybox-initramfs/bionic-updates,bionic-security,now 1:1.27.2-2ubuntu3.2 amd64 [installed]
busybox-static/bionic-updates,bionic-security,now 1:1.27.2-2ubuntu3.2 amd64 [installed]
byobu/bionic,bionic,now 5.125-0ubuntu1 all [installed]
bzip2/bionic-updates,bionic-security,now 1.0.6-8.1ubuntu0.2 amd64 [installed,automatic]
ca-certificates/bionic,bionic,bionic-updates,bionic-updates,now 20180409 all [installed]
cloud-guest-utils/bionic,bionic,now 0.30-0ubuntu5 all [installed]
cloud-initramfs-copymods/bionic-updates,bionic-updates,now 0.40ubuntu1.1 all [installed]
cloud-initramfs-dyn-netconf/bionic-updates,bionic-updates,now 0.40ubuntu1.1 all [installed]
command-not-found/bionic-updates,bionic-updates,now 18.04.5 all [installed]
command-not-found-data/bionic-updates,now 18.04.5 amd64 [installed]
console-setup/bionic-updates,bionic-updates,now 1.178ubuntu2.9 all [installed,automatic]
console-setup-linux/bionic-updates,bionic-updates,now 1.178ubuntu2.9 all [installed,automatic]
coreutils/bionic,now 8.28-1ubuntu1 amd64 [installed]
cpio/bionic-updates,bionic-security,now 2.12+dfsg-6ubuntu0.18.04.1 amd64 [installed]
crda/bionic,now 3.18-1build1 amd64 [installed,automatic]
cron/bionic,now 3.0pl1-128.1ubuntu1 amd64 [installed,automatic]
cryptsetup/bionic-updates,now 2:2.0.2-1ubuntu1.1 amd64 [installed]
cryptsetup-bin/bionic-updates,now 2:2.0.2-1ubuntu1.1 amd64 [installed]
curl/bionic-updates,bionic-security,now 7.58.0-2ubuntu3.8 amd64 [installed]
dash/bionic,now 0.5.8-2.10 amd64 [installed]
dbus/bionic-updates,bionic-security,now 1.12.2-1ubuntu1.1 amd64 [installed]
debconf/bionic-updates,bionic-updates,now 1.5.66ubuntu1 all [installed]
debconf-i18n/bionic-updates,bionic-updates,now 1.5.66ubuntu1 all [installed]
debianutils/bionic,now 4.8.4 amd64 [installed,automatic]
diffutils/bionic,now 1:3.6-1 amd64 [installed]
dirmngr/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
distro-info-data/bionic-updates,bionic-updates,bionic-security,bionic-security,now 0.37ubuntu0.6 all [installed,automatic]
dmeventd/bionic-updates,now 2:1.02.145-4.1ubuntu3.18.04.2 amd64 [installed]
dmidecode/bionic-updates,now 3.1-1ubuntu0.1 amd64 [installed]
dmsetup/bionic-updates,now 2:1.02.145-4.1ubuntu3.18.04.2 amd64 [installed]
dns-root-data/bionic,bionic,now 2018013001 all [installed]
dnsmasq-base/bionic,now 2.79-1 amd64 [installed]
dnsutils/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
dosfstools/bionic,now 4.1-1 amd64 [installed]
dpkg/bionic-updates,now 1.19.0.5ubuntu2.3 amd64 [installed]
e2fsprogs/bionic-updates,bionic-security,now 1.44.1-1ubuntu1.3 amd64 [installed]
ebtables/bionic-updates,now 2.0.10.4-3.5ubuntu2.18.04.3 amd64 [installed]
ed/bionic,now 1.10-2.1 amd64 [installed]
eject/bionic,now 2.1.5+deb1+cvs20081104-13.2 amd64 [installed]
ethtool/bionic,now 1:4.15-0ubuntu1 amd64 [installed]
fdisk/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
file/bionic-updates,bionic-security,now 1:5.32-2ubuntu0.3 amd64 [installed,automatic]
findutils/bionic,now 4.6.0+git+20170828-2 amd64 [installed]
fonts-ubuntu-console/bionic,bionic,now 0.83-2 all [installed]
friendly-recovery/bionic-updates,bionic-updates,now 0.2.38ubuntu1.1 all [installed]
ftp/bionic,now 0.17-34 amd64 [installed]
fuse/bionic,now 2.9.7-1ubuntu1 amd64 [installed]
gawk/bionic,now 1:4.1.4+dfsg-1build1 amd64 [installed]
gcc-8-base/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed]
geoip-database/bionic,bionic,now 20180315-1 all [installed]
gettext-base/bionic-updates,bionic-security,now 0.19.8.1-6ubuntu0.3 amd64 [installed]
gir1.2-glib-2.0/bionic,now 1.56.1-1 amd64 [installed,automatic]
git/bionic-updates,bionic-security,now 1:2.17.1-1ubuntu0.5 amd64 [installed]
git-man/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1:2.17.1-1ubuntu0.5 all [installed]
gnupg/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gnupg-l10n/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2.2.4-1ubuntu1.2 all [installed]
gnupg-utils/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpg/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpg-agent/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpg-wks-client/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpg-wks-server/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpgconf/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpgsm/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpgv/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
grep/bionic-updates,now 3.1-2build1 amd64 [installed]
groff-base/bionic,now 1.22.3-10 amd64 [installed]
grub-common/bionic-updates,now 2.02-2ubuntu8.14 amd64 [installed]
grub-gfxpayload-lists/bionic,now 0.7 amd64 [installed,automatic]
grub-legacy-ec2/bionic,bionic,now 1:1 all [installed]
grub-pc/bionic-updates,now 2.02-2ubuntu8.14 amd64 [installed]
grub-pc-bin/bionic-updates,now 2.02-2ubuntu8.14 amd64 [installed,automatic]
grub2-common/bionic-updates,now 2.02-2ubuntu8.14 amd64 [installed,automatic]
gzip/bionic,now 1.6-5ubuntu1 amd64 [installed]
hdparm/bionic,now 9.54+ds-1 amd64 [installed]
hostname/bionic,now 3.20 amd64 [installed]
htop/bionic,now 2.1.0-3 amd64 [installed]
info/bionic,now 6.5.0.dfsg.1-2 amd64 [installed]
init/bionic,now 1.51 amd64 [installed]
init-system-helpers/bionic,bionic,now 1.51 all [installed]
initramfs-tools/bionic-updates,bionic-updates,now 0.130ubuntu3.9 all [installed]
initramfs-tools-bin/bionic-updates,now 0.130ubuntu3.9 amd64 [installed]
initramfs-tools-core/bionic-updates,bionic-updates,now 0.130ubuntu3.9 all [installed]
install-info/bionic,now 6.5.0.dfsg.1-2 amd64 [installed]
installation-report/bionic,bionic,now 2.62ubuntu1 all [installed]
intel-microcode/bionic-updates,bionic-security,now 3.20191115.1ubuntu0.18.04.2 amd64 [installed,automatic]
iproute2/bionic,now 4.15.0-2ubuntu1 amd64 [installed,automatic]
iptables/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
iputils-ping/bionic-updates,now 3:20161105-1ubuntu3 amd64 [installed,automatic]
iputils-tracepath/bionic-updates,now 3:20161105-1ubuntu3 amd64 [installed]
irqbalance/bionic-updates,now 1.3.0-0.1ubuntu0.18.04.1 amd64 [installed]
isc-dhcp-client/bionic-updates,bionic-security,now 4.3.5-3ubuntu7.1 amd64 [installed,automatic]
isc-dhcp-common/bionic-updates,bionic-security,now 4.3.5-3ubuntu7.1 amd64 [installed,automatic]
iso-codes/bionic,bionic,now 3.79-1 all [installed]
iucode-tool/bionic,now 2.3.1-1 amd64 [installed,automatic]
iw/bionic,now 4.14-0.1 amd64 [installed,automatic]
kbd/bionic,now 2.0.4-2ubuntu1 amd64 [installed,automatic]
keyboard-configuration/bionic-updates,bionic-updates,now 1.178ubuntu2.9 all [installed,automatic]
klibc-utils/bionic,now 2.0.4-9ubuntu2 amd64 [installed]
kmod/bionic-updates,now 24-1ubuntu3.2 amd64 [installed]
krb5-locales/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1.16-2ubuntu0.1 all [installed]
landscape-common/bionic-updates,now 18.01-0ubuntu3.4 amd64 [installed]
language-pack-en/bionic-updates,bionic-updates,now 1:18.04+20190718 all [installed]
language-pack-en-base/bionic-updates,bionic-updates,now 1:18.04+20180712 all [installed,automatic]
language-selector-common/bionic-updates,bionic-updates,now 0.188.3 all [installed]
laptop-detect/bionic,bionic,now 0.16 all [installed,automatic]
less/bionic,now 487-0.1 amd64 [installed,automatic]
libaccountsservice0/bionic,now 0.6.45-1ubuntu1 amd64 [installed]
libacl1/bionic,now 2.2.52-3build1 amd64 [installed]
libapparmor1/bionic-updates,bionic-security,now 2.12-4ubuntu5.1 amd64 [installed]
libapt-inst2.0/bionic-updates,now 1.6.12 amd64 [installed]
libapt-pkg5.0/bionic-updates,now 1.6.12 amd64 [installed]
libargon2-0/bionic,now 0~20161029-1.1 amd64 [installed,automatic]
libasn1-8-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libassuan0/bionic,now 2.5.1-2 amd64 [installed]
libatm1/bionic,now 1:2.5.1-2build1 amd64 [installed,automatic]
libattr1/bionic,now 1:2.4.47-2build1 amd64 [installed]
libaudit-common/bionic,bionic,now 1:2.8.2-1ubuntu1 all [installed]
libaudit1/bionic,now 1:2.8.2-1ubuntu1 amd64 [installed]
libbind9-160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libblkid1/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
libbsd0/bionic-updates,bionic-security,now 0.8.7-1ubuntu0.1 amd64 [installed,automatic]
libbz2-1.0/bionic-updates,bionic-security,now 1.0.6-8.1ubuntu0.2 amd64 [installed]
libc-bin/bionic,now 2.27-3ubuntu1 amd64 [installed,automatic]
libc6/bionic,now 2.27-3ubuntu1 amd64 [installed]
libcap-ng0/bionic,now 0.7.7-3.1 amd64 [installed]
libcap2/bionic,now 1:2.25-1.2 amd64 [installed,automatic]
libcap2-bin/bionic,now 1:2.25-1.2 amd64 [installed,automatic]
libcom-err2/bionic-updates,bionic-security,now 1.44.1-1ubuntu1.3 amd64 [installed]
libcryptsetup12/bionic-updates,now 2:2.0.2-1ubuntu1.1 amd64 [installed,automatic]
libcurl3-gnutls/bionic-updates,bionic-security,now 7.58.0-2ubuntu3.8 amd64 [installed]
libcurl4/bionic-updates,bionic-security,now 7.58.0-2ubuntu3.8 amd64 [installed]
libdb5.3/bionic-updates,bionic-security,now 5.3.28-13.1ubuntu1.1 amd64 [installed]
libdbus-1-3/bionic-updates,bionic-security,now 1.12.2-1ubuntu1.1 amd64 [installed]
libdebconfclient0/bionic,now 0.213ubuntu1 amd64 [installed,automatic]
libdevmapper-event1.02.1/bionic-updates,now 2:1.02.145-4.1ubuntu3.18.04.2 amd64 [installed]
libdevmapper1.02.1/bionic-updates,now 2:1.02.145-4.1ubuntu3.18.04.2 amd64 [installed]
libdns-export1100/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed,automatic]
libdns1100/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libdrm-common/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2.4.99-1ubuntu1~18.04.2 all [installed]
libdrm2/bionic-updates,bionic-security,now 2.4.99-1ubuntu1~18.04.2 amd64 [installed]
libdumbnet1/bionic,now 1.12-7build1 amd64 [installed]
libedit2/bionic,now 3.1-20170329-1 amd64 [installed]
libelf1/bionic-updates,bionic-security,now 0.170-0.4ubuntu0.1 amd64 [installed]
liberror-perl/bionic,bionic,now 0.17025-1 all [installed]
libestr0/bionic,now 0.1.10-2.1 amd64 [installed,automatic]
libevent-2.1-6/bionic,now 2.1.8-stable-4build1 amd64 [installed]
libexpat1/bionic-updates,bionic-security,now 2.2.5-3ubuntu0.2 amd64 [installed]
libext2fs2/bionic-updates,bionic-security,now 1.44.1-1ubuntu1.3 amd64 [installed]
libfastjson4/bionic,now 0.99.8-2 amd64 [installed,automatic]
libfdisk1/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
libffi6/bionic,now 3.2.1-8 amd64 [installed]
libfreetype6/bionic,now 2.8.1-2ubuntu2 amd64 [installed,automatic]
libfribidi0/bionic,now 0.19.7-2 amd64 [installed,automatic]
libfuse2/bionic,now 2.9.7-1ubuntu1 amd64 [installed]
libgcc1/bionic-updates,bionic-security,now 1:8.3.0-6ubuntu1~18.04.1 amd64 [installed]
libgcrypt20/bionic-updates,bionic-security,now 1.8.1-4ubuntu1.2 amd64 [installed]
libgdbm-compat4/bionic,now 1.14.1-6 amd64 [installed]
libgdbm5/bionic,now 1.14.1-6 amd64 [installed]
libgeoip1/bionic,now 1.6.12-1 amd64 [installed]
libgirepository-1.0-1/bionic,now 1.56.1-1 amd64 [installed,automatic]
libglib2.0-0/bionic-updates,bionic-security,now 2.56.4-0ubuntu0.18.04.4 amd64 [installed]
libglib2.0-data/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2.56.4-0ubuntu0.18.04.4 all [installed]
libgmp10/bionic,now 2:6.1.2+dfsg-2 amd64 [installed]
libgnutls30/bionic-updates,bionic-security,now 3.5.18-1ubuntu1.3 amd64 [installed]
libgpg-error0/bionic,now 1.27-6 amd64 [installed]
libgpm2/bionic,now 1.20.7-5 amd64 [installed]
libgssapi-krb5-2/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 amd64 [installed]
libgssapi3-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libhcrypto4-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libheimbase1-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libheimntlm0-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libhogweed4/bionic,now 3.4-1 amd64 [installed]
libhx509-5-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libicu60/bionic,now 60.2-3ubuntu3 amd64 [installed]
libidn11/bionic-updates,now 1.33-2.1ubuntu1.2 amd64 [installed,automatic]
libidn2-0/bionic-updates,bionic-security,now 2.0.4-1.1ubuntu0.2 amd64 [installed]
libip4tc0/bionic,now 1.6.1-2ubuntu2 amd64 [installed,automatic]
libip6tc0/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
libiptc0/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
libirs160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libisc-export169/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed,automatic]
libisc169/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libisccc160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libisccfg160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libisns0/bionic,now 0.97-2build1 amd64 [installed]
libjson-c3/bionic,now 0.12.1-1.3 amd64 [installed,automatic]
libk5crypto3/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 amd64 [installed]
libkeyutils1/bionic,now 1.5.9-9.2ubuntu2 amd64 [installed]
libklibc/bionic,now 2.0.4-9ubuntu2 amd64 [installed]
libkmod2/bionic-updates,now 24-1ubuntu3.2 amd64 [installed]
libkrb5-26-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libkrb5-3/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 amd64 [installed]
libkrb5support0/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 amd64 [installed]
libksba8/bionic,now 1.3.5-2 amd64 [installed]
libldap-2.4-2/bionic-updates,now 2.4.45+dfsg-1ubuntu1.4 amd64 [installed]
libldap-common/bionic-updates,bionic-updates,now 2.4.45+dfsg-1ubuntu1.4 all [installed]
liblocale-gettext-perl/bionic,now 1.07-3build2 amd64 [installed]
liblvm2app2.2/bionic-updates,now 2.02.176-4.1ubuntu3.18.04.2 amd64 [installed]
liblvm2cmd2.02/bionic-updates,now 2.02.176-4.1ubuntu3.18.04.2 amd64 [installed]
liblwres160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
liblxc-common/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
liblxc1/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
liblz4-1/bionic,now 0.0~r131-2ubuntu3 amd64 [installed]
liblzma5/bionic,now 5.2.2-1.3 amd64 [installed]
liblzo2-2/bionic,now 2.08-1.2 amd64 [installed]
libmagic-mgc/bionic-updates,bionic-security,now 1:5.32-2ubuntu0.3 amd64 [installed,automatic]
libmagic1/bionic-updates,bionic-security,now 1:5.32-2ubuntu0.3 amd64 [installed,automatic]
libmnl0/bionic,now 1.0.4-2 amd64 [installed,automatic]
libmount1/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
libmpdec2/bionic,now 2.4.2-1ubuntu1 amd64 [installed,automatic]
libmpfr6/bionic,now 4.0.1-1 amd64 [installed]
libmspack0/bionic-updates,bionic-security,now 0.6-3ubuntu0.3 amd64 [installed]
libncurses5/bionic-updates,now 6.1-1ubuntu1.18.04 amd64 [installed]
libncursesw5/bionic-updates,now 6.1-1ubuntu1.18.04 amd64 [installed]
libnetfilter-conntrack3/bionic,now 1.0.6-2 amd64 [installed]
libnettle6/bionic,now 3.4-1 amd64 [installed]
libnewt0.52/bionic,now 0.52.20-1ubuntu1 amd64 [installed,automatic]
libnfnetlink0/bionic,now 1.0.1-3 amd64 [installed]
libnghttp2-14/bionic,now 1.30.0-1ubuntu1 amd64 [installed]
libnih1/bionic,now 1.0.3-6ubuntu2 amd64 [installed]
libnl-3-200/bionic,now 3.2.29-0ubuntu3 amd64 [installed,automatic]
libnl-genl-3-200/bionic,now 3.2.29-0ubuntu3 amd64 [installed,automatic]
libnpth0/bionic,now 1.5-3 amd64 [installed]
libnss-systemd/bionic-updates,now 237-3ubuntu10.39 amd64 [installed,automatic]
libntfs-3g88/bionic-updates,bionic-security,now 1:2017.3.23-2ubuntu0.18.04.2 amd64 [installed]
libnuma1/bionic-updates,now 2.0.11-2.1ubuntu0.1 amd64 [installed]
libp11-kit0/bionic,now 0.23.9-2 amd64 [installed]
libpam-cap/bionic,now 1:2.25-1.2 amd64 [installed,automatic]
libpam-modules/bionic-updates,now 1.1.8-3.6ubuntu2.18.04.1 amd64 [installed]
libpam-modules-bin/bionic-updates,now 1.1.8-3.6ubuntu2.18.04.1 amd64 [installed]
libpam-runtime/bionic-updates,bionic-updates,now 1.1.8-3.6ubuntu2.18.04.1 all [installed,automatic]
libpam-systemd/bionic-updates,now 237-3ubuntu10.39 amd64 [installed,automatic]
libpam0g/bionic-updates,now 1.1.8-3.6ubuntu2.18.04.1 amd64 [installed]
libparted2/bionic-updates,now 3.2-20ubuntu0.2 amd64 [installed]
libpcap0.8/bionic-updates,bionic-security,now 1.8.1-6ubuntu1.18.04.1 amd64 [installed]
libpci3/bionic-updates,now 1:3.5.2-1ubuntu1.1 amd64 [installed]
libpcre3/bionic,now 2:8.39-9 amd64 [installed]
libperl5.26/bionic-updates,bionic-security,now 5.26.1-6ubuntu0.3 amd64 [installed]
libpipeline1/bionic,now 1.5.0-1 amd64 [installed]
libplymouth4/bionic-updates,now 0.9.3-1ubuntu7.18.04.2 amd64 [installed]
libpng16-16/bionic-updates,bionic-security,now 1.6.34-1ubuntu0.18.04.2 amd64 [installed]
libpolkit-agent-1-0/bionic-updates,bionic-security,now 0.105-20ubuntu0.18.04.5 amd64 [installed]
libpolkit-backend-1-0/bionic-updates,bionic-security,now 0.105-20ubuntu0.18.04.5 amd64 [installed]
libpolkit-gobject-1-0/bionic-updates,bionic-security,now 0.105-20ubuntu0.18.04.5 amd64 [installed]
libpopt0/bionic,now 1.16-11 amd64 [installed,automatic]
libprocps6/bionic-updates,now 2:3.3.12-3ubuntu1.2 amd64 [installed]
libpsl5/bionic,now 0.19.1-5build1 amd64 [installed]
libpython3-stdlib/bionic-updates,now 3.6.7-1~18.04 amd64 [installed,automatic]
libpython3.6/bionic-updates,now 3.6.9-1~18.04 amd64 [installed]
libpython3.6-minimal/bionic-updates,now 3.6.9-1~18.04 amd64 [installed,automatic]
libpython3.6-stdlib/bionic-updates,now 3.6.9-1~18.04 amd64 [installed,automatic]
libreadline5/bionic,now 5.2+dfsg-3build1 amd64 [installed]
libreadline7/bionic,now 7.0-3 amd64 [installed,automatic]
libroken18-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
librtmp1/bionic,now 2.4+20151223.gitfa8646d.1-1 amd64 [installed]
libsasl2-2/bionic-updates,bionic-security,now 2.1.27~101-g0780600+dfsg-3ubuntu2.1 amd64 [installed]
libsasl2-modules/bionic-updates,bionic-security,now 2.1.27~101-g0780600+dfsg-3ubuntu2.1 amd64 [installed]
libsasl2-modules-db/bionic-updates,bionic-security,now 2.1.27~101-g0780600+dfsg-3ubuntu2.1 amd64 [installed]
libseccomp2/bionic-updates,bionic-security,now 2.4.1-0ubuntu0.18.04.2 amd64 [installed]
libselinux1/bionic,now 2.7-2build2 amd64 [installed]
libsemanage-common/bionic,bionic,now 2.7-2build2 all [installed]
libsemanage1/bionic,now 2.7-2build2 amd64 [installed]
libsepol1/bionic,now 2.7-1 amd64 [installed]
libsigsegv2/bionic,now 2.12-1 amd64 [installed]
libslang2/bionic,now 2.3.1a-3ubuntu1 amd64 [installed,automatic]
libsmartcols1/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
libsqlite3-0/bionic-updates,bionic-security,now 3.22.0-1ubuntu0.2 amd64 [installed,automatic]
libss2/bionic-updates,bionic-security,now 1.44.1-1ubuntu1.3 amd64 [installed]
libssl1.0.0/bionic-updates,bionic-security,now 1.0.2n-1ubuntu5.3 amd64 [installed]
libssl1.1/bionic-updates,bionic-security,now 1.1.1-1ubuntu2.1~18.04.5 amd64 [installed]
libstdc++6/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed]
libsystemd0/bionic-updates,now 237-3ubuntu10.39 amd64 [installed]
libtasn1-6/bionic,now 4.13-2 amd64 [installed]
libtext-charwidth-perl/bionic,now 0.04-7.1 amd64 [installed]
libtext-iconv-perl/bionic,now 1.7-5build6 amd64 [installed]
libtext-wrapi18n-perl/bionic,bionic,now 0.06-7.1 all [installed]
libtinfo5/bionic-updates,now 6.1-1ubuntu1.18.04 amd64 [installed]
libudev1/bionic-updates,now 237-3ubuntu10.39 amd64 [installed]
libunistring2/bionic-updates,now 0.9.9-0ubuntu2 amd64 [installed]
libunwind8/bionic,now 1.2.1-8 amd64 [installed]
libusb-1.0-0/bionic,now 2:1.0.21-2 amd64 [installed]
libutempter0/bionic,now 1.1.6-3 amd64 [installed]
libuuid1/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
libuv1/bionic,now 1.18.0-3 amd64 [installed]
libwind0-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libwrap0/bionic,now 7.6.q-27 amd64 [installed]
libx11-6/bionic-updates,now 2:1.6.4-3ubuntu0.2 amd64 [installed]
libx11-data/bionic-updates,bionic-updates,now 2:1.6.4-3ubuntu0.2 all [installed]
libxau6/bionic,now 1:1.0.8-1 amd64 [installed]
libxcb1/bionic-updates,now 1.13-2~ubuntu18.04 amd64 [installed]
libxdmcp6/bionic,now 1:1.1.2-3 amd64 [installed]
libxext6/bionic,now 2:1.3.3-1 amd64 [installed]
libxml2/bionic-updates,bionic-security,now 2.9.4+dfsg1-6.1ubuntu1.3 amd64 [installed]
libxmlsec1/bionic,now 1.2.25-1build1 amd64 [installed]
libxmlsec1-openssl/bionic,now 1.2.25-1build1 amd64 [installed]
libxmuu1/bionic,now 2:1.1.2-2 amd64 [installed]
libxslt1.1/bionic-updates,bionic-security,now 1.1.29-5ubuntu0.2 amd64 [installed]
libxtables12/bionic,now 1.6.1-2ubuntu2 amd64 [installed,automatic]
libyaml-0-2/bionic,now 0.1.7-2ubuntu3 amd64 [installed,automatic]
libzstd1/bionic-updates,bionic-security,now 1.3.3+dfsg-2ubuntu1.1 amd64 [installed]
linux-base/bionic,bionic,now 4.5ubuntu1 all [installed]
linux-firmware/bionic-updates,bionic-updates,now 1.173.14 all [installed,automatic]
linux-generic/bionic-updates,bionic-security,now 4.15.0.88.80 amd64 [installed]
linux-headers-4.15.0-55/bionic-updates,bionic-updates,bionic-security,bionic-security,now 4.15.0-55.60 all [installed,automatic]
linux-headers-4.15.0-55-generic/bionic-updates,bionic-security,now 4.15.0-55.60 amd64 [installed,automatic]
linux-headers-4.15.0-88/bionic-updates,bionic-updates,bionic-security,bionic-security,now 4.15.0-88.88 all [installed,automatic]
linux-headers-4.15.0-88-generic/bionic-updates,bionic-security,now 4.15.0-88.88 amd64 [installed,automatic]
linux-headers-generic/bionic-updates,bionic-security,now 4.15.0.88.80 amd64 [installed]
linux-image-4.15.0-55-generic/bionic-updates,bionic-security,now 4.15.0-55.60 amd64 [installed,automatic]
linux-image-4.15.0-88-generic/bionic-updates,bionic-security,now 4.15.0-88.88 amd64 [installed,automatic]
linux-image-generic/bionic-updates,bionic-security,now 4.15.0.88.80 amd64 [installed,automatic]
linux-modules-4.15.0-55-generic/bionic-updates,bionic-security,now 4.15.0-55.60 amd64 [installed,automatic]
linux-modules-4.15.0-88-generic/bionic-updates,bionic-security,now 4.15.0-88.88 amd64 [installed,automatic]
linux-modules-extra-4.15.0-55-generic/bionic-updates,bionic-security,now 4.15.0-55.60 amd64 [installed,automatic]
linux-modules-extra-4.15.0-88-generic/bionic-updates,bionic-security,now 4.15.0-88.88 amd64 [installed,automatic]
locales/bionic,bionic,now 2.27-3ubuntu1 all [installed]
login/bionic-updates,now 1:4.5-1ubuntu2 amd64 [installed]
logrotate/bionic,now 3.11.0-0.1ubuntu1 amd64 [installed,automatic]
lsb-base/bionic,bionic,now 9.20170808ubuntu1 all [installed]
lsb-release/bionic,bionic,now 9.20170808ubuntu1 all [installed,automatic]
lshw/bionic-updates,now 02.18-0.1ubuntu6.18.04.1 amd64 [installed]
lsof/bionic,now 4.89+dfsg-0.1 amd64 [installed]
ltrace/bionic,now 0.7.3-6ubuntu1 amd64 [installed]
lvm2/bionic-updates,now 2.02.176-4.1ubuntu3.18.04.2 amd64 [installed]
lxcfs/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
lxd/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
lxd-client/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
man-db/bionic-updates,now 2.8.3-2ubuntu0.1 amd64 [installed]
manpages/bionic,bionic,now 4.15-1 all [installed]
mawk/bionic,now 1.3.3-17ubuntu3 amd64 [installed]
mdadm/bionic-updates,now 4.1~rc1-3~ubuntu18.04.4 amd64 [installed]
mime-support/bionic,bionic,now 3.60ubuntu1 all [installed,automatic]
mlocate/bionic,now 0.26-2ubuntu3.1 amd64 [installed]
mount/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed,automatic]
mtr-tiny/bionic,now 0.92-1 amd64 [installed]
multiarch-support/bionic,now 2.27-3ubuntu1 amd64 [installed]
nano/bionic,now 2.9.3-2 amd64 [installed]
ncurses-base/bionic-updates,bionic-updates,now 6.1-1ubuntu1.18.04 all [installed]
ncurses-bin/bionic-updates,now 6.1-1ubuntu1.18.04 amd64 [installed]
ncurses-term/bionic-updates,bionic-updates,now 6.1-1ubuntu1.18.04 all [installed]
net-tools/bionic,now 1.60+git20161116.90da8a0-1ubuntu1 amd64 [installed]
netbase/bionic,bionic,now 5.4 all [installed,automatic]
netcat-openbsd/bionic-updates,now 1.187-1ubuntu0.1 amd64 [installed,automatic]
netplan.io/bionic-updates,now 0.98-0ubuntu1~18.04.1 amd64 [installed,automatic]
networkd-dispatcher/bionic-updates,bionic-updates,now 1.7-0ubuntu3.3 all [installed,automatic]
nplan/bionic-updates,bionic-updates,now 0.98-0ubuntu1~18.04.1 all [installed,automatic]
ntfs-3g/bionic-updates,bionic-security,now 1:2017.3.23-2ubuntu0.18.04.2 amd64 [installed]
open-iscsi/bionic-updates,now 2.0.874-5ubuntu2.7 amd64 [installed]
open-vm-tools/bionic-updates,now 2:11.0.1-2ubuntu0.18.04.2 amd64 [installed]
openssh-client/bionic-updates,bionic-security,now 1:7.6p1-4ubuntu0.3 amd64 [installed]
openssh-server/bionic-updates,bionic-security,now 1:7.6p1-4ubuntu0.3 amd64 [installed]
openssh-sftp-server/bionic-updates,bionic-security,now 1:7.6p1-4ubuntu0.3 amd64 [installed]
openssl/bionic-updates,bionic-security,now 1.1.1-1ubuntu2.1~18.04.5 amd64 [installed]
os-prober/bionic,now 1.74ubuntu1 amd64 [installed,automatic]
overlayroot/bionic-updates,bionic-updates,now 0.40ubuntu1.1 all [installed]
parted/bionic-updates,now 3.2-20ubuntu0.2 amd64 [installed]
passwd/bionic-updates,now 1:4.5-1ubuntu2 amd64 [installed]
pastebinit/bionic,bionic,now 1.5-2 all [installed]
patch/bionic-updates,bionic-security,now 2.7.6-2ubuntu1.1 amd64 [installed]
pciutils/bionic-updates,now 1:3.5.2-1ubuntu1.1 amd64 [installed]
perl/bionic-updates,bionic-security,now 5.26.1-6ubuntu0.3 amd64 [installed]
perl-base/bionic-updates,bionic-security,now 5.26.1-6ubuntu0.3 amd64 [installed]
perl-modules-5.26/bionic-updates,bionic-updates,bionic-security,bionic-security,now 5.26.1-6ubuntu0.3 all [installed]
pinentry-curses/bionic,now 1.1.0-1 amd64 [installed]
plymouth/bionic-updates,now 0.9.3-1ubuntu7.18.04.2 amd64 [installed]
plymouth-theme-ubuntu-text/bionic-updates,now 0.9.3-1ubuntu7.18.04.2 amd64 [installed]
policykit-1/bionic-updates,bionic-security,now 0.105-20ubuntu0.18.04.5 amd64 [installed]
pollinate/bionic-updates,bionic-updates,now 4.33-0ubuntu1~18.04.1 all [installed]
popularity-contest/bionic,bionic,now 1.66ubuntu1 all [installed]
powermgmt-base/bionic,bionic,now 1.33 all [installed]
procps/bionic-updates,now 2:3.3.12-3ubuntu1.2 amd64 [installed]
psmisc/bionic-updates,now 23.1-1ubuntu0.1 amd64 [installed]
publicsuffix/bionic,bionic,now 20180223.1310-1 all [installed]
python-apt-common/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1.6.5ubuntu0.2 all [installed]
python3/bionic-updates,now 3.6.7-1~18.04 amd64 [installed,automatic]
python3-apport/bionic-updates,bionic-updates,now 2.20.9-0ubuntu7.11 all [installed]
python3-apt/bionic-updates,bionic-security,now 1.6.5ubuntu0.2 amd64 [installed]
python3-asn1crypto/bionic,bionic,now 0.24.0-1 all [installed]
python3-attr/bionic,bionic,now 17.4.0-2 all [installed]
python3-automat/bionic,bionic,now 0.6.0-1 all [installed]
python3-certifi/bionic,bionic,now 2018.1.18-2 all [installed]
python3-cffi-backend/bionic,now 1.11.5-1 amd64 [installed]
python3-chardet/bionic,bionic,now 3.0.4-1 all [installed]
python3-click/bionic,bionic,now 6.7-3 all [installed]
python3-colorama/bionic,bionic,now 0.3.7-1 all [installed]
python3-commandnotfound/bionic-updates,bionic-updates,now 18.04.5 all [installed]
python3-configobj/bionic,bionic,now 5.0.6-2 all [installed]
python3-constantly/bionic,bionic,now 15.1.0-1 all [installed]
python3-cryptography/bionic-updates,bionic-security,now 2.1.4-1ubuntu1.3 amd64 [installed]
python3-dbus/bionic,now 1.2.6-1 amd64 [installed,automatic]
python3-debconf/bionic-updates,bionic-updates,now 1.5.66ubuntu1 all [installed]
python3-debian/bionic,bionic,now 0.1.32 all [installed]
python3-distro-info/bionic-updates,bionic-updates,bionic-security,bionic-security,now 0.18ubuntu0.18.04.1 all [installed]
python3-distupgrade/bionic-updates,bionic-updates,now 1:18.04.37 all [installed]
python3-gdbm/bionic-updates,now 3.6.9-1~18.04 amd64 [installed]
python3-gi/bionic-updates,now 3.26.1-2ubuntu1 amd64 [installed,automatic]
python3-httplib2/bionic-updates,bionic-updates,now 0.9.2+dfsg-1ubuntu0.1 all [installed]
python3-hyperlink/bionic,bionic,now 17.3.1-2 all [installed]
python3-idna/bionic,bionic,now 2.6-1 all [installed]
python3-incremental/bionic,bionic,now 16.10.1-3 all [installed]
python3-minimal/bionic-updates,now 3.6.7-1~18.04 amd64 [installed,automatic]
python3-netifaces/bionic,now 0.10.4-0.1build4 amd64 [installed,automatic]
python3-newt/bionic,now 0.52.20-1ubuntu1 amd64 [installed]
python3-openssl/bionic,bionic,now 17.5.0-1ubuntu1 all [installed]
python3-pam/bionic,now 0.4.2-13.2ubuntu4 amd64 [installed]
python3-pkg-resources/bionic,bionic,now 39.0.1-2 all [installed]
python3-problem-report/bionic-updates,bionic-updates,now 2.20.9-0ubuntu7.11 all [installed]
python3-pyasn1/bionic,bionic,now 0.4.2-3 all [installed]
python3-pyasn1-modules/bionic,bionic,now 0.2.1-0.2 all [installed]
python3-requests/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2.18.4-2ubuntu0.1 all [installed]
python3-requests-unixsocket/bionic,bionic,now 0.1.5-3 all [installed]
python3-serial/bionic,bionic,now 3.4-2 all [installed]
python3-service-identity/bionic,bionic,now 16.0.0-2 all [installed]
python3-six/bionic,bionic,now 1.11.0-2 all [installed]
python3-software-properties/bionic-updates,bionic-updates,now 0.96.24.32.12 all [installed]
python3-systemd/bionic,now 234-1build1 amd64 [installed]
python3-twisted/bionic,bionic,now 17.9.0-2 all [installed]
python3-twisted-bin/bionic,now 17.9.0-2 amd64 [installed]
python3-update-manager/bionic-updates,bionic-updates,now 1:18.04.11.10 all [installed]
python3-urllib3/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1.22-1ubuntu0.18.04.1 all [installed]
python3-yaml/bionic,now 3.12-1build2 amd64 [installed,automatic]
python3-zope.interface/bionic,now 4.3.2-1build2 amd64 [installed]
python3.6/bionic-updates,now 3.6.9-1~18.04 amd64 [installed,automatic]
python3.6-minimal/bionic-updates,now 3.6.9-1~18.04 amd64 [installed,automatic]
readline-common/bionic,bionic,now 7.0-3 all [installed,automatic]
rsync/bionic,now 3.1.2-2.1ubuntu1 amd64 [installed]
rsyslog/bionic,now 8.32.0-1ubuntu4 amd64 [installed,automatic]
run-one/bionic,bionic,now 1.17-0ubuntu1 all [installed]
screen/bionic-updates,now 4.6.2-1ubuntu1 amd64 [installed]
sed/bionic,now 4.4-2 amd64 [installed]
sensible-utils/bionic,bionic,now 0.0.12 all [installed]
shared-mime-info/bionic,now 1.9-2 amd64 [installed]
snapd/bionic-updates,now 2.42.1+18.04 amd64 [installed]
software-properties-common/bionic-updates,bionic-updates,now 0.96.24.32.12 all [installed]
sosreport/bionic-updates,now 3.6-1ubuntu0.18.04.4 amd64 [installed]
squashfs-tools/bionic-updates,now 1:4.3-6ubuntu0.18.04.1 amd64 [installed]
ssh-import-id/bionic-updates,bionic-updates,now 5.7-0ubuntu1.1 all [installed]
strace/bionic,now 4.21-1ubuntu1 amd64 [installed]
sudo/bionic-updates,bionic-security,now 1.8.21p2-3ubuntu1.2 amd64 [installed,automatic]
systemd/bionic-updates,now 237-3ubuntu10.39 amd64 [installed,automatic]
systemd-sysv/bionic-updates,now 237-3ubuntu10.39 amd64 [installed,automatic]
sysvinit-utils/bionic,now 2.88dsf-59.10ubuntu1 amd64 [installed]
tar/bionic-updates,now 1.29b-2ubuntu0.1 amd64 [installed]
tasksel/bionic,bionic,now 3.34ubuntu11 all [installed]
tasksel-data/bionic,bionic,now 3.34ubuntu11 all [installed,automatic]
tcpdump/bionic-updates,bionic-security,now 4.9.3-0ubuntu0.18.04.1 amd64 [installed]
telnet/bionic,now 0.17-41 amd64 [installed]
time/bionic,now 1.7-25.1build1 amd64 [installed]
tmux/bionic-updates,now 2.6-3ubuntu0.2 amd64 [installed]
tzdata/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2019c-0ubuntu0.18.04 all [installed,automatic]
ubuntu-advantage-tools/bionic,bionic,now 17 all [installed,automatic]
ubuntu-keyring/bionic-updates,bionic-updates,now 2018.09.18.1~18.04.0 all [installed]
ubuntu-minimal/bionic-updates,now 1.417.4 amd64 [installed]
ubuntu-release-upgrader-core/bionic-updates,bionic-updates,now 1:18.04.37 all [installed]
ubuntu-server/bionic-updates,now 1.417.4 amd64 [installed]
ubuntu-standard/bionic-updates,now 1.417.4 amd64 [installed]
ucf/bionic,bionic,now 3.0038 all [installed]
udev/bionic-updates,now 237-3ubuntu10.39 amd64 [installed]
ufw/bionic-updates,bionic-updates,now 0.36-0ubuntu0.18.04.1 all [installed]
uidmap/bionic-updates,now 1:4.5-1ubuntu2 amd64 [installed]
unattended-upgrades/bionic-updates,bionic-updates,now 1.1ubuntu1.18.04.13 all [installed]
update-manager-core/bionic-updates,bionic-updates,now 1:18.04.11.10 all [installed]
update-notifier-common/bionic-updates,bionic-updates,now 3.192.1.7 all [installed]
ureadahead/bionic-updates,now 0.100.0-21 amd64 [installed]
usbutils/bionic,now 1:007-4build1 amd64 [installed]
util-linux/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
uuid-runtime/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
vim/bionic-updates,bionic-security,now 2:8.0.1453-1ubuntu1.1 amd64 [installed]
vim-common/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2:8.0.1453-1ubuntu1.1 all [installed,automatic]
vim-runtime/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2:8.0.1453-1ubuntu1.1 all [installed]
vim-tiny/bionic-updates,bionic-security,now 2:8.0.1453-1ubuntu1.1 amd64 [installed,automatic]
wget/bionic-updates,bionic-security,now 1.19.4-1ubuntu2.2 amd64 [installed]
whiptail/bionic,now 0.52.20-1ubuntu1 amd64 [installed,automatic]
wireless-regdb/bionic-updates,bionic-updates,now 2018.05.09-0ubuntu1~18.04.1 all [installed,automatic]
xauth/bionic,now 1:1.0.10-1 amd64 [installed]
xdelta3/bionic,now 3.0.11-dfsg-1ubuntu1 amd64 [installed]
xdg-user-dirs/bionic,now 0.17-1ubuntu1 amd64 [installed]
xfsprogs/bionic,now 4.9.0+nmu1ubuntu2 amd64 [installed]
xkb-data/bionic-updates,bionic-updates,now 2.23.1-1ubuntu1.18.04.1 all [installed,automatic]
xxd/bionic-updates,bionic-security,now 2:8.0.1453-1ubuntu1.1 amd64 [installed,automatic]
xz-utils/bionic,now 5.2.2-1.3 amd64 [installed,automatic]
zerofree/bionic,now 1.0.4-1 amd64 [installed]
zlib1g/bionic,now 1:1.2.11.dfsg-0ubuntu2 amd64 [installed]
```

---

### Post by mastablasta on 2020-02-27
wouldn't it make more sense to start with mini.iso (netinstall) and then add what is needed?

i did that with the first Debian server. but after the USB stopped working (yeah i put it on a small USB key), i just installed Ubuntu server on the new one. still if i wanted something light that is what i would do.

---

### Post by LHammonds on 2020-02-27
> **mastablasta said:**
> wouldn't it make more sense to start with mini.iso (netinstall) and then add what is needed?
Yes it would had I known the netinstall was actually a minimal install.  I figured it was just the normal install but with the bulk of the code needing to be downloaded from the net to keep the installer itself small.  Thanks for the heads up.

Here is the list of 367 packages installed by default from the mini.iso (with OpenSSH as the only additional package installed)

```

accountsservice/bionic,now 0.6.45-1ubuntu1 amd64 [installed]
adduser/bionic,bionic,now 3.116ubuntu1 all [installed]
amd64-microcode/bionic-updates,bionic-security,now 3.20191021.1+really3.20181128.1~ubuntu0.18.04.1 amd64 [installed,automatic]
apparmor/bionic-updates,bionic-security,now 2.12-4ubuntu5.1 amd64 [installed]
apt/bionic-updates,now 1.6.12 amd64 [installed]
apt-utils/bionic-updates,now 1.6.12 amd64 [installed]
base-files/bionic-updates,now 10.1ubuntu2.8 amd64 [installed]
base-passwd/bionic,now 3.5.44 amd64 [installed]
bash/bionic-updates,now 4.4.18-2ubuntu1.2 amd64 [installed]
bash-completion/bionic,bionic,now 1:2.8-1ubuntu1 all [installed]
bind9-host/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
bsdmainutils/bionic,now 11.1.2ubuntu1 amd64 [installed]
bsdutils/bionic-updates,now 1:2.31.1-0.4ubuntu3.5 amd64 [installed]
busybox-initramfs/bionic-updates,bionic-security,now 1:1.27.2-2ubuntu3.2 amd64 [installed]
busybox-static/bionic-updates,bionic-security,now 1:1.27.2-2ubuntu3.2 amd64 [installed]
bzip2/bionic-updates,bionic-security,now 1.0.6-8.1ubuntu0.2 amd64 [installed]
ca-certificates/bionic,bionic,bionic-updates,bionic-updates,now 20180409 all [installed]
command-not-found/bionic-updates,bionic-updates,now 18.04.5 all [installed]
command-not-found-data/bionic-updates,now 18.04.5 amd64 [installed]
console-setup/bionic-updates,bionic-updates,now 1.178ubuntu2.9 all [installed]
console-setup-linux/bionic-updates,bionic-updates,now 1.178ubuntu2.9 all [installed]
coreutils/bionic,now 8.28-1ubuntu1 amd64 [installed]
cpio/bionic-updates,bionic-security,now 2.12+dfsg-6ubuntu0.18.04.1 amd64 [installed]
crda/bionic,now 3.18-1build1 amd64 [installed,automatic]
cron/bionic,now 3.0pl1-128.1ubuntu1 amd64 [installed]
dash/bionic,now 0.5.8-2.10 amd64 [installed]
dbus/bionic-updates,bionic-security,now 1.12.2-1ubuntu1.1 amd64 [installed]
debconf/bionic-updates,bionic-updates,now 1.5.66ubuntu1 all [installed]
debconf-i18n/bionic-updates,bionic-updates,now 1.5.66ubuntu1 all [installed]
debianutils/bionic,now 4.8.4 amd64 [installed]
dictionaries-common/bionic,bionic,now 1.27.2 all [installed,automatic]
diffutils/bionic,now 1:3.6-1 amd64 [installed]
distro-info-data/bionic-updates,bionic-updates,bionic-security,bionic-security,now 0.37ubuntu0.6 all [installed]
dmeventd/bionic-updates,now 2:1.02.145-4.1ubuntu3.18.04.2 amd64 [installed,automatic]
dmidecode/bionic-updates,now 3.1-1ubuntu0.1 amd64 [installed]
dmsetup/bionic-updates,now 2:1.02.145-4.1ubuntu3.18.04.2 amd64 [installed]
dnsutils/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
dosfstools/bionic,now 4.1-1 amd64 [installed]
dpkg/bionic-updates,now 1.19.0.5ubuntu2.3 amd64 [installed]
e2fsprogs/bionic-updates,bionic-security,now 1.44.1-1ubuntu1.3 amd64 [installed]
ed/bionic,now 1.10-2.1 amd64 [installed]
eject/bionic,now 2.1.5+deb1+cvs20081104-13.2 amd64 [installed]
emacsen-common/bionic,bionic,now 2.0.8 all [installed,automatic]
fdisk/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
file/bionic-updates,bionic-security,now 1:5.32-2ubuntu0.3 amd64 [installed]
findutils/bionic,now 4.6.0+git+20170828-2 amd64 [installed]
friendly-recovery/bionic-updates,bionic-updates,now 0.2.38ubuntu1.1 all [installed]
ftp/bionic,now 0.17-34 amd64 [installed]
fuse/bionic,now 2.9.7-1ubuntu1 amd64 [installed]
gcc-8-base/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed]
geoip-database/bionic,bionic,now 20180315-1 all [installed]
gettext-base/bionic-updates,bionic-security,now 0.19.8.1-6ubuntu0.3 amd64 [installed]
gir1.2-glib-2.0/bionic,now 1.56.1-1 amd64 [installed]
gpgv/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
grep/bionic-updates,now 3.1-2build1 amd64 [installed]
groff-base/bionic,now 1.22.3-10 amd64 [installed]
grub-common/bionic-updates,now 2.02-2ubuntu8.14 amd64 [installed]
grub-gfxpayload-lists/bionic,now 0.7 amd64 [installed,automatic]
grub-pc/bionic-updates,now 2.02-2ubuntu8.14 amd64 [installed]
grub-pc-bin/bionic-updates,now 2.02-2ubuntu8.14 amd64 [installed,automatic]
grub2-common/bionic-updates,now 2.02-2ubuntu8.14 amd64 [installed,automatic]
gzip/bionic,now 1.6-5ubuntu1 amd64 [installed]
hdparm/bionic,now 9.54+ds-1 amd64 [installed]
hostname/bionic,now 3.20 amd64 [installed]
info/bionic,now 6.5.0.dfsg.1-2 amd64 [installed]
init/bionic,now 1.51 amd64 [installed]
init-system-helpers/bionic,bionic,now 1.51 all [installed]
initramfs-tools/bionic-updates,bionic-updates,now 0.130ubuntu3.9 all [installed]
initramfs-tools-bin/bionic-updates,now 0.130ubuntu3.9 amd64 [installed]
initramfs-tools-core/bionic-updates,bionic-updates,now 0.130ubuntu3.9 all [installed]
install-info/bionic,now 6.5.0.dfsg.1-2 amd64 [installed]
installation-report/bionic,bionic,now 2.62ubuntu1 all [installed]
intel-microcode/bionic-updates,bionic-security,now 3.20191115.1ubuntu0.18.04.2 amd64 [installed,automatic]
iproute2/bionic,now 4.15.0-2ubuntu1 amd64 [installed]
iptables/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
iputils-ping/bionic-updates,now 3:20161105-1ubuntu3 amd64 [installed]
iputils-tracepath/bionic-updates,now 3:20161105-1ubuntu3 amd64 [installed]
irqbalance/bionic-updates,now 1.3.0-0.1ubuntu0.18.04.1 amd64 [installed]
isc-dhcp-client/bionic-updates,bionic-security,now 4.3.5-3ubuntu7.1 amd64 [installed]
isc-dhcp-common/bionic-updates,bionic-security,now 4.3.5-3ubuntu7.1 amd64 [installed]
iso-codes/bionic,bionic,now 3.79-1 all [installed]
iucode-tool/bionic,now 2.3.1-1 amd64 [installed,automatic]
iw/bionic,now 4.14-0.1 amd64 [installed,automatic]
kbd/bionic,now 2.0.4-2ubuntu1 amd64 [installed]
keyboard-configuration/bionic-updates,bionic-updates,now 1.178ubuntu2.9 all [installed]
klibc-utils/bionic,now 2.0.4-9ubuntu2 amd64 [installed]
kmod/bionic-updates,now 24-1ubuntu3.2 amd64 [installed]
krb5-locales/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1.16-2ubuntu0.1 all [installed]
language-pack-en/bionic-updates,bionic-updates,now 1:18.04+20190718 all [installed]
language-pack-en-base/bionic-updates,bionic-updates,now 1:18.04+20180712 all [installed,automatic]
language-pack-gnome-en/bionic-updates,bionic-updates,now 1:18.04+20190718 all [installed]
language-pack-gnome-en-base/bionic-updates,bionic-updates,now 1:18.04+20180712 all [installed,automatic]
language-selector-common/bionic-updates,bionic-updates,now 0.188.3 all [installed]
laptop-detect/bionic,bionic,now 0.16 all [installed,automatic]
less/bionic,now 487-0.1 amd64 [installed]
libaccountsservice0/bionic,now 0.6.45-1ubuntu1 amd64 [installed]
libacl1/bionic,now 2.2.52-3build1 amd64 [installed]
libapparmor1/bionic-updates,bionic-security,now 2.12-4ubuntu5.1 amd64 [installed]
libapt-inst2.0/bionic-updates,now 1.6.12 amd64 [installed]
libapt-pkg5.0/bionic-updates,now 1.6.12 amd64 [installed]
libargon2-0/bionic,now 0~20161029-1.1 amd64 [installed]
libatm1/bionic,now 1:2.5.1-2build1 amd64 [installed]
libattr1/bionic,now 1:2.4.47-2build1 amd64 [installed]
libaudit-common/bionic,bionic,now 1:2.8.2-1ubuntu1 all [installed]
libaudit1/bionic,now 1:2.8.2-1ubuntu1 amd64 [installed]
libbind9-160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libblkid1/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
libbsd0/bionic-updates,bionic-security,now 0.8.7-1ubuntu0.1 amd64 [installed]
libbz2-1.0/bionic-updates,bionic-security,now 1.0.6-8.1ubuntu0.2 amd64 [installed]
libc-bin/bionic,now 2.27-3ubuntu1 amd64 [installed]
libc6/bionic,now 2.27-3ubuntu1 amd64 [installed]
libcap-ng0/bionic,now 0.7.7-3.1 amd64 [installed]
libcap2/bionic,now 1:2.25-1.2 amd64 [installed]
libcap2-bin/bionic,now 1:2.25-1.2 amd64 [installed]
libcom-err2/bionic-updates,bionic-security,now 1.44.1-1ubuntu1.3 amd64 [installed]
libcryptsetup12/bionic-updates,now 2:2.0.2-1ubuntu1.1 amd64 [installed]
libdb5.3/bionic-updates,bionic-security,now 5.3.28-13.1ubuntu1.1 amd64 [installed]
libdbus-1-3/bionic-updates,bionic-security,now 1.12.2-1ubuntu1.1 amd64 [installed]
libdebconfclient0/bionic,now 0.213ubuntu1 amd64 [installed]
libdevmapper-event1.02.1/bionic-updates,now 2:1.02.145-4.1ubuntu3.18.04.2 amd64 [installed,automatic]
libdevmapper1.02.1/bionic-updates,now 2:1.02.145-4.1ubuntu3.18.04.2 amd64 [installed]
libdns-export1100/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libdns1100/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libdrm-common/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2.4.99-1ubuntu1~18.04.2 all [installed]
libdrm2/bionic-updates,bionic-security,now 2.4.99-1ubuntu1~18.04.2 amd64 [installed]
libedit2/bionic,now 3.1-20170329-1 amd64 [installed]
libelf1/bionic-updates,bionic-security,now 0.170-0.4ubuntu0.1 amd64 [installed]
libestr0/bionic,now 0.1.10-2.1 amd64 [installed]
libexpat1/bionic-updates,bionic-security,now 2.2.5-3ubuntu0.2 amd64 [installed]
libext2fs2/bionic-updates,bionic-security,now 1.44.1-1ubuntu1.3 amd64 [installed]
libfastjson4/bionic,now 0.99.8-2 amd64 [installed]
libfdisk1/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
libffi6/bionic,now 3.2.1-8 amd64 [installed]
libfreetype6/bionic,now 2.8.1-2ubuntu2 amd64 [installed,automatic]
libfribidi0/bionic,now 0.19.7-2 amd64 [installed]
libfuse2/bionic,now 2.9.7-1ubuntu1 amd64 [installed]
libgcc1/bionic-updates,bionic-security,now 1:8.3.0-6ubuntu1~18.04.1 amd64 [installed]
libgcrypt20/bionic-updates,bionic-security,now 1.8.1-4ubuntu1.2 amd64 [installed]
libgdbm5/bionic,now 1.14.1-6 amd64 [installed]
libgeoip1/bionic,now 1.6.12-1 amd64 [installed]
libgirepository-1.0-1/bionic,now 1.56.1-1 amd64 [installed]
libglib2.0-0/bionic-updates,bionic-security,now 2.56.4-0ubuntu0.18.04.4 amd64 [installed]
libglib2.0-data/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2.56.4-0ubuntu0.18.04.4 all [installed]
libgmp10/bionic,now 2:6.1.2+dfsg-2 amd64 [installed]
libgnutls30/bionic-updates,bionic-security,now 3.5.18-1ubuntu1.3 amd64 [installed]
libgpg-error0/bionic,now 1.27-6 amd64 [installed]
libgssapi-krb5-2/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 amd64 [installed]
libhogweed4/bionic,now 3.4-1 amd64 [installed]
libicu60/bionic,now 60.2-3ubuntu3 amd64 [installed]
libidn11/bionic-updates,now 1.33-2.1ubuntu1.2 amd64 [installed]
libidn2-0/bionic-updates,bionic-security,now 2.0.4-1.1ubuntu0.2 amd64 [installed]
libip4tc0/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
libip6tc0/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
libiptc0/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
libirs160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libisc-export169/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libisc169/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libisccc160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libisccfg160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
libjson-c3/bionic,now 0.12.1-1.3 amd64 [installed]
libk5crypto3/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 amd64 [installed]
libkeyutils1/bionic,now 1.5.9-9.2ubuntu2 amd64 [installed]
libklibc/bionic,now 2.0.4-9ubuntu2 amd64 [installed]
libkmod2/bionic-updates,now 24-1ubuntu3.2 amd64 [installed]
libkrb5-3/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 amd64 [installed]
libkrb5support0/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 amd64 [installed]
liblocale-gettext-perl/bionic,now 1.07-3build2 amd64 [installed]
liblvm2app2.2/bionic-updates,now 2.02.176-4.1ubuntu3.18.04.2 amd64 [installed,automatic]
liblvm2cmd2.02/bionic-updates,now 2.02.176-4.1ubuntu3.18.04.2 amd64 [installed,automatic]
liblwres160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.11 amd64 [installed]
liblz4-1/bionic,now 0.0~r131-2ubuntu3 amd64 [installed]
liblzma5/bionic,now 5.2.2-1.3 amd64 [installed]
libmagic-mgc/bionic-updates,bionic-security,now 1:5.32-2ubuntu0.3 amd64 [installed]
libmagic1/bionic-updates,bionic-security,now 1:5.32-2ubuntu0.3 amd64 [installed]
libmnl0/bionic,now 1.0.4-2 amd64 [installed]
libmount1/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
libmpdec2/bionic,now 2.4.2-1ubuntu1 amd64 [installed]
libncurses5/bionic-updates,now 6.1-1ubuntu1.18.04 amd64 [installed]
libncursesw5/bionic-updates,now 6.1-1ubuntu1.18.04 amd64 [installed]
libnetfilter-conntrack3/bionic,now 1.0.6-2 amd64 [installed]
libnettle6/bionic,now 3.4-1 amd64 [installed]
libnewt0.52/bionic,now 0.52.20-1ubuntu1 amd64 [installed]
libnfnetlink0/bionic,now 1.0.1-3 amd64 [installed]
libnih1/bionic,now 1.0.3-6ubuntu2 amd64 [installed]
libnl-3-200/bionic,now 3.2.29-0ubuntu3 amd64 [installed,automatic]
libnl-genl-3-200/bionic,now 3.2.29-0ubuntu3 amd64 [installed,automatic]
libnss-systemd/bionic-updates,now 237-3ubuntu10.39 amd64 [installed]
libntfs-3g88/bionic-updates,bionic-security,now 1:2017.3.23-2ubuntu0.18.04.2 amd64 [installed]
libnuma1/bionic-updates,now 2.0.11-2.1ubuntu0.1 amd64 [installed]
libp11-kit0/bionic,now 0.23.9-2 amd64 [installed]
libpam-cap/bionic,now 1:2.25-1.2 amd64 [installed]
libpam-modules/bionic-updates,now 1.1.8-3.6ubuntu2.18.04.1 amd64 [installed]
libpam-modules-bin/bionic-updates,now 1.1.8-3.6ubuntu2.18.04.1 amd64 [installed]
libpam-runtime/bionic-updates,bionic-updates,now 1.1.8-3.6ubuntu2.18.04.1 all [installed]
libpam-systemd/bionic-updates,now 237-3ubuntu10.39 amd64 [installed]
libpam0g/bionic-updates,now 1.1.8-3.6ubuntu2.18.04.1 amd64 [installed]
libparted2/bionic-updates,now 3.2-20ubuntu0.2 amd64 [installed]
libpcap0.8/bionic-updates,bionic-security,now 1.8.1-6ubuntu1.18.04.1 amd64 [installed]
libpci3/bionic-updates,now 1:3.5.2-1ubuntu1.1 amd64 [installed]
libpcre3/bionic,now 2:8.39-9 amd64 [installed]
libpipeline1/bionic,now 1.5.0-1 amd64 [installed]
libplymouth4/bionic-updates,now 0.9.3-1ubuntu7.18.04.2 amd64 [installed]
libpng16-16/bionic-updates,bionic-security,now 1.6.34-1ubuntu0.18.04.2 amd64 [installed]
libpolkit-gobject-1-0/bionic-updates,bionic-security,now 0.105-20ubuntu0.18.04.5 amd64 [installed]
libpopt0/bionic,now 1.16-11 amd64 [installed]
libprocps6/bionic-updates,now 2:3.3.12-3ubuntu1.2 amd64 [installed]
libpsl5/bionic,now 0.19.1-5build1 amd64 [installed]
libpython3-stdlib/bionic-updates,now 3.6.7-1~18.04 amd64 [installed]
libpython3.6-minimal/bionic-updates,now 3.6.9-1~18.04 amd64 [installed]
libpython3.6-stdlib/bionic-updates,now 3.6.9-1~18.04 amd64 [installed]
libreadline5/bionic,now 5.2+dfsg-3build1 amd64 [installed,automatic]
libreadline7/bionic,now 7.0-3 amd64 [installed]
libseccomp2/bionic-updates,bionic-security,now 2.4.1-0ubuntu0.18.04.2 amd64 [installed]
libselinux1/bionic,now 2.7-2build2 amd64 [installed]
libsemanage-common/bionic,bionic,now 2.7-2build2 all [installed]
libsemanage1/bionic,now 2.7-2build2 amd64 [installed]
libsepol1/bionic,now 2.7-1 amd64 [installed]
libslang2/bionic,now 2.3.1a-3ubuntu1 amd64 [installed]
libsmartcols1/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
libsqlite3-0/bionic-updates,bionic-security,now 3.22.0-1ubuntu0.2 amd64 [installed]
libss2/bionic-updates,bionic-security,now 1.44.1-1ubuntu1.3 amd64 [installed]
libssl1.0.0/bionic-updates,bionic-security,now 1.0.2n-1ubuntu5.3 amd64 [installed]
libssl1.1/bionic-updates,bionic-security,now 1.1.1-1ubuntu2.1~18.04.5 amd64 [installed]
libstdc++6/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed]
libsystemd0/bionic-updates,now 237-3ubuntu10.39 amd64 [installed]
libtasn1-6/bionic,now 4.13-2 amd64 [installed]
libtext-charwidth-perl/bionic,now 0.04-7.1 amd64 [installed]
libtext-iconv-perl/bionic,now 1.7-5build6 amd64 [installed]
libtext-wrapi18n-perl/bionic,bionic,now 0.06-7.1 all [installed]
libtinfo5/bionic-updates,now 6.1-1ubuntu1.18.04 amd64 [installed]
libudev1/bionic-updates,now 237-3ubuntu10.39 amd64 [installed]
libunistring2/bionic-updates,now 0.9.9-0ubuntu2 amd64 [installed]
libunwind8/bionic,now 1.2.1-8 amd64 [installed]
libusb-1.0-0/bionic,now 2:1.0.21-2 amd64 [installed]
libuuid1/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
libwrap0/bionic,now 7.6.q-27 amd64 [installed]
libx11-6/bionic-updates,now 2:1.6.4-3ubuntu0.2 amd64 [installed]
libx11-data/bionic-updates,bionic-updates,now 2:1.6.4-3ubuntu0.2 all [installed]
libxau6/bionic,now 1:1.0.8-1 amd64 [installed]
libxcb1/bionic-updates,now 1.13-2~ubuntu18.04 amd64 [installed]
libxdmcp6/bionic,now 1:1.1.2-3 amd64 [installed]
libxext6/bionic,now 2:1.3.3-1 amd64 [installed]
libxml2/bionic-updates,bionic-security,now 2.9.4+dfsg1-6.1ubuntu1.3 amd64 [installed]
libxmuu1/bionic,now 2:1.1.2-2 amd64 [installed]
libxtables12/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
libyaml-0-2/bionic,now 0.1.7-2ubuntu3 amd64 [installed]
libzstd1/bionic-updates,bionic-security,now 1.3.3+dfsg-2ubuntu1.1 amd64 [installed]
linux-base/bionic,bionic,now 4.5ubuntu1 all [installed]
linux-firmware/bionic-updates,bionic-updates,now 1.173.15 all [installed,automatic]
linux-generic/bionic-updates,bionic-security,now 4.15.0.88.80 amd64 [installed]
linux-headers-4.15.0-88/bionic-updates,bionic-updates,bionic-security,bionic-security,now 4.15.0-88.88 all [installed,automatic]
linux-headers-4.15.0-88-generic/bionic-updates,bionic-security,now 4.15.0-88.88 amd64 [installed,automatic]
linux-headers-generic/bionic-updates,bionic-security,now 4.15.0.88.80 amd64 [installed]
linux-image-4.15.0-88-generic/bionic-updates,bionic-security,now 4.15.0-88.88 amd64 [installed,automatic]
linux-image-generic/bionic-updates,bionic-security,now 4.15.0.88.80 amd64 [installed,automatic]
linux-modules-4.15.0-88-generic/bionic-updates,bionic-security,now 4.15.0-88.88 amd64 [installed,automatic]
linux-modules-extra-4.15.0-88-generic/bionic-updates,bionic-security,now 4.15.0-88.88 amd64 [installed,automatic]
locales/bionic,bionic,now 2.27-3ubuntu1 all [installed]
login/bionic-updates,now 1:4.5-1ubuntu2 amd64 [installed]
logrotate/bionic,now 3.11.0-0.1ubuntu1 amd64 [installed]
lsb-base/bionic,bionic,now 9.20170808ubuntu1 all [installed]
lsb-release/bionic,bionic,now 9.20170808ubuntu1 all [installed]
lshw/bionic-updates,now 02.18-0.1ubuntu6.18.04.1 amd64 [installed]
lsof/bionic,now 4.89+dfsg-0.1 amd64 [installed]
ltrace/bionic,now 0.7.3-6ubuntu1 amd64 [installed]
lvm2/bionic-updates,now 2.02.176-4.1ubuntu3.18.04.2 amd64 [installed]
man-db/bionic-updates,now 2.8.3-2ubuntu0.1 amd64 [installed]
manpages/bionic,bionic,now 4.15-1 all [installed]
mawk/bionic,now 1.3.3-17ubuntu3 amd64 [installed]
mime-support/bionic,bionic,now 3.60ubuntu1 all [installed]
mlocate/bionic,now 0.26-2ubuntu3.1 amd64 [installed]
mount/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
mtr-tiny/bionic,now 0.92-1 amd64 [installed]
multiarch-support/bionic,now 2.27-3ubuntu1 amd64 [installed]
nano/bionic,now 2.9.3-2 amd64 [installed]
ncurses-base/bionic-updates,bionic-updates,now 6.1-1ubuntu1.18.04 all [installed]
ncurses-bin/bionic-updates,now 6.1-1ubuntu1.18.04 amd64 [installed]
ncurses-term/bionic-updates,bionic-updates,now 6.1-1ubuntu1.18.04 all [installed]
netbase/bionic,bionic,now 5.4 all [installed]
netcat-openbsd/bionic-updates,now 1.187-1ubuntu0.1 amd64 [installed]
netplan.io/bionic-updates,now 0.98-0ubuntu1~18.04.1 amd64 [installed]
networkd-dispatcher/bionic-updates,bionic-updates,now 1.7-0ubuntu3.3 all [installed]
nplan/bionic-updates,bionic-updates,now 0.98-0ubuntu1~18.04.1 all [installed]
ntfs-3g/bionic-updates,bionic-security,now 1:2017.3.23-2ubuntu0.18.04.2 amd64 [installed]
openssh-client/bionic-updates,bionic-security,now 1:7.6p1-4ubuntu0.3 amd64 [installed]
openssh-server/bionic-updates,bionic-security,now 1:7.6p1-4ubuntu0.3 amd64 [installed]
openssh-sftp-server/bionic-updates,bionic-security,now 1:7.6p1-4ubuntu0.3 amd64 [installed]
openssl/bionic-updates,bionic-security,now 1.1.1-1ubuntu2.1~18.04.5 amd64 [installed]
os-prober/bionic,now 1.74ubuntu1 amd64 [installed,automatic]
parted/bionic-updates,now 3.2-20ubuntu0.2 amd64 [installed]
passwd/bionic-updates,now 1:4.5-1ubuntu2 amd64 [installed]
pciutils/bionic-updates,now 1:3.5.2-1ubuntu1.1 amd64 [installed]
perl-base/bionic-updates,bionic-security,now 5.26.1-6ubuntu0.3 amd64 [installed]
plymouth/bionic-updates,now 0.9.3-1ubuntu7.18.04.2 amd64 [installed]
plymouth-theme-ubuntu-text/bionic-updates,now 0.9.3-1ubuntu7.18.04.2 amd64 [installed]
popularity-contest/bionic,bionic,now 1.66ubuntu1 all [installed]
powermgmt-base/bionic,bionic,now 1.33 all [installed]
procps/bionic-updates,now 2:3.3.12-3ubuntu1.2 amd64 [installed]
psmisc/bionic-updates,now 23.1-1ubuntu0.1 amd64 [installed]
publicsuffix/bionic,bionic,now 20180223.1310-1 all [installed]
python-apt-common/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1.6.5ubuntu0.2 all [installed]
python3/bionic-updates,now 3.6.7-1~18.04 amd64 [installed]
python3-apt/bionic-updates,bionic-security,now 1.6.5ubuntu0.2 amd64 [installed]
python3-certifi/bionic,bionic,now 2018.1.18-2 all [installed]
python3-chardet/bionic,bionic,now 3.0.4-1 all [installed]
python3-commandnotfound/bionic-updates,bionic-updates,now 18.04.5 all [installed]
python3-dbus/bionic,now 1.2.6-1 amd64 [installed]
python3-distro-info/bionic-updates,bionic-updates,bionic-security,bionic-security,now 0.18ubuntu0.18.04.1 all [installed]
python3-distupgrade/bionic-updates,bionic-updates,now 1:18.04.37 all [installed]
python3-gdbm/bionic-updates,now 3.6.9-1~18.04 amd64 [installed]
python3-gi/bionic-updates,now 3.26.1-2ubuntu1 amd64 [installed]
python3-idna/bionic,bionic,now 2.6-1 all [installed]
python3-minimal/bionic-updates,now 3.6.7-1~18.04 amd64 [installed]
python3-netifaces/bionic,now 0.10.4-0.1build4 amd64 [installed,automatic]
python3-pkg-resources/bionic,bionic,now 39.0.1-2 all [installed]
python3-requests/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2.18.4-2ubuntu0.1 all [installed]
python3-six/bionic,bionic,now 1.11.0-2 all [installed]
python3-update-manager/bionic-updates,bionic-updates,now 1:18.04.11.10 all [installed]
python3-urllib3/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1.22-1ubuntu0.18.04.1 all [installed]
python3-yaml/bionic,now 3.12-1build2 amd64 [installed]
python3.6/bionic-updates,now 3.6.9-1~18.04 amd64 [installed]
python3.6-minimal/bionic-updates,now 3.6.9-1~18.04 amd64 [installed]
readline-common/bionic,bionic,now 7.0-3 all [installed]
rsync/bionic-updates,bionic-security,now 3.1.2-2.1ubuntu1.1 amd64 [installed]
rsyslog/bionic,now 8.32.0-1ubuntu4 amd64 [installed]
sed/bionic,now 4.4-2 amd64 [installed]
sensible-utils/bionic,bionic,now 0.0.12 all [installed]
shared-mime-info/bionic,now 1.9-2 amd64 [installed]
ssh-import-id/bionic-updates,bionic-updates,now 5.7-0ubuntu1.1 all [installed]
strace/bionic,now 4.21-1ubuntu1 amd64 [installed]
sudo/bionic-updates,bionic-security,now 1.8.21p2-3ubuntu1.2 amd64 [installed]
systemd/bionic-updates,now 237-3ubuntu10.39 amd64 [installed]
systemd-sysv/bionic-updates,now 237-3ubuntu10.39 amd64 [installed]
sysvinit-utils/bionic,now 2.88dsf-59.10ubuntu1 amd64 [installed]
tar/bionic-updates,now 1.29b-2ubuntu0.1 amd64 [installed]
tasksel/bionic,bionic,now 3.34ubuntu11 all [installed]
tasksel-data/bionic,bionic,now 3.34ubuntu11 all [installed,automatic]
tcpdump/bionic-updates,bionic-security,now 4.9.3-0ubuntu0.18.04.1 amd64 [installed]
telnet/bionic,now 0.17-41 amd64 [installed]
time/bionic,now 1.7-25.1build1 amd64 [installed]
tzdata/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2019c-0ubuntu0.18.04 all [installed]
ubuntu-advantage-tools/bionic,bionic,now 17 all [installed]
ubuntu-keyring/bionic-updates,bionic-updates,now 2018.09.18.1~18.04.0 all [installed]
ubuntu-minimal/bionic-updates,now 1.417.4 amd64 [installed]
ubuntu-release-upgrader-core/bionic-updates,bionic-updates,now 1:18.04.37 all [installed]
ubuntu-standard/bionic-updates,now 1.417.4 amd64 [installed]
ucf/bionic,bionic,now 3.0038 all [installed]
udev/bionic-updates,now 237-3ubuntu10.39 amd64 [installed]
ufw/bionic-updates,bionic-updates,now 0.36-0ubuntu0.18.04.1 all [installed]
update-manager-core/bionic-updates,bionic-updates,now 1:18.04.11.10 all [installed]
ureadahead/bionic-updates,now 0.100.0-21 amd64 [installed]
usbutils/bionic,now 1:007-4build1 amd64 [installed]
util-linux/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
uuid-runtime/bionic-updates,now 2.31.1-0.4ubuntu3.5 amd64 [installed]
vim-common/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2:8.0.1453-1ubuntu1.1 all [installed]
vim-tiny/bionic-updates,bionic-security,now 2:8.0.1453-1ubuntu1.1 amd64 [installed]
wamerican/bionic,bionic,now 2017.08.24-1 all [installed]
wbritish/bionic,bionic,now 2017.08.24-1 all [installed]
wget/bionic-updates,bionic-security,now 1.19.4-1ubuntu2.2 amd64 [installed]
whiptail/bionic,now 0.52.20-1ubuntu1 amd64 [installed]
wireless-regdb/bionic-updates,bionic-updates,now 2018.05.09-0ubuntu1~18.04.1 all [installed,automatic]
xauth/bionic,now 1:1.0.10-1 amd64 [installed]
xdg-user-dirs/bionic,now 0.17-1ubuntu1 amd64 [installed]
xkb-data/bionic-updates,bionic-updates,now 2.23.1-1ubuntu1.18.04.1 all [installed]
xxd/bionic-updates,bionic-security,now 2:8.0.1453-1ubuntu1.1 amd64 [installed]
xz-utils/bionic,now 5.2.2-1.3 amd64 [installed]
zlib1g/bionic,now 1:1.2.11.dfsg-0ubuntu2 amd64 [installed]

```

---

### Post by LHammonds on 2020-02-28
If I am seeing this right, the [Ubuntu Server 18.04 Network (Minimal) Installer](https://ubuntu.com/download/alternative-downloads#network-installer) has 2 packages that the standard install does not have:

```

language-pack-gnome-en/bionic-updates,bionic-updates,now 1:18.04+20190718 all [installed]
language-pack-gnome-en-base/bionic-updates,bionic-updates,now 1:18.04+20180712 all [installed,automatic] 

```

The [Ubuntu Server 18.04 traditional installer](https://ubuntu.com/download/alternative-downloads#alternate-ubuntu-server-installer) has 139 packages that the Network Installer does not have:

```

acl/bionic,now 2.2.52-3build1 amd64 [installed]
acpid/bionic,now 1:2.0.28-1ubuntu1 amd64 [installed]
apport/bionic-updates,bionic-updates,now 2.20.9-0ubuntu7.11 all [installed]
apport-symptoms/bionic,bionic,now 0.20 all [installed]
at/bionic,now 3.1.20-3.1ubuntu2 amd64 [installed]
bc/bionic,now 1.07.1-2 amd64 [installed]
bcache-tools/bionic,now 1.0.8-2build1 amd64 [installed]
btrfs-progs/bionic,now 4.15.1-1build1 amd64 [installed]
btrfs-tools/bionic,now 4.15.1-1build1 amd64 [installed]
byobu/bionic,bionic,now 5.125-0ubuntu1 all [installed]
cloud-guest-utils/bionic,bionic,now 0.30-0ubuntu5 all [installed]
cloud-initramfs-copymods/bionic-updates,bionic-updates,now 0.40ubuntu1.1 all [installed]
cloud-initramfs-dyn-netconf/bionic-updates,bionic-updates,now 0.40ubuntu1.1 all [installed] 
cryptsetup/bionic-updates,now 2:2.0.2-1ubuntu1.1 amd64 [installed]
cryptsetup-bin/bionic-updates,now 2:2.0.2-1ubuntu1.1 amd64 [installed]
curl/bionic-updates,bionic-security,now 7.58.0-2ubuntu3.8 amd64 [installed]
dirmngr/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
dns-root-data/bionic,bionic,now 2018013001 all [installed]
dnsmasq-base/bionic,now 2.79-1 amd64 [installed]
ebtables/bionic-updates,now 2.0.10.4-3.5ubuntu2.18.04.3 amd64 [installed]
fonts-ubuntu-console/bionic,bionic,now 0.83-2 all [installed]
gawk/bionic,now 1:4.1.4+dfsg-1build1 amd64 [installed]
git/bionic-updates,bionic-security,now 1:2.17.1-1ubuntu0.5 amd64 [installed]
git-man/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1:2.17.1-1ubuntu0.5 all [installed]
gnupg/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gnupg-l10n/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2.2.4-1ubuntu1.2 all [installed]
gnupg-utils/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpg/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpg-agent/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpg-wks-client/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpg-wks-server/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpgconf/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
gpgsm/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
grub-legacy-ec2/bionic,bionic,now 1:1 all [installed]
htop/bionic,now 2.1.0-3 amd64 [installed]
landscape-common/bionic-updates,now 18.01-0ubuntu3.4 amd64 [installed]
libasn1-8-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libassuan0/bionic,now 2.5.1-2 amd64 [installed]
libcurl3-gnutls/bionic-updates,bionic-security,now 7.58.0-2ubuntu3.8 amd64 [installed]
libcurl4/bionic-updates,bionic-security,now 7.58.0-2ubuntu3.8 amd64 [installed]
libdumbnet1/bionic,now 1.12-7build1 amd64 [installed]
liberror-perl/bionic,bionic,now 0.17025-1 all [installed]
libevent-2.1-6/bionic,now 2.1.8-stable-4build1 amd64 [installed]
libgdbm-compat4/bionic,now 1.14.1-6 amd64 [installed]
libgpm2/bionic,now 1.20.7-5 amd64 [installed]
libgssapi3-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libhcrypto4-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libheimbase1-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libheimntlm0-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libhx509-5-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libisns0/bionic,now 0.97-2build1 amd64 [installed]
libkrb5-26-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libksba8/bionic,now 1.3.5-2 amd64 [installed]
libldap-2.4-2/bionic-updates,now 2.4.45+dfsg-1ubuntu1.4 amd64 [installed]
libldap-common/bionic-updates,bionic-updates,now 2.4.45+dfsg-1ubuntu1.4 all [installed]
liblxc-common/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
liblxc1/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
liblzo2-2/bionic,now 2.08-1.2 amd64 [installed]
libmpfr6/bionic,now 4.0.1-1 amd64 [installed]
libmspack0/bionic-updates,bionic-security,now 0.6-3ubuntu0.3 amd64 [installed]
libnghttp2-14/bionic,now 1.30.0-1ubuntu1 amd64 [installed]
libnpth0/bionic,now 1.5-3 amd64 [installed]
libperl5.26/bionic-updates,bionic-security,now 5.26.1-6ubuntu0.3 amd64 [installed]
libpolkit-agent-1-0/bionic-updates,bionic-security,now 0.105-20ubuntu0.18.04.5 amd64 [installed]
libpolkit-backend-1-0/bionic-updates,bionic-security,now 0.105-20ubuntu0.18.04.5 amd64 [installed]
libpython3.6-minimal/bionic-updates,now 3.6.9-1~18.04 amd64 [installed,automatic]
libpython3.6-stdlib/bionic-updates,now 3.6.9-1~18.04 amd64 [installed,automatic]
libroken18-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
librtmp1/bionic,now 2.4+20151223.gitfa8646d.1-1 amd64 [installed]
libsasl2-2/bionic-updates,bionic-security,now 2.1.27~101-g0780600+dfsg-3ubuntu2.1 amd64 [installed]
libsasl2-modules/bionic-updates,bionic-security,now 2.1.27~101-g0780600+dfsg-3ubuntu2.1 amd64 [installed]
libsasl2-modules-db/bionic-updates,bionic-security,now 2.1.27~101-g0780600+dfsg-3ubuntu2.1 amd64 [installed]
libsigsegv2/bionic,now 2.12-1 amd64 [installed]
libutempter0/bionic,now 1.1.6-3 amd64 [installed]
libuv1/bionic,now 1.18.0-3 amd64 [installed]
libwind0-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
libxmlsec1/bionic,now 1.2.25-1build1 amd64 [installed]
libxmlsec1-openssl/bionic,now 1.2.25-1build1 amd64 [installed]
libxslt1.1/bionic-updates,bionic-security,now 1.1.29-5ubuntu0.2 amd64 [installed]
linux-headers-4.15.0-55/bionic-updates,bionic-updates,bionic-security,bionic-security,now 4.15.0-55.60 all [installed,automatic]
linux-headers-4.15.0-55-generic/bionic-updates,bionic-security,now 4.15.0-55.60 amd64 [installed,automatic]
linux-image-4.15.0-55-generic/bionic-updates,bionic-security,now 4.15.0-55.60 amd64 [installed,automatic]
linux-modules-4.15.0-55-generic/bionic-updates,bionic-security,now 4.15.0-55.60 amd64 [installed,automatic]
linux-modules-extra-4.15.0-55-generic/bionic-updates,bionic-security,now 4.15.0-55.60 amd64 [installed,automatic]
lxcfs/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
lxd/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
lxd-client/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
mdadm/bionic-updates,now 4.1~rc1-3~ubuntu18.04.4 amd64 [installed]
net-tools/bionic,now 1.60+git20161116.90da8a0-1ubuntu1 amd64 [installed]
open-iscsi/bionic-updates,now 2.0.874-5ubuntu2.7 amd64 [installed]
open-vm-tools/bionic-updates,now 2:11.0.1-2ubuntu0.18.04.2 amd64 [installed]
overlayroot/bionic-updates,bionic-updates,now 0.40ubuntu1.1 all [installed]
pastebinit/bionic,bionic,now 1.5-2 all [installed]
patch/bionic-updates,bionic-security,now 2.7.6-2ubuntu1.1 amd64 [installed]
perl/bionic-updates,bionic-security,now 5.26.1-6ubuntu0.3 amd64 [installed]
perl-modules-5.26/bionic-updates,bionic-updates,bionic-security,bionic-security,now 5.26.1-6ubuntu0.3 all [installed]
pinentry-curses/bionic,now 1.1.0-1 amd64 [installed]
policykit-1/bionic-updates,bionic-security,now 0.105-20ubuntu0.18.04.5 amd64 [installed]
pollinate/bionic-updates,bionic-updates,now 4.33-0ubuntu1~18.04.1 all [installed]
python3-apport/bionic-updates,bionic-updates,now 2.20.9-0ubuntu7.11 all [installed]
python3-asn1crypto/bionic,bionic,now 0.24.0-1 all [installed]
python3-attr/bionic,bionic,now 17.4.0-2 all [installed]
python3-automat/bionic,bionic,now 0.6.0-1 all [installed]
python3-cffi-backend/bionic,now 1.11.5-1 amd64 [installed]
python3-click/bionic,bionic,now 6.7-3 all [installed]
python3-colorama/bionic,bionic,now 0.3.7-1 all [installed]
python3-configobj/bionic,bionic,now 5.0.6-2 all [installed]
python3-constantly/bionic,bionic,now 15.1.0-1 all [installed]
python3-cryptography/bionic-updates,bionic-security,now 2.1.4-1ubuntu1.3 amd64 [installed]
python3-debconf/bionic-updates,bionic-updates,now 1.5.66ubuntu1 all [installed]
python3-debian/bionic,bionic,now 0.1.32 all [installed]
python3-httplib2/bionic-updates,bionic-updates,now 0.9.2+dfsg-1ubuntu0.1 all [installed]
python3-hyperlink/bionic,bionic,now 17.3.1-2 all [installed]
python3-incremental/bionic,bionic,now 16.10.1-3 all [installed]
python3-newt/bionic,now 0.52.20-1ubuntu1 amd64 [installed]
python3-openssl/bionic,bionic,now 17.5.0-1ubuntu1 all [installed]
python3-pam/bionic,now 0.4.2-13.2ubuntu4 amd64 [installed]
python3-problem-report/bionic-updates,bionic-updates,now 2.20.9-0ubuntu7.11 all [installed]
python3-pyasn1/bionic,bionic,now 0.4.2-3 all [installed]
python3-pyasn1-modules/bionic,bionic,now 0.2.1-0.2 all [installed]
python3-requests-unixsocket/bionic,bionic,now 0.1.5-3 all [installed]
python3-serial/bionic,bionic,now 3.4-2 all [installed]
python3-service-identity/bionic,bionic,now 16.0.0-2 all [installed]
python3-software-properties/bionic-updates,bionic-updates,now 0.96.24.32.12 all [installed]
python3-systemd/bionic,now 234-1build1 amd64 [installed]
python3-twisted/bionic,bionic,now 17.9.0-2 all [installed]
python3-twisted-bin/bionic,now 17.9.0-2 amd64 [installed]
python3-zope.interface/bionic,now 4.3.2-1build2 amd64 [installed]
run-one/bionic,bionic,now 1.17-0ubuntu1 all [installed]
screen/bionic-updates,now 4.6.2-1ubuntu1 amd64 [installed]
tmux/bionic-updates,now 2.6-3ubuntu0.2 amd64 [installed]
ubuntu-server/bionic-updates,now 1.417.4 amd64 [installed]
uidmap/bionic-updates,now 1:4.5-1ubuntu2 amd64 [installed]
unattended-upgrades/bionic-updates,bionic-updates,now 1.1ubuntu1.18.04.13 all [installed]
update-notifier-common/bionic-updates,bionic-updates,now 3.192.1.7 all [installed]
vim-common/bionic-updates,bionic-updates,bionic-security,bionic-security,now 2:8.0.1453-1ubuntu1.1 all [installed,automatic]
xdelta3/bionic,now 3.0.11-dfsg-1ubuntu1 amd64 [installed]
xfsprogs/bionic,now 4.9.0+nmu1ubuntu2 amd64 [installed]
zerofree/bionic,now 1.0.4-1 amd64 [installed]

```

---

### Post by LHammonds on 2020-05-10
Even though I'm not using Ubuntu for a base KVM server now, I still need to know what packages are installed depending on which installer is used so I'll document that here.

Command to show what is installed:
```
apt list --installed
```

NOTE: lines in bold green are installed by the specific installer only.

Ubuntu 20.04 LTS Live Installer (unpatched, 1st version of the ISO image) - 568 installed entries:
```

accountsservice/focal,now 0.6.55-0ubuntu11 amd64
adduser/focal,now 3.118ubuntu2 all
alsa-topology-conf/focal,now 1.2.2-1 all
alsa-ucm-conf/focal,now 1.2.2-1 all
amd64-microcode/focal,now 3.20191218.1ubuntu1 amd64
apparmor/focal,now 2.13.3-7ubuntu5 amd64
apport-symptoms/focal,now 0.23 all
apport/focal,now 2.20.11-0ubuntu27 all
apt-utils/focal,now 2.0.2 amd64
apt/focal,now 2.0.2 amd64
at/focal,now 3.1.23-1ubuntu1 amd64
base-files/focal,now 11ubuntu5 amd64
base-passwd/focal,now 3.5.47 amd64
bash-completion/focal,now 1:2.10-1ubuntu1 all
bash/focal,now 5.0-6ubuntu1 amd64
bc/focal,now 1.07.1-2build1 amd64
bcache-tools/focal,now 1.0.8-3 amd64
bind9-dnsutils/focal,now 1:9.16.1-0ubuntu2 amd64
bind9-host/focal,now 1:9.16.1-0ubuntu2 amd64
bind9-libs/focal,now 1:9.16.1-0ubuntu2 amd64
bolt/focal,now 0.8-4 amd64
bsdmainutils/focal,now 11.1.2ubuntu3 amd64
bsdutils/focal,now 1:2.34-0.1ubuntu9 amd64
btrfs-progs/focal,now 5.4.1-2 amd64
busybox-initramfs/focal,now 1:1.30.1-4ubuntu6 amd64
busybox-static/focal,now 1:1.30.1-4ubuntu6 amd64
byobu/focal,now 5.133-0ubuntu1 all
bzip2/focal,now 1.0.8-2 amd64
ca-certificates/focal,now 20190110ubuntu1 all
cloud-guest-utils/focal,now 0.31-7-gd99b2d76-0ubuntu1 all
[COLOR=green]**cloud-init/focal,now 20.1-10-g71af48df-0ubuntu5 all**[/COLOR]
cloud-initramfs-copymods/focal,now 0.45ubuntu1 all
cloud-initramfs-dyn-netconf/focal,now 0.45ubuntu1 all
command-not-found/focal,now 20.04.2 all
console-setup-linux/focal,now 1.194ubuntu3 all
[COLOR=green]**console-setup/focal,now 1.194ubuntu3 all**[/COLOR]
coreutils/focal,now 8.30-3ubuntu2 amd64
cpio/focal,now 2.13+dfsg-2 amd64
crda/focal,now 3.18-1build1 amd64
cron/focal,now 3.0pl1-136ubuntu1 amd64
cryptsetup-bin/focal,now 2:2.2.2-3ubuntu2 amd64
cryptsetup-initramfs/focal,now 2:2.2.2-3ubuntu2 all
cryptsetup-run/focal,now 2:2.2.2-3ubuntu2 all
cryptsetup/focal,now 2:2.2.2-3ubuntu2 amd64
curl/focal,now 7.68.0-1ubuntu2 amd64
dash/focal,now 0.5.10.2-6 amd64
dbus-user-session/focal,now 1.12.16-2ubuntu2 amd64
dbus/focal,now 1.12.16-2ubuntu2 amd64
dconf-gsettings-backend/focal,now 0.36.0-1 amd64
dconf-service/focal,now 0.36.0-1 amd64
debconf-i18n/focal,now 1.5.73 all
debconf/focal,now 1.5.73 all
debianutils/focal,now 4.9.1 amd64
diffutils/focal,now 1:3.7-3 amd64
dirmngr/focal,now 2.2.19-3ubuntu2 amd64
distro-info-data/focal,now 0.43ubuntu1 all
dmeventd/focal,now 2:1.02.167-1ubuntu1 amd64
dmidecode/focal,now 3.2-3 amd64
dmsetup/focal,now 2:1.02.167-1ubuntu1 amd64
dosfstools/focal,now 4.1-2 amd64
dpkg/focal,now 1.19.7ubuntu3 amd64
e2fsprogs/focal,now 1.45.5-2ubuntu1 amd64
[COLOR=green]**eatmydata/focal,now 105-7 all**[/COLOR]
ed/focal,now 1.16-1 amd64
eject/focal,now 2.1.5+deb1+cvs20081104-14 amd64
ethtool/focal,now 1:5.4-1 amd64
fdisk/focal,now 2.34-0.1ubuntu9 amd64
file/focal,now 1:5.38-4 amd64
finalrd/focal,now 5 all
findutils/focal,now 4.7.0-1ubuntu1 amd64
fonts-ubuntu-console/focal,now 0.83-4ubuntu1 all
friendly-recovery/focal,now 0.2.41 all
ftp/focal,now 0.17-34.1 amd64
fuse/focal,now 2.9.9-3 amd64
fwupd-signed/focal,now 1.27+1.3.9-4 amd64
fwupd/focal,now 1.3.9-4 amd64
gawk/focal,now 1:5.0.1+dfsg-1 amd64
gcc-10-base/focal,now 10-20200411-0ubuntu1 amd64
[COLOR=green]**gdisk/focal,now 1.0.5-1 amd64**[/COLOR]
gettext-base/focal,now 0.19.8.1-10build1 amd64
gir1.2-glib-2.0/focal,now 1.64.0-2 amd64
gir1.2-packagekitglib-1.0/focal,now 1.1.13-2ubuntu1 amd64
git-man/focal,now 1:2.25.1-1ubuntu3 all
git/focal,now 1:2.25.1-1ubuntu3 amd64
glib-networking-common/focal,now 2.64.1-1 all
glib-networking-services/focal,now 2.64.1-1 amd64
glib-networking/focal,now 2.64.1-1 amd64
gnupg-l10n/focal,now 2.2.19-3ubuntu2 all
gnupg-utils/focal,now 2.2.19-3ubuntu2 amd64
gnupg/focal,now 2.2.19-3ubuntu2 all
gpg-agent/focal,now 2.2.19-3ubuntu2 amd64
gpg-wks-client/focal,now 2.2.19-3ubuntu2 amd64
gpg-wks-server/focal,now 2.2.19-3ubuntu2 amd64
gpg/focal,now 2.2.19-3ubuntu2 amd64
gpgconf/focal,now 2.2.19-3ubuntu2 amd64
gpgsm/focal,now 2.2.19-3ubuntu2 amd64
gpgv/focal,now 2.2.19-3ubuntu2 amd64
grep/focal,now 3.4-1 amd64
groff-base/focal,now 1.22.4-4build1 amd64
grub-common/focal,now 2.04-1ubuntu26 amd64
grub-gfxpayload-lists/focal,now 0.7 amd64
grub-pc-bin/focal,now 2.04-1ubuntu26 amd64
grub-pc/focal,now 2.04-1ubuntu26 amd64
grub2-common/focal,now 2.04-1ubuntu26 amd64
gsettings-desktop-schemas/focal,now 3.36.0-1ubuntu1 all
gzip/focal,now 1.10-0ubuntu4 amd64
hdparm/focal,now 9.58+ds-4 amd64
hostname/focal,now 3.23 amd64
htop/focal,now 2.2.0-2build1 amd64
info/focal,now 6.7.0.dfsg.2-5 amd64
init-system-helpers/focal,now 1.57 all
init/focal,now 1.57 amd64
initramfs-tools-bin/focal,now 0.136ubuntu6 amd64
initramfs-tools-core/focal,now 0.136ubuntu6 all
initramfs-tools/focal,now 0.136ubuntu6 all
install-info/focal,now 6.7.0.dfsg.2-5 amd64
intel-microcode/focal,now 3.20191115.1ubuntu3 amd64
iproute2/focal,now 5.5.0-1ubuntu1 amd64
iptables/focal,now 1.8.4-3ubuntu2 amd64
iputils-ping/focal,now 3:20190709-3 amd64
iputils-tracepath/focal,now 3:20190709-3 amd64
irqbalance/focal,now 1.6.0-3ubuntu1 amd64
isc-dhcp-client/focal,now 4.4.1-2.1ubuntu5 amd64
isc-dhcp-common/focal,now 4.4.1-2.1ubuntu5 amd64
iso-codes/focal,now 4.4-1 all
iucode-tool/focal,now 2.3.1-1 amd64
iw/focal,now 5.4-1 amd64
kbd/focal,now 2.0.4-4ubuntu2 amd64
keyboard-configuration/focal,now 1.194ubuntu3 all
klibc-utils/focal,now 2.0.7-1ubuntu5 amd64
kmod/focal,now 27-1ubuntu2 amd64
kpartx/focal,now 0.8.3-1ubuntu2 amd64
krb5-locales/focal,now 1.17-6ubuntu4 all
landscape-common/focal,now 19.12-0ubuntu4 amd64
language-selector-common/focal,now 0.204 all
less/focal,now 551-1 amd64
libaccountsservice0/focal,now 0.6.55-0ubuntu11 amd64
libacl1/focal,now 2.2.53-6 amd64
libaio1/focal,now 0.3.112-5 amd64
libapparmor1/focal,now 2.13.3-7ubuntu5 amd64
libappstream4/focal,now 0.12.10-2 amd64
libapt-pkg6.0/focal,now 2.0.2 amd64
libarchive13/focal,now 3.4.0-2ubuntu1 amd64
libargon2-1/focal,now 0~20171227-0.2 amd64
libasn1-8-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libasound2-data/focal,now 1.2.2-2.1 all
libasound2/focal,now 1.2.2-2.1 amd64
libassuan0/focal,now 2.5.3-7ubuntu2 amd64
libatm1/focal,now 1:2.5.1-4 amd64
libattr1/focal,now 1:2.4.48-5 amd64
libaudit-common/focal,now 1:2.8.5-2ubuntu6 all
libaudit1/focal,now 1:2.8.5-2ubuntu6 amd64
libblkid1/focal,now 2.34-0.1ubuntu9 amd64
libbrotli1/focal,now 1.0.7-6build1 amd64
libbsd0/focal,now 0.10.0-1 amd64
libbz2-1.0/focal,now 1.0.8-2 amd64
libc-bin/focal,now 2.31-0ubuntu9 amd64
libc6/focal,now 2.31-0ubuntu9 amd64
libcanberra0/focal,now 0.30-7ubuntu1 amd64
libcap-ng0/focal,now 0.7.9-2.1build1 amd64
libcap2-bin/focal,now 1:2.32-1 amd64
libcap2/focal,now 1:2.32-1 amd64
libcbor0.6/focal,now 0.6.0-0ubuntu1 amd64
libcom-err2/focal,now 1.45.5-2ubuntu1 amd64
libcrypt1/focal,now 1:4.4.10-10ubuntu4 amd64
libcryptsetup12/focal,now 2:2.2.2-3ubuntu2 amd64
libcurl3-gnutls/focal,now 7.68.0-1ubuntu2 amd64
libcurl4/focal,now 7.68.0-1ubuntu2 amd64
libdb5.3/focal,now 5.3.28+dfsg1-0.6ubuntu2 amd64
libdbus-1-3/focal,now 1.12.16-2ubuntu2 amd64
libdbus-glib-1-2/focal,now 0.110-5fakssync1 amd64
libdconf1/focal,now 0.36.0-1 amd64
libdebconfclient0/focal,now 0.251ubuntu1 amd64
libdevmapper-event1.02.1/focal,now 2:1.02.167-1ubuntu1 amd64
libdevmapper1.02.1/focal,now 2:1.02.167-1ubuntu1 amd64
libdns-export1109/focal,now 1:9.11.16+dfsg-3~build1 amd64
libdrm-common/focal,now 2.4.101-2 all
libdrm2/focal,now 2.4.101-2 amd64
[COLOR=green]**libeatmydata1/focal,now 105-7 amd64**[/COLOR]
libedit2/focal,now 3.1-20191231-1 amd64
libefiboot1/focal,now 37-2ubuntu2 amd64
libefivar1/focal,now 37-2ubuntu2 amd64
libelf1/focal,now 0.176-1.1build1 amd64
liberror-perl/focal,now 0.17029-1 all
libestr0/focal,now 0.1.10-2.1 amd64
libevent-2.1-7/focal,now 2.1.11-stable-1 amd64
libexpat1/focal,now 2.2.9-1build1 amd64
libext2fs2/focal,now 1.45.5-2ubuntu1 amd64
libfastjson4/focal,now 0.99.8-2 amd64
libfdisk1/focal,now 2.34-0.1ubuntu9 amd64
libffi7/focal,now 3.3-4 amd64
libfido2-1/focal,now 1.3.1-1ubuntu2 amd64
libfl2/focal,now 2.6.4-6.2 amd64
libfreetype6/focal,now 2.10.1-2 amd64
libfribidi0/focal,now 1.0.8-2 amd64
libfuse2/focal,now 2.9.9-3 amd64
libfwupd2/focal,now 1.3.9-4 amd64
libfwupdplugin1/focal,now 1.3.9-4 amd64
libgcab-1.0-0/focal,now 1.4-1 amd64
libgcc-s1/focal,now 10-20200411-0ubuntu1 amd64
libgcrypt20/focal,now 1.8.5-5ubuntu1 amd64
libgdbm-compat4/focal,now 1.18.1-5 amd64
libgdbm6/focal,now 1.18.1-5 amd64
libgirepository-1.0-1/focal,now 1.64.0-2 amd64
libglib2.0-0/focal,now 2.64.2-1~fakesync1 amd64
libglib2.0-bin/focal,now 2.64.2-1~fakesync1 amd64
libglib2.0-data/focal,now 2.64.2-1~fakesync1 all
libgmp10/focal,now 2:6.2.0+dfsg-4 amd64
libgnutls30/focal,now 3.6.13-2ubuntu1 amd64
libgpg-error0/focal,now 1.37-1 amd64
libgpgme11/focal,now 1.13.1-7ubuntu2 amd64
libgpm2/focal,now 1.20.7-5 amd64
libgssapi-krb5-2/focal,now 1.17-6ubuntu4 amd64
libgssapi3-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libgstreamer1.0-0/focal,now 1.16.2-2 amd64
libgudev-1.0-0/focal,now 1:233-1 amd64
libgusb2/focal,now 0.3.4-0.1 amd64
libhcrypto4-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libheimbase1-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libheimntlm0-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libhogweed5/focal,now 3.5.1+really3.5.1-2 amd64
libhx509-5-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libicu66/focal,now 66.1-2ubuntu2 amd64
libidn2-0/focal,now 2.2.0-2 amd64
libip4tc2/focal,now 1.8.4-3ubuntu2 amd64
libip6tc2/focal,now 1.8.4-3ubuntu2 amd64
libisc-export1105/focal,now 1:9.11.16+dfsg-3~build1 amd64
libisns0/focal,now 0.97-3 amd64
libjson-c4/focal,now 0.13.1+dfsg-7 amd64
libjson-glib-1.0-0/focal,now 1.4.4-2ubuntu2 amd64
libjson-glib-1.0-common/focal,now 1.4.4-2ubuntu2 all
libk5crypto3/focal,now 1.17-6ubuntu4 amd64
libkeyutils1/focal,now 1.6-6ubuntu1 amd64
libklibc/focal,now 2.0.7-1ubuntu5 amd64
libkmod2/focal,now 27-1ubuntu2 amd64
libkrb5-26-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libkrb5-3/focal,now 1.17-6ubuntu4 amd64
libkrb5support0/focal,now 1.17-6ubuntu4 amd64
libksba8/focal,now 1.3.5-2 amd64
libldap-2.4-2/focal-updates,focal-security,now 2.4.49+dfsg-2ubuntu1.2 amd64
libldap-common/focal-updates,focal-security,now 2.4.49+dfsg-2ubuntu1.2 all
liblmdb0/focal,now 0.9.24-1 amd64
liblocale-gettext-perl/focal,now 1.07-4 amd64
libltdl7/focal,now 2.4.6-14 amd64
liblvm2cmd2.03/focal,now 2.03.07-1ubuntu1 amd64
liblz4-1/focal,now 1.9.2-2 amd64
liblzma5/focal,now 5.2.4-1 amd64
liblzo2-2/focal,now 2.10-2 amd64
libmagic-mgc/focal,now 1:5.38-4 amd64
libmagic1/focal,now 1:5.38-4 amd64
libmaxminddb0/focal,now 1.4.2-0ubuntu1 amd64
libmnl0/focal,now 1.0.4-2 amd64
libmount1/focal,now 2.34-0.1ubuntu9 amd64
libmpdec2/focal,now 2.4.2-3 amd64
libmpfr6/focal,now 4.0.2-1 amd64
libmspack0/focal,now 0.10.1-2 amd64
libncurses6/focal,now 6.2-0ubuntu2 amd64
libncursesw6/focal,now 6.2-0ubuntu2 amd64
libnetfilter-conntrack3/focal,now 1.0.7-2 amd64
libnetplan0/focal,now 0.99-0ubuntu1 amd64
libnettle7/focal,now 3.5.1+really3.5.1-2 amd64
libnewt0.52/focal,now 0.52.21-4ubuntu2 amd64
libnfnetlink0/focal,now 1.0.1-3build1 amd64
libnftnl11/focal,now 1.1.5-1 amd64
libnghttp2-14/focal,now 1.40.0-1build1 amd64
libnl-3-200/focal,now 3.4.0-1 amd64
libnl-genl-3-200/focal,now 3.4.0-1 amd64
libnpth0/focal,now 1.6-1 amd64
libnss-systemd/focal,now 245.4-4ubuntu3 amd64
libntfs-3g883/focal,now 1:2017.3.23AR.3-3ubuntu1 amd64
libnuma1/focal,now 2.0.12-1 amd64
libogg0/focal,now 1.3.4-0ubuntu1 amd64
libp11-kit0/focal,now 0.23.20-1build1 amd64
libpackagekit-glib2-18/focal,now 1.1.13-2ubuntu1 amd64
libpam-cap/focal,now 1:2.32-1 amd64
libpam-modules-bin/focal,now 1.3.1-5ubuntu4 amd64
libpam-modules/focal,now 1.3.1-5ubuntu4 amd64
libpam-runtime/focal,now 1.3.1-5ubuntu4 all
libpam-systemd/focal,now 245.4-4ubuntu3 amd64
libpam0g/focal,now 1.3.1-5ubuntu4 amd64
libparted2/focal,now 3.3-4 amd64
libpcap0.8/focal,now 1.9.1-3 amd64
libpci3/focal,now 1:3.6.4-1 amd64
libpcre2-8-0/focal,now 10.34-7 amd64
libpcre3/focal,now 2:8.39-12build1 amd64
libperl5.30/focal,now 5.30.0-9build1 amd64
libpipeline1/focal,now 1.5.2-2build1 amd64
libplymouth5/focal,now 0.9.4git20200323-0ubuntu6 amd64
libpng16-16/focal,now 1.6.37-2 amd64
libpolkit-agent-1-0/focal,now 0.105-26ubuntu1 amd64
libpolkit-gobject-1-0/focal,now 0.105-26ubuntu1 amd64
libpopt0/focal,now 1.16-14 amd64
libprocps8/focal,now 2:3.3.16-1ubuntu2 amd64
libproxy1v5/focal,now 0.4.15-10 amd64
libpsl5/focal,now 0.21.0-1ubuntu1 amd64
libpython3-stdlib/focal,now 3.8.2-0ubuntu2 amd64
libpython3.8-minimal/focal-updates,focal-security,now 3.8.2-1ubuntu1.1 amd64
libpython3.8-stdlib/focal-updates,focal-security,now 3.8.2-1ubuntu1.1 amd64
libpython3.8/focal-updates,focal-security,now 3.8.2-1ubuntu1.1 amd64
libreadline5/focal,now 5.2+dfsg-3build3 amd64
libreadline8/focal,now 8.0-4 amd64
libroken18-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
librtmp1/focal,now 2.4+20151223.gitfa8646d.1-2build1 amd64
libsasl2-2/focal,now 2.1.27+dfsg-2 amd64
libsasl2-modules-db/focal,now 2.1.27+dfsg-2 amd64
libsasl2-modules/focal,now 2.1.27+dfsg-2 amd64
libseccomp2/focal,now 2.4.3-1ubuntu1 amd64
libselinux1/focal,now 3.0-1build2 amd64
libsemanage-common/focal,now 3.0-1build2 all
libsemanage1/focal,now 3.0-1build2 amd64
libsepol1/focal,now 3.0-1 amd64
libsgutils2-2/focal,now 1.44-1ubuntu2 amd64
libsigsegv2/focal,now 2.12-2 amd64
libslang2/focal,now 2.3.2-4 amd64
libsmartcols1/focal,now 2.34-0.1ubuntu9 amd64
libsmbios-c2/focal,now 2.4.3-1 amd64
libsodium23/focal,now 1.0.18-1 amd64
libsoup2.4-1/focal,now 2.70.0-1 amd64
libsqlite3-0/focal,now 3.31.1-4 amd64
libss2/focal,now 1.45.5-2ubuntu1 amd64
libssh-4/focal,now 0.9.3-2ubuntu2 amd64
libssl1.1/focal,now 1.1.1f-1ubuntu2 amd64
libstdc++6/focal,now 10-20200411-0ubuntu1 amd64
libstemmer0d/focal,now 0+svn585-2 amd64
libsystemd0/focal,now 245.4-4ubuntu3 amd64
libtasn1-6/focal,now 4.16.0-2 amd64
libtdb1/focal,now 1.4.2-3build1 amd64
libtext-charwidth-perl/focal,now 0.04-10 amd64
libtext-iconv-perl/focal,now 1.7-7 amd64
libtext-wrapi18n-perl/focal,now 0.06-9 all
libtinfo6/focal,now 6.2-0ubuntu2 amd64
libtss2-esys0/focal,now 2.3.2-1 amd64
libuchardet0/focal,now 0.0.6-3build1 amd64
libudev1/focal,now 245.4-4ubuntu3 amd64
libunistring2/focal,now 0.9.10-2 amd64
libunwind8/focal,now 1.2.1-9build1 amd64
liburcu6/focal,now 0.11.1-2 amd64
libusb-1.0-0/focal,now 2:1.0.23-2build1 amd64
libutempter0/focal,now 1.1.6-4 amd64
libuuid1/focal,now 2.34-0.1ubuntu9 amd64
libuv1/focal,now 1.34.2-1ubuntu1 amd64
libvorbis0a/focal,now 1.3.6-2ubuntu1 amd64
libvorbisfile3/focal,now 1.3.6-2ubuntu1 amd64
libwind0-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libwrap0/focal,now 7.6.q-30 amd64
libx11-6/focal,now 2:1.6.9-2ubuntu1 amd64
libx11-data/focal,now 2:1.6.9-2ubuntu1 all
libxau6/focal,now 1:1.0.9-0ubuntu1 amd64
libxcb1/focal,now 1.14-2 amd64
libxdmcp6/focal,now 1:1.1.3-0ubuntu1 amd64
libxext6/focal,now 2:1.3.4-0ubuntu1 amd64
libxml2/focal,now 2.9.10+dfsg-5 amd64
libxmlb1/focal,now 0.1.15-2 amd64
libxmlsec1-openssl/focal,now 1.2.28-2 amd64
libxmlsec1/focal,now 1.2.28-2 amd64
libxmuu1/focal,now 2:1.1.3-0ubuntu1 amd64
libxslt1.1/focal,now 1.1.34-4 amd64
libxtables12/focal,now 1.8.4-3ubuntu2 amd64
libyaml-0-2/focal,now 0.2.2-1 amd64
libzstd1/focal,now 1.4.4+dfsg-3 amd64
linux-base/focal,now 4.5ubuntu3 all
linux-firmware/focal,now 1.187 all
linux-generic/focal-updates,focal-security,now 5.4.0.29.34 amd64
linux-headers-5.4.0-29-generic/focal-updates,focal-security,now 5.4.0-29.33 amd64
linux-headers-5.4.0-29/focal-updates,focal-security,now 5.4.0-29.33 all
linux-headers-generic/focal-updates,focal-security,now 5.4.0.29.34 amd64
linux-image-5.4.0-29-generic/focal-updates,focal-security,now 5.4.0-29.33 amd64
linux-image-generic/focal-updates,focal-security,now 5.4.0.29.34 amd64
linux-modules-5.4.0-29-generic/focal-updates,focal-security,now 5.4.0-29.33 amd64
linux-modules-extra-5.4.0-29-generic/focal-updates,focal-security,now 5.4.0-29.33 amd64
locales/focal,now 2.31-0ubuntu9 all
login/focal,now 1:4.8.1-1ubuntu5 amd64
logrotate/focal,now 3.14.0-4ubuntu3 amd64
logsave/focal,now 1.45.5-2ubuntu1 amd64
lsb-base/focal,now 11.1.0ubuntu2 all
lsb-release/focal,now 11.1.0ubuntu2 all
lshw/focal,now 02.18.85-0.3ubuntu2 amd64
lsof/focal,now 4.93.2+dfsg-1 amd64
ltrace/focal,now 0.7.3-6.1ubuntu1 amd64
lvm2/focal,now 2.03.07-1ubuntu1 amd64
lxd-agent-loader/focal,now 0.4 all
lz4/focal,now 1.9.2-2 amd64
man-db/focal,now 2.9.1-1 amd64
manpages/focal,now 5.05-1 all
mawk/focal,now 1.3.4.20200120-2 amd64
mdadm/focal,now 4.1-5ubuntu1 amd64
mime-support/focal,now 3.64ubuntu1 all
mount/focal,now 2.34-0.1ubuntu9 amd64
mtr-tiny/focal,now 0.93-1 amd64
multipath-tools/focal,now 0.8.3-1ubuntu2 amd64
nano/focal,now 4.8-1ubuntu1 amd64
ncurses-base/focal,now 6.2-0ubuntu2 all
ncurses-bin/focal,now 6.2-0ubuntu2 amd64
ncurses-term/focal,now 6.2-0ubuntu2 all
netbase/focal,now 6.1 all
netcat-openbsd/focal,now 1.206-1ubuntu1 amd64
netplan.io/focal,now 0.99-0ubuntu1 amd64
networkd-dispatcher/focal,now 2.0.1-1 all
ntfs-3g/focal,now 1:2017.3.23AR.3-3ubuntu1 amd64
open-iscsi/focal,now 2.0.874-7.1ubuntu6 amd64
open-vm-tools/focal,now 2:11.0.5-4 amd64
openssh-client/focal,now 1:8.2p1-4 amd64
openssh-server/focal,now 1:8.2p1-4 amd64
openssh-sftp-server/focal,now 1:8.2p1-4 amd64
openssl/focal,now 1.1.1f-1ubuntu2 amd64
os-prober/focal,now 1.74ubuntu2 amd64
overlayroot/focal,now 0.45ubuntu1 all
packagekit-tools/focal,now 1.1.13-2ubuntu1 amd64
packagekit/focal,now 1.1.13-2ubuntu1 amd64
parted/focal,now 3.3-4 amd64
passwd/focal,now 1:4.8.1-1ubuntu5 amd64
pastebinit/focal,now 1.5.1-1 all
patch/focal,now 2.7.6-6 amd64
pci.ids/focal,now 0.0~2020.03.20-1 all
pciutils/focal,now 1:3.6.4-1 amd64
perl-base/focal,now 5.30.0-9build1 amd64
perl-modules-5.30/focal,now 5.30.0-9build1 all
perl/focal,now 5.30.0-9build1 amd64
pinentry-curses/focal,now 1.1.0-3build1 amd64
plymouth-theme-ubuntu-text/focal,now 0.9.4git20200323-0ubuntu6 amd64
plymouth/focal,now 0.9.4git20200323-0ubuntu6 amd64
policykit-1/focal,now 0.105-26ubuntu1 amd64
pollinate/focal,now 4.33-3ubuntu1 all
popularity-contest/focal,now 1.69ubuntu1 all
powermgmt-base/focal,now 1.36 all
procps/focal,now 2:3.3.16-1ubuntu2 amd64
psmisc/focal,now 23.3-1 amd64
publicsuffix/focal,now 20200303.0012-1 all
python-apt-common/focal,now 2.0.0 all
python3-apport/focal,now 2.20.11-0ubuntu27 all
python3-apt/focal,now 2.0.0 amd64
python3-attr/focal,now 19.3.0-2 all
python3-automat/focal,now 0.8.0-1ubuntu1 all
python3-blinker/focal,now 1.4+dfsg1-0.3ubuntu1 all
python3-certifi/focal,now 2019.11.28-1 all
python3-cffi-backend/focal,now 1.14.0-1build1 amd64
python3-chardet/focal,now 3.0.4-4build1 all
python3-click/focal,now 7.0-3 all
python3-colorama/focal,now 0.4.3-1build1 all
python3-commandnotfound/focal,now 20.04.2 all
python3-configobj/focal,now 5.0.6-4 all
python3-constantly/focal,now 15.1.0-1build1 all
python3-cryptography/focal,now 2.8-3 amd64
python3-dbus/focal,now 1.2.16-1build1 amd64
python3-debconf/focal,now 1.5.73 all
python3-debian/focal,now 0.1.36ubuntu1 all
python3-distro-info/focal,now 0.23ubuntu1 all
python3-distro/focal,now 1.4.0-1 all
python3-distupgrade/focal,now 1:20.04.18 all
[COLOR=green]**python3-distutils/focal,now 3.8.2-1ubuntu1 all**[/COLOR]
python3-entrypoints/focal,now 0.3-2ubuntu1 all
python3-gdbm/focal,now 3.8.2-1ubuntu1 amd64
python3-gi/focal,now 3.36.0-1 amd64
python3-hamcrest/focal,now 1.9.0-3 all
python3-httplib2/focal,now 0.14.0-1ubuntu1 all
python3-hyperlink/focal,now 19.0.0-1 all
python3-idna/focal,now 2.8-1 all
[COLOR=green]**python3-importlib-metadata/focal,now 1.5.0-1 all**[/COLOR]
python3-incremental/focal,now 16.10.1-3.2 all
[COLOR=green]**python3-jinja2/focal,now 2.10.1-2 all**[/COLOR]
[COLOR=green]**python3-json-pointer/focal,now 2.0-0ubuntu1 all**[/COLOR]
[COLOR=green]**python3-jsonpatch/focal,now 1.23-3 all**[/COLOR]
[COLOR=green]**python3-jsonschema/focal,now 3.2.0-0ubuntu2 all**[/COLOR]
python3-jwt/focal,now 1.7.1-2ubuntu2 all
python3-keyring/focal,now 18.0.1-2ubuntu1 all
python3-launchpadlib/focal,now 1.10.13-1 all
python3-lazr.restfulclient/focal,now 0.14.2-2build1 all
python3-lazr.uri/focal,now 1.0.3-4build1 all
[COLOR=green]**python3-lib2to3/focal,now 3.8.2-1ubuntu1 all**[/COLOR]
[COLOR=green]**python3-markupsafe/focal,now 1.1.0-1build2 amd64**[/COLOR]
python3-minimal/focal,now 3.8.2-0ubuntu2 amd64
[COLOR=green]**python3-more-itertools/focal,now 4.2.0-1build1 all**[/COLOR]
python3-nacl/focal,now 1.3.0-5 amd64
python3-netifaces/focal,now 0.10.4-1ubuntu4 amd64
python3-newt/focal,now 0.52.21-4ubuntu2 amd64
python3-oauthlib/focal,now 3.1.0-1ubuntu2 all
python3-openssl/focal,now 19.0.0-1build1 all
python3-pkg-resources/focal,now 45.2.0-1 all
python3-problem-report/focal,now 2.20.11-0ubuntu27 all
python3-pyasn1-modules/focal,now 0.2.1-0.2build1 all
python3-pyasn1/focal,now 0.4.2-3build1 all
python3-pymacaroons/focal,now 0.13.0-3 all
[COLOR=green]**python3-pyrsistent/focal,now 0.15.5-1build1 amd64**[/COLOR]
python3-requests-unixsocket/focal,now 0.2.0-2 all
python3-requests/focal,now 2.22.0-2ubuntu1 all
python3-secretstorage/focal,now 2.3.1-2ubuntu1 all
[COLOR=green]**python3-serial/focal,now 3.4-5.1 all**[/COLOR]
python3-service-identity/focal,now 18.1.0-5build1 all
[COLOR=green]**python3-setuptools/focal,now 45.2.0-1 all**[/COLOR]
python3-simplejson/focal,now 3.16.0-2ubuntu2 amd64
python3-six/focal,now 1.14.0-2 all
python3-software-properties/focal,now 0.98.9 all
python3-systemd/focal,now 234-3build2 amd64
python3-twisted-bin/focal,now 18.9.0-11 amd64
python3-twisted/focal,now 18.9.0-11 all
python3-update-manager/focal,now 1:20.04.9 all
python3-urllib3/focal,now 1.25.8-2 all
python3-wadllib/focal,now 1.3.3-3build1 all
python3-yaml/focal,now 5.3.1-1 amd64
[COLOR=green]**python3-zipp/focal,now 1.0.0-1 all**[/COLOR]
python3-zope.interface/focal,now 4.7.1-1 amd64
python3.8-minimal/focal-updates,focal-security,now 3.8.2-1ubuntu1.1 amd64
python3.8/focal-updates,focal-security,now 3.8.2-1ubuntu1.1 amd64
python3/focal,now 3.8.2-0ubuntu2 amd64
readline-common/focal,now 8.0-4 all
rsync/focal,now 3.1.3-8 amd64
rsyslog/focal,now 8.2001.0-1ubuntu1 amd64
run-one/focal,now 1.17-0ubuntu1 all
sbsigntool/focal,now 0.9.2-2ubuntu1 amd64
screen/focal,now 4.8.0-1 amd64
secureboot-db/focal,now 1.5 amd64
sed/focal,now 4.7-1 amd64
sensible-utils/focal,now 0.0.12+nmu1 all
sg3-utils-udev/focal,now 1.44-1ubuntu2 all
sg3-utils/focal,now 1.44-1ubuntu2 amd64
shared-mime-info/focal,now 1.15-1 amd64
snapd/focal,now 2.44.3+20.04 amd64
software-properties-common/focal,now 0.98.9 all
sosreport/focal,now 3.9-1ubuntu2 amd64
sound-theme-freedesktop/focal,now 0.8-2ubuntu1 all
squashfs-tools/focal,now 1:4.4-1 amd64
ssh-import-id/focal,now 5.10-0ubuntu1 all
strace/focal,now 4.26-0.2ubuntu3 amd64
sudo/focal,now 1.8.31-1ubuntu1 amd64
systemd-sysv/focal,now 245.4-4ubuntu3 amd64
systemd-timesyncd/focal,now 245.4-4ubuntu3 amd64
systemd/focal,now 245.4-4ubuntu3 amd64
sysvinit-utils/focal,now 2.96-2.1ubuntu1 amd64
tar/focal,now 1.30+dfsg-7 amd64
tcpdump/focal,now 4.9.3-4 amd64
telnet/focal,now 0.17-41.2build1 amd64
[COLOR=green]**thermald/focal,now 1.9.1-1build1 amd64**[/COLOR]
thin-provisioning-tools/focal,now 0.8.5-4build1 amd64
time/focal,now 1.7-25.1build1 amd64
tmux/focal,now 3.0a-2 amd64
tpm-udev/focal,now 0.4 all
tzdata/focal,now 2019c-3ubuntu1 all
ubuntu-advantage-tools/focal,now 20.3 amd64
ubuntu-keyring/focal,now 2020.02.11.2 all
ubuntu-minimal/focal,now 1.450 amd64
ubuntu-release-upgrader-core/focal,now 1:20.04.18 all
ubuntu-server/focal,now 1.450 amd64
ubuntu-standard/focal,now 1.450 amd64
ucf/focal,now 3.0038+nmu1 all
udev/focal,now 245.4-4ubuntu3 amd64
ufw/focal,now 0.36-6 all
unattended-upgrades/focal,now 2.3 all
update-manager-core/focal,now 1:20.04.9 all
update-notifier-common/focal,now 3.192.30 all
usb.ids/focal,now 2020.03.19-1 all
usbutils/focal,now 1:012-2 amd64
util-linux/focal,now 2.34-0.1ubuntu9 amd64
uuid-runtime/focal,now 2.34-0.1ubuntu9 amd64
vim-common/focal,now 2:8.1.2269-1ubuntu5 all
vim-runtime/focal,now 2:8.1.2269-1ubuntu5 all
vim-tiny/focal,now 2:8.1.2269-1ubuntu5 amd64
vim/focal,now 2:8.1.2269-1ubuntu5 amd64
wget/focal,now 1.20.3-1ubuntu1 amd64
whiptail/focal,now 0.52.21-4ubuntu2 amd64
wireless-regdb/focal,now 2018.05.09-0ubuntu1 all
xauth/focal,now 1:1.1-0ubuntu1 amd64
xdg-user-dirs/focal,now 0.17-2ubuntu1 amd64
xfsprogs/focal,now 5.3.0-1ubuntu2 amd64
xkb-data/focal,now 2.29-2 all
xxd/focal,now 2:8.1.2269-1ubuntu5 amd64
xz-utils/focal,now 5.2.4-1 amd64
zerofree/focal,now 1.1.1-1 amd64
zlib1g/focal,now 1:1.2.11.dfsg-2ubuntu1 amd64

```

**EDIT:** Here are just the lines that are installed with the "live" installer that are not installed with the "legacy" installer:

```

[color=green]**cloud-init/focal,now 20.1-10-g71af48df-0ubuntu5 all**[/color]
[color=green]**console-setup/focal,now 1.194ubuntu3 all**[/color]
[color=green]**eatmydata/focal,now 105-7 all**[/color]
[color=green]**gdisk/focal,now 1.0.5-1 amd64**[/color]
[color=green]**libeatmydata1/focal,now 105-7 amd64**[/color]
[color=green]**python3-distutils/focal,now 3.8.2-1ubuntu1 all**[/color]
[color=green]**python3-importlib-metadata/focal,now 1.5.0-1 all**[/color]
[color=green]**python3-jinja2/focal,now 2.10.1-2 all**[/color]
[color=green]**python3-json-pointer/focal,now 2.0-0ubuntu1 all**[/color]
[color=green]**python3-jsonpatch/focal,now 1.23-3 all**[/color]
[color=green]**python3-jsonschema/focal,now 3.2.0-0ubuntu2 all**[/color]
[color=green]**python3-lib2to3/focal,now 3.8.2-1ubuntu1 all**[/color]
[color=green]**python3-markupsafe/focal,now 1.1.0-1build2 amd64**[/color]
[color=green]**python3-more-itertools/focal,now 4.2.0-1build1 all**[/color]
[color=green]**python3-pyrsistent/focal,now 0.15.5-1build1 amd64**[/color]
[color=green]**python3-serial/focal,now 3.4-5.1 all**[/color]
[color=green]**python3-setuptools/focal,now 45.2.0-1 all**[/color]
[color=green]**python3-zipp/focal,now 1.0.0-1 all**[/color]
[color=green]**thermald/focal,now 1.9.1-1build1 amd64**[/color]

```

---

### Post by LHammonds on 2020-05-10
Command to show what is installed:
```
apt list --installed
```

NOTE: lines in bold green are installed by the specific installer only.

Ubuntu 20.04 LTS Legacy Installer (unpatched, 1st version of the ISO image) - 555 installed entries:
```

accountsservice/focal,now 0.6.55-0ubuntu11 amd64
adduser/focal,focal,now 3.118ubuntu2 all
alsa-topology-conf/focal,focal,now 1.2.2-1 all
alsa-ucm-conf/focal,focal,now 1.2.2-1 all
amd64-microcode/focal,now 3.20191218.1ubuntu1 amd64
apparmor/focal,now 2.13.3-7ubuntu5 amd64
apport-symptoms/focal,focal,now 0.23 all
apport/focal,focal,now 2.20.11-0ubuntu27 all
apt-utils/focal,now 2.0.2 amd64
apt/focal,now 2.0.2 amd64
at/focal,now 3.1.23-1ubuntu1 amd64
base-files/focal,now 11ubuntu5 amd64
base-passwd/focal,now 3.5.47 amd64
bash-completion/focal,focal,now 1:2.10-1ubuntu1 all
bash/focal,now 5.0-6ubuntu1 amd64
bc/focal,now 1.07.1-2build1 amd64
bcache-tools/focal,now 1.0.8-3 amd64
bind9-dnsutils/focal,now 1:9.16.1-0ubuntu2 amd64
bind9-host/focal,now 1:9.16.1-0ubuntu2 amd64
bind9-libs/focal,now 1:9.16.1-0ubuntu2 amd64
bolt/focal,now 0.8-4 amd64
bsdmainutils/focal,now 11.1.2ubuntu3 amd64
bsdutils/focal,now 1:2.34-0.1ubuntu9 amd64
btrfs-progs/focal,now 5.4.1-2 amd64
busybox-initramfs/focal,now 1:1.30.1-4ubuntu6 amd64
busybox-static/focal,now 1:1.30.1-4ubuntu6 amd64
byobu/focal,focal,now 5.133-0ubuntu1 all
bzip2/focal,now 1.0.8-2 amd64
ca-certificates/focal,focal,now 20190110ubuntu1 all
cloud-guest-utils/focal,focal,now 0.31-7-gd99b2d76-0ubuntu1 all
cloud-initramfs-copymods/focal,focal,now 0.45ubuntu1 all
cloud-initramfs-dyn-netconf/focal,focal,now 0.45ubuntu1 all
command-not-found/focal,focal,now 20.04.2 all
console-setup-linux/focal,focal,now 1.194ubuntu3 all
console-setup/focal,focal,now 1.194ubuntu3 all
coreutils/focal,now 8.30-3ubuntu2 amd64
cpio/focal,now 2.13+dfsg-2 amd64
crda/focal,now 3.18-1build1 amd64
cron/focal,now 3.0pl1-136ubuntu1 amd64
cryptsetup-bin/focal,now 2:2.2.2-3ubuntu2 amd64
cryptsetup-initramfs/focal,focal,now 2:2.2.2-3ubuntu2 all
cryptsetup-run/focal,focal,now 2:2.2.2-3ubuntu2 all
cryptsetup/focal,now 2:2.2.2-3ubuntu2 amd64
curl/focal,now 7.68.0-1ubuntu2 amd64
dash/focal,now 0.5.10.2-6 amd64
dbus-user-session/focal,now 1.12.16-2ubuntu2 amd64
dbus/focal,now 1.12.16-2ubuntu2 amd64
dconf-gsettings-backend/focal,now 0.36.0-1 amd64
dconf-service/focal,now 0.36.0-1 amd64
debconf-i18n/focal,focal,now 1.5.73 all
debconf/focal,focal,now 1.5.73 all
debianutils/focal,now 4.9.1 amd64
diffutils/focal,now 1:3.7-3 amd64
dirmngr/focal,now 2.2.19-3ubuntu2 amd64
distro-info-data/focal,focal,now 0.43ubuntu1 all
dmeventd/focal,now 2:1.02.167-1ubuntu1 amd64
dmidecode/focal,now 3.2-3 amd64
dmsetup/focal,now 2:1.02.167-1ubuntu1 amd64
dosfstools/focal,now 4.1-2 amd64
dpkg/focal,now 1.19.7ubuntu3 amd64
e2fsprogs/focal,now 1.45.5-2ubuntu1 amd64
ed/focal,now 1.16-1 amd64
eject/focal,now 2.1.5+deb1+cvs20081104-14 amd64
ethtool/focal,now 1:5.4-1 amd64
fdisk/focal,now 2.34-0.1ubuntu9 amd64
file/focal,now 1:5.38-4 amd64
finalrd/focal,focal,now 5 all
findutils/focal,now 4.7.0-1ubuntu1 amd64
fonts-ubuntu-console/focal,focal,now 0.83-4ubuntu1 all
friendly-recovery/focal,focal,now 0.2.41 all
ftp/focal,now 0.17-34.1 amd64
fuse/focal,now 2.9.9-3 amd64
fwupd-signed/focal,now 1.27+1.3.9-4 amd64
fwupd/focal,now 1.3.9-4 amd64
gawk/focal,now 1:5.0.1+dfsg-1 amd64
gcc-10-base/focal,now 10-20200411-0ubuntu1 amd64
gettext-base/focal,now 0.19.8.1-10build1 amd64
gir1.2-glib-2.0/focal,now 1.64.0-2 amd64
gir1.2-packagekitglib-1.0/focal,now 1.1.13-2ubuntu1 amd64
git-man/focal,focal,now 1:2.25.1-1ubuntu3 all
git/focal,now 1:2.25.1-1ubuntu3 amd64
glib-networking-common/focal,focal,now 2.64.1-1 all
glib-networking-services/focal,now 2.64.1-1 amd64
glib-networking/focal,now 2.64.1-1 amd64
gnupg-l10n/focal,focal,now 2.2.19-3ubuntu2 all
gnupg-utils/focal,now 2.2.19-3ubuntu2 amd64
gnupg/focal,focal,now 2.2.19-3ubuntu2 all
gpg-agent/focal,now 2.2.19-3ubuntu2 amd64
gpg-wks-client/focal,now 2.2.19-3ubuntu2 amd64
gpg-wks-server/focal,now 2.2.19-3ubuntu2 amd64
gpg/focal,now 2.2.19-3ubuntu2 amd64
gpgconf/focal,now 2.2.19-3ubuntu2 amd64
gpgsm/focal,now 2.2.19-3ubuntu2 amd64
gpgv/focal,now 2.2.19-3ubuntu2 amd64
grep/focal,now 3.4-1 amd64
groff-base/focal,now 1.22.4-4build1 amd64
grub-common/focal,now 2.04-1ubuntu26 amd64
grub-gfxpayload-lists/focal,now 0.7 amd64
grub-pc-bin/focal,now 2.04-1ubuntu26 amd64
grub-pc/focal,now 2.04-1ubuntu26 amd64
grub2-common/focal,now 2.04-1ubuntu26 amd64
gsettings-desktop-schemas/focal,focal,now 3.36.0-1ubuntu1 all
gzip/focal,now 1.10-0ubuntu4 amd64
hdparm/focal,now 9.58+ds-4 amd64
hostname/focal,now 3.23 amd64
htop/focal,now 2.2.0-2build1 amd64
info/focal,now 6.7.0.dfsg.2-5 amd64
init-system-helpers/focal,focal,now 1.57 all
init/focal,now 1.57 amd64
initramfs-tools-bin/focal,now 0.136ubuntu6 amd64
initramfs-tools-core/focal,focal,now 0.136ubuntu6 all
initramfs-tools/focal,focal,now 0.136ubuntu6 all
install-info/focal,now 6.7.0.dfsg.2-5 amd64
[COLOR=green]**installation-report/focal,focal,now 2.62ubuntu1 all**[/COLOR]
intel-microcode/focal,now 3.20191115.1ubuntu3 amd64
iproute2/focal,now 5.5.0-1ubuntu1 amd64
iptables/focal,now 1.8.4-3ubuntu2 amd64
iputils-ping/focal,now 3:20190709-3 amd64
iputils-tracepath/focal,now 3:20190709-3 amd64
irqbalance/focal,now 1.6.0-3ubuntu1 amd64
isc-dhcp-client/focal,now 4.4.1-2.1ubuntu5 amd64
isc-dhcp-common/focal,now 4.4.1-2.1ubuntu5 amd64
iso-codes/focal,focal,now 4.4-1 all
iucode-tool/focal,now 2.3.1-1 amd64
iw/focal,now 5.4-1 amd64
kbd/focal,now 2.0.4-4ubuntu2 amd64
keyboard-configuration/focal,focal,now 1.194ubuntu3 all
klibc-utils/focal,now 2.0.7-1ubuntu5 amd64
kmod/focal,now 27-1ubuntu2 amd64
kpartx/focal,now 0.8.3-1ubuntu2 amd64
krb5-locales/focal,focal,now 1.17-6ubuntu4 all
landscape-common/focal,now 19.12-0ubuntu4 amd64
[COLOR=green]**language-pack-en-base/focal,focal,now 1:20.04+20200416 all**[/COLOR]
[COLOR=green]**language-pack-en/focal,focal,now 1:20.04+20200416 all**[/COLOR]
language-selector-common/focal,focal,now 0.204 all
[COLOR=green]**laptop-detect/focal,focal,now 0.16 all**[/COLOR]
less/focal,now 551-1 amd64
libaccountsservice0/focal,now 0.6.55-0ubuntu11 amd64
libacl1/focal,now 2.2.53-6 amd64
libaio1/focal,now 0.3.112-5 amd64
libapparmor1/focal,now 2.13.3-7ubuntu5 amd64
libappstream4/focal,now 0.12.10-2 amd64
libapt-pkg6.0/focal,now 2.0.2 amd64
libarchive13/focal,now 3.4.0-2ubuntu1 amd64
libargon2-1/focal,now 0~20171227-0.2 amd64
libasn1-8-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libasound2-data/focal,focal,now 1.2.2-2.1 all
libasound2/focal,now 1.2.2-2.1 amd64
libassuan0/focal,now 2.5.3-7ubuntu2 amd64
libatm1/focal,now 1:2.5.1-4 amd64
libattr1/focal,now 1:2.4.48-5 amd64
libaudit-common/focal,focal,now 1:2.8.5-2ubuntu6 all
libaudit1/focal,now 1:2.8.5-2ubuntu6 amd64
libblkid1/focal,now 2.34-0.1ubuntu9 amd64
libbrotli1/focal,now 1.0.7-6build1 amd64
libbsd0/focal,now 0.10.0-1 amd64
libbz2-1.0/focal,now 1.0.8-2 amd64
libc-bin/focal,now 2.31-0ubuntu9 amd64
libc6/focal,now 2.31-0ubuntu9 amd64
libcanberra0/focal,now 0.30-7ubuntu1 amd64
libcap-ng0/focal,now 0.7.9-2.1build1 amd64
libcap2-bin/focal,now 1:2.32-1 amd64
libcap2/focal,now 1:2.32-1 amd64
libcbor0.6/focal,now 0.6.0-0ubuntu1 amd64
libcom-err2/focal,now 1.45.5-2ubuntu1 amd64
libcrypt1/focal,now 1:4.4.10-10ubuntu4 amd64
libcryptsetup12/focal,now 2:2.2.2-3ubuntu2 amd64
libcurl3-gnutls/focal,now 7.68.0-1ubuntu2 amd64
libcurl4/focal,now 7.68.0-1ubuntu2 amd64
libdb5.3/focal,now 5.3.28+dfsg1-0.6ubuntu2 amd64
libdbus-1-3/focal,now 1.12.16-2ubuntu2 amd64
libdconf1/focal,now 0.36.0-1 amd64
libdebconfclient0/focal,now 0.251ubuntu1 amd64
libdevmapper-event1.02.1/focal,now 2:1.02.167-1ubuntu1 amd64
libdevmapper1.02.1/focal,now 2:1.02.167-1ubuntu1 amd64
libdns-export1109/focal,now 1:9.11.16+dfsg-3~build1 amd64
libdrm-common/focal,focal,now 2.4.101-2 all
libdrm2/focal,now 2.4.101-2 amd64
libedit2/focal,now 3.1-20191231-1 amd64
libefiboot1/focal,now 37-2ubuntu2 amd64
libefivar1/focal,now 37-2ubuntu2 amd64
libelf1/focal,now 0.176-1.1build1 amd64
liberror-perl/focal,focal,now 0.17029-1 all
libestr0/focal,now 0.1.10-2.1 amd64
libevent-2.1-7/focal,now 2.1.11-stable-1 amd64
libexpat1/focal,now 2.2.9-1build1 amd64
libext2fs2/focal,now 1.45.5-2ubuntu1 amd64
libfastjson4/focal,now 0.99.8-2 amd64
libfdisk1/focal,now 2.34-0.1ubuntu9 amd64
libffi7/focal,now 3.3-4 amd64
libfido2-1/focal,now 1.3.1-1ubuntu2 amd64
libfl2/focal,now 2.6.4-6.2 amd64
libfreetype6/focal,now 2.10.1-2 amd64
libfribidi0/focal,now 1.0.8-2 amd64
libfuse2/focal,now 2.9.9-3 amd64
libfwupd2/focal,now 1.3.9-4 amd64
libfwupdplugin1/focal,now 1.3.9-4 amd64
libgcab-1.0-0/focal,now 1.4-1 amd64
libgcc-s1/focal,now 10-20200411-0ubuntu1 amd64
libgcrypt20/focal,now 1.8.5-5ubuntu1 amd64
libgdbm-compat4/focal,now 1.18.1-5 amd64
libgdbm6/focal,now 1.18.1-5 amd64
libgirepository-1.0-1/focal,now 1.64.0-2 amd64
libglib2.0-0/focal,now 2.64.2-1~fakesync1 amd64
libglib2.0-bin/focal,now 2.64.2-1~fakesync1 amd64
libglib2.0-data/focal,focal,now 2.64.2-1~fakesync1 all
libgmp10/focal,now 2:6.2.0+dfsg-4 amd64
libgnutls30/focal,now 3.6.13-2ubuntu1 amd64
libgpg-error0/focal,now 1.37-1 amd64
libgpgme11/focal,now 1.13.1-7ubuntu2 amd64
libgpm2/focal,now 1.20.7-5 amd64
libgssapi-krb5-2/focal,now 1.17-6ubuntu4 amd64
libgssapi3-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libgstreamer1.0-0/focal,now 1.16.2-2 amd64
libgudev-1.0-0/focal,now 1:233-1 amd64
libgusb2/focal,now 0.3.4-0.1 amd64
libhcrypto4-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libheimbase1-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libheimntlm0-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libhogweed5/focal,now 3.5.1+really3.5.1-2 amd64
libhx509-5-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libicu66/focal,now 66.1-2ubuntu2 amd64
libidn2-0/focal,now 2.2.0-2 amd64
libip4tc2/focal,now 1.8.4-3ubuntu2 amd64
libip6tc2/focal,now 1.8.4-3ubuntu2 amd64
libisc-export1105/focal,now 1:9.11.16+dfsg-3~build1 amd64
libisns0/focal,now 0.97-3 amd64
libjson-c4/focal,now 0.13.1+dfsg-7 amd64
libjson-glib-1.0-0/focal,now 1.4.4-2ubuntu2 amd64
libjson-glib-1.0-common/focal,focal,now 1.4.4-2ubuntu2 all
libk5crypto3/focal,now 1.17-6ubuntu4 amd64
libkeyutils1/focal,now 1.6-6ubuntu1 amd64
libklibc/focal,now 2.0.7-1ubuntu5 amd64
libkmod2/focal,now 27-1ubuntu2 amd64
libkrb5-26-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libkrb5-3/focal,now 1.17-6ubuntu4 amd64
libkrb5support0/focal,now 1.17-6ubuntu4 amd64
libksba8/focal,now 1.3.5-2 amd64
libldap-2.4-2/focal,now 2.4.49+dfsg-2ubuntu1 amd64
libldap-common/focal,focal,now 2.4.49+dfsg-2ubuntu1 all
liblmdb0/focal,now 0.9.24-1 amd64
liblocale-gettext-perl/focal,now 1.07-4 amd64
libltdl7/focal,now 2.4.6-14 amd64
liblvm2cmd2.03/focal,now 2.03.07-1ubuntu1 amd64
liblz4-1/focal,now 1.9.2-2 amd64
liblzma5/focal,now 5.2.4-1 amd64
liblzo2-2/focal,now 2.10-2 amd64
libmagic-mgc/focal,now 1:5.38-4 amd64
libmagic1/focal,now 1:5.38-4 amd64
libmaxminddb0/focal,now 1.4.2-0ubuntu1 amd64
libmnl0/focal,now 1.0.4-2 amd64
libmount1/focal,now 2.34-0.1ubuntu9 amd64
libmpdec2/focal,now 2.4.2-3 amd64
libmpfr6/focal,now 4.0.2-1 amd64
libmspack0/focal,now 0.10.1-2 amd64
libncurses6/focal,now 6.2-0ubuntu2 amd64
libncursesw6/focal,now 6.2-0ubuntu2 amd64
libnetfilter-conntrack3/focal,now 1.0.7-2 amd64
libnetplan0/focal,now 0.99-0ubuntu1 amd64
libnettle7/focal,now 3.5.1+really3.5.1-2 amd64
libnewt0.52/focal,now 0.52.21-4ubuntu2 amd64
libnfnetlink0/focal,now 1.0.1-3build1 amd64
libnftnl11/focal,now 1.1.5-1 amd64
libnghttp2-14/focal,now 1.40.0-1build1 amd64
libnl-3-200/focal,now 3.4.0-1 amd64
libnl-genl-3-200/focal,now 3.4.0-1 amd64
libnpth0/focal,now 1.6-1 amd64
libnss-systemd/focal,now 245.4-4ubuntu3 amd64
libntfs-3g883/focal,now 1:2017.3.23AR.3-3ubuntu1 amd64
libnuma1/focal,now 2.0.12-1 amd64
libogg0/focal,now 1.3.4-0ubuntu1 amd64
libp11-kit0/focal,now 0.23.20-1build1 amd64
libpackagekit-glib2-18/focal,now 1.1.13-2ubuntu1 amd64
libpam-cap/focal,now 1:2.32-1 amd64
libpam-modules-bin/focal,now 1.3.1-5ubuntu4 amd64
libpam-modules/focal,now 1.3.1-5ubuntu4 amd64
libpam-runtime/focal,focal,now 1.3.1-5ubuntu4 all
libpam-systemd/focal,now 245.4-4ubuntu3 amd64
libpam0g/focal,now 1.3.1-5ubuntu4 amd64
libparted2/focal,now 3.3-4 amd64
libpcap0.8/focal,now 1.9.1-3 amd64
libpci3/focal,now 1:3.6.4-1 amd64
libpcre2-8-0/focal,now 10.34-7 amd64
libpcre3/focal,now 2:8.39-12build1 amd64
libperl5.30/focal,now 5.30.0-9build1 amd64
libpipeline1/focal,now 1.5.2-2build1 amd64
libplymouth5/focal,now 0.9.4git20200323-0ubuntu6 amd64
libpng16-16/focal,now 1.6.37-2 amd64
libpolkit-agent-1-0/focal,now 0.105-26ubuntu1 amd64
libpolkit-gobject-1-0/focal,now 0.105-26ubuntu1 amd64
libpopt0/focal,now 1.16-14 amd64
libprocps8/focal,now 2:3.3.16-1ubuntu2 amd64
libproxy1v5/focal,now 0.4.15-10 amd64
libpsl5/focal,now 0.21.0-1ubuntu1 amd64
libpython3-stdlib/focal,now 3.8.2-0ubuntu2 amd64
libpython3.8-minimal/focal,now 3.8.2-1ubuntu1 amd64
libpython3.8-stdlib/focal,now 3.8.2-1ubuntu1 amd64
libpython3.8/focal,now 3.8.2-1ubuntu1 amd64
libreadline5/focal,now 5.2+dfsg-3build3 amd64
libreadline8/focal,now 8.0-4 amd64
libroken18-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
librtmp1/focal,now 2.4+20151223.gitfa8646d.1-2build1 amd64
libsasl2-2/focal,now 2.1.27+dfsg-2 amd64
libsasl2-modules-db/focal,now 2.1.27+dfsg-2 amd64
libsasl2-modules/focal,now 2.1.27+dfsg-2 amd64
libseccomp2/focal,now 2.4.3-1ubuntu1 amd64
libselinux1/focal,now 3.0-1build2 amd64
libsemanage-common/focal,focal,now 3.0-1build2 all
libsemanage1/focal,now 3.0-1build2 amd64
libsepol1/focal,now 3.0-1 amd64
libsgutils2-2/focal,now 1.44-1ubuntu2 amd64
libsigsegv2/focal,now 2.12-2 amd64
libslang2/focal,now 2.3.2-4 amd64
libsmartcols1/focal,now 2.34-0.1ubuntu9 amd64
libsmbios-c2/focal,now 2.4.3-1 amd64
libsodium23/focal,now 1.0.18-1 amd64
libsoup2.4-1/focal,now 2.70.0-1 amd64
libsqlite3-0/focal,now 3.31.1-4 amd64
libss2/focal,now 1.45.5-2ubuntu1 amd64
libssh-4/focal,now 0.9.3-2ubuntu2 amd64
libssl1.1/focal,now 1.1.1f-1ubuntu2 amd64
libstdc++6/focal,now 10-20200411-0ubuntu1 amd64
libstemmer0d/focal,now 0+svn585-2 amd64
libsystemd0/focal,now 245.4-4ubuntu3 amd64
libtasn1-6/focal,now 4.16.0-2 amd64
libtdb1/focal,now 1.4.2-3build1 amd64
libtext-charwidth-perl/focal,now 0.04-10 amd64
libtext-iconv-perl/focal,now 1.7-7 amd64
libtext-wrapi18n-perl/focal,focal,now 0.06-9 all
libtinfo6/focal,now 6.2-0ubuntu2 amd64
libtss2-esys0/focal,now 2.3.2-1 amd64
libuchardet0/focal,now 0.0.6-3build1 amd64
libudev1/focal,now 245.4-4ubuntu3 amd64
libunistring2/focal,now 0.9.10-2 amd64
libunwind8/focal,now 1.2.1-9build1 amd64
liburcu6/focal,now 0.11.1-2 amd64
libusb-1.0-0/focal,now 2:1.0.23-2build1 amd64
libutempter0/focal,now 1.1.6-4 amd64
libuuid1/focal,now 2.34-0.1ubuntu9 amd64
libuv1/focal,now 1.34.2-1ubuntu1 amd64
libvorbis0a/focal,now 1.3.6-2ubuntu1 amd64
libvorbisfile3/focal,now 1.3.6-2ubuntu1 amd64
libwind0-heimdal/focal,now 7.7.0+dfsg-1ubuntu1 amd64
libwrap0/focal,now 7.6.q-30 amd64
libx11-6/focal,now 2:1.6.9-2ubuntu1 amd64
libx11-data/focal,focal,now 2:1.6.9-2ubuntu1 all
libxau6/focal,now 1:1.0.9-0ubuntu1 amd64
libxcb1/focal,now 1.14-2 amd64
libxdmcp6/focal,now 1:1.1.3-0ubuntu1 amd64
libxext6/focal,now 2:1.3.4-0ubuntu1 amd64
libxml2/focal,now 2.9.10+dfsg-5 amd64
libxmlb1/focal,now 0.1.15-2 amd64
libxmlsec1-openssl/focal,now 1.2.28-2 amd64
libxmlsec1/focal,now 1.2.28-2 amd64
libxmuu1/focal,now 2:1.1.3-0ubuntu1 amd64
libxslt1.1/focal,now 1.1.34-4 amd64
libxtables12/focal,now 1.8.4-3ubuntu2 amd64
libyaml-0-2/focal,now 0.2.2-1 amd64
libzstd1/focal,now 1.4.4+dfsg-3 amd64
linux-base/focal,focal,now 4.5ubuntu3 all
linux-firmware/focal,focal,now 1.187 all
linux-generic/focal,now 5.4.0.26.32 amd64
linux-headers-5.4.0-26-generic/focal,now 5.4.0-26.30 amd64
linux-headers-5.4.0-26/focal,focal,now 5.4.0-26.30 all
linux-headers-generic/focal,now 5.4.0.26.32 amd64
linux-image-5.4.0-26-generic/focal,now 5.4.0-26.30 amd64
linux-image-generic/focal,now 5.4.0.26.32 amd64
linux-modules-5.4.0-26-generic/focal,now 5.4.0-26.30 amd64
linux-modules-extra-5.4.0-26-generic/focal,now 5.4.0-26.30 amd64
locales/focal,focal,now 2.31-0ubuntu9 all
login/focal,now 1:4.8.1-1ubuntu5 amd64
logrotate/focal,now 3.14.0-4ubuntu3 amd64
logsave/focal,now 1.45.5-2ubuntu1 amd64
lsb-base/focal,focal,now 11.1.0ubuntu2 all
lsb-release/focal,focal,now 11.1.0ubuntu2 all
lshw/focal,now 02.18.85-0.3ubuntu2 amd64
lsof/focal,now 4.93.2+dfsg-1 amd64
ltrace/focal,now 0.7.3-6.1ubuntu1 amd64
lvm2/focal,now 2.03.07-1ubuntu1 amd64
lxd-agent-loader/focal,focal,now 0.4 all
lz4/focal,now 1.9.2-2 amd64
man-db/focal,now 2.9.1-1 amd64
manpages/focal,focal,now 5.05-1 all
mawk/focal,now 1.3.4.20200120-2 amd64
mdadm/focal,now 4.1-5ubuntu1 amd64
mime-support/focal,focal,now 3.64ubuntu1 all
mount/focal,now 2.34-0.1ubuntu9 amd64
mtr-tiny/focal,now 0.93-1 amd64
multipath-tools/focal,now 0.8.3-1ubuntu2 amd64
nano/focal,now 4.8-1ubuntu1 amd64
ncurses-base/focal,focal,now 6.2-0ubuntu2 all
ncurses-bin/focal,now 6.2-0ubuntu2 amd64
ncurses-term/focal,focal,now 6.2-0ubuntu2 all
netbase/focal,focal,now 6.1 all
netcat-openbsd/focal,now 1.206-1ubuntu1 amd64
netplan.io/focal,now 0.99-0ubuntu1 amd64
networkd-dispatcher/focal,focal,now 2.0.1-1 all
ntfs-3g/focal,now 1:2017.3.23AR.3-3ubuntu1 amd64
open-iscsi/focal,now 2.0.874-7.1ubuntu6 amd64
open-vm-tools/focal,now 2:11.0.5-4 amd64
openssh-client/focal,now 1:8.2p1-4 amd64
openssh-server/focal,now 1:8.2p1-4 amd64
openssh-sftp-server/focal,now 1:8.2p1-4 amd64
openssl/focal,now 1.1.1f-1ubuntu2 amd64
os-prober/focal,now 1.74ubuntu2 amd64
overlayroot/focal,focal,now 0.45ubuntu1 all
packagekit-tools/focal,now 1.1.13-2ubuntu1 amd64
packagekit/focal,now 1.1.13-2ubuntu1 amd64
parted/focal,now 3.3-4 amd64
passwd/focal,now 1:4.8.1-1ubuntu5 amd64
pastebinit/focal,focal,now 1.5.1-1 all
patch/focal,now 2.7.6-6 amd64
pci.ids/focal,focal,now 0.0~2020.03.20-1 all
pciutils/focal,now 1:3.6.4-1 amd64
perl-base/focal,now 5.30.0-9build1 amd64
perl-modules-5.30/focal,focal,now 5.30.0-9build1 all
perl/focal,now 5.30.0-9build1 amd64
pinentry-curses/focal,now 1.1.0-3build1 amd64
plymouth-theme-ubuntu-text/focal,now 0.9.4git20200323-0ubuntu6 amd64
plymouth/focal,now 0.9.4git20200323-0ubuntu6 amd64
policykit-1/focal,now 0.105-26ubuntu1 amd64
pollinate/focal,focal,now 4.33-3ubuntu1 all
popularity-contest/focal,focal,now 1.69ubuntu1 all
powermgmt-base/focal,focal,now 1.36 all
procps/focal,now 2:3.3.16-1ubuntu2 amd64
psmisc/focal,now 23.3-1 amd64
publicsuffix/focal,focal,now 20200303.0012-1 all
python-apt-common/focal,focal,now 2.0.0 all
python3-apport/focal,focal,now 2.20.11-0ubuntu27 all
python3-apt/focal,now 2.0.0 amd64
python3-attr/focal,focal,now 19.3.0-2 all
python3-automat/focal,focal,now 0.8.0-1ubuntu1 all
python3-blinker/focal,focal,now 1.4+dfsg1-0.3ubuntu1 all
python3-certifi/focal,focal,now 2019.11.28-1 all
python3-cffi-backend/focal,now 1.14.0-1build1 amd64
python3-chardet/focal,focal,now 3.0.4-4build1 all
python3-click/focal,focal,now 7.0-3 all
python3-colorama/focal,focal,now 0.4.3-1build1 all
python3-commandnotfound/focal,focal,now 20.04.2 all
python3-configobj/focal,focal,now 5.0.6-4 all
python3-constantly/focal,focal,now 15.1.0-1build1 all
python3-cryptography/focal,now 2.8-3 amd64
python3-dbus/focal,now 1.2.16-1build1 amd64
python3-debconf/focal,focal,now 1.5.73 all
python3-debian/focal,focal,now 0.1.36ubuntu1 all
python3-distro-info/focal,focal,now 0.23ubuntu1 all
python3-distro/focal,focal,now 1.4.0-1 all
python3-distupgrade/focal,focal,now 1:20.04.18 all
python3-entrypoints/focal,focal,now 0.3-2ubuntu1 all
python3-gdbm/focal,now 3.8.2-1ubuntu1 amd64
python3-gi/focal,now 3.36.0-1 amd64
python3-hamcrest/focal,focal,now 1.9.0-3 all
python3-httplib2/focal,focal,now 0.14.0-1ubuntu1 all
python3-hyperlink/focal,focal,now 19.0.0-1 all
python3-idna/focal,focal,now 2.8-1 all
python3-incremental/focal,focal,now 16.10.1-3.2 all
python3-jwt/focal,focal,now 1.7.1-2ubuntu2 all
python3-keyring/focal,focal,now 18.0.1-2ubuntu1 all
python3-launchpadlib/focal,focal,now 1.10.13-1 all
python3-lazr.restfulclient/focal,focal,now 0.14.2-2build1 all
python3-lazr.uri/focal,focal,now 1.0.3-4build1 all
python3-minimal/focal,now 3.8.2-0ubuntu2 amd64
python3-nacl/focal,now 1.3.0-5 amd64
python3-netifaces/focal,now 0.10.4-1ubuntu4 amd64
python3-newt/focal,now 0.52.21-4ubuntu2 amd64
python3-oauthlib/focal,focal,now 3.1.0-1ubuntu2 all
python3-openssl/focal,focal,now 19.0.0-1build1 all
python3-pkg-resources/focal,focal,now 45.2.0-1 all
python3-problem-report/focal,focal,now 2.20.11-0ubuntu27 all
python3-pyasn1-modules/focal,focal,now 0.2.1-0.2build1 all
python3-pyasn1/focal,focal,now 0.4.2-3build1 all
python3-pymacaroons/focal,focal,now 0.13.0-3 all
python3-requests-unixsocket/focal,focal,now 0.2.0-2 all
python3-requests/now 2.22.0-2build1 all
python3-secretstorage/focal,focal,now 2.3.1-2ubuntu1 all
python3-service-identity/focal,focal,now 18.1.0-5build1 all
python3-simplejson/focal,now 3.16.0-2ubuntu2 amd64
python3-six/focal,focal,now 1.14.0-2 all
python3-software-properties/focal,focal,now 0.98.9 all
python3-systemd/focal,now 234-3build2 amd64
python3-twisted-bin/focal,now 18.9.0-11 amd64
python3-twisted/focal,focal,now 18.9.0-11 all
python3-update-manager/focal,focal,now 1:20.04.9 all
python3-urllib3/focal,focal,now 1.25.8-2 all
python3-wadllib/focal,focal,now 1.3.3-3build1 all
python3-yaml/focal,now 5.3.1-1 amd64
python3-zope.interface/focal,now 4.7.1-1 amd64
python3.8-minimal/focal,now 3.8.2-1ubuntu1 amd64
python3.8/focal,now 3.8.2-1ubuntu1 amd64
python3/focal,now 3.8.2-0ubuntu2 amd64
readline-common/focal,focal,now 8.0-4 all
rsync/focal,now 3.1.3-8 amd64
rsyslog/focal,now 8.2001.0-1ubuntu1 amd64
run-one/focal,focal,now 1.17-0ubuntu1 all
sbsigntool/focal,now 0.9.2-2ubuntu1 amd64
screen/focal,now 4.8.0-1 amd64
secureboot-db/focal,now 1.5 amd64
sed/focal,now 4.7-1 amd64
sensible-utils/focal,focal,now 0.0.12+nmu1 all
sg3-utils-udev/focal,focal,now 1.44-1ubuntu2 all
sg3-utils/focal,now 1.44-1ubuntu2 amd64
shared-mime-info/focal,now 1.15-1 amd64
snapd/focal,now 2.44.3+20.04 amd64
software-properties-common/focal,focal,now 0.98.9 all
sosreport/focal,now 3.9-1ubuntu2 amd64
sound-theme-freedesktop/focal,focal,now 0.8-2ubuntu1 all
squashfs-tools/focal,now 1:4.4-1 amd64
ssh-import-id/focal,focal,now 5.10-0ubuntu1 all
strace/focal,now 4.26-0.2ubuntu3 amd64
sudo/focal,now 1.8.31-1ubuntu1 amd64
systemd-sysv/focal,now 245.4-4ubuntu3 amd64
systemd-timesyncd/focal,now 245.4-4ubuntu3 amd64
systemd/focal,now 245.4-4ubuntu3 amd64
sysvinit-utils/focal,now 2.96-2.1ubuntu1 amd64
tar/focal,now 1.30+dfsg-7 amd64
[COLOR=green]**tasksel-data/focal,focal,now 3.34ubuntu16 all**[/COLOR]
[COLOR=green]**tasksel/focal,focal,now 3.34ubuntu16 all**[/COLOR]
tcpdump/focal,now 4.9.3-4 amd64
telnet/focal,now 0.17-41.2build1 amd64
thin-provisioning-tools/focal,now 0.8.5-4build1 amd64
time/focal,now 1.7-25.1build1 amd64
tmux/focal,now 3.0a-2 amd64
tpm-udev/focal,focal,now 0.4 all
tzdata/focal,focal,now 2019c-3ubuntu1 all
ubuntu-advantage-tools/focal,now 20.3 amd64
ubuntu-keyring/focal,focal,now 2020.02.11.2 all
ubuntu-minimal/focal,now 1.450 amd64
ubuntu-release-upgrader-core/focal,focal,now 1:20.04.18 all
ubuntu-server/focal,now 1.450 amd64
ubuntu-standard/focal,now 1.450 amd64
ucf/focal,focal,now 3.0038+nmu1 all
udev/focal,now 245.4-4ubuntu3 amd64
ufw/focal,focal,now 0.36-6 all
unattended-upgrades/focal,focal,now 2.3 all
update-manager-core/focal,focal,now 1:20.04.9 all
update-notifier-common/focal,focal,now 3.192.30 all
usb.ids/focal,focal,now 2020.03.19-1 all
usbutils/focal,now 1:012-2 amd64
util-linux/focal,now 2.34-0.1ubuntu9 amd64
uuid-runtime/focal,now 2.34-0.1ubuntu9 amd64
vim-common/focal,focal,now 2:8.1.2269-1ubuntu5 all
vim-runtime/focal,focal,now 2:8.1.2269-1ubuntu5 all
vim-tiny/focal,now 2:8.1.2269-1ubuntu5 amd64
vim/focal,now 2:8.1.2269-1ubuntu5 amd64
wget/focal,now 1.20.3-1ubuntu1 amd64
whiptail/focal,now 0.52.21-4ubuntu2 amd64
wireless-regdb/focal,focal,now 2018.05.09-0ubuntu1 all
xauth/focal,now 1:1.1-0ubuntu1 amd64
xdg-user-dirs/focal,now 0.17-2ubuntu1 amd64
xfsprogs/focal,now 5.3.0-1ubuntu2 amd64
xkb-data/focal,focal,now 2.29-2 all
xxd/focal,now 2:8.1.2269-1ubuntu5 amd64
xz-utils/focal,now 5.2.4-1 amd64
zerofree/focal,now 1.1.1-1 amd64
zlib1g/focal,now 1:1.2.11.dfsg-2ubuntu1 amd64

```

**EDIT:** Here are just the lines that are installed with the "legacy" installer that are not installed with the "live" installer

```

[color=green]**installation-report/focal,focal,now 2.62ubuntu1 all**[/color]
[color=green]**language-pack-en-base/focal,focal,now 1:20.04+20200416 all**[/color]
[color=green]**language-pack-en/focal,focal,now 1:20.04+20200416 all**[/color]
[color=green]**laptop-detect/focal,focal,now 0.16 all**[/color]
[color=green]**tasksel-data/focal,focal,now 3.34ubuntu16 all**[/color]
[color=green]**tasksel/focal,focal,now 3.34ubuntu16 all**[/color]

```

---

### Post by mastablasta on 2020-05-12
tasksel makes sense so it is easier to add services (the whole packages).

but why is the en language pack needed for? maybe it's a dependency of tasksel as it explains some things?

also laptop detect => nice. good for those trying to go really minimal.

---

### Post by LHammonds on 2020-05-12
I have no idea why there is a different end-result when using two different installers.

If you were trying to make a different installer, one would think an important goal of such a project would be to end up with an identical system when done but this clearly was not the goal and I have no idea why it wasn't.  I just need to make sure that when I use the "live" installer that I get a system I want.  After I posted the differences here, I thought it a good idea to go ahead and create a new thread dedicated to finding out what the differences are between live and legacy in 20.04 like we had in 18.04.

LHammonds

---

