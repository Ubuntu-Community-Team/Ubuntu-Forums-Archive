---
title: "FTP Server - File Sharing"
date: 2012-05-31
forum: Server Platforms
---

### Post by amer-sa on 2012-05-31
Hello everyone 

I'am trying to set up an FTP server form my firms file shearing(sending big files to our costumers) and I've already installed Ubuntu 12.04 server. Now I'am having trouble joining my Windows domain (active directory). I'am following this [tutorial]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto")  and cant get past editing smb.conf, I've installed everything above.

Can you help me? 

Thanks.

---

### Post by Cheesemill on 2012-05-31
What problems are you having with editing smb.conf?
The tutorial looks straight forward enough to me.

Also bear in mind that FTP is an inherently insecure protocol and should never be used unless you have a very good reason as it transmits usernames, passwords and files in unencrypted form that anyone can sniff out, you could be giving out your AD usernames and passwords to the internet at large.

You should consider using SSH instead to transfer files.

Also why do you need to connect your FTP server to your AD domain?

---

### Post by amer-sa on 2012-05-31
currently i have a win 7 comp that is being used as an FTP Server and i what to transfer to a new comp with more space and ubuntu. i have to make seamless transfer.

a cant restart samba

when i type sudo /etc/init.d/samba restart i get an error sudo: /etc/init.d/samba: command not found

(Also why do you need to connect your FTP server to your AD domain?)
beceuse the curent FTP server is connceted to AD.

---

### Post by Cheesemill on 2012-05-31
Can you post the output of:
```
ls -l /etc/init.d/
```

---

### Post by amer-sa on 2012-05-31
> hamer@ftpserver:~$ ls -l /etc/init.d/
total 188
lrwxrwxrwx 1 root root   21 Dec  8 19:47 acpid -> /lib/init/upstart-job
-rwxr-xr-x 1 root root  652 Jan  5  2010 acpi-support
lrwxrwxrwx 1 root root   21 Apr  4 06:13 alsa-restore -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr  4 06:13 alsa-store -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Jun 20  2010 anacron -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 7621 Feb  7 05:16 apache2
-rwxr-xr-x 1 root root 4596 Apr 12 13:17 apparmor
lrwxrwxrwx 1 root root   21 Apr 27 18:34 apport -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Oct 25  2011 atd -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Dec 17 16:48 avahi-daemon -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 3449 Apr 13 22:33 bind9
lrwxrwxrwx 1 root root   21 Mar 21 22:07 bluetooth -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2444 Apr 14 11:26 bootlogd
-rwxr-xr-x 1 root root 2125 Mar  1  2011 brltty
lrwxrwxrwx 1 root root   21 Apr 19 18:18 console-setup -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr  2 11:55 cron -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr 10 08:53 cups -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Feb 22 09:48 dbus -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Mar 30 19:23 dmesg -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 1242 Dec 13 18:11 dns-clean
lrwxrwxrwx 1 root root   21 Apr 15 06:29 failsafe-x -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Mar 14 15:02 friendly-recovery -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 1105 Apr 17 19:57 grub-common
-rwxr-xr-x 1 root root 1329 Apr 14 11:26 halt
lrwxrwxrwx 1 root root   21 May 26  2011 hostname -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Mar 30 07:34 hwclock -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Mar 30 07:34 hwclock-save -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Feb  4 06:27 irqbalance -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 1893 Apr 19 00:50 kerneloops
-rwxr-xr-x 1 root root 1293 Apr 14 11:26 killprocs
lrwxrwxrwx 1 root root   21 Apr 19 23:40 lightdm -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Mar 24 13:41 modemmanager -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Nov 20  2011 module-init-tools -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Mar 30 06:48 mysql -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2797 Feb 13 19:19 networking
lrwxrwxrwx 1 root root   21 Apr  5 07:19 network-interface -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr  5 07:19 network-interface-container -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr  5 07:19 network-interface-security -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 May  2 10:46 network-manager -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr 24 23:39 nmbd -> /lib/init/upstart-job
-rwxr-xr-x 1 root root  882 Apr 14 11:26 ondemand
lrwxrwxrwx 1 root root   21 Apr 13 17:49 plymouth -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr 13 17:49 plymouth-log -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr 13 17:49 plymouth-splash -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr 13 17:49 plymouth-stop -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr 13 17:49 plymouth-upstart-bridge -> /lib/init/upstart-job
-rwxr-xr-x 1 root root  561 Feb  4  2011 pppd-dns
lrwxrwxrwx 1 root root   21 Dec 12 18:42 procps -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2180 Apr 12 07:04 pulseaudio
-rwxr-xr-x 1 root root 8635 Apr 14 11:26 rc
-rwxr-xr-x 1 root root  801 Apr 14 11:26 rc.local
-rwxr-xr-x 1 root root  117 Apr 14 11:26 rcS
-rw-r--r-- 1 root root 2427 Apr 14 11:26 README
-rwxr-xr-x 1 root root  639 Apr 14 11:26 reboot
lrwxrwxrwx 1 root root   21 May 14 18:42 resolvconf -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Mar 22 22:01 rfkill-restore -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Mar 22 22:01 rfkill-store -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 4395 Nov  8  2011 rsync
lrwxrwxrwx 1 root root   21 Mar 30 19:23 rsyslog -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2344 Dec  5 00:07 saned
lrwxrwxrwx 1 root root   21 Jun  6  2011 screen-cleanup -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 4321 Apr 14 11:26 sendsigs
lrwxrwxrwx 1 root root   21 Apr 19 18:18 setvtrgb -> /lib/init/upstart-job
-rwxr-xr-x 1 root root  590 Apr 14 11:26 single
-rw-r--r-- 1 root root 4304 Apr 14 11:26 skeleton
lrwxrwxrwx 1 root root   21 Apr 24 23:39 smbd -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2107 May 16  2011 speech-dispatcher
-rwxr-xr-x 1 root root 4371 Apr  2 13:48 ssh
-rwxr-xr-x 1 root root  567 Apr 14 11:26 stop-bootlogd
-rwxr-xr-x 1 root root 1143 Apr 14 11:26 stop-bootlogd-single
-rwxr-xr-x 1 root root  700 Oct 27  2011 sudo
-rwxr-xr-x 1 root root 7929 Mar 16 15:28 tomcat6
lrwxrwxrwx 1 root root   21 Apr  5 21:18 udev -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr  5 21:18 udev-fallback-graphics -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr  5 21:18 udev-finish -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr  5 21:18 udevmonitor -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr  5 21:18 udevtrigger -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 Apr  5 20:16 ufw -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2800 Apr 14 11:26 umountfs
-rwxr-xr-x 1 root root 2211 Apr 14 11:26 umountnfs.sh
-rwxr-xr-x 1 root root 2926 Apr 14 11:26 umountroot
-rwxr-xr-x 1 root root 1039 Nov  9  2011 unattended-upgrades
-rwxr-xr-x 1 root root 1985 Apr 14 11:26 urandom
lrwxrwxrwx 1 root root   21 Apr 18 14:22 whoopsie -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 1342 Nov 12  2011 winbind
-rwxr-xr-x 1 root root 2666 Mar 22 18:35 x11-common

there you go

---

### Post by Cheesemill on 2012-05-31
The name has changed since the tutorial was written. Instead you need to do:
```
sudo /etc/init.d/smbd restart
```
to restart Samba

---

### Post by amer-sa on 2012-05-31
that worked THANKS

but i dont understand what i need to do now

> Request a valid Kerberos TGT for an account using kinit....

whena i type sudo kinit [email]Administrator@fabrika.local[/email]
i get sudo: kinit: command not found

---

### Post by Cheesemill on 2012-05-31
> **amer-sa said:**
> that worked THANKS

but i dont understand what i need to do now

Just keep following the tutorial, the code you need is just below 'Request a valid Kerberos TGT for an account using kinit....'

---

### Post by amer-sa on 2012-05-31
whena i type > sudo kinit [email]Administrator@fabrika.local[/email]
i get>  sudo: kinit: command not found

---

### Post by Cheesemill on 2012-05-31
What version of Ubuntu are you using?

That tutorial states that it is tested and working for 8.04, so if you are using anything later you are probably better of looking for a more up to date tutorial.

---

### Post by amer-sa on 2012-06-04
12.04

i've added the Ubuntu machine to AD, now i need to share a folder to all users so they can add and delete files from it.

i get an net usershare error 255.

---

