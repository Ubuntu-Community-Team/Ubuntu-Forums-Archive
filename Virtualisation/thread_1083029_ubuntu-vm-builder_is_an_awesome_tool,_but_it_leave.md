---
title: "ubuntu-vm-builder is an awesome tool, but it leaves out so many packages"
date: 2009-02-28
forum: Virtualisation
---

### Post by samosamo on 2009-02-28
I think it's a great tool but I have one gripe.  Default settings builds an image that is very, very bare.  It doesn't include any basic tools that make a modern linux distro like ubuntu so great.  Simple things like nano, logrotate, rsync, bash-completion, nothing!  It can't even boot up on it's own because the image will not be built with a kernel unless you specify "restricted" repo.  the --components defaults to main.  Even the ISO installer's sources.list has the restricted repo in there.  What gives?

Here is a list of packages that are installed by default with ubuntu-server 8.04.2, but are NOT included when making a vm using this command:

```
$ sudo ubuntu-vm-builder vmserver hardy --arch 'amd64' --kernel-flavour 'server' --mirror 'http://archive.ubuntu.com/ubuntu'  --components 'main,universe,restricted' 
```

```
$ comm -3 default_install_pkgs.txt ubuntu-vm-server_pkgs.txt 
apparmor
apparmor-utils
at	
bash-completion
bind9-host
bsdmainutils
command-not-found
command-not-found-data
cpp	
cpp-4.2	
cron	
dnsutils
dosfstools
ed	
fdutils	
file	
friendly-recovery
ftp	
fuse-utils
groff-base
hdparm	
info	
inputattach
installation-report
iptables
iputils-arping
iputils-tracepath
libbind9-30
libdns35
libedit2
libelfg0
libexpat1
libfuse2
libgc1c2
libgdbm3
libgpmg1
libhtml-parser-perl
libhtml-tagset-perl
libhtml-tree-perl
libisc35
libisccc30
libisccfg30
liblwres30
libmagic1
libntfs-3g23
libparted1.7-1
libpcap0.8
librpc-xml-perl
libterm-readkey-perl
liburi-perl
libwww-perl
libxml-parser-perl
linux-image-2.6.24-16-server
linux-image-2.6.24-23-server
linux-ubuntu-modules-2.6.24-16-server
linux-ubuntu-modules-2.6.24-23-server
logrotate
lshw	
lsof	
ltrace	
man-db	
manpages
memtest86+
mlocate	
mtr-tiny
nano	
ntfs-3g	
openssh-client
parted	
perl-base
perl	
perl-base
perl-modules
popularity-contest
ppp	
pppconfig
pppoeconf
psmisc	
python-apt
python-central
python-gdbm
python-gnupginterface
python2.5
python2.5-minimal
python-support
python2.5
python2.5-minimal
reiserfsprogs
rsync	
strace	
tcpdump	
telnet	
time	
ubuntu-standard
ufw	
update-manager-core
w3m	
wget	
```

edit:

Here is the list formatted for the --pkg-add parameter, or apt-get install
```
apparmor apparmor-utils at bash-completion bind9-host bsdmainutils command-not-found command-not-found-data cpp cpp-4.2 cron dnsutils dosfstools ed fdutils file friendly-recovery ftp fuse-utils groff-base hdparm info inputattach installation-report iptables iputils-arping iputils-tracepath libbind9-30 libdns35 libedit2 libelfg0 libexpat1 libfuse2 libgc1c2 libgdbm3 libgpmg1 libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libisc35 libisccc30 libisccfg30 liblwres30 libmagic1 libntfs-3g23 libparted1.7-1 libpcap0.8 librpc-xml-perl libterm-readkey-perl liburi-perl libwww-perl libxml-parser-perl linux-image-2.6.24-16-server linux-image-2.6.24-23-server linux-ubuntu-modules-2.6.24-16-server linux-ubuntu-modules-2.6.24-23-server logrotate lshw lsof ltrace man-db manpages memtest86+ mlocate mtr-tiny nano ntfs-3g openssh-client parted perl-base perl perl-base perl-modules popularity-contest ppp pppconfig pppoeconf psmisc python-apt python-central python-gdbm python-gnupginterface python2.5 python2.5-minimal python-support python2.5 python2.5-minimal reiserfsprogs rsync strace tcpdump telnet time ubuntu-standard ufw update-manager-core w3m wget
```

---

### Post by dendrobates on 2009-03-03
That is as designed.  By default the images should be as small as possible.

if you pass the --addpkg ubuntu-server^ and leave out the --components it should give you a full ubuntu server install.

```
sudo ubuntu-vm-builder vmserver hardy --arch 'amd64' --kernel-flavour 'server'  --addpkg ubuntu-server^
```

You can install any tasksel task by appending a ^ to the name of the task in the --addpkg switch. 

There was a bug in hardy that caused the kernel not to be installed, but that was fixed quite a while ago.  Make sure you are using the latest version.

Rick

---

### Post by samosamo on 2009-03-08
Thanks for clearing that up!

---

### Post by samosamo on 2009-03-10
Damn, your idea didn't work

```
$ sudo apt-get install ubuntu-server^
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
E: Couldn't find task ubuntu-server

```

This is not an actual task.

---

### Post by samosamo on 2009-03-30
Well, it took me a while, but I finally figured out what the hell I'm supposed to do to get a full copy of ubuntu-server to build from this util.

install this meta package and you're done: ubuntu-standard

*sigh*

---

