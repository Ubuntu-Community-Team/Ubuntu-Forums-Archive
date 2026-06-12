---
title: "Can't access a few addresses"
date: 2010-05-28
forum: Server Platforms
---

### Post by EvilTchnlgy on 2010-05-28
Hi!
I am having an issue on my server where I can't access certain ip's erratically. These addresses could previously connect to us.
I think it may be related to us getting rootkitted. I know the risks in not reinstalling but we are not able to install yet at this point. I cleaned out shv4 and shv5 from the os and setup tripwire. 

The client can't ping the server and likewise back.
From my personal computer they both respond to pings.
The server is running denyhosts but that is about it in-terms of security.
I can't find anyhting anywhere... No ipchains present, nothing in host.deny, subnet is 255.255.255.0.
I'm really at a loss so I'm looking for some direction


I know someone is going to tell me that I have to assume all my files are compromised and i should reinstall; I did md5 checks on alot of files and there is no data on here that shouldnt get out and I check for stuff running that shouldn't be daily.

The server is 10.04 server. Latest updates.
Here is a list of installed packages
```
adduser						install
anacron						install
apache2						install
apache2-mpm-prefork				install
apache2-utils					install
apache2.2-bin					install
apache2.2-common				install
apparmor					install
apparmor-utils					install
apport						install
apport-symptoms					install
apt						install
apt-transport-https				install
apt-utils					install
aptitude					install
base-files					install
base-passwd					install
bash						install
bash-completion					install
bc						install
bind9						install
bind9-doc					install
bind9-host					install
bind9utils					install
binutils					install
bison						install
bsd-mailx					install
bsdmainutils					install
bsdutils					install
btrfs-tools					install
build-essential					install
busybox-initramfs				install
busybox-static					install
byobu						install
bzip2						install
ca-certificates					install
cadaver						install
chkrootkit					install
clamav						install
clamav-base					install
clamav-daemon					install
clamav-freshclam				install
cmake						install
cmake-data					install
command-not-found				install
command-not-found-data				install
console-setup					install
console-terminus				install
consolekit					install
coreutils					install
cpio						install
cpp						install
cpp-4.4						install
cpu-checker					install
cron						install
cvs						install
dash						install
dbconfig-common					install
dbus						install
dbus-x11					install
debconf						install
debconf-i18n					install
debianutils					install
debsums						install
defoma						install
denyhosts					install
dhcp3-client					install
dhcp3-common					install
diff						install
diffutils					install
dmidecode					install
dmsetup						install
dnsutils					install
dosfstools					install
dpkg						install
dpkg-dev					install
e2fslibs					install
e2fsprogs					install
ebox						install
ed						install
eject						install
emacsen-common					install
exim4						install
exim4-base					install
exim4-config					install
exim4-daemon-light				install
fakeroot					install
file						install
findutils					install
flex						install
fontconfig					install
fontconfig-config				install
friendly-recovery				install
ftp						install
fuse-utils					install
g++						install
g++-4.4						install
gcc						install
gcc-4.4						install
gcc-4.4-base					install
gconf2						install
gconf2-common					install
geoip-database					install
gettext						install
gettext-base					install
gnupg						install
gnupg-curl					install
gpgv						install
grep						install
groff-base					install
grub-common					install
grub-pc						install
gzip						install
hddtemp						install
hdparm						install
hicolor-icon-theme				install
hostname					install
ifupdown					install
info						install
initramfs-tools					install
initramfs-tools-bin				install
initscripts					install
insserv						install
install-info					install
installation-report				install
iproute						install
iptables					install
iputils-arping					install
iputils-ping					install
iputils-tracepath				install
irqbalance					install
iso-codes					install
javascript-common				install
john						install
john-data					install
kbd						install
klibc-utils					install
language-pack-cs				install
language-pack-cs-base				install
language-pack-de				install
language-pack-de-base				install
language-pack-en				install
language-pack-en-base				install
language-pack-fi				install
language-pack-fi-base				install
language-pack-fr				install
language-pack-fr-base				install
language-pack-it				install
language-pack-it-base				install
language-pack-lt				install
language-pack-lt-base				install
language-pack-lv				install
language-pack-lv-base				install
language-pack-nl				install
language-pack-nl-base				install
language-pack-pl				install
language-pack-pl-base				install
language-pack-pt				install
language-pack-pt-base				install
language-selector-common			install
less						install
libacl1						install
libapache-singleton-perl			install
libapache2-mod-perl2				install
libapache2-mod-php5				install
libapache2-reload-perl				install
libapparmor-perl				install
libapparmor1					install
libapr1						install
libaprutil1					install
libaprutil1-dbd-sqlite3				install
libaprutil1-ldap				install
libatk1.0-0					install
libatk1.0-data					install
libatm1						install
libattr1					install
libauthen-sasl-perl				install
libavahi-client3				install
libavahi-common-data				install
libavahi-common3				install
libbind9-60					install
libblkid1					install
libboost-date-time1.40.0			deinstall
libboost-filesystem1.40.0			deinstall
libboost-regex1.40.0				deinstall
libboost-serialization1.40.0			deinstall
libboost-system1.40.0				deinstall
libboost-thread1.40.0				deinstall
libbsd-resource-perl				install
libbsd0						install
libbz2-1.0					install
libbz2-dev					install
libc-bin					install
libc-dev-bin					install
libc6						install
libc6-dev					install
libc6-i686					install
libcache-cache-perl				install
libcairo2					install
libcap-ng0					install
libcap2						install
libchart-perl					install
libck-connector0				install
libclamav6					install
libclass-accessor-perl				install
libclass-container-perl				install
libclass-data-inheritable-perl			install
libclass-singleton-perl				install
libclone-perl					install
libcomerr2					install
libcommon-sense-perl				install
libconvert-binhex-perl				install
libcroco3					install
libcrypt-ssleay-perl				install
libcups2					install
libcurl3					install
libcurl3-gnutls					install
libcwidget3					install
libdatetime-format-mail-perl			install
libdatetime-format-w3cdtf-perl			install
libdatetime-locale-perl				install
libdatetime-perl				install
libdatetime-timezone-perl			install
libdatrie1					install
libdb4.8					install
libdbd-mysql-perl				install
libdbd-pg-perl					install
libdbi-perl					install
libdbus-1-3					install
libdbus-glib-1-2				install
libdevel-stacktrace-perl			install
libdevel-symdump-perl				install
libdevmapper-event1.02.1			install
libdevmapper1.02.1				install
libdigest-sha1-perl				install
libdirectfb-1.2-0				install
libdns64					install
libdrm-intel1					install
libdrm-nouveau1					install
libdrm-radeon1					install
libdrm2						install
libebox						install
libedit2					install
libeggdbus-1-0					install
libelf1						install
libept0						install
liberror-perl					install
libevent-1.4-2					install
libexception-class-perl				install
libexpat1					install
libfcgi-perl					install
libffi5						install
libfile-copy-recursive-perl			install
libfile-mmagic-perl				install
libfile-slurp-perl				install
libfile-tail-perl				install
libfilesys-df-perl				install
libfont-afm-perl				install
libfontconfig1					install
libfontenc1					install
libfreetype6					install
libfribidi0					install
libfuse2					install
libgc1c2					install
libgcc1						install
libgconf2-4					install
libgcrypt11					install
libgd-gd2-perl					install
libgd2-xpm					install
libgdbm3					install
libgeoip1					install
libglib-perl					install
libglib2.0-0					install
libgmp3-dev					install
libgmp3c2					install
libgmpxx4ldbl					install
libgnome2-gconf-perl				install
libgnutls26					install
libgomp1					install
libgpg-error0					install
libgpm2						install
libgssapi-krb5-2				install
libgtk2.0-0					install
libgtk2.0-bin					install
libgtk2.0-common				install
libhtml-format-perl				install
libhtml-mason-perl				install
libhtml-parser-perl				install
libhtml-tagset-perl				install
libhtml-template-perl				install
libhtml-tree-perl				install
libicu42					deinstall
libidl0						install
libidn11					install
libintl-perl					install
libio-socket-ssl-perl				install
libio-string-perl				install
libio-stringy-perl				install
libipc-sharelite-perl				install
libisc60					install
libisccc60					install
libisccfg60					install
libjasper1					install
libjpeg62					install
libjs-jquery					install
libjs-mootools					install
libjs-prototype					install
libjs-scriptaculous				install
libjson-perl					install
libjson-xs-perl					install
libk5crypto3					install
libkeyutils1					install
libklibc					install
libkrb5-3					install
libkrb5support0					install
libldap-2.4-2					install
liblist-moreutils-perl				install
liblocale-gettext-perl				install
liblockfile1					install
liblog-dispatch-perl				install
liblog-log4perl-perl				install
libltdl7					install
liblwres60					install
liblzma1					install
libmagic1					install
libmail-rfc822-address-perl			install
libmailtools-perl				install
libmcrypt4					install
libmime-tools-perl				install
libmpfr1ldbl					install
libmysql++-dev					install
libmysql++3					install
libmysqlclient-dev				install
libmysqlclient16				install
libncurses5					install
libncursesw5					install
libneon27-gnutls				install
libnet-daemon-perl				install
libnet-ip-perl					install
libnet-jabber-perl				install
libnet-libidn-perl				install
libnet-ssleay-perl				install
libnet-xmpp-perl				install
libnewt0.52					install
libnih-dbus1					install
libnih1						install
libnl1						install
libntfs-3g75					install
liborbit2					install
libossp-uuid-perl				install
libossp-uuid16					install
libpam-ck-connector				install
libpam-modules					install
libpam-runtime					install
libpam0g					install
libpango1.0-0					install
libpango1.0-common				install
libparams-validate-perl				install
libparse-debianchangelog-perl			install
libparted0					install
libparted0debian1				install
libpcap0.8					install
libpci3						install
libpcre3					install
libpcsclite1					install
libperl5.10					install
libperl6-junction-perl				install
libpixman-1-0					install
libplrpc-perl					install
libplymouth2					install
libpng12-0					install
libpolkit-gobject-1-0				install
libpopt0					install
libpq5						install
libproc-process-perl				install
libproc-processtable-perl			install
libpython2.6					install
libreadline6					install
libreadonly-perl				install
libreadonly-xs-perl				install
librpc-xml-perl					install
libsasl2-2					install
libsasl2-modules				install
libselinux1					install
libsepol1					install
libsigc++-2.0-0c2a				install
libslang2					install
libsoap-lite-perl				install
libsqlite3-0					install
libss2						install
libssl0.9.8					install
libstdc++6					install
libstdc++6-4.4-dev				install
libstring-shellquote-perl			install
libsub-name-perl				install
libsvn1						install
libsys-cpu-perl					install
libsys-cpuload-perl				install
libsysfs2					install
libt1-5						install
libtask-weaken-perl				install
libtasn1-3					install
libterm-readkey-perl				install
libtext-charwidth-perl				install
libtext-iconv-perl				install
libtext-wrapi18n-perl				install
libthai-data					install
libthai0					install
libtiff4					install
libtimedate-perl				install
libtommath0					install
libts-0.0-0					install
libudev0					install
liburi-perl					install
libusb-0.1-4					install
libuuid1					install
libwrap0					install
libwww-perl					install
libx11-6					install
libx11-data					install
libxapian15					install
libxau6						install
libxcb-render-util0				install
libxcb-render0					install
libxcb1						install
libxcomposite1					install
libxcursor1					install
libxdamage1					install
libxdmcp6					install
libxext6					install
libxfixes3					install
libxfont1					install
libxft2						install
libxi6						install
libxinerama1					install
libxml-libxml-perl				install
libxml-namespacesupport-perl			install
libxml-parser-perl				install
libxml-rss-perl					install
libxml-sax-expat-perl				install
libxml-sax-perl					install
libxml-stream-perl				install
libxml2						install
libxpm4						install
libxrandr2					install
libxrender1					install
libyaml-tiny-perl				install
linux-firmware					install
linux-image-2.6.32-22-generic			install
linux-image-generic				install
linux-libc-dev					install
locales						install
lockfile-progs					install
login						install
logrotate					install
lsb-base					install
lsb-release					install
lshw						install
lsof						install
ltrace						install
lvm2						install
lynx						install
lynx-cur					install
lzma						install
m4						install
make						install
makedev						install
man-db						install
manpages					install
manpages-de					install
manpages-dev					install
manpages-es					install
manpages-fr					install
manpages-it					install
manpages-pl					install
manpages-pt					install
mawk						install
mdadm						install
mercurial					install
mercurial-common				install
mime-support					install
mlocate						install
module-init-tools				install
mount						install
mountall					install
mtr-tiny					install
mysql-client					install
mysql-client-5.1				install
mysql-client-core-5.1				install
mysql-common					install
mysql-server					install
mysql-server-5.1				install
mysql-server-core-5.1				install
nano						install
ncurses-base					install
ncurses-bin					install
net-tools					install
netbase						install
netcat-openbsd					install
ntfs-3g						install
ntpdate						install
openssh-blacklist				install
openssh-blacklist-extra				install
openssh-client					install
openssh-server					install
openssl						install
parted						install
passwd						install
patch						install
pciutils					install
perl						install
perl-base					install
perl-modules					install
php-pear					install
php5						install
php5-cgi					install
php5-cli					install
php5-common					install
php5-curl					install
php5-gd						install
php5-mcrypt					install
php5-mysql					install
phpmyadmin					install
plymouth					install
plymouth-theme-ubuntu-text			install
popularity-contest				install
postgresql					install
postgresql-8.4					install
postgresql-client-8.4				install
postgresql-client-common			install
postgresql-common				install
procps						install
psmisc						install
python						install
python-apport					install
python-apt					install
python-central					install
python-dbus					install
python-dev					install
python-gdbm					install
python-gnupginterface				install
python-gobject					install
python-httplib2					install
python-launchpadlib				install
python-lazr.restfulclient			install
python-lazr.uri					install
python-minimal					install
python-newt					install
python-oauth					install
python-openssl					install
python-pam					install
python-pexpect					install
python-pkg-resources				install
python-problem-report				install
python-pycurl					install
python-serial					install
python-simplejson				install
python-smartpm					install
python-support					install
python-twisted-bin				install
python-twisted-core				install
python-wadllib					install
python-zope.interface				install
python2.6					install
python2.6-dev					install
python2.6-minimal				install
readline-common					install
reiserfsprogs					install
rkhunter					install
rsync						install
rsyslog						install
screen						install
sed						install
sensible-utils					install
sgml-base					install
shared-mime-info				install
smartmontools					install
ssl-cert					install
strace						install
subversion					install
sudo						install
sysv-rc						install
sysvinit-utils					install
tar						install
tasksel						install
tasksel-data					install
tcpdump						install
telnet						install
tiger						install
time						install
traceroute					install
transmission-cli				install
transmission-common				install
transmission-daemon				install
tripwire					install
tsconf						install
ttf-dejavu-core					install
tzdata						install
ubuntu-keyring					install
ubuntu-minimal					install
ubuntu-serverguide				install
ucf						install
udev						install
ufw						install
unhide						install
unzip						install
update-inetd					install
update-manager-core				install
update-notifier-common				install
upstart						install
ureadahead					install
usbutils					install
util-linux					install
uuid-runtime					install
vim						install
vim-common					install
vim-runtime					install
vim-tiny					install
w3m						install
watershed					install
wget						install
whiptail					install
wireless-crda					install
wwwconfig-common				install
x-ttcidfont-conf				install
x11-common					install
xfonts-encodings				install
xfonts-utils					install
xkb-data					install
xml-core					install
xz-utils					install
zlib1g						install
zlib1g-dev					install

```

Here is a traceroute from a web service to the client:
```
216.106.99.53 is from Canada(CA) in region North America

TraceRoute to 216.106.99.53 [ppp-216-106-99-53.storm.ca]
Hop	(ms)	(ms)	(ms)		IP Address	Host name
1	23	23	21		72.249.128.105	 -
2	22	14	6		206.123.64.82	 -
3	22	15	25		64.129.174.181	64-129-174-181.static.twtelecom.net
4	52	32	29		66.192.243.138	peer-02-ge-7-1-0.chcg.twtelecom.net
5	38	69	46		64.230.186.121	core3-toronto21_pos0-2-0-0.net.bell.ca
6	63	53	46		64.230.186.121	core3-toronto21_pos0-2-0-0.net.bell.ca
7	45	42	47		64.230.48.20	core1-ottawatc_pos3-0-0.net.bell.ca
8	47	47	45		206.108.99.130	dis10-ottawa23_pos2-0.net.bell.ca
9	58	50	56		206.108.99.130	dis10-ottawa23_pos2-0.net.bell.ca
10	46	54	46		67.69.228.82	 -
11	85	53	48		209.87.239.169	wireless-f1-0.storm.ca
12	99	76	54		216.106.99.53	ppp-216-106-99-53.storm.ca

```

And here is a traceroute on my server to the client:
```
traceroute 216.106.99.53
traceroute to 216.106.99.53 (216.106.99.53), 30 hops max, 60 byte packets
 1  p19-26-m1.routers.ovh.net (213.251.173.253)  0.623 ms  0.696 ms  0.808 ms
 2  p19-7-6k.routers.ovh.net (213.186.32.1)  4.570 ms * *
 3  * * 80g.th1-1-6k.routers.chtix.eu (213.186.32.134)  7.951 ms
 4  30g.teleglobe.th1-1-6k.routers.chtix.eu (213.186.32.246)  0.576 ms  0.653 ms  0.702 ms
 5  if-3-0-0.core1.PV1-Paris.as6453.net (195.219.224.38)  0.590 ms  0.602 ms  0.618 ms
 6  if-13-0-0-1869.mcore4.MTT-Montreal.as6453.net (216.6.115.33)  91.449 ms  91.225 ms  91.806 ms
 7  ix-6-0-0.mcore4.MTT-Montreal.as6453.net (216.6.115.30)  92.201 ms  91.746 ms  92.174 ms
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```

The server is running a game server, we have ALOT of clients who connect. Previously we had no issues but now we always have people coming to us telling us they can't connect. Connections cant be made between these clients and the server by ping, http, ssh, or via the game being hosted.
Most clients have no issue connecting though.

Would love some help as I've been tearing my hair out over this one!
Thanks!

---

### Post by EvilTchnlgy on 2010-05-28
Also, ufw is installed but spits out
```
ufw status
Status: inactive

```
This is my excuse for an early bump ^^

---

### Post by Vegan on 2010-05-28
ufw is the firewall, all it means is that its not blocking anything. Its that way by default for a server.

If you cannot resolve tracert, that is due to firwalls and no ping support etc.

---

### Post by EvilTchnlgy on 2010-05-28
Hehe I was trying to show that it wasn't enabled for anyone who saw it in the package list and suspected it might be a culprit. It's not just my inability to ping the client. No sort of connection can be made at all between the 2 boxs.

---

### Post by EvilTchnlgy on 2010-05-31
Bump! Anyone else?

---

