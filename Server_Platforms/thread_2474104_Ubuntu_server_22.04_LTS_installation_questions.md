---
title: "Ubuntu server 22.04 LTS installation questions"
date: 2022-04-22
forum: Server Platforms
---

### Post by smeerbartje on 2022-04-22
Hey here!
I'm running 3x Ubuntu servers on my homelab on a Proxmox box. Very happy with it.
Now I'm checking out the new 22.04 LTS release of ubuntu server and I have two questions.

[LIST=1]
[*]First, what is Ubuntu server minimized? I cannot really find information about this.
[*]How long does the "probing for block devices" take? I looks like it takes forever
[/LIST]

---

### Post by Doug S on 2022-04-23
> **smeerbartje said:**
> 
How long does the "probing for block devices" take? I looks like it takes forever
 Are you saying ISO boot up hangs before you even get to the install or test run decision? It hangs for me (not on a Proxmox box). See [here ]("https://ubuntuforums.org/showthread.php?t=2473780&p=14091638#post14091638")and perhaps chime in on the linked bug reports.

---

### Post by smeerbartje on 2022-05-01
Yeah well, I just retried and now everything works fine. Don't know what happened earlier.
The problem occured AFTER installing ubuntu server on the VM. Right after the moment that it complains about the presence of the installation ISO.

---

### Post by LHammonds on 2022-05-02
> **smeerbartje said:**
> what is Ubuntu server minimized? I cannot really find information about this.
Good question.  From what I have seen, the minimized version is a reduced set of pre-installed software compared to the normal server installation.  For example, I could not even find a text editor on the minimized version to make changes to a config file.  No VI, no nano, nothing that I could find.

I will install both versions and save the installed software to a file and then compare the differences and post what I find here.

Here are the commands I will run on the minimized version:
```

apt list --installed > /tmp/ubuntu-2204-minimized-apps.txt

```
I will then transfer the file to the full install and run these commands on it:
```

apt list --installed > /tmp/ubuntu-2204-full-apps.txt
diff /tmp/ubuntu-2204-minimized-apps.txt /tmp/ubuntu-2204-full-apps.txt > /tmp/ubuntu-2204-apps-diff.txt

```

Contents of /tmp/ubuntu-2204-minimized-apps.txt (420 packages)
```

Linux 2204minimized 5.15.0-27-generic #28-Ubuntu SMP Thu Apr 14 04:55:28 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
adduser/jammy,now 3.118ubuntu5
amd64-microcode/jammy,now 3.20191218.1ubuntu2
apparmor/jammy,now 3.0.4-2ubuntu2
apport-symptoms/jammy,now 0.24
apport/jammy,now 2.20.11-0ubuntu82
apt/jammy,now 2.4.5
base-files/jammy-updates,now 12ubuntu4.1
base-passwd/jammy,now 3.5.52build1
bash/jammy,now 5.1-6ubuntu1
bcache-tools/jammy,now 1.0.8-4ubuntu3
binutils-common/jammy,now 2.38-3ubuntu1
binutils-x86-64-linux-gnu/jammy,now 2.38-3ubuntu1
binutils/jammy,now 2.38-3ubuntu1
bsdutils/jammy,now 1:2.37.2-4ubuntu3
btrfs-progs/jammy,now 5.16.2-1
busybox-initramfs/jammy,now 1:1.30.1-7ubuntu3
ca-certificates/jammy,now 20211016
cloud-guest-utils/jammy,now 0.32-22-g45fe84a5-0ubuntu1
cloud-init/jammy,now 22.1-14-g2e17a0d6-0ubuntu1~22.04.5
console-setup-linux/jammy,now 1.205ubuntu3
console-setup/jammy,now 1.205ubuntu3
coreutils/jammy,now 8.32-4.1ubuntu1
cpio/jammy,now 2.13+dfsg-7
cryptsetup-bin/jammy,now 2:2.4.3-1ubuntu1
cryptsetup-initramfs/jammy,now 2:2.4.3-1ubuntu1
cryptsetup/jammy,now 2:2.4.3-1ubuntu1
curl/jammy-updates,jammy-security,now 7.81.0-1ubuntu1.1
dash/jammy,now 0.5.11+git20210903+057cd650a4ed-3build1
dbus-user-session/jammy,now 1.12.20-2ubuntu4
dbus/jammy,now 1.12.20-2ubuntu4
debconf/jammy,now 1.5.79ubuntu1
debianutils/jammy,now 5.5-1ubuntu2
diffutils/jammy,now 1:3.8-0ubuntu2
dirmngr/jammy,now 2.2.27-3ubuntu2
distro-info-data/jammy-updates,jammy-security,now 0.52ubuntu0.1
dmeventd/jammy,now 2:1.02.175-2.1ubuntu4
dmsetup/jammy,now 2:1.02.175-2.1ubuntu4
dpkg/jammy,now 1.21.1ubuntu2
e2fsprogs/jammy,now 1.46.5-2ubuntu1
eatmydata/jammy,now 130-2build1
fdisk/jammy,now 2.37.2-4ubuntu3
finalrd/jammy,now 9build1
findutils/jammy,now 4.8.0-1ubuntu3
firmware-sof-signed/jammy,now 2.0-1ubuntu2
fuse3/jammy,now 3.10.5-1build1
gawk/jammy,now 1:5.1.0-1build3
gcc-12-base/jammy,now 12-20220319-1ubuntu1
gdisk/jammy,now 1.0.8-4build1
gettext-base/jammy,now 0.21-4ubuntu4
gir1.2-glib-2.0/jammy,now 1.72.0-1
gir1.2-packagekitglib-1.0/jammy,now 1.2.5-2ubuntu2
gnupg-l10n/jammy,now 2.2.27-3ubuntu2
gnupg-utils/jammy,now 2.2.27-3ubuntu2
gnupg/jammy,now 2.2.27-3ubuntu2
gpg-agent/jammy,now 2.2.27-3ubuntu2
gpg-wks-client/jammy,now 2.2.27-3ubuntu2
gpg-wks-server/jammy,now 2.2.27-3ubuntu2
gpg/jammy,now 2.2.27-3ubuntu2
gpgconf/jammy,now 2.2.27-3ubuntu2
gpgsm/jammy,now 2.2.27-3ubuntu2
gpgv/jammy,now 2.2.27-3ubuntu2
grep/jammy,now 3.7-1build1
groff-base/jammy,now 1.22.4-8build1
grub-common/jammy,now 2.06-2ubuntu7
grub-gfxpayload-lists/jammy,now 0.7
grub-pc-bin/jammy,now 2.06-2ubuntu7
grub-pc/jammy,now 2.06-2ubuntu7
grub2-common/jammy,now 2.06-2ubuntu7
gzip/jammy,now 1.10-4ubuntu4
hostname/jammy,now 3.23ubuntu2
init-system-helpers/jammy,now 1.62
initramfs-tools-bin/jammy,now 0.140ubuntu13
initramfs-tools-core/jammy,now 0.140ubuntu13
initramfs-tools/jammy,now 0.140ubuntu13
intel-microcode/jammy,now 3.20210608.2ubuntu1
iproute2/jammy,now 5.15.0-1ubuntu2
isc-dhcp-client/jammy,now 4.4.1-2.3ubuntu2
isc-dhcp-common/jammy,now 4.4.1-2.3ubuntu2
iso-codes/jammy,now 4.9.0-1
iucode-tool/jammy,now 2.3.1-1build1
kbd/jammy,now 2.3.0-3ubuntu4
keyboard-configuration/jammy,now 1.205ubuntu3
klibc-utils/jammy,now 2.0.10-4
kmod/jammy,now 29-1ubuntu1
kpartx/jammy,now 0.8.8-1ubuntu1
libacl1/jammy,now 2.3.1-1
libaio1/jammy,now 0.3.112-13build1
libapparmor1/jammy,now 3.0.4-2ubuntu2
libappstream4/jammy,now 0.15.2-2
libapt-pkg6.0/jammy,now 2.4.5
libargon2-1/jammy,now 0~20171227-0.3
libassuan0/jammy,now 2.5.5-1build1
libatm1/jammy,now 1:2.5.1-4build2
libattr1/jammy,now 1:2.5.1-1build1
libaudit-common/jammy,now 1:3.0.7-1build1
libaudit1/jammy,now 1:3.0.7-1build1
libbinutils/jammy,now 2.38-3ubuntu1
libblkid1/jammy,now 2.37.2-4ubuntu3
libbpf0/jammy,now 1:0.5.0-1
libbrotli1/jammy,now 1.0.9-2build6
libbsd0/jammy,now 0.11.5-1
libbz2-1.0/jammy,now 1.0.8-5build1
libc-bin/jammy,now 2.35-0ubuntu3
libc6/jammy,now 2.35-0ubuntu3
libcap-ng0/jammy,now 0.7.9-2.2build3
libcap2-bin/jammy,now 1:2.44-1build3
libcap2/jammy,now 1:2.44-1build3
libcbor0.8/jammy,now 0.8.0-2ubuntu1
libcom-err2/jammy,now 1.46.5-2ubuntu1
libcrypt1/jammy,now 1:4.4.27-1
libcryptsetup12/jammy,now 2:2.4.3-1ubuntu1
libctf-nobfd0/jammy,now 2.38-3ubuntu1
libctf0/jammy,now 2.38-3ubuntu1
libcurl3-gnutls/jammy-updates,jammy-security,now 7.81.0-1ubuntu1.1
libcurl4/jammy-updates,jammy-security,now 7.81.0-1ubuntu1.1
libdb5.3/jammy,now 5.3.28+dfsg1-0.8ubuntu3
libdbus-1-3/jammy,now 1.12.20-2ubuntu4
libdbus-glib-1-2/jammy,now 0.112-2build1
libdebconfclient0/jammy,now 0.261ubuntu1
libdevmapper-event1.02.1/jammy,now 2:1.02.175-2.1ubuntu4
libdevmapper1.02.1/jammy,now 2:1.02.175-2.1ubuntu4
libdns-export1110/jammy,now 1:9.11.19+dfsg-2.1ubuntu3
libdrm-common/jammy,now 2.4.110-1ubuntu1
libdrm2/jammy,now 2.4.110-1ubuntu1
libdw1/jammy,now 0.186-1build1
libeatmydata1/jammy,now 130-2build1
libedit2/jammy,now 3.1-20210910-1build1
libefiboot1/jammy,now 37-6ubuntu2
libefivar1/jammy,now 37-6ubuntu2
libelf1/jammy,now 0.186-1build1
libevdev2/jammy,now 1.12.1+dfsg-1
libexpat1/jammy,now 2.4.7-1
libext2fs2/jammy,now 1.46.5-2ubuntu1
libfdisk1/jammy,now 2.37.2-4ubuntu3
libffi8/jammy,now 3.4.2-4
libfido2-1/jammy,now 1.10.0-1
libfreetype6/jammy,now 2.11.1+dfsg-1build1
libfuse3-3/jammy,now 3.10.5-1build1
libgcc-s1/jammy,now 12-20220319-1ubuntu1
libgcrypt20/jammy,now 1.9.4-3ubuntu3
libgdbm-compat4/jammy,now 1.23-1
libgdbm6/jammy,now 1.23-1
libgirepository-1.0-1/jammy,now 1.72.0-1
libglib2.0-0/jammy,now 2.72.1-1
libglib2.0-bin/jammy,now 2.72.1-1
libglib2.0-data/jammy,now 2.72.1-1
libgmp10/jammy,now 2:6.2.1+dfsg-3ubuntu1
libgnutls30/jammy,now 3.7.3-4ubuntu1
libgpg-error0/jammy,now 1.43-3
libgssapi-krb5-2/jammy,now 1.19.2-2
libgstreamer1.0-0/jammy,now 1.20.1-1
libgudev-1.0-0/jammy,now 1:237-2build1
libhogweed6/jammy,now 3.7.3-1build2
libicu70/jammy,now 70.1-2
libidn2-0/jammy,now 2.3.2-2build1
libimobiledevice6/jammy,now 1.3.0-6build3
libinih1/jammy,now 53-1ubuntu3
libintl-perl/jammy,now 1.26-3build2
libintl-xs-perl/jammy,now 1.26-3build2
libip4tc2/jammy,now 1.8.7-1ubuntu5
libisc-export1105/jammy,now 1:9.11.19+dfsg-2.1ubuntu3
libisns0/jammy,now 0.101-0ubuntu2
libjson-c5/jammy,now 0.15-2build4
libk5crypto3/jammy,now 1.19.2-2
libkeyutils1/jammy,now 1.6.1-2ubuntu3
libklibc/jammy,now 2.0.10-4
libkmod2/jammy,now 29-1ubuntu1
libkrb5-3/jammy,now 1.19.2-2
libkrb5support0/jammy,now 1.19.2-2
libksba8/jammy,now 1.6.0-2build1
libldap-2.5-0/jammy,now 2.5.11+dfsg-1~exp1ubuntu3
libldap-common/jammy,now 2.5.11+dfsg-1~exp1ubuntu3
liblocale-gettext-perl/jammy,now 1.07-4build3
liblvm2cmd2.03/jammy,now 2.03.11-2.1ubuntu4
liblz4-1/jammy,now 1.9.3-2build2
liblzma5/jammy,now 5.2.5-2ubuntu1
liblzo2-2/jammy,now 2.10-2build3
libmd0/jammy,now 1.0.4-1build1
libmnl0/jammy,now 1.0.4-3build2
libmodule-find-perl/jammy,now 0.15-1
libmodule-scandeps-perl/jammy,now 1.31-1
libmount1/jammy,now 2.37.2-4ubuntu3
libmpdec3/jammy,now 2.5.1-2build2
libmpfr6/jammy,now 4.1.0-3build3
libncurses6/jammy,now 6.3-2
libncursesw6/jammy,now 6.3-2
libnetplan0/jammy,now 0.104-0ubuntu2
libnettle8/jammy,now 3.7.3-1build2
libnghttp2-14/jammy,now 1.43.0-1build3
libnpth0/jammy,now 1.6-3build2
libnsl2/jammy,now 1.3.0-2build2
libnss-systemd/jammy,now 249.11-0ubuntu3
libntfs-3g89/jammy,now 1:2021.8.22-3ubuntu1
libopeniscsiusr/jammy,now 2.1.5-1ubuntu1
libp11-kit0/jammy,now 0.24.0-6build1
libpackagekit-glib2-18/jammy,now 1.2.5-2ubuntu2
libpam-cap/jammy,now 1:2.44-1build3
libpam-modules-bin/jammy,now 1.4.0-11ubuntu2
libpam-modules/jammy,now 1.4.0-11ubuntu2
libpam-runtime/jammy,now 1.4.0-11ubuntu2
libpam-systemd/jammy,now 249.11-0ubuntu3
libpam0g/jammy,now 1.4.0-11ubuntu2
libpci3/jammy,now 1:3.7.0-6
libpcre2-8-0/jammy,now 10.39-3build1
libpcre3/jammy,now 2:8.39-13build5
libperl5.34/jammy,now 5.34.0-3ubuntu1
libplist3/jammy,now 2.2.0-6build2
libplymouth5/jammy,now 0.9.5+git20211018-1ubuntu3
libpng16-16/jammy,now 1.6.37-3build5
libpolkit-agent-1-0/jammy,now 0.105-33
libpolkit-gobject-1-0/jammy,now 0.105-33
libpopt0/jammy,now 1.18-3build1
libproc-processtable-perl/jammy,now 0.634-1build1
libprocps8/jammy,now 2:3.3.17-6ubuntu2
libpsl5/jammy,now 0.21.0-1.2build2
libpython3-stdlib/jammy,now 3.10.4-0ubuntu2
libpython3.10-minimal/jammy,now 3.10.4-3
libpython3.10-stdlib/jammy,now 3.10.4-3
libreadline8/jammy,now 8.1.2-1
librtmp1/jammy,now 2.4+20151223.gitfa8646d.1-2build4
libsasl2-2/jammy,now 2.1.27+dfsg2-3ubuntu1
libsasl2-modules-db/jammy,now 2.1.27+dfsg2-3ubuntu1
libsasl2-modules/jammy,now 2.1.27+dfsg2-3ubuntu1
libseccomp2/jammy,now 2.5.3-2ubuntu2
libselinux1/jammy,now 3.3-1build2
libsemanage-common/jammy,now 3.3-1build2
libsemanage2/jammy,now 3.3-1build2
libsepol2/jammy,now 3.3-1build1
libsgutils2-2/jammy,now 1.46-1build1
libsigsegv2/jammy,now 2.13-1ubuntu3
libsmartcols1/jammy,now 2.37.2-4ubuntu3
libsort-naturally-perl/jammy,now 1.03-2
libsqlite3-0/jammy,now 3.37.2-2
libss2/jammy,now 1.46.5-2ubuntu1
libssh-4/jammy,now 0.9.6-2build1
libssl3/jammy,now 3.0.2-0ubuntu1
libstdc++6/jammy,now 12-20220319-1ubuntu1
libstemmer0d/jammy,now 2.2.0-1build1
libsystemd0/jammy,now 249.11-0ubuntu3
libtasn1-6/jammy,now 4.18.0-4build1
libterm-readkey-perl/jammy,now 2.38-1build4
libtinfo6/jammy,now 6.3-2
libtirpc-common/jammy,now 1.3.2-2build1
libtirpc3/jammy,now 1.3.2-2build1
libuchardet0/jammy,now 0.0.7-1build2
libudev1/jammy,now 249.11-0ubuntu3
libunistring2/jammy,now 1.0-1
libunwind8/jammy,now 1.3.2-2build2
libupower-glib3/jammy,now 0.99.17-1
liburcu8/jammy,now 0.13.1-1
libusb-1.0-0/jammy,now 2:1.0.25-1ubuntu1
libusbmuxd6/jammy,now 2.0.2-3build2
libuuid1/jammy,now 2.37.2-4ubuntu3
libwrap0/jammy,now 7.6.q-31build2
libx11-6/jammy,now 2:1.7.5-1
libx11-data/jammy,now 2:1.7.5-1
libxau6/jammy,now 1:1.0.9-1build5
libxcb1/jammy,now 1.14-3ubuntu3
libxdmcp6/jammy,now 1:1.1.3-0ubuntu5
libxext6/jammy,now 2:1.3.4-1build1
libxml2/jammy,now 2.9.13+dfsg-1build1
libxmlb2/jammy,now 0.3.6-2build1
libxmuu1/jammy,now 2:1.1.3-3
libxtables12/jammy,now 1.8.7-1ubuntu5
libxxhash0/jammy,now 0.8.1-1
libyaml-0-2/jammy,now 0.2.2-1build2
libzstd1/jammy,now 1.4.8+dfsg-3build1
linux-base/jammy,now 4.5ubuntu9
linux-firmware/jammy,now 20220329.git681281e4-0ubuntu1
linux-generic/jammy-updates,jammy-security,now 5.15.0.27.30
linux-headers-5.15.0-27-generic/jammy-updates,jammy-security,now 5.15.0-27.28
linux-headers-5.15.0-27/jammy-updates,jammy-security,now 5.15.0-27.28
linux-headers-generic/jammy-updates,jammy-security,now 5.15.0.27.30
linux-image-5.15.0-27-generic/jammy-updates,jammy-security,now 5.15.0-27.28
linux-image-generic/jammy-updates,jammy-security,now 5.15.0.27.30
linux-modules-5.15.0-27-generic/jammy-updates,jammy-security,now 5.15.0-27.28
linux-modules-extra-5.15.0-27-generic/jammy-updates,jammy-security,now 5.15.0-27.28
login/jammy,now 1:4.8.1-2ubuntu2
logsave/jammy,now 1.46.5-2ubuntu1
lsb-base/jammy,now 11.1.0ubuntu4
lsb-release/jammy,now 11.1.0ubuntu4
lvm2/jammy,now 2.03.11-2.1ubuntu4
lxd-installer/jammy,now 1
mawk/jammy,now 1.3.4.20200120-3
mdadm/jammy,now 4.2-0ubuntu1
media-types/jammy,now 7.0.0
mount/jammy,now 2.37.2-4ubuntu3
multipath-tools/jammy,now 0.8.8-1ubuntu1
ncurses-base/jammy,now 6.3-2
ncurses-bin/jammy,now 6.3-2
ncurses-term/jammy,now 6.3-2
needrestart/jammy,now 3.5-5ubuntu2
netbase/jammy,now 6.3
netplan.io/jammy,now 0.104-0ubuntu2
networkd-dispatcher/jammy-updates,jammy-security,now 2.1-2ubuntu0.22.04.1
ntfs-3g/jammy,now 1:2021.8.22-3ubuntu1
open-iscsi/jammy,now 2.1.5-1ubuntu1
openssh-client/jammy,now 1:8.9p1-3
openssh-server/jammy,now 1:8.9p1-3
openssh-sftp-server/jammy,now 1:8.9p1-3
openssl/jammy,now 3.0.2-0ubuntu1
os-prober/jammy,now 1.79ubuntu2
packagekit-tools/jammy,now 1.2.5-2ubuntu2
packagekit/jammy,now 1.2.5-2ubuntu2
passwd/jammy,now 1:4.8.1-2ubuntu2
pci.ids/jammy,now 0.0~2022.01.22-1
pciutils/jammy,now 1:3.7.0-6
perl-base/jammy,now 5.34.0-3ubuntu1
perl-modules-5.34/jammy,now 5.34.0-3ubuntu1
perl/jammy,now 5.34.0-3ubuntu1
pinentry-curses/jammy,now 1.1.1-1build2
pkexec/jammy,now 0.105-33
plymouth-theme-ubuntu-text/jammy,now 0.9.5+git20211018-1ubuntu3
plymouth/jammy,now 0.9.5+git20211018-1ubuntu3
policykit-1/jammy,now 0.105-33
polkitd/jammy,now 0.105-33
pollinate/jammy,now 4.33-3ubuntu2
procps/jammy,now 2:3.3.17-6ubuntu2
publicsuffix/jammy,now 20211207.1025-1
python-apt-common/jammy,now 2.3.0ubuntu2
python-babel-localedata/jammy,now 2.8.0+dfsg.1-7
python3-apport/jammy,now 2.20.11-0ubuntu82
python3-apt/jammy,now 2.3.0ubuntu2
python3-attr/jammy,now 21.2.0-1
python3-babel/jammy,now 2.8.0+dfsg.1-7
python3-blinker/jammy,now 1.4+dfsg1-0.4
python3-certifi/jammy,now 2020.6.20-1
python3-cffi-backend/jammy,now 1.15.0-1build2
python3-chardet/jammy,now 4.0.0-1
python3-click/jammy,now 8.0.3-1
python3-colorama/jammy,now 0.4.4-1
python3-configobj/jammy,now 5.0.6-5
python3-cryptography/jammy,now 3.4.8-1ubuntu2
python3-dbus/jammy,now 1.2.18-3build1
python3-distro-info/jammy,now 1.1build1
python3-distro/jammy,now 1.7.0-1
python3-distupgrade/jammy,now 1:22.04.10
python3-distutils/jammy,now 3.10.4-0ubuntu1
python3-gi/jammy,now 3.42.0-3build1
python3-httplib2/jammy,now 0.20.2-2
python3-idna/jammy,now 3.3-1
python3-importlib-metadata/jammy,now 4.6.4-1
python3-jeepney/jammy,now 0.7.1-3
python3-jinja2/jammy,now 3.0.3-1
python3-json-pointer/jammy,now 2.0-0ubuntu1
python3-jsonpatch/jammy,now 1.32-2
python3-jsonschema/jammy,now 3.2.0-0ubuntu2
python3-jwt/jammy,now 2.3.0-1
python3-keyring/jammy,now 23.5.0-1
python3-launchpadlib/jammy,now 1.10.16-1
python3-lazr.restfulclient/jammy,now 0.14.4-1
python3-lazr.uri/jammy,now 1.0.6-2
python3-lib2to3/jammy,now 3.10.4-0ubuntu1
python3-markupsafe/jammy,now 2.0.1-2build1
python3-minimal/jammy,now 3.10.4-0ubuntu2
python3-more-itertools/jammy,now 8.10.0-2
python3-netifaces/jammy,now 0.11.0-1build2
python3-oauthlib/jammy,now 3.2.0-1
python3-pkg-resources/jammy,now 59.6.0-1.2
python3-problem-report/jammy,now 2.20.11-0ubuntu82
python3-pyparsing/jammy,now 2.4.7-1
python3-pyrsistent/jammy,now 0.18.1-1build1
python3-requests/jammy,now 2.25.1+dfsg-2
python3-secretstorage/jammy,now 3.3.1-1
python3-serial/jammy,now 3.5-1
python3-setuptools/jammy,now 59.6.0-1.2
python3-six/jammy,now 1.16.0-3ubuntu1
python3-software-properties/jammy,now 0.99.22
python3-systemd/jammy,now 234-3ubuntu2
python3-tz/jammy,now 2022.1-1
python3-update-manager/jammy,now 1:22.04.9
python3-urllib3/jammy,now 1.26.5-1~exp1
python3-wadllib/jammy,now 1.3.6-1
python3-xkit/jammy,now 0.5.0ubuntu5
python3-yaml/jammy,now 5.4.1-1ubuntu1
python3-zipp/jammy,now 1.0.0-3
python3.10-minimal/jammy,now 3.10.4-3
python3.10/jammy,now 3.10.4-3
python3/jammy,now 3.10.4-0ubuntu2
readline-common/jammy,now 8.1.2-1
sed/jammy,now 4.8-1ubuntu2
sensible-utils/jammy,now 0.0.17
sg3-utils-udev/jammy,now 1.46-1build1
sg3-utils/jammy,now 1.46-1build1
shared-mime-info/jammy,now 2.1-2
snapd/jammy-updates,now 2.55.3+22.04ubuntu1
software-properties-common/jammy,now 0.99.22
squashfs-tools/jammy,now 1:4.5-3build1
ssh-import-id/jammy,now 5.11-0ubuntu1
sudo/jammy,now 1.9.9-1ubuntu2
systemd-sysv/jammy,now 249.11-0ubuntu3
systemd-timesyncd/jammy,now 249.11-0ubuntu3
systemd/jammy,now 249.11-0ubuntu3
sysvinit-utils/jammy,now 3.01-1ubuntu1
tar/jammy,now 1.34+dfsg-1build3
thermald/jammy,now 2.4.9-1
thin-provisioning-tools/jammy,now 0.9.0-2ubuntu1
tzdata/jammy,now 2022a-0ubuntu1
ubuntu-drivers-common/jammy,now 1:0.9.6.1
ubuntu-keyring/jammy,now 2021.03.26
ubuntu-release-upgrader-core/jammy,now 1:22.04.10
ubuntu-server-minimal/jammy,now 1.481
ucf/jammy,now 3.0043
udev/jammy,now 249.11-0ubuntu3
unattended-upgrades/jammy,now 2.8ubuntu1
upower/jammy,now 0.99.17-1
usbmuxd/jammy,now 1.1.1-2build2
usbutils/jammy,now 1:014-1build1
usrmerge/jammy,now 25ubuntu2
util-linux/jammy,now 2.37.2-4ubuntu3
wget/jammy,now 1.21.2-2ubuntu1
wireless-regdb/jammy,now 2021.08.28-0ubuntu1
xauth/jammy,now 1:1.1-1build2
xdg-user-dirs/jammy,now 0.17-2ubuntu4
xfsprogs/jammy,now 5.13.0-1ubuntu2
xkb-data/jammy,now 2.33-1
xxd/jammy,now 2:8.2.3995-1ubuntu2
xz-utils/jammy,now 5.2.5-2ubuntu1
zlib1g/jammy,now 1:1.2.11.dfsg-2ubuntu9
zstd/jammy,now 1.4.8+dfsg-3build1

```

Contents of /tmp/ubuntu-2204-full-apps.txt (606 packages)
```

Linux 2204full 5.15.0-27-generic #28-Ubuntu SMP Thu Apr 14 04:55:28 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
adduser/jammy,now 3.118ubuntu5
amd64-microcode/jammy,now 3.20191218.1ubuntu2
apparmor/jammy,now 3.0.4-2ubuntu2
apport-symptoms/jammy,now 0.24
apport/jammy,now 2.20.11-0ubuntu82
apt-utils/jammy,now 2.4.5
apt/jammy,now 2.4.5
base-files/jammy-updates,now 12ubuntu4.1
base-passwd/jammy,now 3.5.52build1
bash-completion/jammy,now 1:2.11-5ubuntu1
bash/jammy,now 5.1-6ubuntu1
bc/jammy,now 1.07.1-3build1
bcache-tools/jammy,now 1.0.8-4ubuntu3
bind9-dnsutils/jammy,now 1:9.18.1-1ubuntu1
bind9-host/jammy,now 1:9.18.1-1ubuntu1
bind9-libs/jammy,now 1:9.18.1-1ubuntu1
binutils-common/jammy,now 2.38-3ubuntu1
binutils-x86-64-linux-gnu/jammy,now 2.38-3ubuntu1
binutils/jammy,now 2.38-3ubuntu1
bolt/jammy,now 0.9.2-1
bsdextrautils/jammy,now 2.37.2-4ubuntu3
bsdutils/jammy,now 1:2.37.2-4ubuntu3
btrfs-progs/jammy,now 5.16.2-1
busybox-initramfs/jammy,now 1:1.30.1-7ubuntu3
busybox-static/jammy,now 1:1.30.1-7ubuntu3
byobu/jammy,now 5.133-1
ca-certificates/jammy,now 20211016
cloud-guest-utils/jammy,now 0.32-22-g45fe84a5-0ubuntu1
cloud-init/jammy,now 22.1-14-g2e17a0d6-0ubuntu1~22.04.5
cloud-initramfs-copymods/jammy,now 0.47ubuntu1
cloud-initramfs-dyn-netconf/jammy,now 0.47ubuntu1
command-not-found/jammy,now 22.04.0
console-setup-linux/jammy,now 1.205ubuntu3
console-setup/jammy,now 1.205ubuntu3
coreutils/jammy,now 8.32-4.1ubuntu1
cpio/jammy,now 2.13+dfsg-7
cron/jammy,now 3.0pl1-137ubuntu3
cryptsetup-bin/jammy,now 2:2.4.3-1ubuntu1
cryptsetup-initramfs/jammy,now 2:2.4.3-1ubuntu1
cryptsetup/jammy,now 2:2.4.3-1ubuntu1
curl/jammy-updates,jammy-security,now 7.81.0-1ubuntu1.1
dash/jammy,now 0.5.11+git20210903+057cd650a4ed-3build1
dbus-user-session/jammy,now 1.12.20-2ubuntu4
dbus/jammy,now 1.12.20-2ubuntu4
debconf-i18n/jammy,now 1.5.79ubuntu1
debconf/jammy,now 1.5.79ubuntu1
debianutils/jammy,now 5.5-1ubuntu2
diffutils/jammy,now 1:3.8-0ubuntu2
dirmngr/jammy,now 2.2.27-3ubuntu2
distro-info-data/jammy-updates,jammy-security,now 0.52ubuntu0.1
distro-info/jammy,now 1.1build1
dmeventd/jammy,now 2:1.02.175-2.1ubuntu4
dmidecode/jammy,now 3.3-3
dmsetup/jammy,now 2:1.02.175-2.1ubuntu4
dosfstools/jammy,now 4.2-1build3
dpkg/jammy,now 1.21.1ubuntu2
e2fsprogs/jammy,now 1.46.5-2ubuntu1
eatmydata/jammy,now 130-2build1
ed/jammy,now 1.18-1
eject/jammy,now 2.37.2-4ubuntu3
ethtool/jammy,now 1:5.16-1
fdisk/jammy,now 2.37.2-4ubuntu3
file/jammy,now 1:5.41-3
finalrd/jammy,now 9build1
findutils/jammy,now 4.8.0-1ubuntu3
firmware-sof-signed/jammy,now 2.0-1ubuntu2
fonts-ubuntu-console/jammy,now 0.83-6ubuntu1
friendly-recovery/jammy,now 0.2.42
ftp/jammy,now 20210827-4build1
fuse3/jammy,now 3.10.5-1build1
fwupd-signed/jammy,now 1.44+1.2-3
fwupd/jammy,now 1.7.5-3
gawk/jammy,now 1:5.1.0-1build3
gcc-12-base/jammy,now 12-20220319-1ubuntu1
gdisk/jammy,now 1.0.8-4build1
gettext-base/jammy,now 0.21-4ubuntu4
gir1.2-glib-2.0/jammy,now 1.72.0-1
gir1.2-packagekitglib-1.0/jammy,now 1.2.5-2ubuntu2
git-man/jammy-updates,jammy-security,now 1:2.34.1-1ubuntu1.2
git/jammy-updates,jammy-security,now 1:2.34.1-1ubuntu1.2
gnupg-l10n/jammy,now 2.2.27-3ubuntu2
gnupg-utils/jammy,now 2.2.27-3ubuntu2
gnupg/jammy,now 2.2.27-3ubuntu2
gpg-agent/jammy,now 2.2.27-3ubuntu2
gpg-wks-client/jammy,now 2.2.27-3ubuntu2
gpg-wks-server/jammy,now 2.2.27-3ubuntu2
gpg/jammy,now 2.2.27-3ubuntu2
gpgconf/jammy,now 2.2.27-3ubuntu2
gpgsm/jammy,now 2.2.27-3ubuntu2
gpgv/jammy,now 2.2.27-3ubuntu2
grep/jammy,now 3.7-1build1
groff-base/jammy,now 1.22.4-8build1
grub-common/jammy,now 2.06-2ubuntu7
grub-gfxpayload-lists/jammy,now 0.7
grub-pc-bin/jammy,now 2.06-2ubuntu7
grub-pc/jammy,now 2.06-2ubuntu7
grub2-common/jammy,now 2.06-2ubuntu7
gzip/jammy,now 1.10-4ubuntu4
hdparm/jammy,now 9.60+ds-1build3
hostname/jammy,now 3.23ubuntu2
htop/jammy,now 3.0.5-7build2
info/jammy,now 6.8-4build1
init-system-helpers/jammy,now 1.62
init/jammy,now 1.62
initramfs-tools-bin/jammy,now 0.140ubuntu13
initramfs-tools-core/jammy,now 0.140ubuntu13
initramfs-tools/jammy,now 0.140ubuntu13
install-info/jammy,now 6.8-4build1
intel-microcode/jammy,now 3.20210608.2ubuntu1
iproute2/jammy,now 5.15.0-1ubuntu2
iptables/jammy,now 1.8.7-1ubuntu5
iputils-ping/jammy,now 3:20211215-1
iputils-tracepath/jammy,now 3:20211215-1
irqbalance/jammy,now 1.8.0-1build1
isc-dhcp-client/jammy,now 4.4.1-2.3ubuntu2
isc-dhcp-common/jammy,now 4.4.1-2.3ubuntu2
iso-codes/jammy,now 4.9.0-1
iucode-tool/jammy,now 2.3.1-1build1
kbd/jammy,now 2.3.0-3ubuntu4
keyboard-configuration/jammy,now 1.205ubuntu3
klibc-utils/jammy,now 2.0.10-4
kmod/jammy,now 29-1ubuntu1
kpartx/jammy,now 0.8.8-1ubuntu1
landscape-common/jammy,now 19.12-0ubuntu13
less/jammy,now 590-1build1
libacl1/jammy,now 2.3.1-1
libaio1/jammy,now 0.3.112-13build1
libapparmor1/jammy,now 3.0.4-2ubuntu2
libappstream4/jammy,now 0.15.2-2
libapt-pkg6.0/jammy,now 2.4.5
libarchive13/jammy,now 3.6.0-1ubuntu1
libargon2-1/jammy,now 0~20171227-0.3
libassuan0/jammy,now 2.5.5-1build1
libatasmart4/jammy,now 0.19-5build2
libatm1/jammy,now 1:2.5.1-4build2
libattr1/jammy,now 1:2.5.1-1build1
libaudit-common/jammy,now 1:3.0.7-1build1
libaudit1/jammy,now 1:3.0.7-1build1
libbinutils/jammy,now 2.38-3ubuntu1
libblkid1/jammy,now 2.37.2-4ubuntu3
libblockdev-crypto2/jammy,now 2.26-1
libblockdev-fs2/jammy,now 2.26-1
libblockdev-loop2/jammy,now 2.26-1
libblockdev-part-err2/jammy,now 2.26-1
libblockdev-part2/jammy,now 2.26-1
libblockdev-swap2/jammy,now 2.26-1
libblockdev-utils2/jammy,now 2.26-1
libblockdev2/jammy,now 2.26-1
libbpf0/jammy,now 1:0.5.0-1
libbrotli1/jammy,now 1.0.9-2build6
libbsd0/jammy,now 0.11.5-1
libbz2-1.0/jammy,now 1.0.8-5build1
libc-bin/jammy,now 2.35-0ubuntu3
libc6/jammy,now 2.35-0ubuntu3
libcap-ng0/jammy,now 0.7.9-2.2build3
libcap2-bin/jammy,now 1:2.44-1build3
libcap2/jammy,now 1:2.44-1build3
libcbor0.8/jammy,now 0.8.0-2ubuntu1
libcom-err2/jammy,now 1.46.5-2ubuntu1
libcrypt1/jammy,now 1:4.4.27-1
libcryptsetup12/jammy,now 2:2.4.3-1ubuntu1
libctf-nobfd0/jammy,now 2.38-3ubuntu1
libctf0/jammy,now 2.38-3ubuntu1
libcurl3-gnutls/jammy-updates,jammy-security,now 7.81.0-1ubuntu1.1
libcurl4/jammy-updates,jammy-security,now 7.81.0-1ubuntu1.1
libdb5.3/jammy,now 5.3.28+dfsg1-0.8ubuntu3
libdbus-1-3/jammy,now 1.12.20-2ubuntu4
libdbus-glib-1-2/jammy,now 0.112-2build1
libdebconfclient0/jammy,now 0.261ubuntu1
libdevmapper-event1.02.1/jammy,now 2:1.02.175-2.1ubuntu4
libdevmapper1.02.1/jammy,now 2:1.02.175-2.1ubuntu4
libdns-export1110/jammy,now 1:9.11.19+dfsg-2.1ubuntu3
libdrm-common/jammy,now 2.4.110-1ubuntu1
libdrm2/jammy,now 2.4.110-1ubuntu1
libdw1/jammy,now 0.186-1build1
libeatmydata1/jammy,now 130-2build1
libedit2/jammy,now 3.1-20210910-1build1
libefiboot1/jammy,now 37-6ubuntu2
libefivar1/jammy,now 37-6ubuntu2
libelf1/jammy,now 0.186-1build1
liberror-perl/jammy,now 0.17029-1
libestr0/jammy,now 0.1.10-2.1build3
libevdev2/jammy,now 1.12.1+dfsg-1
libevent-core-2.1-7/jammy,now 2.1.12-stable-1build3
libexpat1/jammy,now 2.4.7-1
libext2fs2/jammy,now 1.46.5-2ubuntu1
libfastjson4/jammy,now 0.99.9-1build2
libfdisk1/jammy,now 2.37.2-4ubuntu3
libffi8/jammy,now 3.4.2-4
libfido2-1/jammy,now 1.10.0-1
libflashrom1/jammy,now 1.2-5build1
libfreetype6/jammy,now 2.11.1+dfsg-1build1
libfribidi0/jammy-updates,jammy-security,now 1.0.8-2ubuntu3.1
libftdi1-2/jammy,now 1.5-5build3
libfuse3-3/jammy,now 3.10.5-1build1
libfwupd2/jammy,now 1.7.5-3
libfwupdplugin5/jammy,now 1.7.5-3
libgcab-1.0-0/jammy,now 1.4-3build2
libgcc-s1/jammy,now 12-20220319-1ubuntu1
libgcrypt20/jammy,now 1.9.4-3ubuntu3
libgdbm-compat4/jammy,now 1.23-1
libgdbm6/jammy,now 1.23-1
libgirepository-1.0-1/jammy,now 1.72.0-1
libglib2.0-0/jammy,now 2.72.1-1
libglib2.0-bin/jammy,now 2.72.1-1
libglib2.0-data/jammy,now 2.72.1-1
libgmp10/jammy,now 2:6.2.1+dfsg-3ubuntu1
libgnutls30/jammy,now 3.7.3-4ubuntu1
libgpg-error0/jammy,now 1.43-3
libgpgme11/jammy,now 1.16.0-1.2ubuntu4
libgpm2/jammy,now 1.20.7-10build1
libgssapi-krb5-2/jammy,now 1.19.2-2
libgstreamer1.0-0/jammy,now 1.20.1-1
libgudev-1.0-0/jammy,now 1:237-2build1
libgusb2/jammy,now 0.3.10-1
libhogweed6/jammy,now 3.7.3-1build2
libicu70/jammy,now 70.1-2
libidn2-0/jammy,now 2.3.2-2build1
libimobiledevice6/jammy,now 1.3.0-6build3
libinih1/jammy,now 53-1ubuntu3
libintl-perl/jammy,now 1.26-3build2
libintl-xs-perl/jammy,now 1.26-3build2
libip4tc2/jammy,now 1.8.7-1ubuntu5
libip6tc2/jammy,now 1.8.7-1ubuntu5
libisc-export1105/jammy,now 1:9.11.19+dfsg-2.1ubuntu3
libisns0/jammy,now 0.101-0ubuntu2
libjansson4/jammy,now 2.13.1-1.1build3
libjcat1/jammy,now 0.1.9-1
libjson-c5/jammy,now 0.15-2build4
libjson-glib-1.0-0/jammy,now 1.6.6-1build1
libjson-glib-1.0-common/jammy,now 1.6.6-1build1
libk5crypto3/jammy,now 1.19.2-2
libkeyutils1/jammy,now 1.6.1-2ubuntu3
libklibc/jammy,now 2.0.10-4
libkmod2/jammy,now 29-1ubuntu1
libkrb5-3/jammy,now 1.19.2-2
libkrb5support0/jammy,now 1.19.2-2
libksba8/jammy,now 1.6.0-2build1
libldap-2.5-0/jammy,now 2.5.11+dfsg-1~exp1ubuntu3
libldap-common/jammy,now 2.5.11+dfsg-1~exp1ubuntu3
liblmdb0/jammy,now 0.9.24-1build2
liblocale-gettext-perl/jammy,now 1.07-4build3
liblvm2cmd2.03/jammy,now 2.03.11-2.1ubuntu4
liblz4-1/jammy,now 1.9.3-2build2
liblzma5/jammy,now 5.2.5-2ubuntu1
liblzo2-2/jammy,now 2.10-2build3
libmagic-mgc/jammy,now 1:5.41-3
libmagic1/jammy,now 1:5.41-3
libmaxminddb0/jammy,now 1.5.2-1build2
libmbim-glib4/jammy,now 1.26.2-1build1
libmbim-proxy/jammy,now 1.26.2-1build1
libmd0/jammy,now 1.0.4-1build1
libmm-glib0/jammy,now 1.18.6-1
libmnl0/jammy,now 1.0.4-3build2
libmodule-find-perl/jammy,now 0.15-1
libmodule-scandeps-perl/jammy,now 1.31-1
libmount1/jammy,now 2.37.2-4ubuntu3
libmpdec3/jammy,now 2.5.1-2build2
libmpfr6/jammy,now 4.1.0-3build3
libmspack0/jammy,now 0.10.1-2build2
libncurses6/jammy,now 6.3-2
libncursesw6/jammy,now 6.3-2
libnetfilter-conntrack3/jammy,now 1.0.9-1
libnetplan0/jammy,now 0.104-0ubuntu2
libnettle8/jammy,now 3.7.3-1build2
libnewt0.52/jammy,now 0.52.21-5ubuntu2
libnfnetlink0/jammy,now 1.0.1-3build3
libnftables1/jammy,now 1.0.2-1ubuntu2
libnftnl11/jammy,now 1.2.1-1build1
libnghttp2-14/jammy,now 1.43.0-1build3
libnl-3-200/jammy,now 3.5.0-0.1
libnl-genl-3-200/jammy,now 3.5.0-0.1
libnpth0/jammy,now 1.6-3build2
libnsl2/jammy,now 1.3.0-2build2
libnspr4/jammy,now 2:4.32-3build1
libnss-systemd/jammy,now 249.11-0ubuntu3
libnss3/jammy,now 2:3.68.2-0ubuntu1
libntfs-3g89/jammy,now 1:2021.8.22-3ubuntu1
libnuma1/jammy,now 2.0.14-3ubuntu2
libopeniscsiusr/jammy,now 2.1.5-1ubuntu1
libp11-kit0/jammy,now 0.24.0-6build1
libpackagekit-glib2-18/jammy,now 1.2.5-2ubuntu2
libpam-cap/jammy,now 1:2.44-1build3
libpam-modules-bin/jammy,now 1.4.0-11ubuntu2
libpam-modules/jammy,now 1.4.0-11ubuntu2
libpam-runtime/jammy,now 1.4.0-11ubuntu2
libpam-systemd/jammy,now 249.11-0ubuntu3
libpam0g/jammy,now 1.4.0-11ubuntu2
libparted-fs-resize0/jammy,now 3.4-2build1
libparted2/jammy,now 3.4-2build1
libpcap0.8/jammy,now 1.10.1-4build1
libpci3/jammy,now 1:3.7.0-6
libpcre2-8-0/jammy,now 10.39-3build1
libpcre3/jammy,now 2:8.39-13build5
libperl5.34/jammy,now 5.34.0-3ubuntu1
libpipeline1/jammy,now 1.5.5-1
libplist3/jammy,now 2.2.0-6build2
libplymouth5/jammy,now 0.9.5+git20211018-1ubuntu3
libpng16-16/jammy,now 1.6.37-3build5
libpolkit-agent-1-0/jammy,now 0.105-33
libpolkit-gobject-1-0/jammy,now 0.105-33
libpopt0/jammy,now 1.18-3build1
libproc-processtable-perl/jammy,now 0.634-1build1
libprocps8/jammy,now 2:3.3.17-6ubuntu2
libpsl5/jammy,now 0.21.0-1.2build2
libpython3-stdlib/jammy,now 3.10.4-0ubuntu2
libpython3.10-minimal/jammy,now 3.10.4-3
libpython3.10-stdlib/jammy,now 3.10.4-3
libpython3.10/jammy,now 3.10.4-3
libqmi-glib5/jammy,now 1.30.4-1
libqmi-proxy/jammy,now 1.30.4-1
libreadline8/jammy,now 8.1.2-1
librtmp1/jammy,now 2.4+20151223.gitfa8646d.1-2build4
libsasl2-2/jammy,now 2.1.27+dfsg2-3ubuntu1
libsasl2-modules-db/jammy,now 2.1.27+dfsg2-3ubuntu1
libsasl2-modules/jammy,now 2.1.27+dfsg2-3ubuntu1
libseccomp2/jammy,now 2.5.3-2ubuntu2
libselinux1/jammy,now 3.3-1build2
libsemanage-common/jammy,now 3.3-1build2
libsemanage2/jammy,now 3.3-1build2
libsepol2/jammy,now 3.3-1build1
libsgutils2-2/jammy,now 1.46-1build1
libsigsegv2/jammy,now 2.13-1ubuntu3
libslang2/jammy,now 2.3.2-5build4
libsmartcols1/jammy,now 2.37.2-4ubuntu3
libsmbios-c2/jammy,now 2.4.3-1build1
libsodium23/jammy,now 1.0.18-1build2
libsort-naturally-perl/jammy,now 1.03-2
libsqlite3-0/jammy,now 3.37.2-2
libss2/jammy,now 1.46.5-2ubuntu1
libssh-4/jammy,now 0.9.6-2build1
libssl3/jammy,now 3.0.2-0ubuntu1
libstdc++6/jammy,now 12-20220319-1ubuntu1
libstemmer0d/jammy,now 2.2.0-1build1
libsystemd0/jammy,now 249.11-0ubuntu3
libtasn1-6/jammy,now 4.18.0-4build1
libtcl8.6/jammy,now 8.6.12+dfsg-1build1
libterm-readkey-perl/jammy,now 2.38-1build4
libtext-charwidth-perl/jammy,now 0.04-10build3
libtext-iconv-perl/jammy,now 1.7-7build3
libtext-wrapi18n-perl/jammy,now 0.06-9
libtinfo6/jammy,now 6.3-2
libtirpc-common/jammy,now 1.3.2-2build1
libtirpc3/jammy,now 1.3.2-2build1
libtss2-esys-3.0.2-0/jammy,now 3.2.0-1ubuntu1
libtss2-mu0/jammy,now 3.2.0-1ubuntu1
libtss2-sys1/jammy,now 3.2.0-1ubuntu1
libtss2-tcti-cmd0/jammy,now 3.2.0-1ubuntu1
libtss2-tcti-device0/jammy,now 3.2.0-1ubuntu1
libtss2-tcti-mssim0/jammy,now 3.2.0-1ubuntu1
libtss2-tcti-swtpm0/jammy,now 3.2.0-1ubuntu1
libuchardet0/jammy,now 0.0.7-1build2
libudev1/jammy,now 249.11-0ubuntu3
libudisks2-0/jammy,now 2.9.4-1ubuntu2
libunistring2/jammy,now 1.0-1
libunwind8/jammy,now 1.3.2-2build2
libupower-glib3/jammy,now 0.99.17-1
liburcu8/jammy,now 0.13.1-1
libusb-1.0-0/jammy,now 2:1.0.25-1ubuntu1
libusbmuxd6/jammy,now 2.0.2-3build2
libutempter0/jammy,now 1.2.1-2build2
libuuid1/jammy,now 2.37.2-4ubuntu3
libuv1/jammy,now 1.43.0-1
libvolume-key1/jammy,now 0.3.12-3.1build3
libwrap0/jammy,now 7.6.q-31build2
libx11-6/jammy,now 2:1.7.5-1
libx11-data/jammy,now 2:1.7.5-1
libxau6/jammy,now 1:1.0.9-1build5
libxcb1/jammy,now 1.14-3ubuntu3
libxdmcp6/jammy,now 1:1.1.3-0ubuntu5
libxext6/jammy,now 2:1.3.4-1build1
libxml2/jammy,now 2.9.13+dfsg-1build1
libxmlb2/jammy,now 0.3.6-2build1
libxmlsec1-openssl/jammy,now 1.2.33-1build2
libxmlsec1/jammy,now 1.2.33-1build2
libxmuu1/jammy,now 2:1.1.3-3
libxslt1.1/jammy,now 1.1.34-4build2
libxtables12/jammy,now 1.8.7-1ubuntu5
libxxhash0/jammy,now 0.8.1-1
libyaml-0-2/jammy,now 0.2.2-1build2
libzstd1/jammy,now 1.4.8+dfsg-3build1
linux-base/jammy,now 4.5ubuntu9
linux-firmware/jammy,now 20220329.git681281e4-0ubuntu1
linux-generic/jammy-updates,jammy-security,now 5.15.0.27.30
linux-headers-5.15.0-27-generic/jammy-updates,jammy-security,now 5.15.0-27.28
linux-headers-5.15.0-27/jammy-updates,jammy-security,now 5.15.0-27.28
linux-headers-generic/jammy-updates,jammy-security,now 5.15.0.27.30
linux-image-5.15.0-27-generic/jammy-updates,jammy-security,now 5.15.0-27.28
linux-image-generic/jammy-updates,jammy-security,now 5.15.0.27.30
linux-modules-5.15.0-27-generic/jammy-updates,jammy-security,now 5.15.0-27.28
linux-modules-extra-5.15.0-27-generic/jammy-updates,jammy-security,now 5.15.0-27.28
locales/jammy,now 2.35-0ubuntu3
login/jammy,now 1:4.8.1-2ubuntu2
logrotate/jammy,now 3.19.0-1ubuntu1
logsave/jammy,now 1.46.5-2ubuntu1
lsb-base/jammy,now 11.1.0ubuntu4
lsb-release/jammy,now 11.1.0ubuntu4
lshw/jammy,now 02.19.git.2021.06.19.996aaad9c7-2build1
lsof/jammy,now 4.93.2+dfsg-1.1build2
lvm2/jammy,now 2.03.11-2.1ubuntu4
lxd-agent-loader/jammy,now 0.5
man-db/jammy,now 2.10.2-1
manpages/jammy,now 5.10-1ubuntu1
mawk/jammy,now 1.3.4.20200120-3
mdadm/jammy,now 4.2-0ubuntu1
media-types/jammy,now 7.0.0
modemmanager/jammy,now 1.18.6-1
motd-news-config/jammy-updates,now 12ubuntu4.1
mount/jammy,now 2.37.2-4ubuntu3
mtr-tiny/jammy,now 0.95-1
multipath-tools/jammy,now 0.8.8-1ubuntu1
nano/jammy,now 6.2-1
ncurses-base/jammy,now 6.3-2
ncurses-bin/jammy,now 6.3-2
ncurses-term/jammy,now 6.3-2
needrestart/jammy,now 3.5-5ubuntu2
netbase/jammy,now 6.3
netcat-openbsd/jammy,now 1.218-4ubuntu1
netplan.io/jammy,now 0.104-0ubuntu2
networkd-dispatcher/jammy-updates,jammy-security,now 2.1-2ubuntu0.22.04.1
nftables/jammy,now 1.0.2-1ubuntu2
ntfs-3g/jammy,now 1:2021.8.22-3ubuntu1
open-iscsi/jammy,now 2.1.5-1ubuntu1
open-vm-tools/jammy,now 2:11.3.5-1ubuntu4
openssh-client/jammy,now 1:8.9p1-3
openssh-server/jammy,now 1:8.9p1-3
openssh-sftp-server/jammy,now 1:8.9p1-3
openssl/jammy,now 3.0.2-0ubuntu1
os-prober/jammy,now 1.79ubuntu2
overlayroot/jammy,now 0.47ubuntu1
packagekit-tools/jammy,now 1.2.5-2ubuntu2
packagekit/jammy,now 1.2.5-2ubuntu2
parted/jammy,now 3.4-2build1
passwd/jammy,now 1:4.8.1-2ubuntu2
pastebinit/jammy,now 1.5.1-1ubuntu1
patch/jammy,now 2.7.6-7build2
pci.ids/jammy,now 0.0~2022.01.22-1
pciutils/jammy,now 1:3.7.0-6
perl-base/jammy,now 5.34.0-3ubuntu1
perl-modules-5.34/jammy,now 5.34.0-3ubuntu1
perl/jammy,now 5.34.0-3ubuntu1
pinentry-curses/jammy,now 1.1.1-1build2
pkexec/jammy,now 0.105-33
plymouth-theme-ubuntu-text/jammy,now 0.9.5+git20211018-1ubuntu3
plymouth/jammy,now 0.9.5+git20211018-1ubuntu3
policykit-1/jammy,now 0.105-33
polkitd/jammy,now 0.105-33
pollinate/jammy,now 4.33-3ubuntu2
powermgmt-base/jammy,now 1.36
procps/jammy,now 2:3.3.17-6ubuntu2
psmisc/jammy,now 23.4-2build3
publicsuffix/jammy,now 20211207.1025-1
python-apt-common/jammy,now 2.3.0ubuntu2
python-babel-localedata/jammy,now 2.8.0+dfsg.1-7
python3-apport/jammy,now 2.20.11-0ubuntu82
python3-apt/jammy,now 2.3.0ubuntu2
python3-attr/jammy,now 21.2.0-1
python3-automat/jammy,now 20.2.0-1
python3-babel/jammy,now 2.8.0+dfsg.1-7
python3-bcrypt/jammy,now 3.2.0-1build1
python3-blinker/jammy,now 1.4+dfsg1-0.4
python3-certifi/jammy,now 2020.6.20-1
python3-cffi-backend/jammy,now 1.15.0-1build2
python3-chardet/jammy,now 4.0.0-1
python3-click/jammy,now 8.0.3-1
python3-colorama/jammy,now 0.4.4-1
python3-commandnotfound/jammy,now 22.04.0
python3-configobj/jammy,now 5.0.6-5
python3-constantly/jammy,now 15.1.0-2
python3-cryptography/jammy,now 3.4.8-1ubuntu2
python3-dbus/jammy,now 1.2.18-3build1
python3-debconf/jammy,now 1.5.79ubuntu1
python3-debian/jammy,now 0.1.43ubuntu1
python3-distro-info/jammy,now 1.1build1
python3-distro/jammy,now 1.7.0-1
python3-distupgrade/jammy,now 1:22.04.10
python3-distutils/jammy,now 3.10.4-0ubuntu1
python3-gdbm/jammy,now 3.10.4-0ubuntu1
python3-gi/jammy,now 3.42.0-3build1
python3-hamcrest/jammy,now 2.0.2-2
python3-httplib2/jammy,now 0.20.2-2
python3-hyperlink/jammy,now 21.0.0-3
python3-idna/jammy,now 3.3-1
python3-importlib-metadata/jammy,now 4.6.4-1
python3-incremental/jammy,now 21.3.0-1
python3-jeepney/jammy,now 0.7.1-3
python3-jinja2/jammy,now 3.0.3-1
python3-json-pointer/jammy,now 2.0-0ubuntu1
python3-jsonpatch/jammy,now 1.32-2
python3-jsonschema/jammy,now 3.2.0-0ubuntu2
python3-jwt/jammy,now 2.3.0-1
python3-keyring/jammy,now 23.5.0-1
python3-launchpadlib/jammy,now 1.10.16-1
python3-lazr.restfulclient/jammy,now 0.14.4-1
python3-lazr.uri/jammy,now 1.0.6-2
python3-lib2to3/jammy,now 3.10.4-0ubuntu1
python3-markupsafe/jammy,now 2.0.1-2build1
python3-minimal/jammy,now 3.10.4-0ubuntu2
python3-more-itertools/jammy,now 8.10.0-2
python3-netifaces/jammy,now 0.11.0-1build2
python3-newt/jammy,now 0.52.21-5ubuntu2
python3-oauthlib/jammy,now 3.2.0-1
python3-openssl/jammy,now 21.0.0-1
python3-pexpect/jammy,now 4.8.0-2ubuntu1
python3-pkg-resources/jammy,now 59.6.0-1.2
python3-problem-report/jammy,now 2.20.11-0ubuntu82
python3-ptyprocess/jammy,now 0.7.0-3
python3-pyasn1-modules/jammy,now 0.2.1-1
python3-pyasn1/jammy,now 0.4.8-1
python3-pyparsing/jammy,now 2.4.7-1
python3-pyrsistent/jammy,now 0.18.1-1build1
python3-requests/jammy,now 2.25.1+dfsg-2
python3-secretstorage/jammy,now 3.3.1-1
python3-serial/jammy,now 3.5-1
python3-service-identity/jammy,now 18.1.0-6
python3-setuptools/jammy,now 59.6.0-1.2
python3-six/jammy,now 1.16.0-3ubuntu1
python3-software-properties/jammy,now 0.99.22
python3-systemd/jammy,now 234-3ubuntu2
python3-twisted/jammy,now 22.1.0-2ubuntu2
python3-tz/jammy,now 2022.1-1
python3-update-manager/jammy,now 1:22.04.9
python3-urllib3/jammy,now 1.26.5-1~exp1
python3-wadllib/jammy,now 1.3.6-1
python3-xkit/jammy,now 0.5.0ubuntu5
python3-yaml/jammy,now 5.4.1-1ubuntu1
python3-zipp/jammy,now 1.0.0-3
python3-zope.interface/jammy,now 5.4.0-1build1
python3.10-minimal/jammy,now 3.10.4-3
python3.10/jammy,now 3.10.4-3
python3/jammy,now 3.10.4-0ubuntu2
readline-common/jammy,now 8.1.2-1
rsync/jammy,now 3.2.3-8ubuntu3
rsyslog/jammy,now 8.2112.0-2ubuntu2
run-one/jammy,now 1.17-0ubuntu1
sbsigntool/jammy,now 0.9.4-2ubuntu2
screen/jammy,now 4.9.0-1
secureboot-db/jammy,now 1.8
sed/jammy,now 4.8-1ubuntu2
sensible-utils/jammy,now 0.0.17
sg3-utils-udev/jammy,now 1.46-1build1
sg3-utils/jammy,now 1.46-1build1
shared-mime-info/jammy,now 2.1-2
snapd/jammy-updates,now 2.55.3+22.04ubuntu1
software-properties-common/jammy,now 0.99.22
sosreport/jammy,now 4.3-1ubuntu2
squashfs-tools/jammy,now 1:4.5-3build1
ssh-import-id/jammy,now 5.11-0ubuntu1
strace/jammy,now 5.16-0ubuntu3
sudo/jammy,now 1.9.9-1ubuntu2
systemd-sysv/jammy,now 249.11-0ubuntu3
systemd-timesyncd/jammy,now 249.11-0ubuntu3
systemd/jammy,now 249.11-0ubuntu3
sysvinit-utils/jammy,now 3.01-1ubuntu1
tar/jammy,now 1.34+dfsg-1build3
tcl8.6/jammy,now 8.6.12+dfsg-1build1
tcl/jammy,now 8.6.11+1build2
tcpdump/jammy,now 4.99.1-3build2
telnet/jammy,now 0.17-44build1
thermald/jammy,now 2.4.9-1
thin-provisioning-tools/jammy,now 0.9.0-2ubuntu1
time/jammy,now 1.9-0.1build2
tmux/jammy,now 3.2a-4build1
tnftp/jammy,now 20210827-4build1
tpm-udev/jammy,now 0.6
tzdata/jammy,now 2022a-0ubuntu1
ubuntu-advantage-tools/jammy-updates,now 27.8~22.04.1
ubuntu-drivers-common/jammy,now 1:0.9.6.1
ubuntu-keyring/jammy,now 2021.03.26
ubuntu-minimal/jammy,now 1.481
ubuntu-release-upgrader-core/jammy,now 1:22.04.10
ubuntu-server-minimal/jammy,now 1.481
ubuntu-server/jammy,now 1.481
ubuntu-standard/jammy,now 1.481
ucf/jammy,now 3.0043
udev/jammy,now 249.11-0ubuntu3
udisks2/jammy,now 2.9.4-1ubuntu2
ufw/jammy,now 0.36.1-4build1
unattended-upgrades/jammy,now 2.8ubuntu1
update-manager-core/jammy,now 1:22.04.9
update-notifier-common/jammy,now 3.192.54
upower/jammy,now 0.99.17-1
usb-modeswitch-data/jammy,now 20191128-4
usb-modeswitch/jammy,now 2.6.1-3ubuntu2
usb.ids/jammy,now 2022.04.02-1
usbmuxd/jammy,now 1.1.1-2build2
usbutils/jammy,now 1:014-1build1
usrmerge/jammy,now 25ubuntu2
util-linux/jammy,now 2.37.2-4ubuntu3
uuid-runtime/jammy,now 2.37.2-4ubuntu3
vim-common/jammy,now 2:8.2.3995-1ubuntu2
vim-runtime/jammy,now 2:8.2.3995-1ubuntu2
vim-tiny/jammy,now 2:8.2.3995-1ubuntu2
vim/jammy,now 2:8.2.3995-1ubuntu2
wget/jammy,now 1.21.2-2ubuntu1
whiptail/jammy,now 0.52.21-5ubuntu2
wireless-regdb/jammy,now 2021.08.28-0ubuntu1
xauth/jammy,now 1:1.1-1build2
xdg-user-dirs/jammy,now 0.17-2ubuntu4
xfsprogs/jammy,now 5.13.0-1ubuntu2
xkb-data/jammy,now 2.33-1
xxd/jammy,now 2:8.2.3995-1ubuntu2
xz-utils/jammy,now 5.2.5-2ubuntu1
zerofree/jammy,now 1.1.1-1build3
zlib1g/jammy,now 1:1.2.11.dfsg-2ubuntu9
zstd/jammy,now 1.4.8+dfsg-3build1

```

Contents of /tmp/ubuntu-2204-apps-diff.txt
```

1c1
< Linux 2204minimized 5.15.0-27-generic #28-Ubuntu SMP Thu Apr 14 04:55:28 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
---
> Linux 2204full 5.15.0-27-generic #28-Ubuntu SMP Thu Apr 14 04:55:28 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
6a7
> apt-utils/jammy,now 2.4.5
9a11
> bash-completion/jammy,now 1:2.11-5ubuntu1
10a13
> bc/jammy,now 1.07.1-3build1
11a15,17
> bind9-dnsutils/jammy,now 1:9.18.1-1ubuntu1
> bind9-host/jammy,now 1:9.18.1-1ubuntu1
> bind9-libs/jammy,now 1:9.18.1-1ubuntu1
14a21,22
> bolt/jammy,now 0.9.2-1
> bsdextrautils/jammy,now 2.37.2-4ubuntu3
17a26,27
> busybox-static/jammy,now 1:1.30.1-7ubuntu3
> byobu/jammy,now 5.133-1
20a31,33
> cloud-initramfs-copymods/jammy,now 0.47ubuntu1
> cloud-initramfs-dyn-netconf/jammy,now 0.47ubuntu1
> command-not-found/jammy,now 22.04.0
24a38
> cron/jammy,now 3.0pl1-137ubuntu3
31a46
> debconf-i18n/jammy,now 1.5.79ubuntu1
36a52
> distro-info/jammy,now 1.1build1
37a54
> dmidecode/jammy,now 3.3-3
38a56
> dosfstools/jammy,now 4.2-1build3
41a60,62
> ed/jammy,now 1.18-1
> eject/jammy,now 2.37.2-4ubuntu3
> ethtool/jammy,now 1:5.16-1
42a64
> file/jammy,now 1:5.41-3
45a68,70
> fonts-ubuntu-console/jammy,now 0.83-6ubuntu1
> friendly-recovery/jammy,now 0.2.42
> ftp/jammy,now 20210827-4build1
46a72,73
> fwupd-signed/jammy,now 1.44+1.2-3
> fwupd/jammy,now 1.7.5-3
52a80,81
> git-man/jammy-updates,jammy-security,now 1:2.34.1-1ubuntu1.2
> git/jammy-updates,jammy-security,now 1:2.34.1-1ubuntu1.2
70a100
> hdparm/jammy,now 9.60+ds-1build3
71a102,103
> htop/jammy,now 3.0.5-7build2
> info/jammy,now 6.8-4build1
72a105
> init/jammy,now 1.62
75a109
> install-info/jammy,now 6.8-4build1
77a112,115
> iptables/jammy,now 1.8.7-1ubuntu5
> iputils-ping/jammy,now 3:20211215-1
> iputils-tracepath/jammy,now 3:20211215-1
> irqbalance/jammy,now 1.8.0-1build1
86a125,126
> landscape-common/jammy,now 19.12-0ubuntu13
> less/jammy,now 590-1build1
91a132
> libarchive13/jammy,now 3.6.0-1ubuntu1
93a135
> libatasmart4/jammy,now 0.19-5build2
99a142,149
> libblockdev-crypto2/jammy,now 2.26-1
> libblockdev-fs2/jammy,now 2.26-1
> libblockdev-loop2/jammy,now 2.26-1
> libblockdev-part-err2/jammy,now 2.26-1
> libblockdev-part2/jammy,now 2.26-1
> libblockdev-swap2/jammy,now 2.26-1
> libblockdev-utils2/jammy,now 2.26-1
> libblockdev2/jammy,now 2.26-1
131a182,183
> liberror-perl/jammy,now 0.17029-1
> libestr0/jammy,now 0.1.10-2.1build3
132a185
> libevent-core-2.1-7/jammy,now 2.1.12-stable-1build3
134a188
> libfastjson4/jammy,now 0.99.9-1build2
137a192
> libflashrom1/jammy,now 1.2-5build1
138a194,195
> libfribidi0/jammy-updates,jammy-security,now 1.0.8-2ubuntu3.1
> libftdi1-2/jammy,now 1.5-5build3
139a197,199
> libfwupd2/jammy,now 1.7.5-3
> libfwupdplugin5/jammy,now 1.7.5-3
> libgcab-1.0-0/jammy,now 1.4-3build2
150a211,212
> libgpgme11/jammy,now 1.16.0-1.2ubuntu4
> libgpm2/jammy,now 1.20.7-10build1
153a216
> libgusb2/jammy,now 0.3.10-1
161a225
> libip6tc2/jammy,now 1.8.7-1ubuntu5
163a228,229
> libjansson4/jammy,now 2.13.1-1.1build3
> libjcat1/jammy,now 0.1.9-1
164a231,232
> libjson-glib-1.0-0/jammy,now 1.6.6-1build1
> libjson-glib-1.0-common/jammy,now 1.6.6-1build1
173a242
> liblmdb0/jammy,now 0.9.24-1build2
178a248,252
> libmagic-mgc/jammy,now 1:5.41-3
> libmagic1/jammy,now 1:5.41-3
> libmaxminddb0/jammy,now 1.5.2-1build2
> libmbim-glib4/jammy,now 1.26.2-1build1
> libmbim-proxy/jammy,now 1.26.2-1build1
179a254
> libmm-glib0/jammy,now 1.18.6-1
185a261
> libmspack0/jammy,now 0.10.1-2build2
187a264
> libnetfilter-conntrack3/jammy,now 1.0.9-1
189a267,270
> libnewt0.52/jammy,now 0.52.21-5ubuntu2
> libnfnetlink0/jammy,now 1.0.1-3build3
> libnftables1/jammy,now 1.0.2-1ubuntu2
> libnftnl11/jammy,now 1.2.1-1build1
190a272,273
> libnl-3-200/jammy,now 3.5.0-0.1
> libnl-genl-3-200/jammy,now 3.5.0-0.1
192a276
> libnspr4/jammy,now 2:4.32-3build1
193a278
> libnss3/jammy,now 2:3.68.2-0ubuntu1
194a280
> libnuma1/jammy,now 2.0.14-3ubuntu2
203a290,292
> libparted-fs-resize0/jammy,now 3.4-2build1
> libparted2/jammy,now 3.4-2build1
> libpcap0.8/jammy,now 1.10.1-4build1
207a297
> libpipeline1/jammy,now 1.5.5-1
219a310,312
> libpython3.10/jammy,now 3.10.4-3
> libqmi-glib5/jammy,now 1.30.4-1
> libqmi-proxy/jammy,now 1.30.4-1
231a325
> libslang2/jammy,now 2.3.2-5build4
232a327,328
> libsmbios-c2/jammy,now 2.4.3-1build1
> libsodium23/jammy,now 1.0.18-1build2
241a338
> libtcl8.6/jammy,now 8.6.12+dfsg-1build1
242a340,342
> libtext-charwidth-perl/jammy,now 0.04-10build3
> libtext-iconv-perl/jammy,now 1.7-7build3
> libtext-wrapi18n-perl/jammy,now 0.06-9
245a346,352
> libtss2-esys-3.0.2-0/jammy,now 3.2.0-1ubuntu1
> libtss2-mu0/jammy,now 3.2.0-1ubuntu1
> libtss2-sys1/jammy,now 3.2.0-1ubuntu1
> libtss2-tcti-cmd0/jammy,now 3.2.0-1ubuntu1
> libtss2-tcti-device0/jammy,now 3.2.0-1ubuntu1
> libtss2-tcti-mssim0/jammy,now 3.2.0-1ubuntu1
> libtss2-tcti-swtpm0/jammy,now 3.2.0-1ubuntu1
247a355
> libudisks2-0/jammy,now 2.9.4-1ubuntu2
253a362
> libutempter0/jammy,now 1.2.1-2build2
254a364,365
> libuv1/jammy,now 1.43.0-1
> libvolume-key1/jammy,now 0.3.12-3.1build3
263a375,376
> libxmlsec1-openssl/jammy,now 1.2.33-1build2
> libxmlsec1/jammy,now 1.2.33-1build2
264a378
> libxslt1.1/jammy,now 1.1.34-4build2
278a393
> locales/jammy,now 2.35-0ubuntu3
279a395
> logrotate/jammy,now 3.19.0-1ubuntu1
282a399,400
> lshw/jammy,now 02.19.git.2021.06.19.996aaad9c7-2build1
> lsof/jammy,now 4.93.2+dfsg-1.1build2
284c402,404
< lxd-installer/jammy,now 1
---
> lxd-agent-loader/jammy,now 0.5
> man-db/jammy,now 2.10.2-1
> manpages/jammy,now 5.10-1ubuntu1
287a408,409
> modemmanager/jammy,now 1.18.6-1
> motd-news-config/jammy-updates,now 12ubuntu4.1
288a411
> mtr-tiny/jammy,now 0.95-1
289a413
> nano/jammy,now 6.2-1
294a419
> netcat-openbsd/jammy,now 1.218-4ubuntu1
296a422
> nftables/jammy,now 1.0.2-1ubuntu2
298a425
> open-vm-tools/jammy,now 2:11.3.5-1ubuntu4
303a431
> overlayroot/jammy,now 0.47ubuntu1
305a434
> parted/jammy,now 3.4-2build1
306a436,437
> pastebinit/jammy,now 1.5.1-1ubuntu1
> patch/jammy,now 2.7.6-7build2
318a450
> powermgmt-base/jammy,now 1.36
319a452
> psmisc/jammy,now 23.4-2build3
325a459
> python3-automat/jammy,now 20.2.0-1
326a461
> python3-bcrypt/jammy,now 3.2.0-1build1
332a468
> python3-commandnotfound/jammy,now 22.04.0
333a470
> python3-constantly/jammy,now 15.1.0-2
335a473,474
> python3-debconf/jammy,now 1.5.79ubuntu1
> python3-debian/jammy,now 0.1.43ubuntu1
339a479
> python3-gdbm/jammy,now 3.10.4-0ubuntu1
340a481
> python3-hamcrest/jammy,now 2.0.2-2
341a483
> python3-hyperlink/jammy,now 21.0.0-3
343a486
> python3-incremental/jammy,now 21.3.0-1
358a502
> python3-newt/jammy,now 0.52.21-5ubuntu2
359a504,505
> python3-openssl/jammy,now 21.0.0-1
> python3-pexpect/jammy,now 4.8.0-2ubuntu1
361a508,510
> python3-ptyprocess/jammy,now 0.7.0-3
> python3-pyasn1-modules/jammy,now 0.2.1-1
> python3-pyasn1/jammy,now 0.4.8-1
366a516
> python3-service-identity/jammy,now 18.1.0-6
370a521
> python3-twisted/jammy,now 22.1.0-2ubuntu2
377a529
> python3-zope.interface/jammy,now 5.4.0-1build1
381a534,539
> rsync/jammy,now 3.2.3-8ubuntu3
> rsyslog/jammy,now 8.2112.0-2ubuntu2
> run-one/jammy,now 1.17-0ubuntu1
> sbsigntool/jammy,now 0.9.4-2ubuntu2
> screen/jammy,now 4.9.0-1
> secureboot-db/jammy,now 1.8
388a547
> sosreport/jammy,now 4.3-1ubuntu2
390a550
> strace/jammy,now 5.16-0ubuntu3
396a557,560
> tcl8.6/jammy,now 8.6.12+dfsg-1build1
> tcl/jammy,now 8.6.11+1build2
> tcpdump/jammy,now 4.99.1-3build2
> telnet/jammy,now 0.17-44build1
398a563,566
> time/jammy,now 1.9-0.1build2
> tmux/jammy,now 3.2a-4build1
> tnftp/jammy,now 20210827-4build1
> tpm-udev/jammy,now 0.6
399a568
> ubuntu-advantage-tools/jammy-updates,now 27.8~22.04.1
401a571
> ubuntu-minimal/jammy,now 1.481
403a574,575
> ubuntu-server/jammy,now 1.481
> ubuntu-standard/jammy,now 1.481
405a578,579
> udisks2/jammy,now 2.9.4-1ubuntu2
> ufw/jammy,now 0.36.1-4build1
406a581,582
> update-manager-core/jammy,now 1:22.04.9
> update-notifier-common/jammy,now 3.192.54
407a584,586
> usb-modeswitch-data/jammy,now 20191128-4
> usb-modeswitch/jammy,now 2.6.1-3ubuntu2
> usb.ids/jammy,now 2022.04.02-1
411a591,595
> uuid-runtime/jammy,now 2.37.2-4ubuntu3
> vim-common/jammy,now 2:8.2.3995-1ubuntu2
> vim-runtime/jammy,now 2:8.2.3995-1ubuntu2
> vim-tiny/jammy,now 2:8.2.3995-1ubuntu2
> vim/jammy,now 2:8.2.3995-1ubuntu2
412a597
> whiptail/jammy,now 0.52.21-5ubuntu2
419a605
> zerofree/jammy,now 1.1.1-1build3

```

LHammonds

---

### Post by smeerbartje on 2022-05-02
Thanks! Decent investigation!
Do you think that it’s ONLY about saving storage space? Or is it also about a more leaner memory usage, etc.?

---

### Post by Doug S on 2022-05-02
The storage space difference between the two is only ~400 Megabytes, 6.7G instead of 6.3G. Logs file methods are different also, as found on [this thread]("https://ubuntuforums.org/showthread.php?t=2474502&p=14093330#post14093330").

I overcame my issues from earlier and installed both, but I didn't think to do the packages compare as LHammonds is doing. On the non-minimum I have 610 packages:

```
doug@serv-jj:~$ wc -l ubuntu-2204-full-apps.txt
610 ubuntu-2204-full-apps.txt
```I only recall installing the mlocate package since installation (but it drag along 2 others, I think).

---

### Post by smeerbartje on 2022-05-02
Ok, my conclusion so far: for my homeserver, I'll avoid the minimal installation :).

---

### Post by LHammonds on 2022-05-02
> **smeerbartje said:**
> Do you think that it&#8217;s ONLY about saving storage space? Or is it also about a more leaner memory usage, etc.?
As you have noticed, there is next to nothing written on the internet about the "minimized" version.  Most information I get about it is what's noted when selecting it....which says it is for servers where humans are not expected to login...which probably means most user-based command-line tools were removed.

Well, let's take a look at some of the facts about what we know and then we can theorize on the why or how it can be utilized.

Minimized has 420 packages installed.
Normal/Full has 606 packages installed.
That is a difference of 186 less packages in the minimized version which is a 31% reduction.

Minimized takes up 4,126 MB storage when initially installed and fully patched as of today.
Normal/Full takes up 4,585 MB storage when initially installed and fully patched as of today.
That is a difference of 459 MB which is about a 11% reduction in size requirements.

Minimized uses 178,896 KB of RAM
Normal/Full uses 196,040 KB of RAM
That is a difference of 17,144 KB of RAM which is about a 9% reduction in RAM size requirements.

Minimized has 3 open ports that are actively listening for connections (2 of which are from sshd on IPv4 and IPv6)
Normal/Full has 3 open ports that are actively listening for connections (2 of which are from sshd on IPv4 and IPv6)

Other notes about what I see when I look at a Minimized installation:
 * No text editor (vi, vim, nano)
 * No ufw nor iptables command (but iptables is installed)
* No man pages (documentation)

In my still-uneducated opinion, I would think that the vast majority of everyone installing Ubuntu Server would NOT want to select the "Minimized" version.

That said, there is nothing stopping you from using the Minimized version and just tack on what you want added...such as "apt install vim-nox"

LHammonds

---

### Post by Doug S on 2022-05-02
Thanks for your informative work on this.

I get the same as you for everything except storage, but maybe I measure it incorrectly using "df -h". (well, I don't still have the minimal VM to check RAM usage). I do see a swap.img file in / at 4.0G.

I agree with your conclusion, don't install minimal.

---

### Post by LHammonds on 2022-05-02
> **Doug S said:**
> I get the same as you for everything except storage, but maybe I measure it incorrectly using "df -h".
I noticed I did not get enough detail when using **-h** so I used **--block-size=M**

---

### Post by TheFu on 2022-05-03
I did a minimal install of 22.04. Think it was 4.3G total storage.  But so many shell tools were missing to make working at the shell a chore. I really missed the bash-completion tool.  There's a meta package that can be installed to bring it up to the full Server install. I think the storage increased to 4.6G.  I suspect most of what got added back were manpages, which I can't live without, especially on a new OS where the options often change in tools I've used for 25 yrs.

I was a little disappointed that the server install setup a swap file, not a swap LV/partition, especially since I'd made an LV for swap, which was ignored. Made me wonder what were these people thinking?

**UPDATE:**
```
$ df -Th -x tmpfs
Filesystem               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg--00-lv--0 ext4  9.8G  3.1G  6.2G  34% /
/dev/vda2                ext4  739M  242M  443M  36% /boot

$ sudo lvs
  LV      VG    Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-0    vg-00 -wi-ao---- 10.00g                                                    
  lv-swap vg-00 -wi-ao----  1.00g          
```

Ran those commands today. Seems that apt-get autoremove/autoclean dropped over 1G of storage.  I manually setup the storage BEFORE letting the installer do much. I find that easier than trying to use the storage setup GUI to fix all the less-than-great default choices in the installer.

If we want a truly minimal Linux install, alpine can do that. It comes with nothing except vim. It is under 10MB (6.11MB is the size of my install).  I bet slackware can be in the 200MB or less size, but package management on it feels like it is from the mid-1990s (quite painful).  If a physical install isn't needed, lxd installs of Ubuntu are fairly small - around 600MB, but bloat out quickly to 1.5G-2G with minimal server stuff added.  I'm looking at an email gateway and a caching DNS server and regex filter for those last two sized.

---

### Post by smeerbartje on 2022-05-03
Hero! Thanks!

---

