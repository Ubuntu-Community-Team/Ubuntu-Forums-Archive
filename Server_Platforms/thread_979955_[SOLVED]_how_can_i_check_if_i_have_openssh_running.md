---
title: "[SOLVED] how can i check if i have openssh running"
date: 2008-11-12
forum: Server Platforms
---

### Post by Fertech on 2008-11-12
im trying to use winscp but says cant connect to the network, i try putty same error. i was looking around the forums and seen i someone had the same problem. then i guess i found out that he needed to install openssh. well me i already have it install, but dont know if its running, how can i check if its running.

---

### Post by Simian Man on 2008-11-12
The ssh daemon is called 'sshd'.  To see if it is running, open a terminal and type 'ps -A | grep sshd'.  This will list all processes that have sshd in their names.  If you see one, then the daemon is running; otherwise it is not.

---

### Post by Titan8990 on 2008-11-12
Use this command:

ps aux | grep ssh


My results:

```
jordan@einstein:~$ ps aux | grep ssh
root      5301  0.0  0.0   5280   988 ?        Ss   Oct20   0:00 /usr/sbin/sshd
jordan    6734  0.0  0.0   4432   540 ?        Ss   Oct20   0:04 /usr/bin/ssh-agent x-session-manager
jordan   27014  0.0  0.0   2980   776 pts/0    S+   12:21   0:00 grep ssh
```

sshd is the server

---

### Post by CrucifiedEgo on 2008-11-12
In the true spirit of unix, there's more than one way to do anything.  I'd recommend doing something like:

```
sudo netstat -natp | grep sshd
```

This should show you if sshd is running, and if it is, what ip address and port it's listening on.  It outputs something like this:

```
james@poseidon [~] $ sudo netstat -natp | grep ssh
tcp        0      0 67.207.149.257:30000     0.0.0.0:*    LISTEN 3647/sshd
```

In this case, it's listening on 67.207.149.257(this is fake for obvious reasons), port 30000.

---

### Post by HermanAB on 2008-11-12
I always use telnet to test low level stuff:
$ telnet servernameoripaddress portnumber

Ferinstance:
$ telnet mylab 22
Trying 172.24.107.10...
Connected to mylab.example.com.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.7

Now I know the DNS resolves, the server is listening and the firewall allows the port through.

Cheers,

Herman

---

### Post by Fertech on 2008-11-12
fertech@fertech-desktop:~$ ps aux |grep ssh
fertech   7851  0.0  0.0   3004   768 pts/0    S+   14:26   0:00 grep ssh
fertech@fertech-desktop:~$

---

### Post by Fertech on 2008-11-12
this is what i got back.

fertech@fertech-desktop:~$ sudo netstat -natp | grep sshd
fertech@fertech-desktop:~$

---

### Post by MJN on 2008-11-12
Yours isn't running.

Start it with [B]sudo /etc/init.d/ssh start

[/B]Mathew

---

### Post by Fertech on 2008-11-12
fertech@fertech-desktop:~$ sudo /etc/init.d/ssh start
[sudo] password for fertech: 
sudo: /etc/init.d/ssh: command not found

---

### Post by hictio on 2008-11-12
Did you installed it?
```

sudo aptitude install openssh-server (ENTER)

```

---

### Post by Fertech on 2008-11-21
I try to install it from Synaptic

---

### Post by Fertech on 2008-11-21
their was some errors, let me know if it's ok

fertech@fertech-desktop:~$ sudo aptitude install openssh-server
[sudo] password for fertech: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been automatically kept back:
  adept-common arts cervisia enscript kaddressbook kappfinder kapptemplate 
  kate kbabel kbugbuster kcachegrind kcontrol kdebase kdebase-bin 
  kdebase-bin-kde3 kdebase-data kdebase-dev kdebase-kio-plugins kdelibs 
  kdelibs-data kdelibs4-dev kdelibs4c2a kdepasswd kdeprint kdesdk 
  kdesdk-kfile-plugins kdesdk-kio-plugins kdesdk-misc kdesdk-scripts 
  kdesktop kdevelop kdevelop-data kfind khelpcenter kicker klipper 
  kmenuedit kmtrace kompare konqueror konqueror-nsplugins konsole kpager 
  kpersonalizer ksmserver ksplash kspy ksysguard ksysguardd ktip kuiviewer 
  kunittest kwin libarts1-dev libarts1c2a libartsc0 libartsc0-dev 
  libclamav3 libcupsys2-dev libcvsservice0 libdbus-1-dev libdns35 
  libglib2.0-dev libgtk2.0-dev libkcal2b libkdepim1a libkleopatra1 libkonq4 
  libkonq4-dev libktnef1 libmysqlclient15off libsmbclient-dev libxml2-dev 
  linux-libc-dev linux-restricted-modules-common mysql-common poxml tk8.4 
  umbrello 
The following packages have been kept back:
  adept-manager alacarte apt-utils base-files bind9-host clamav clamav-base 
  clamav-daemon clamav-dbg clamav-docs clamav-freshclam clamav-milter 
  clamav-testfiles cupsys cupsys-bsd cupsys-client cupsys-common dbus 
  dbus-x11 dnsutils evince firefox firefox-2 firefox-3.0 
  firefox-3.0-gnome-support firefox-gnome-support foo2zjs 
  gstreamer0.10-plugins-bad gstreamer0.10-tools gtk2-engines-pixbuf gvfs 
  gvfs-backends gvfs-fuse havp hpijs hplip hplip-data jockey-common 
  jockey-gtk kdebase-doc kdelibs4-doc kdeutils-doc kdevelop-dev 
  kdevelop-doc libbind9-30 libclamav-dev libcupsimage2 libcupsys2 
  libdbus-1-3 libexif12 libglib2.0-0 libgphoto2-2 libgphoto2-port0 
  libgstreamer0.10-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common 
  libgvfscommon0 libisccc30 libisccfg30 liblwres30 libsmbclient libxml2 
  libxml2-utils linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules-generic login logrotate module-init-tools 
  nautilus-sendto passwd pciutils python-apt python-libxml2 samba-common 
  smbclient thunderbird-locale-en-gb tzdata update-notifier 
  update-notifier-common xkb-data xserver-xorg-video-intel xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following partially installed packages will be configured:
  openssh-blacklist openssh-server ssh 
0 packages upgraded, 0 newly installed, 0 to remove and 165 not upgraded.
Need to get 155kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe havp 0.86-1build1 [155kB]
Fetched 155kB in 0s (161kB/s)
Preconfiguring packages ...
(Reading database ... 211409 files and directories currently installed.)
Preparing to replace havp 0.86-1build1 (using .../havp_0.86-1build1_i386.deb) ...
Unmounting /var/spool/havp ...umount: /var/spool/havp: device is busy
umount: /var/spool/havp: device is busy
invoke-rc.d: initscript havp, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Unmounting /var/spool/havp ...umount: /var/spool/havp: device is busy
umount: /var/spool/havp: device is busy
invoke-rc.d: initscript havp, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/havp_0.86-1build1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Starting havp: Starting HAVP Version: 0.86
Could not create server (already running?)
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/havp_0.86-1build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing havp (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up openssh-blacklist (0.1-1ubuntu0.8.04.1) ...
Setting up openssh-server (1:4.7p1-8ubuntu1.2) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 

Setting up ssh (1:4.7p1-8ubuntu1.2) ...

Errors were encountered while processing:
 havp
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
fertech@fertech-desktop:~$

---

### Post by hictio on 2008-11-21
You have a sh*t load of dependencies, really bizarre dependencies for a Ubuntu Server... What kind of Ubuntu Server install did you do? Have you installed anything else after the original isntall? Did you try to install the Desktop?

---

### Post by Fertech on 2009-01-22
no just update, and some basic programs nothing specail

---

