---
title: "machine freezes on compile"
date: 2009-06-09
forum: Server Platforms
---

### Post by spikeman on 2009-06-09
Hello, i have a dedicated box hosted at iweb.com running ubuntu server 8.04 and every time i try to compile a (somewhat large) program the box freezes completely and i am left with no choice other than an APC reboot.Now, i have ordered a memtest and they reported the memory is fine.I've also left it frozen overnight in hope it would unlock but it just timed out my ssh session and the machine was still locked.

the deps i need for my program are:
```

automake autoconf zlib1g-dev libssl-dev libtool libstdc++5 libgd2-xpm libpcre3-dev
```also here's a list of all the installed packages on the system:

```

acpi                        install
acpid                        install
adduser                        install
apache2                        install
apache2-mpm-prefork                install
apache2-utils                    install
apache2.2-common                install
apparmor                    install
apparmor-utils                    install
apt                        install
apt-utils                    install
aptitude                    install
aspell                        install
aspell-en                    install
at                        install
autoconf                    install
automake                    install
autotools-dev                    install
base-files                    install
base-passwd                    install
bash                        install
bash-completion                    install
bc                        install
belocs-locales-bin                install
bind9-host                    install
binutils                    install
binutils-static                    install
bittornado                    install
bsdmainutils                    install
bsdutils                    install
build-essential                    install
busybox-initramfs                install
bzip2                        install
command-not-found                install
command-not-found-data                install
console-setup                    install
console-terminus                install
console-tools                    install
coreutils                    install
cpio                        install
cpp                        install
cpp-4.2                        install
cron                        install
dash                        install
dbconfig-common                    install
debconf                        install
debconf-i18n                    install
debianutils                    install
defoma                        install
dhcp3-client                    install
dhcp3-common                    install
dictionaries-common                install
diff                        install
dmidecode                    install
dnsutils                    install
dosfstools                    install
dpkg                        install
dpkg-dev                    install
e2fslibs                    install
e2fsprogs                    install
ed                        install
eject                        install
ethtool                        install
fdutils                        install
file                        install
findutils                    install
fontconfig-config                install
friendly-recovery                install
ftp                        install
fuse-utils                    install
g++                        install
g++-4.2                        install
gcc                        install
gcc-3.3-base                    install
gcc-4.2                        install
gcc-4.2-base                    install
gettext-base                    install
gimp-help-common                install
gimp-help-en                    install
gnupg                        install
gpgv                        install
grep                        install
groff-base                    install
grub                        install
gzip                        install
hdparm                        install
hostname                    install
iamerican                    install
ibritish                    install
ifupdown                    install
info                        install
initramfs-tools                    install
initscripts                    install
inputattach                    install
installation-report                install
iproute                        install
iptables                    install
iputils-arping                    install
iputils-ping                    install
iputils-tracepath                install
ispell                        install
klibc-utils                    install
klogd                        install
language-pack-en                install
language-pack-en-base                install
language-pack-gnome-en                install
language-pack-gnome-en-base            install
language-support-en                install
language-support-translations-en        install
language-support-writing-en            install
laptop-detect                    install
less                        install
libacl1                        install
libapache2-mod-php5                install
libapr1                        install
libaprutil1                    install
libaspell15                    install
libatm1                        install
libattr1                    install
libbind9-30                    install
libblkid1                    install
libbz2-1.0                    install
libc6                        install
libc6-dev                    install
libcap1                        install
libck-connector0                install
libcomerr2                    install
libconsole                    install
libcurl3-gnutls                    install
libcwidget3                    install
libdb4.6                    install
libdbd-mysql-perl                install
libdbi-perl                    install
libdbus-1-3                    install
libdevmapper1.02.1                install
libdns32                    install
libdns35                    install
libedit2                    install
libelfg0                    install
libexpat1                    install
libfontconfig1                    install
libfreetype6                    install
libfribidi0                    install
libfuse2                    install
libgc1c2                    install
libgcc1                        install
libgcrypt11                    install
libgd2-xpm                    install
libgdbm3                    install
libgnutls13                    install
libgomp1                    install
libgpg-error0                    install
libgpmg1                    install
libhtml-parser-perl                install
libhtml-tagset-perl                install
libhtml-tree-perl                install
libidn11                    install
libisc32                    install
libisc35                    install
libisccc30                    install
libisccfg30                    install
libiw29                        install
libjpeg62                    install
libkeyutils1                    install
libklibc                    install
libkrb53                    install
libldap-2.4-2                    install
liblocale-gettext-perl                install
liblockfile1                    install
liblwres30                    install
liblzo2-2                    install
libmagic1                    install
libmysql++2c2a                    install
libmysqlclient15-dev                install
libmysqlclient15off                install
libncurses5                    install
libncursesw5                    install
libneon27                    install
libnet-daemon-perl                install
libnewt0.52                    install
libntfs-3g23                    install
libopencdk10                    install
libpam-modules                    install
libpam-runtime                    install
libpam0g                    install
libparted1.7-1                    install
libpcap0.8                    install
libpcre3                    install
libpcre3-dev                    install
libpcrecpp0                    install
libphp-adodb                    install
libplrpc-perl                    install
libpng12-0                    install
libpopt0                    install
libpq5                        install
libreadline5                    install
librpc-xml-perl                    install
libsasl2-2                    install
libsasl2-modules                install
libselinux1                    install
libsepol1                    install
libsigc++-2.0-0c2a                install
libslang2                    install
libsqlite3-0                    install
libss2                        install
libssl-dev                    install
libssl0.9.8                    install
libstdc++5                    install
libstdc++6                    install
libstdc++6-4.2-dev                install
libsvn1                        install
libsysfs2                    install
libtasn1-3                    install
libterm-readkey-perl                install
libtext-charwidth-perl                install
libtext-iconv-perl                install
libtext-wrapi18n-perl                install
libtimedate-perl                install
libtool                        install
liburi-perl                    install
libusb-0.1-4                    install
libuuid1                    install
libvolume-id0                    install
libwrap0                    install
libwww-perl                    install
libx11-6                    install
libx11-data                    install
libxau6                        install
libxcb-xlib0                    install
libxcb1                        install
libxdmcp6                    install
libxml-parser-perl                install
libxml2                        install
libxpm4                        install
linux-generic                    install
linux-image-2.6.24-24-generic            install
linux-image-generic                install
linux-libc-dev                    install
linux-restricted-modules-2.6.24-24-generic    install
linux-restricted-modules-common            install
linux-restricted-modules-generic        install
linux-ubuntu-modules-2.6.24-24-generic        install
locales                        install
login                        install
logrotate                    install
lsb-base                    install
lsb-release                    install
lshw                        install
lsof                        install
ltrace                        install
lzma                        install
m4                        install
mailx                        install
make                        install
makedev                        install
man-db                        install
manpages                    install
mawk                        install
memtest86+                    install
mii-diag                    install
mime-support                    install
mktemp                        install
mlocate                        install
module-init-tools                install
mount                        install
mtr-tiny                    install
myspell-en-gb                    install
myspell-en-us                    install
myspell-en-za                    install
mysql-client                    install
mysql-client-5.0                install
mysql-common                    install
mysql-server                    install
mysql-server-5.0                install
nano                        install
ncurses-base                    install
ncurses-bin                    install
net-tools                    install
netbase                        install
netcat                        install
netcat-traditional                install
ntfs-3g                        install
ntpdate                        install
nvidia-kernel-common                install
openoffice.org-help-en-gb            install
openoffice.org-help-en-us            install
openoffice.org-hyphenation            install
openoffice.org-hyphenation-en-us        install
openoffice.org-l10n-common            install
openoffice.org-l10n-en-gb            install
openoffice.org-l10n-en-za            install
openoffice.org-thesaurus-en-au            install
openoffice.org-thesaurus-en-us            install
openssh-blacklist                install
openssh-client                    install
openssh-server                    install
openssl                        install
openssl-blacklist                install
parted                        install
passwd                        install
patch                        install
pciutils                    install
pcmciautils                    install
perl                        install
perl-base                    install
perl-modules                    install
php5                        install
php5-common                    install
php5-mysql                    install
popularity-contest                install
postfix                        install
ppp                        install
pppconfig                    install
pppoeconf                    install
procps                        install
proftpd                        deinstall
proftpd-common                    install
psmisc                        install
python                        install
python-apt                    install
python-central                    install
python-gdbm                    install
python-gnupginterface                install
python-minimal                    install
python-support                    install
python2.5                    install
python2.5-minimal                install
readline-common                    install
reiserfsprogs                    install
rsync                        install
screen                        install
sed                        install
smartmontools                    install
ssl-cert                    install
startup-tasks                    install
strace                        install
subversion                    install
sudo                        install
sysklogd                    install
sysstat                        install
system-services                    install
sysv-rc                        install
sysvutils                    install
tar                        install
tasksel                        install
tasksel-data                    install
tcpd                        install
tcpdump                        install
telnet                        install
thunderbird-locale-en-gb            install
time                        install
torrentflux                    install
ttf-dejavu                    install
ttf-dejavu-core                    install
ttf-dejavu-extra                install
tzdata                        install
ubuntu-keyring                    install
ubuntu-minimal                    install
ubuntu-standard                    install
ucf                        install
udev                        install
ufw                        install
unzip                        install
update-inetd                    install
update-manager-core                install
upstart                        install
upstart-compat-sysv                install
upstart-logd                    install
usbutils                    install
util-linux                    install
util-linux-locales                install
uuid-runtime                    install
vim                        install
vim-common                    install
vim-runtime                    install
vim-tiny                    install
w3m                        install
wamerican                    install
wbritish                    install
wget                        install
whiptail                    install
wireless-tools                    install
wpasupplicant                    install
x11-common                    install
xkb-data                    install
zip                        install
zlib1g                        install
zlib1g-dev                    install

```any ideeas on what to try to stop this from happening?


Paul.

---

### Post by macooper on 2009-06-09
This is a bit of a stab in the dark, as you don't have much to go on.  But the most likely thing to happen to cause these problems is that you are either running out of swap space or you are filling the /tmp partition.  I'd bet on the swap space.  
 
To get round this, assumijng you can't increase the size of your swap partition, you could add a swap file as follows :
[FONT=Courier New][SIZE=5][/SIZE][/FONT] 
```

 
dd if=/dev/zero of=/var/swapfile bs=1024 count=1048576
 
mkswap /var/swapfile
 
swapon /var/swapfile
 
vi /etc/fstab
 
/var/swapfile swap swap defaults 0 0
 

```
 
This gives you an extra gig of swap space.  You may have to adjust the file path depending on where you have space on your partions.
 
Good luck.

---

### Post by spikeman on 2009-06-10
i'll try adding swap although the box has 6 gb of ram wich i constantly monitored using top,but every ideea gets something done so i'll try this later today.

i've also cleaned all the junk packages using deborphan so i've got my fingers crossed.

btw,i can compile apache2 just fine but mine freezes so thats why i'm thinking libs here.

---

### Post by macooper on 2009-06-10
There is one other possibility that I can think of, do you have the ability to check the temperature of the box, especially the CPU when it freezes ?  A few years ago, I had a box that worked fine 24/7, but used to panic when compiling GCC (which again is a large compile).  I eventually tracked that down to the heatsink on the CPU not being properly seated, so under load, the CPU would overheat causing teh panic.
 
If this is the case, you should have details of the crash on the screen, so see if you can get a tech to watch the monitor and pass on details of anything displayed at the time of the freeze.  
 
I agree that with 6GB RAM, swap is unlikely to be the issue

---

### Post by spikeman on 2009-06-10
looks like swap had nothing to do with it.

---

### Post by spikeman on 2009-06-10
i installed lm-sensors and it looks like temp is the issue
it hops over the 85 degree alarm in seconds so im guessing its hitting the 95 degree built in fail point after some time.

i can request a cpu change:

Celeron E Dual Core - Included /month
Celeron 2.4GHz - Included /month
Pentium 4 2.4GHz - $5.00 /month
Celeron E 1.6GHz Dual Core - $10.00 /month
Pentium E Dual Core - $10.00 /month
Core2 Duo 2.0 GHz - $15.00 /month
Pentium E 2.0GHz, Dual Core - $15.00 /month
Core2 Duo 2.4GHz (800MHz FSB) - $30.00 /month
Core2 Duo 3.16GHz - $45.00 /month
Core2 Duo 3.0GHz (1333MHz FSB) - $45.00 /month
Core2 Quad 2.4GHz - $70.00 /month
Core2 Quad 2.66GHz - $80.00 /month
Core2 Quad 2.83GHz - $80.00 /month
AMD PH-8750 T-Core 2400 - $20.00 /month
AMD PH-9850 Quad-Core - $35.00 /month

right now im using Core2 Duo 2.0 GHz - $15.00 /month

LE: for information purposes this is where it freezes:
```

it8718-isa-0290
Adapter: ISA adapter
in0:         +1.30 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.84 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.34 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.99 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +3.10 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +0.02 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +0.10 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.10 V
fan1:       2947 RPM  (min =    0 RPM)
fan2:       1869 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +47.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp2:      +118.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        -1.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:          N/A  (crit = +85.0°C)                  ALARM

coretemp-isa-0001
Adapter: ISA adapter
Core 1:          N/A  (crit = +85.0°C)                  ALARM


```

---

