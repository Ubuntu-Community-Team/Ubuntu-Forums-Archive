---
title: "Warning flagged by the 'rkhunter'"
date: 2011-02-01
forum: Security
---

### Post by gkt.pro on 2011-02-01
when I scanned my Ubuntu 10.04 with rkhunter a root kit hunter toolkit, it gave following warning:
  Is there something that I have to worry about.


```

[23:06:19]   /usr/sbin/adduser                               [ Warning ]
            [23:06:19] Warning: The command '/usr/sbin/adduser' has been replaced by a script: /usr/sbin/adduser: a /usr/bin/perl script text executable
            [23:06:20]   /usr/sbin/rsyslogd                              [ Warning ]
            [23:06:20] Warning: The file properties have changed:
            [23:06:22]   /usr/bin/dpkg                                   [ Warning ]
            [23:06:22] Warning: The file properties have changed:
            [23:06:22]   /usr/bin/dpkg-query                             [ Warning ]
            [23:06:22] Warning: The file properties have changed:
            [23:06:24]   /usr/bin/ldd                                    [ Warning ]
            [23:06:24] Warning: The file properties have changed:
            [23:06:24] Warning: The command '/usr/bin/ldd' has been replaced by a script: /usr/bin/ldd: Bourne-Again shell script text executable
            [23:06:24]   /usr/bin/logger                                 [ Warning ]
            [23:06:24] Warning: The file properties have changed:
            [23:06:25]   /usr/bin/mail                                   [ Warning ]
            [23:06:25] Warning: The file '/usr/bin/mail' exists on the system, but it is not present in the rkhunter.dat file.
            [23:06:27]   /usr/bin/sudo                                   [ Warning ]
            [23:06:27] Warning: The file properties have changed:
            [23:06:29]   /usr/bin/whereis                                [ Warning ]
            [23:06:29] Warning: The file properties have changed:
            [23:06:29]   /usr/bin/lwp-request                            [ Warning ]
            [23:06:29] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: a /usr/bin/perl -w script text executable
            [23:06:29]   /usr/bin/bsd-mailx                              [ Warning ]
            [23:06:29] Warning: The file '/usr/bin/bsd-mailx' exists on the system, but it is not present in the rkhunter.dat file.
            [23:06:30]   /sbin/fsck                                      [ Warning ]
            [23:06:30] Warning: The file properties have changed:
            [23:06:30]   /sbin/ifdown                                    [ Warning ]
            [23:06:30] Warning: The file properties have changed:
            [23:06:31]   /sbin/ifup                                      [ Warning ]
            [23:06:31] Warning: The file properties have changed:
            [23:06:34]   /bin/dmesg                                      [ Warning ]
            [23:06:34] Warning: The file properties have changed:
            [23:06:35]   /bin/more                                       [ Warning ]
            [23:06:35] Warning: The file properties have changed:
            [23:06:36]   /bin/mount                                      [ Warning ]
            [23:06:36] Warning: The file properties have changed:
            [23:06:37]   /bin/which                                      [ Warning ]
            [23:06:37] Warning: The command '/bin/which' has been replaced by a script: /bin/which: POSIX shell script text executable
            [23:08:58]   Checking /dev for suspicious file types         [ Warning ]
            [23:08:58] Warning: Suspicious file types found in /dev:
            [23:08:58]   Checking for hidden files and directories       [ Warning ]
            [23:08:58] Warning: Hidden directory found: /etc/.java
            [23:08:58] Warning: Hidden directory found: /dev/.udev
            [23:08:58] Warning: Hidden directory found: /dev/.initramfs
            [23:09:01]   Checking version of Exim MTA                    [ Warning ]
            [23:09:01] Warning: Application 'exim', version '4.71', is out of date, and possibly a security risk.
            [23:09:01]   Checking version of GnuPG                       [ Warning ]
            [23:09:01] Warning: Application 'gpg', version '1.4.10', is out of date, and possibly a security risk.
            [23:09:01]   Checking version of OpenSSL                     [ Warning ]
            [23:09:01] Warning: Application 'openssl', version '0.9.8k', is out of date, and possibly a security risk.

```

---

### Post by uRock on 2011-02-01
Hello and welcome to the forums.

rkhunter is well known for its false positives. I recommend uninstalling it and using ClamAV. ClamAV has definitions for finding rootkits in Linux.

Unless you have been installing packages from sources other than the Ubuntu repos, you shouldn't have anything to worry about.

Cheers,
uRock

---

### Post by cariboo on 2011-02-01
If you must use rkhunter, do an update to the internal database before running it for the first time, or your results are never going to be any good.:

```
sudo rkhunter -update
```

---

### Post by gkt.pro on 2011-02-02
> **cariboo907 said:**
> If you must use rkhunter, do an update to the internal database before running it for the first time, or your results are never going to be any good.:

```
sudo rkhunter -update
```

I have updated rkhunter before scanning..

---

### Post by gkt.pro on 2011-02-02
> **uRock said:**
> Hello and welcome to the forums.

rkhunter is well known for its false positives. I recommend uninstalling it and using ClamAV. ClamAV has definitions for finding rootkits in Linux.

Unless you have been installing packages from sources other than the Ubuntu repos, you shouldn't have anything to worry about.

Cheers,
uRock

Is it KlamAV or ClamAv
I scanned the whole system with KlamAv and got nothing unusual except with some program that I installed using wine.But when I restarted my system,before even desktop is loaded, a window pops up showing me this error:

"couldn't update .ICEauthority file /home/gktpro/.ICEauthority"

then i tried to run klamav, it showed me the same problem,but when i run it with sudo it worked but with some warning and errors.
 Any clue why I have I am being forced to use sudo to run klamav, while it worked without sudo earlier. :mad:

---

### Post by gkt.pro on 2011-02-02
I don't like klamAv user interface it lacks some important features like autoprotect, firewall etc. Also I am not able to update it bcos the update now button is always disabled.
Isn't there any other good anti virus, what about avast i think it is available for ubuntu.

---

### Post by uRock on 2011-02-02
Antivirus and firewall are handled separately in Ubuntu. KlamAV is for Kubuntu as ClamAV is for Ubuntu and Xubuntu.

It may be helpful to take a look at this thread to learn more about how security works in Ubuntu. [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by bodhi.zazen on 2011-02-02
> **gkt.pro said:**
> I don't like klamAv user interface it lacks some important features like autoprotect, firewall etc. Also I am not able to update it bcos the update now button is always disabled.
Isn't there any other good anti virus, what about avast i think it is available for ubuntu.

I think a better question is what makes you feel you need these things in Linux at all ? This is not windows.

---

