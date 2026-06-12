---
title: "telnetd issues"
date: 2005-03-11
forum: Server Platforms
---

### Post by FamMan on 2005-03-11
1st I have to say so far Ubuntu is a great distro., it's light and most things work the way they are suppose to. 

I will mostly be using Ubuntu for my server. I have apache2 and vsftpd working but I am having problems connecting remotely through telnet. 
I installed telnetd_0.17-24_i386.deb, what more do I need to do? 

When I try to telnet the message I get is: Could not open connection to the host, on port 23:
Connect failed

I have my port open and it was working when I was using Fedora Core 3 and RedHat 9. 

Thank you,

---

### Post by dmatrix on 2005-03-11
You should really look at replacing FTP and Telnet with a secure protocol like SSH. SSH can do secure shell sessions and secure file transfers.

sudo apt-get install ssh-server

If you would still really like telnet you will have to enable it in the inetd.conf or xinetd configuration.

---

### Post by theantix on 2005-03-11
[QUOTE=FamMan]1st I have to say so far Ubuntu is a great distro., it's light and most things work the way they are suppose to. 

I will mostly be using Ubuntu for my server. I have apache2 and vsftpd working but I am having problems connecting remotely through telnet. 
I installed telnetd_0.17-24_i386.deb, what more do I need to do? 

When I try to telnet the message I get is: Could not open connection to the host, on port 23:
Connect failed

I have my port open and it was working when I was using Fedora Core 3 and RedHat 9. 

Thank you,[/QUOTE]

Well I'm going to have to agree with the other poster, telnet is deadly insecure and should be discouraged.  But if you *really* need it for something and are willing to take the security risk, it should work on Ubuntu fairly easily.  Just to test I ran "apt-get install telnetd", and immediately I was able to telnet into my machine from localhost and from outside hosts as well[1].  Unlike you I was using the newer
telnetd_0.17-26_i386.deb from Hoary Hedgehog, but it seems like there is nothing inherent about the Ubuntu setup that would prevent you from using telnetd.

Perhaps you have changed something in your firewall or routing that would prevent access to this machine?  Alternately perhaps you have altered your hosts.* files from the Ubuntu defaults?  Hope that gives so something to work with, I realize my answer may not be exactly what you were hoping for.

[1] After my test I then immediately removed telnetd as it's a security hazard.

---

### Post by FamMan on 2005-03-12
Thanks for the advice. I uninstalled telnetd and installed ssh. I'm new to ssh so what would be a solid and easy to configure telnet and ftp server applications that supports ssh?

---

### Post by FamMan on 2005-03-22
OK, I am unable to get telnet to work period. I tried telnet ssl and telnetd. I am unable to connect. 

I didn't make any changes to my router. 

The only changes I made was replacing Fedora Core 3 with Ubuntu. Telnet worked fine when I was using Fedora Core 3 and Red Hat 9 before Fedora. 
I just need telnet to work. I'm not worried about the security issue, my server does not contain anything critical or important. I never had a problem with having telnet in the past either. 

The message I get is: 
telnet: Unable to connect to remote host: Connection refused

I checked my data port and 23 is open and pointing to my server. As I said before it worked fine when I was running Fedora, so Ubuntu is blocking the connection some how. 

Please help.

---

### Post by theantix on 2005-03-22
[QUOTE=FamMan]OK, I am unable to get telnet to work period. I tried telnet ssl and telnetd. I am unable to connect. 

I didn't make any changes to my router. 

The only changes I made was replacing Fedora Core 3 with Ubuntu. Telnet worked fine when I was using Fedora Core 3 and Red Hat 9 before Fedora. 
I just need telnet to work. I'm not worried about the security issue, my server does not contain anything critical or important. I never had a problem with having telnet in the past either. 

The message I get is: 
telnet: Unable to connect to remote host: Connection refused

I checked my data port and 23 is open and pointing to my server. As I said before it worked fine when I was running Fedora, so Ubuntu is blocking the connection some how. 

Please help.[/QUOTE]

Sadly I am not able to help you at all.  Like I said in my previous post, I installed ubuntu's telnetd and I could connect from a remote machine instantly.  Just now I tried doing the same on my Warty box, so no matter what version of Ubuntu you are using, the steps required are quite simple: install the "telnetd" via apt-get or synaptic.  That's it, if you've done that it should be working and can connect to it from any machine.

Do you have nmap installed?  If not, install nmap and then paste in the output of "nmap localhost" -- that will tell us if your machine is actually running the telnet server daemon.  I suspect the problem is that you just don't have the package installed and/or running.  If the output of nmap shows to me that it is indeed running, trying doing an nmap from your remote computer and see if *that* can see telnet or anything else running.  I'll try to debug further from that point.

---

### Post by FamMan on 2005-03-22
I installed telnetd manually. I just uninstalled to install it with apt-get.

When I do: apt-get install telnetd I get the following message,

Reading Package Lists... Done
Building Dependency Tree... Done
Package telnetd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package telnetd has no installation candidate

I take it that the server apt-get is trying to grab telnetd from does not have it.
So where should I have apt-get grab files and updates?

---

### Post by theantix on 2005-03-22
[QUOTE=FamMan]I take it that the server apt-get is trying to grab telnetd from does not have it.
So where should I have apt-get grab files and updates?[/QUOTE]

Okay, that may explain the origin of your issue.  I should have suspected that when you originally mentioned using dpkg to install it.  It seems like that package you installed was broken somehow, or it did not correctly configure itself.  I'd start by removing that package if you can.

To install telnetd you need to enable the "universe" repository.  This contains programs that aren't supported by Ubuntu but are imported from the Debian project and generally work well.  See [http://www.ubuntulinux.org/wiki/UniversePackages](http://www.ubuntulinux.org/wiki/UniversePackages) for information on how to enable that in synaptic, or if you prefer to do it manually edit the /etc/apt/sources.list to include "universe" at the end of the lines that have "main restricted", like the following:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe

After doing that and updating via "apt-get update" or reloading in synaptic, you'll be able to easily install telnetd, and then it should work no problem at all.

---

### Post by meseleto on 2006-09-30
I tried installing ssh but I got this message


Reading package lists... Done
Building dependency tree... Done
Package ssh-server is a virtual package provided by:
  openssh-server 1:4.2p1-7ubuntu3
  ssh-krb5 3.8.1p1-10
  lsh-server 2.0.1cdbs-4
You should explicitly select one to install.
E: Package ssh-server has no installation candidate

What did I do wrong?

---

### Post by drinky76 on 2007-01-04
> **meseleto said:**
> I tried installing ssh but I got this message


Reading package lists... Done
Building dependency tree... Done
Package ssh-server is a virtual package provided by:
  openssh-server 1:4.2p1-7ubuntu3
  ssh-krb5 3.8.1p1-10
  lsh-server 2.0.1cdbs-4
You should explicitly select one to install.
E: Package ssh-server has no installation candidate

What did I do wrong?

What the error is telling you is that ssh-server isn't a real package but is a package provided for the sake of compatibility with other things which expect or require it to be installed and it is provided by one of the other real packages which are listed. You want to install openssh-server.

---

### Post by nihilocrat on 2007-01-04
> **meseleto said:**
> 
E: Package ssh-server has no installation candidate
What did I do wrong?

For future reference, whenever you get an error like this try:
```
apt-cache search [package name]
```
It should list packages which have similar names, descriptions, or files under that name in them. Really handy tool.

If you install either SSH or telnet from apt-get they should work swimmingly. I figure telnet is really only okay on 'security through obscurity' boxes, but it is a good idea to use FTP vs. SFTP (that's FTP through SSH) because in my experience SFTP slows down file transfers a whole lot.

---

### Post by CareySchug on 2007-01-26
I have the same problem, I get "telnet: Unable to connedt to remote host: COnnection refused", and I am trying to telnet from the local machine.  I need tellnet for a tn3270 emulator, which, as far as I can find, only connects via telnet, and not ssh.  I need either to  learn how to connect tn3270 via ssh Iwithout modifying the target machine) or get telnet opened up.  I installed "telnetd" via apt-get, could not telnet.  I removed that and installed inetutils-telnetd, still got same error.  I removed that and installed telnetd-ssl with firestarter, still same error.  Each time I rebooted in case it just didn't get initialized by being installed.  I saw your post and installed nmap, and this is all I get (the target machine is different, so its easier to type it in that copy and send it over:

Starting Nmap 4.10 (....)
Interesting ports on localhost (127...)
Not shown: 1678 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

that is all.

After some of the installs I did things like "man telnetd" and tried to bring up telnet daemon manualy, but I don't think anything I did had any effect.

Just now si removed telnetd-ssl (because a find / -name telnet*.* found nothing that looked executable) and re-installed  with apt-get the telnetd packate.  When I run "/usr/sbin/in.telnetd &" I get "telnetd: getpeername: Socket operation on non-socket" making me think that tcp/23 socket has been disabled, and needs to be enabled


> **theantix said:**
> Sadly I am not able to help you at all.  Like I said in my previous post, I installed ubuntu's telnetd and I could connect from a remote machine instantly.  Just now I tried doing the same on my Warty box, so no matter what version of Ubuntu you are using, the steps required are quite simple: install the "telnetd" via apt-get or synaptic.  That's it, if you've done that it should be working and can connect to it from any machine.

Do you have nmap installed?  If not, install nmap and then paste in the output of "nmap localhost" -- that will tell us if your machine is actually running the telnet server daemon.  I suspect the problem is that you just don't have the package installed and/or running.  If the output of nmap shows to me that it is indeed running, trying doing an nmap from your remote computer and see if *that* can see telnet or anything else running.  I'll try to debug further from that point.

---

### Post by drinky76 on 2007-01-27
Ok, I managed to get this working after some messing around, but that was a few weeks ago and I had forgotten about this thread so my instructions are a bit flaky.

To run telnetd, via inetd you need some of:

netkit-inetd - The Internet Superserver
inetutils-inetd - Internet super server
inetutils-telnetd - Telnet server
telnetd - The telnet server

So install them with

  sudo apt-get install <packagename1> <packagename2>

You can see what packages you have installed with

  sudo dpkg --get-selections | grep telnetd
  sudo dpkg --get-selections | grep inetd

As I said, my recollection is patchy, so play with combinations of the above and use the following instructions. I'm pretty certain you need the netkit package and one of the others causes it to be removed, so watch out for that. If it doesn't work that way, try installing the package which causes netkit to be removed and restart the inetd daemon.

You need to removed the #<off># part on the telnet line of /etc/inetd.conf file so it looks like this:

  telnet                 stream  tcp     nowait  telnetd.telnetd /usr/sbin/tcpd  /usr/sbin/in.telnetd

Then run 

  /etc/init.d/inetutils-inetd start

to start the service. Now you should be able to connect. I'm sorry to anyone struggling with this for not being able to be more exact.

---

### Post by franganghi on 2007-04-06
](*,) 

So, i've followed up a lot of tutorial, but i still can't figure out how to obtain telnet to be enabled on my workstation! I know, it's insecure, but instead of talk about security it's better to think that there are some rare situations where port 23 is the only port available!

Ok, now i'll explain mine and excuse for my english.

inetd seems to be working

```
useruser@rebuntu:/etc/init.d$ sudo ./inetutils-inetd restart
 * Restarting internet superserver inetd                                 [ ok ] 
```

Needed software seems to be installed

```

useruser@rebuntu:/etc/init.d$ ls -l
totale 436
-rwxr-xr-x 1 root root 2445 2006-09-15 19:48 acpid
-rwxr-xr-x 1 root root  867 2006-03-28 18:26 acpi-support
-rwxr-xr-x 1 root root 9342 2006-07-31 03:50 alsa-utils
-rwxr-xr-x 1 root root 1015 2006-09-20 16:21 anacron
-rwxr-xr-x 1 root root 4705 2006-09-27 18:54 apache2
-rwxr-xr-x 1 root root 1386 2006-07-21 04:16 apmd
-rwxr-xr-x 1 root root 2252 2006-09-28 20:09 apport
-rwxr-xr-x 1 root root  969 2006-07-21 04:15 atd
-rwxr-xr-x 1 root root 3747 2006-09-09 16:34 avahi-daemon
-rwxr-xr-x 1 root root 1109 2005-10-27 14:15 binfmt-support
-rwxr-xr-x 1 root root 6980 2006-10-20 20:02 bluetooth
-rwxr-xr-x 1 root root 3597 2006-10-06 13:34 bootclean
-rwxr-xr-x 1 root root 2121 2006-10-06 13:34 bootlogd
-rwxr-xr-x 1 root root 1883 2006-10-06 13:34 bootmisc.sh
-rwxr-xr-x 1 root root  881 2006-10-12 02:32 brltty
-rwxr-xr-x 1 root root 2887 2006-10-06 13:34 checkfs.sh
-rwxr-xr-x 1 root root 9875 2006-10-06 13:34 checkroot.sh
-rwxr-xr-x 1 root root 6211 2006-09-08 00:36 console-screen.sh
-rwxr-xr-x 1 root root  680 2006-09-22 17:53 console-setup
-rwxr-xr-x 1 root root 1741 2006-07-21 04:14 cron
-rwxr-xr-x 1 root root 2130 2006-10-09 18:54 cupsys
-rwxr-xr-x 1 root root 2545 2006-10-20 13:45 dbus
-rwxr-xr-x 1 root root  795 2006-06-29 01:59 dns-clean
-rwxr-xr-x 1 root root 1196 2006-10-06 16:53 festival
-rwxr-xr-x 1 root root 2590 2006-10-21 01:35 gdm
-rwxr-xr-x 1 root root 6175 2006-10-10 16:46 glibc.sh
-rwxr-xr-x 1 root root 1228 2006-10-06 13:34 halt
-rwxr-xr-x 1 root root 2350 2006-10-12 04:45 hddtemp
-rwxr-xr-x 1 root root 5137 2005-04-21 12:10 hdparm
-rwxr-xr-x 1 root root  909 2006-10-06 13:34 hostname.sh
-rwxr-xr-x 1 root root 2245 2006-04-29 21:09 hotkey-setup
-rwxr-xr-x 1 root root 4438 2006-10-13 19:34 hplip
-rwxr-xr-x 1 root root 3634 2006-10-12 17:47 hwclock.sh
-rwxr-xr-x 1 root root 1850 2006-10-14 05:33 inetd
-rwxr-xr-x 1 root root 1393 2006-06-21 19:40 inetutils-inetd
-rwxr-xr-x 1 root root  677 2006-07-03 22:16 initrd-tools.sh
-rwxr-xr-x 1 root root  493 2006-09-22 17:53 keyboard-setup
-rwxr-xr-x 1 root root  944 2006-10-06 13:34 killprocs
-rwxr-xr-x 1 root root 1928 2006-10-06 15:46 klogd
-rwxr-xr-x 1 root root 1221 2006-10-06 15:47 laptop-mode
-rwxr-xr-x 1 root root  349 2006-10-20 04:42 linux-restricted-modules-common
-rwxr-xr-x 1 root root  614 2006-09-18 20:55 lm-sensors
-rwxr-xr-x 1 root root  748 2006-01-23 19:47 loopback
-rwxr-xr-x 1 root root 1053 2006-07-21 04:08 makedev
-rwxr-xr-x 1 root root 1234 2006-07-05 04:01 module-init-tools
-rwxr-xr-x 1 root root  737 2006-08-31 20:37 modutils
-rwxr-xr-x 1 root root  617 2006-10-06 13:34 mountall-bootclean.sh
-rwxr-xr-x 1 root root 2354 2006-10-06 13:34 mountall.sh
-rwxr-xr-x 1 root root 1491 2006-10-06 13:34 mountdevsubfs.sh
-rwxr-xr-x 1 root root 1087 2006-10-06 13:34 mountkernfs.sh
-rwxr-xr-x 1 root root  615 2006-10-06 13:34 mountnfs-bootclean.sh
-rwxr-xr-x 1 root root 2689 2006-10-06 13:34 mtab.sh
-rwxr-xr-x 1 root root 6128 2006-10-12 01:41 mysql
-rwxr-xr-x 1 root root 2051 2006-10-12 01:41 mysql-ndb
-rwxr-xr-x 1 root root 1980 2006-10-12 01:41 mysql-ndb-mgm
-rwxr-xr-x 1 root root 1685 2006-07-03 21:12 networking
-rwxr-xr-x 1 root root  927 2006-09-18 21:07 ntp-server
-rwxr-xr-x 1 root root  860 2005-10-29 04:48 nvidia-kernel
-rwxr-xr-x 1 root root 6568 2006-07-21 03:02 pcmcia
-rwxr-xr-x 1 root root 2302 2006-07-21 03:02 pcmciautils
-rwxr-xr-x 1 root root 4107 2006-09-29 20:33 powernowd
-rwxr-xr-x 1 root root  177 2006-09-29 20:33 powernowd.early
-rwxr-xr-x 1 root root  345 2006-07-10 21:13 pppd-dns
-rwxr-xr-x 1 root root 1226 2006-09-08 17:24 procps.sh
-rwxr-xr-x 1 root root 8197 2006-10-06 13:34 rc
-rwxr-xr-x 1 root root  522 2006-10-06 13:34 rc.local
-rwxr-xr-x 1 root root  117 2006-10-06 13:34 rcS
-rwxr-xr-x 1 root root 1400 2006-10-20 20:37 readahead
-rwxr-xr-x 1 root root 1859 2006-10-20 20:37 readahead-desktop
-rw-r--r-- 1 root root 1335 2006-10-06 13:34 README
-rwxr-xr-x 1 root root  692 2006-10-06 13:34 reboot
-rwxr-xr-x 1 root root 1000 2006-10-06 13:34 rmnologin
-rwxr-xr-x 1 root root 3417 2006-07-21 04:06 rsync
-rwxr-xr-x 1 root root  452 2006-04-26 23:39 screen
-rwxr-xr-x 1 root root  755 2006-10-06 13:34 sendsigs
-rwxr-xr-x 1 root root 1632 2006-09-18 20:55 sensord
-rwxr-xr-x 1 root root  585 2006-10-06 13:34 single
-rwxr-xr-x 1 root root 4215 2006-10-06 13:34 skeleton
-rwxr-xr-x 1 root root 2468 2006-02-23 17:27 stop-bootchart
-rwxr-xr-x 1 root root  510 2006-10-06 13:34 stop-bootlogd
-rwxr-xr-x 1 root root  647 2006-10-06 13:34 stop-bootlogd-single
-rwxr-xr-x 1 root root  864 2006-10-20 20:37 stop-readahead
-rwxr-xr-x 1 root root 1804 2006-10-06 15:46 sysklogd
-rwxr-xr-x 1 root root 2584 2006-10-16 14:39 udev
-rwxr-xr-x 1 root root 3477 2006-10-06 13:34 umountfs
-rwxr-xr-x 1 root root 1833 2006-10-06 13:34 umountnfs.sh
-rwxr-xr-x 1 root root 1105 2006-10-06 13:34 umountroot
-rwxr-xr-x 1 root root 1815 2006-10-06 13:34 urandom
-rwxr-xr-x 1 root root 2120 2006-10-05 17:47 usplash
-rwxr-xr-x 1 root root  820 2006-10-15 21:30 vbesave
-rwxr-xr-x 1 root root 1939 2006-10-06 13:34 waitnfs.sh
-rwxr-xr-x 1 root root 1895 2006-08-11 19:05 wpa-ifupdown
-rwxr-xr-x 1 root root 1832 2006-09-10 16:21 x11-commo
```

inetd.conf seems to be ok

```

useruser@rebuntu:/etc$ cat inetd.conf 
telnet          stream  tcp     nowait  telnetd.telnetd /usr/sbin/tcpd  /usr/sbin/in.telnetd
```

in.telnetd started in debug mode works perfectly

```

useruser@rebuntu:/usr/sbin$ sudo ./in.telnetd -debug 23
```

telnetd in passwd is now in this situation

```
telnetd:x:111:117::/nonexistent:/bin/false
```

But everytime i try to start the service with inetblabla i find a line like this in my syslog

```
Apr  6 15:46:36 rebuntu inetd[12835]: telnet/tcp: No such user 'telnetd.telnetd', service ignored
```

So i thing that is this the reason why telnetd is not loaded... or thinking better, is immediately unloaded after load!

```
useruser@rebuntu:/var/log$ ps -ef|grep telnetd
useruser  13502  7428  0 16:05 pts/2    00:00:00 grep telnetd
```

My user export for any purpose

```

useruser@rebuntu:/var/log$ export
declare -x COLORTERM="gnome-terminal"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-083GTiA1pr,guid=7f2916466041d949ae2416af4232be00"
declare -x DESKTOP_SESSION="default"
declare -x DISPLAY=":0.0"
declare -x GDMSESSION="default"
declare -x GDM_XSERVER_LOCATION="local"
declare -x GNOME_DESKTOP_SESSION_ID="Default"
declare -x GNOME_KEYRING_SOCKET="/tmp/keyring-RyiUno/socket"
declare -x GTK_RC_FILES="/etc/gtk/gtkrc:/home/useruser/.gtkrc-1.2-gnome2"
declare -x HISTCONTROL="ignoredups"
declare -x HOME="/home/useruser"
declare -x LANG="it_IT.UTF-8"
declare -x LANGUAGE="it_IT:it:en_GB:en"
declare -x LD_LIBRARY_PATH="/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/lib:"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="useruser"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:"
declare -x OLDPWD="/etc"
declare -x ORACLE_HOME="/usr/lib/oracle/xe/app/oracle/product/10.2.0/client"
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
declare -x PWD="/var/log"
declare -x SESSION_MANAGER="local/rebuntu:/tmp/.ICE-unix/6633"
declare -x SHELL="/bin/bash"
declare -x SHLVL="2"
declare -x SSH_AGENT_PID="6668"
declare -x SSH_AUTH_SOCK="/tmp/ssh-BypAKH6633/agent.6633"
declare -x TERM="xterm"
declare -x USER="useruser"
declare -x USERNAME="useruser"
declare -x WINDOWID="52438013"
declare -x WINDOW_MANAGER="~/.gnome-compiz-manager/openbox"
declare -x XAUTHORITY="/home/useruser/.Xauthority"
declare -x http_proxy="http://127.0.0.1:5865/"
declare -x no_proxy="localhost,127.0.0.0/8,*.local"

```

Help me please, i need telnet, the fantastic, insecure, issuissableled, magical telnet.

Giovanni - ROMA - IT

---

### Post by mekon on 2007-04-21
Hi there

I got telnet working tonight by running:

sudo apt-get install netkit-inetd

The following came up:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  inetutils-inetd
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  inetutils-inetd
The following NEW packages will be installed:
  netkit-inetd
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 32.6kB of archives.
After unpacking 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main netkit-inetd 0.10-10.3ubuntu4 [32.6kB]
Fetched 32.6kB in 0s (99.8kB/s)
Preconfiguring packages ...
(Reading database ... 107210 files and directories currently installed.)
Removing inetutils-inetd ...
 * Stopping internet superserver inetd                                   [ ok ] 
Selecting previously deselected package netkit-inetd.
(Reading database ... 107202 files and directories currently installed.)
Unpacking netkit-inetd (from .../netkit-inetd_0.10-10.3ubuntu4_i386.deb) ...
Setting up netkit-inetd (0.10-10.3ubuntu4) ...
 * Starting internet superserver...                                      [ ok ]

---

### Post by franganghi on 2007-04-21
Ok, i'll try on monday morning at office. Thanks.

---

### Post by cmnorton on 2007-06-22
I tried installing telnetd two ways, via psuedo apt-get install telnetd and Synaptic. Both installations succeeded. However, I cannot connect. This is what happens when I try to connect locally. sshd is running, and I can connect using that.

cnorton@linux-testU:~$ telnet linux-testU
Trying 127.0.0.1...
Trying 127.0.1.1...
telnet: Unable to connect to remote host: Connection refused
cnorton@linux-testU:~$

Here are the lines in /etc/inetd.conf.

#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd
telnet          stream  tcp     nowait  telnetd.telnetd /usr/sbin/tcpd  /usr/sbin/in.telnetd

I would appreciate any suggestions on what to look at next.

tnx
cmn

---

### Post by franganghi on 2007-06-22
> **cmnorton said:**
> 
However, I cannot connect. This is what happens when I try to connect locally. sshd is running, and I can connect using that.


If you type "ps -ef|grep telnet" you can see that the process isn't running.
This is the reason why you can connect.

I'm still trying to fix the problem on my box.

---

### Post by cmnorton on 2007-07-10
I installed netkit-inetd and telnetd and made some progress. Instead of the connenction being flatly refused, I get this:


root@linux-testU:~# telnet localhost
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.

At least it's connected, but then supposes a control-D was sent. Does anyone have any ideas of what I can change to make the connnection complete?

tnx
cmn

---

### Post by franganghi on 2007-07-10
I tryed with ssh and i had no problems.
With tftp the problem was some grant in a /var/ dir: maybe is the same with telnet?

Ciao

---

### Post by TimSNL on 2007-07-23
> **cmnorton said:**
> I installed netkit-inetd and telnetd and made some progress. Instead of the connenction being flatly refused, I get this:


root@linux-testU:~# telnet localhost
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.

At least it's connected, but then supposes a control-D was sent. Does anyone have any ideas of what I can change to make the connnection complete?

tnx
cmn

I have the same problem.  Did you get past this point?

---

### Post by TimSNL on 2007-07-24
Just incase anyone else is having a problem with telnet - here is my solution :)

My /etc/inetd.conf file looked like this
```
#<off># ftp     stream  tcp     nowait  root    /usr/sbin/tcpd /usr/sbin/proftpd
telnet          stream  tcp     nowait  telnetd-ssl.telnetd-ssl /usr/sbin/tcpd /usr/sbin/in.telnetd
```

I changed the user to root and it let me login with telnet
```
#<off># ftp     stream  tcp     nowait  root    /usr/sbin/tcpd /usr/sbin/proftpd
telnet          stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/in.telnetd
```

I dont know what the side effects of this are and maybe there is a better solution.  But this got me going.

---

