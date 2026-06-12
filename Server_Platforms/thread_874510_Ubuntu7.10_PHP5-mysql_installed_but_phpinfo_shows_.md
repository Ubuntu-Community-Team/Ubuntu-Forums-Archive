---
title: "Ubuntu7.10 PHP5-mysql installed but phpinfo shows no mysql?!"
date: 2008-07-30
forum: Server Platforms
---

### Post by dogbowl on 2008-07-30
Have LAMP server thats executing PHP5 fine, but now I'm trying to do some mysql work. 

PHP5-mysql is installed (along with PHP5 and mysql 5) and I have added "extension=mysql.so" and extension_dir= "/usr/lib/php5/20060613+lfs" to my php.ini, but when I call any mysql function, I get:

> Call to undefined function mysql_connect() in /var/www/vinelodge/tool/assets/includes/include.php

One thing to note is that phpinfo() does not show any references to mysql 
[http://www.vinelodge.com/test.php ]("http://www.vinelodge.com/test.php")


Anyone have any tips? What am I missing ??

---

### Post by dogbowl on 2008-07-30
Here's an outpout of my dpkg.  Am I missing something?

```
> dpkg --get-selections
adduser						install
apache2						install
apache2-mpm-prefork				install
apache2-utils					install
apache2.2-common				install
apachetop					install
apt						install
apt-utils					install
aptitude					install
awstats						install
base-files					install
base-passwd					install
bash						install
belocs-locales-bin				install
bind9						install
bind9-host					install
bsdmainutils					install
bsdutils					install
busybox-initramfs				install
bzip2						install
console-common					install
console-data					install
console-tools					install
coreutils					install
cpio						install
cramfsprogs					install
cron						install
dash						install
debconf						install
debconf-i18n					install
debianutils					install
dhcp3-client					install
dhcp3-common					install
diff						install
dmsetup						install
dnsutils					install
dovecot-common					install
dovecot-imapd					install
dpkg						install
dselect						install
e2fslibs					install
e2fsprogs					install
ed						install
file						install
findutils					install
ftp						install
gamin						install
gcc-4.1-base					install
gcc-4.2-base					install
gettext-base					install
gnupg						install
gpgv						install
grep						install
grepmap						install
groff-base					install
gzip						install
hostname					install
ifupdown					install
initramfs-tools					install
initscripts					install
iproute						install
iptables					install
iputils-arping					install
iputils-ping					install
iputils-tracepath				install
klibc-utils					install
klogd						install
less						install
libacl1						install
libadns1					install
libapache2-mod-php5				install
libapr1						install
libaprutil1					install
libarchive-tar-perl				install
libatm1						install
libattr1					install
libbind9-0					deinstall
libbind9-30					install
libblkid1					install
libbz2-1.0					install
libc6						install
libc6-dev					install
libc6-i686					install
libcap1						install
libcomerr2					install
libcompress-raw-zlib-perl			install
libcompress-zlib-perl				install
libconsole					install
libcupsys2					deinstall
libcurl3-gnutls					install
libdb1-compat					install
libdb3						install
libdb4.2					install
libdb4.3					install
libdb4.4					install
libdb4.5					install
libdbd-mysql-perl				install
libdbi-perl					install
libdevmapper1.00				install
libdevmapper1.01				install
libdevmapper1.02				deinstall
libdevmapper1.02.1				install
libdigest-hmac-perl				install
libdigest-sha1-perl				install
libdns16					install
libdns20					install
libdns21					install
libdns22					deinstall
libdns32					install
libedit2					install
libelfg0					install
liberror-perl					install
libevms-2.5					deinstall
libexpat1					install
libfreetype6					install
libfribidi0					install
libgamin0					install
libgc1c2					install
libgcc1						install
libgcrypt11					install
libgcrypt7					install
libgd2-noxpm					install
libgdbm3					install
libgeoip1					install
libglib2.0-0					install
libgnutls10					install
libgnutls11					install
libgnutls12					install
libgnutls13					install
libgpg-error0					install
libgpmg1					install
libhtml-parser-perl				install
libhtml-tagset-perl				install
libhtml-tree-perl				install
libidn11					install
libio-compress-base-perl			install
libio-compress-zlib-perl			install
libio-zlib-perl					install
libisc11					install
libisc32					install
libisc7						install
libisc9						install
libisccc0					deinstall
libisccc30					install
libisccfg1					deinstall
libisccfg30					install
libiw27						install
libiw28						deinstall
libjpeg62					install
libkeyutils1					install
libklibc					install
libkrb53					install
libldap2					install
liblocale-gettext-perl				install
liblockfile1					install
liblwres1					install
liblwres30					install
liblwres9					deinstall
liblzo1						install
liblzo2-2					install
libmagic1					install
libmail-spf-perl				install
libmysqlclient15-dev				install
libmysqlclient15off				install
libncurses5					install
libncursesw5					install
libnet-daemon-perl				install
libnet-dns-perl					install
libnet-ip-perl					install
libnetaddr-ip-perl				install
libnewt0.52					install
libopencdk8					install
libpam-foreground				install
libpam-modules					install
libpam-runtime					install
libpam0g					install
libpcap0.7					install
libpcap0.8					install
libpci2						install
libpcre3					install
libplrpc-perl					install
libpng12-0					install
libpopt0					install
libpq5						install
libreadline5					install
libreiserfs0.3-0				install
libsasl2-2					install
libsasl2-modules				install
libselinux1					install
libsepol1					install
libsigc++-1.2-5c2				install
libsigc++-2.0-0c2a				install
libslang2					install
libsocket6-perl					install
libsqlite3-0					install
libss2						install
libssl0.9.7					install
libssl0.9.8					install
libstdc++6					install
libsys-hostname-long-perl			install
libtasn1-2					install
libtasn1-3					install
libtext-charwidth-perl				install
libtext-iconv-perl				install
libtext-wrapi18n-perl				install
liburi-perl					install
libusb-0.1-4					install
libuuid1					install
libversion-perl					install
libvolume-id0					install
libwrap0					install
libwww-perl					install
libxml2						install
linux-libc-dev					install
locales						install
login						install
logrotate					install
lsb-base					install
lsb-release					install
lsof						install
ltrace						install
make						install
makedev						install
man-db						install
manpages					install
mawk						install
mime-support					install
mktemp						install
module-init-tools				install
mount						install
mtr-tiny					install
mysql-client					install
mysql-client-5.0				install
mysql-common					install
mysql-server					install
mysql-server-5.0				install
nano						install
ncurses-base					install
ncurses-bin					install
net-tools					install
netbase						install
netkit-inetd					deinstall
openssh-blacklist				install
openssh-client					install
openssh-server					install
openssl						install
openssl-blacklist				install
passwd						install
patch						install
perl						install
perl-base					install
perl-modules					install
php5						install
php5-cli					deinstall
php5-common					install
php5-mysql					install
postfix						install
procps						install
proftpd						install
psmisc						install
python						install
python-apt					install
python-central					install
python-gnupginterface				install
python-minimal					install
python-support					install
python2.4-minimal				install
python2.5					install
python2.5-minimal				install
readline-common					install
rmail						deinstall
rsync						install
samba						deinstall
samba-common					deinstall
sasl2-bin					install
sed						install
sendmail-base					deinstall
sendmail-bin					deinstall
sendmail-cf					deinstall
sensible-mda					deinstall
slang1a-utf8					install
spamassassin					install
ssh						install
ssl-cert					install
startup-tasks					install
strace						install
sudo						install
sysklogd					install
system-services					install
sysv-rc						install
sysvutils					install
tar						install
tcpd						install
tcpdump						install
time						install
tzdata						install
ucf						install
udev						install
unzip						install
update-inetd					install
update-manager-core				install
upstart						install
upstart-compat-sysv				install
upstart-logd					install
util-linux					install
vim						install
vim-common					install
vim-runtime					install
volumeid					install
webalizer					install
wget						install
whiptail					install
zlib1g						install
zlib1g-dev					install


```

---

### Post by dogbowl on 2008-07-30
I've got this working out now.

For some reason PHP wasn't loading the .so extension files.  The old phpinfo() showed:
```
additional .ini files parsed 	/etc/php5/apache2/conf.d/pdo.ini 

```

whereas my new (and corrected) phpinfo() now shows:
```

additional .ini files parsed 	/etc/php5/apache2/conf.d/curl.ini, /etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini 

```

I think it may have had something to do with an uninstalled php-cli package still hanging around, or some other odd dependancy.

---

### Post by dan_hill on 2009-05-22
I was having a similar problem on Ubuntu Server 9.04. phpinfo() showed only the pdo.ini in "additional .ini files parsed", although other .ini files are present in /etc/php5/conf.d/ directory as well as the directory is listed is "Scan this dir for additional .ini files". 

"invoke-rc.d lighttpd restart" didn't help, but somehow a full "reboot" did.

---

