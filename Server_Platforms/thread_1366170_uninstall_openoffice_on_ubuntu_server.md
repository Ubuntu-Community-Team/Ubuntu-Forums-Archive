---
title: "uninstall openoffice on ubuntu server"
date: 2009-12-28
forum: Server Platforms
---

### Post by mansonthomas on 2009-12-28
Hi,

  I've recently install a new server with Ubuntu 9.04 and then upgrade it to 9.10 (I've no other way to do that, provider constraints)

  During the upgrade process, I've notice some strange and unwanted package : open office, X, Java.

  Digging with aptitude, I find out that some files of open office are needed by "language-support-writing-en".

  Is there any way to get rid of openoffice (and dependencies) without breaking everything ?

  What's the use of openoffice.org-hyphenation-en-us in the base system ? Do I really need that ? 

Thanks for any help,
Thomas.

---

### Post by mansonthomas on 2009-12-29
up

---

### Post by CharlesA on 2009-12-29
So you do not need open-office, X, or Java?

Is the server running a Gnome GUI?

If it is you can remote it by running:

```
sudo apt-get remove ubuntu-desktop
```

That should remove everything if you don't want a GUI.

---

### Post by mansonthomas on 2009-12-29
That's what is strange.

It's a server install, installed from scratch (but it may have been tweak by the ISP).

So, no, I don't need any X feature or java or open office.

but

"language-support-writing-en" needs openoffice.org-hyphenation-en-us

language-support-writing-en, seems to be a base file, and I wonder if I can remove it without breaking something so openoffice and depedencies are not necessary anymore.

Thomas.

---

### Post by mansonthomas on 2009-12-29
I try just to see what would happen (as I supposed, it was not installed)

[PHP]root@ns1:/# aptitude remove ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
[/PHP]

---

### Post by CharlesA on 2009-12-29
Strange.

You can list all the installed packages with dpkg --get-selections | more

Maybe remove them with aptitude if you don't have a GUI.

---

### Post by Lori700698 on 2009-12-30
> **mansonthomas said:**
> 

  Is there any way to get rid of openoffice (and dependencies) without breaking everything ?


I just checked, and I don't have any of those packages in/on my server.(I'm using 8.10) Something with the upgrade probably added those packages.  One awesome thing about Ubuntu is that it will only keep what it needs when you remove unwanted packages, no need to think about it, but please look anyway before you hit y.  If Ubuntu really needs "language-support-writing-en" it will keep it and not offer to remove it.

sudo apt-get purge openoffice

using purge will look and remove unused dependencies associated with openoffice along with the program.

and if your still paranoid you have scattered junk

sudo apt-get autoremove

This will get you a list of unassociated dependencies that can be removed. (It will not remove unused programs, only loose ends)

Lori

---

### Post by mansonthomas on 2009-12-30
Hi,

 I've started with : 

language-support-translations-en                
language-support-writing-en                     


then all openoffice package (quite manually...)

when I did aptitude purge openoffice.org-common, it proposes to remove all package that depends on  this one, but not other package where propose for removal (like openjdk-6-jre).

here is my current package list: 

openoffice still appears as "deinstall", is it normal ?  

[PHP]adduser						install
apg						install
apport						install
apport-symptoms					install
apt						install
apt-listchanges					install
apt-utils					install
apticron					install
aptitude					install
base-files					install
base-passwd					install
bash						install
bind9						install
bind9utils					install
bsd-mailx					install
bsdmainutils					install
bsdutils					install
busybox-initramfs				install
byobu						install
bzip2						install
ca-certificates					install
ca-certificates-java				install
console-setup					install
console-terminus				install
consolekit					install
coreutils					install
cpio						install
cpp						install
cpp-4.4						install
cron						install
dash						install
dbus						install
dbus-x11					install
debconf						install
debconf-i18n					install
debianutils					install
default-jre					install
default-jre-headless				install
defoma						install
dhcp3-client					install
dhcp3-common					install
dictionaries-common				install
diff						install
dmidecode					install
dmsetup						install
dpkg						install
e2fslibs					install
e2fsprogs					install
eject						install
exim4						install
exim4-base					install
exim4-config					install
exim4-daemon-light				install
expect						install
fail2ban					install
file						install
findutils					install
fontconfig					install
fontconfig-config				install
gcc-4.3-base					install
gcc-4.4-base					install
geoip-database					install
gettext-base					install
gimp						deinstall
gimp-data					deinstall
gnupg						install
gpgv						install
grep						install
groff-base					install
grub						install
grub-common					install
gsfonts						deinstall
gzip						install
hicolor-icon-theme				install
hostname					install
hunspell-en-us					install
ifupdown					install
initramfs-tools					install
initscripts					install
insserv						install
iproute						install
iptables					install
iputils-ping					install
iso-codes					install
java-common					install
john						install
john-data					install
kbd						install
klibc-utils					install
klogd						deinstall
landscape-common				install
language-pack-en				install
language-pack-en-base				install
language-support-translations-en		deinstall
language-support-writing-en			deinstall
laptop-detect					install
latex-xft-fonts					install
less						install
libaa1						deinstall
libaccess-bridge-java				install
libaccess-bridge-java-jni			install
libacl1						install
libasound2					install
libatk1.0-0					install
libatk1.0-data					install
libatm1						install
libattr1					install
libavahi-client3				install
libavahi-common-data				install
libavahi-common3				install
libbabl-0.0-0					deinstall
libbind9-40					deinstall
libbind9-50					install
libblkid1					install
libbsd0						install
libbz2-1.0					install
libc-bin					install
libc6						install
libc6-i686					install
libcairo2					install
libcap2						install
libck-connector0				install
libclass-accessor-perl				install
libcolamd2.7.1					install
libcomerr2					install
libcroco3					deinstall
libcups2					install
libcurl3-gnutls					install
libcwidget3					install
libdatrie0					deinstall
libdatrie1					install
libdb4.6					install
libdb4.7					install
libdbus-1-3					install
libdbus-glib-1-2				install
libdevmapper1.02.1				install
libdirectfb-1.0-0				deinstall
libdirectfb-1.2-0				install
libdns45					deinstall
libdns46					deinstall
libdns53					install
libedit2					install
libeggdbus-1-0					install
libept0						install
libexif12					deinstall
libexpat1					install
libffi5						install
libflac8					install
libfontconfig1					install
libfontenc1					install
libfreetype6					install
libfribidi0					install
libgcc1						install
libgcrypt11					install
libgdbm3					install
libgegl-0.0-0					deinstall
libgeoip1					install
libgif4						install
libgimp2.0					deinstall
libglib2.0-0					install
libglib2.0-data					install
libgmp3c2					install
libgnutls26					install
libgpg-error0					install
libgpm2						install
libgsf-1-114					deinstall
libgssapi-krb5-2				install
libgstreamer-plugins-base0.10-0			install
libgstreamer0.10-0				install
libgtk2.0-0					install
libgtk2.0-bin					install
libgtk2.0-common				install
libhal1						deinstall
libhsqldb-java					install
libhunspell-1.2-0				install
libhyphen0					install
libice6						install
libicu40					install
libidn11					install
libilmbase6					deinstall
libio-string-perl				install
libisc45					deinstall
libisc50					install
libisccc40					deinstall
libisccc50					install
libisccfg40					deinstall
libisccfg50					install
libiw29						install
libjasper1					install
libjline-java					install
libjpeg62					install
libjs-jquery					install
libk5crypto3					install
libkeyutils1					install
libklibc					install
libkrb5-3					install
libkrb53					deinstall
libkrb5support0					install
liblcms1					install
libldap-2.4-2					install
liblocale-gettext-perl				install
liblockfile1					install
liblua5.1-0					install
liblwres40					deinstall
liblwres50					install
libmagic1					install
libmng1						deinstall
libmpfr1ldbl					install
libmysqlclient16				install
libncurses5					install
libncursesw5					install
libneon27-gnutls				install
libnet1						install
libnewt0.52					install
libnl1						install
libnspr4-0d					install
libnss3-1d					install
libogg0						install
libopenexr6					deinstall
libpam-ck-connector				install
libpam-modules					install
libpam-runtime					install
libpam0g					install
libpango1.0-0					install
libpango1.0-common				install
libparse-debianchangelog-perl			install
libpcap0.8					install
libpcre3					install
libpcsclite1					install
libpixman-1-0					install
libpng12-0					install
libpolkit-gobject-1-0				install
libpolkit2					install
libpoppler-glib4				deinstall
libpoppler4					deinstall
libpoppler5					deinstall
libpopt0					install
libpq5						install
libpulse0					install
libpython2.6					install
libraptor1					install
librasqal1					install
librdf0						install
libreadline5					install
libreadline6					install
librsvg2-2					deinstall
libsasl2-2					install
libsasl2-modules				install
libsdl1.2debian-alsa				deinstall
libselinux1					install
libsepol1					install
libservlet2.4-java				install
libsigc++-2.0-0c2a				install
libslang2					install
libsm6						install
libsmbios2					deinstall
libsndfile1					install
libsqlite3-0					install
libss2						install
libssl0.9.8					install
libstdc++6					install
libstlport4.6ldbl				install
libsub-name-perl				install
libsysfs2					install
libtasn1-3					install
libtext-charwidth-perl				install
libtext-iconv-perl				install
libtext-wrapi18n-perl				install
libthai-data					install
libthai0					install
libtiff4					install
libtimedate-perl				install
libts-0.0-0					install
libudev0					install
libusb-0.1-4					install
libuuid1					install
libvorbis0a					install
libvorbisenc2					install
libwmf0.2-7					deinstall
libwpd8c2a					install
libwpg-0.1-1					install
libwps-0.1-1					install
libwrap0					install
libx11-6					install
libx11-data					install
libxapian15					install
libxau6						install
libxaw7						install
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
libxml2						install
libxmu6						install
libxmuu1					install
libxpm4						install
libxrandr2					install
libxrender1					install
libxslt1.1					install
libxt6						install
libxtst6					install
linux-firmware					install
linux-generic					install
linux-image-2.6.28-11-server			install
linux-image-2.6.28-17-server			deinstall
linux-image-2.6.31-16-generic			install
linux-image-2.6.31-16-generic-pae		install
linux-image-generic				install
linux-image-generic-pae				install
linux-image-server				install
locales						install
locate						install
lockfile-progs					install
login						install
logrotate					install
lp-solve					install
lsb-base					install
lsb-release					install
lynx						install
lynx-cur					install
lzma						install
mailx						install
make						install
makedev						install
man-db						install
mawk						install
mdadm						install
mime-support					install
mktemp						install
module-init-tools				install
mount						install
mountall					install
myspell-en-au					install
myspell-en-gb					install
myspell-en-za					install
mysql-common					install
ncurses-base					install
ncurses-bin					install
ndisc6						install
net-tools					install
netbase						install
netcat						install
netcat-traditional				install
nmap						install
ntpdate						install
openjdk-6-jre					install
openjdk-6-jre-headless				install
openjdk-6-jre-lib				install
openntpd					install
openoffice.org-base				deinstall
openoffice.org-calc				deinstall
openoffice.org-common				deinstall
openoffice.org-core				deinstall
openoffice.org-draw				deinstall
openoffice.org-emailmerge			deinstall
openoffice.org-filter-binfilter			deinstall
openoffice.org-hyphenation			deinstall
openoffice.org-hyphenation-en-us		deinstall
openoffice.org-impress				deinstall
openoffice.org-l10n-common			deinstall
openoffice.org-math				deinstall
openoffice.org-thesaurus-en-au			deinstall
openoffice.org-thesaurus-en-us			deinstall
openoffice.org-writer				deinstall
openssh-client					install
openssh-server					install
openssl						install
os-prober					install
passwd						install
patch						install
perl						install
perl-base					install
perl-modules					install
postfix						deinstall
procps						install
psmisc						install
python						install
python-apport					install
python-apt					install
python-central					install
python-dbus					install
python-gdbm					install
python-gnupginterface				install
python-gobject					install
python-httplib2					install
python-launchpadlib				install
python-lazr-restfulclient			install
python-lazr-uri					install
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
python2.6-minimal				install
raptor-utils					install
readline-common					install
redland-utils					install
reiserfsprogs					install
rhino						install
rsyslog						install
screen						install
screen-profiles					install
sed						install
sgml-base					install
shared-mime-info				install
ssh						install
ssl-cert					deinstall
sudo						install
sysklogd					deinstall
sysstat						install
system-services					deinstall
sysv-rc						install
sysvinit-utils					install
tar						install
tasksel						install
tasksel-data					install
tcl8.4						install
tcpd						install
tcpdump						install
tcptraceroute					install
telnet						install
traceroute					install
tsconf						install
ttf-dejavu					install
ttf-dejavu-core					install
ttf-dejavu-extra				install
ttf-liberation					install
ttf-opensymbol					install
tzdata						install
tzdata-java					install
ubuntu-keyring					install
ubuntu-minimal					install
ubuntu-serverguide				install
ucf						install
udev						install
ufw						install
uno-libs3					install
unzip						install
update-manager-core				install
update-notifier-common				install
upstart						install
upstart-compat-sysv				deinstall
upstart-logd					deinstall
ure						install
ureadahead					install
util-linux					install
vim						install
vim-common					install
vim-runtime					install
vim-tiny					install
wamerican					install
wbritish					install
whiptail					install
whois						install
wireless-crda					install
wireless-tools					install
wpasupplicant					install
x-ttcidfont-conf				install
x11-common					install
xauth						install
xfonts-encodings				install
xfonts-mathml					install
xfonts-utils					install
xfsprogs					install
xkb-data					install
xml-core					install
zlib1g						install
[/PHP]

---

### Post by mansonthomas on 2009-12-30
uninstalling java is also painful...

[PHP]root@ns1:~# aptitude purge java-common default-jre-headless default-jre
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
The following packages are BROKEN:
  openjdk-6-jre-headless
The following packages will be REMOVED:
  default-jre{p} default-jre-headless{p} java-common{p}
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 590kB will be freed.
The following packages have unmet dependencies:
  openjdk-6-jre-headless: Depends: java-common (>= 0.28) but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
ca-certificates-java
libaccess-bridge-java
libaccess-bridge-java-jni
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib

Install the following packages:
gcj-4.3-base [4.3.4-4ubuntu1 (karmic)]
gij-4.3 [4.3.4-4ubuntu1 (karmic)]
libgcj-common [1:4.4.1-1ubuntu2 (karmic)]
libgcj9-0 [4.3.4-4ubuntu1 (karmic)]
libgcj9-jar [4.3.4-4ubuntu1 (karmic)]

Score is 419
[/PHP]

the only way I figure out getting rid of java is to run 

[PHP]root@ns1:~# aptitude purge java-common default-jre-headless default-jre gcj-4.3-base gij-4.3 libgcj-common libgcj9-0 libgcj9-jar
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
The following packages are BROKEN:
  openjdk-6-jre-headless
The following packages will be REMOVED:
  default-jre{p} default-jre-headless{p} java-common{p}
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 590kB will be freed.
The following packages have unmet dependencies:
  openjdk-6-jre-headless: Depends: java-common (>= 0.28) but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
ca-certificates-java
libaccess-bridge-java
libaccess-bridge-java-jni
libhsqldb-java
libjline-java
libservlet2.4-java
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
rhino

Score is 740
[/PHP]

---

### Post by bobwdn on 2010-03-08
My experiences:

I had done an Ubuntu-server 9.10 install from the mini.iso CD. (It pulls the most current packages when installing.) And for whatever reason it installed openoffice as well as the other programs discussed above.

So, I had an extra old P3-700 and decided to install Ubuntu-server 9.10 from the complete CD as apposed to the mini.iso image. The complete 32-bit CD image did not install openoffice.

So, my guess (emphasis on guess) is that there is something set on the mini.iso that causes openoffice to be loaded.

Now, on my existing 9.10 server (that had been installed from the mini.iso image) I still had openoffice using hard drive space. So, this morning I began experimenting with aptitude purge to find what I could un-install that might cause aptitude to un-install the dependencies at the same time. The following code worked for me:```
sudo aptitude purge openoffice.org-core
```This resulted in removal of the following packages: language-support-en, language-support-writing-en, openoffice.org, openoffice.org-base, openoffice.org-calc, openoffice.org-draw, openoffice-hyphenation-en-us, openoffice.org-impress, openoffice.org-math, openoffice.org-officebean, openoffice.org-report-builder-bin, openoffice.org-thesaurus-en and finally openoffice.org-writer.

On my machine, this freed up 467Mb of space that was otherwise doing nothing. I was satisfied with that and have stopped here.

Others may want to add removing this or that, but this (in my opinion) got the bulk of it.

Happy computing:D

---

