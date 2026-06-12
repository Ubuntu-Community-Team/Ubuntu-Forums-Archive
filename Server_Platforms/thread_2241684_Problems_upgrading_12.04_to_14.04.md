---
title: "Problems upgrading 12.04 to 14.04"
date: 2014-08-27
forum: Server Platforms
---

### Post by gregor9 on 2014-08-27
Hi!

I'm trying to do "do-release-upgrade" and every time I get failed upgrade. Upgrade process returns error code 100. And I'm stuck there. I have sa-compile crash report if anyone woul be so kind to help me out of this mess.

---

### Post by Bashing-om on 2014-08-27
gregor9; Hi ! Welcome to the forum .

Generally there is but 2 things that will cause a failing release upgrade:
a) 3rd party software that is non-compatible with the new release;
Make sure ALL PPA's are reverted to either what is available in ubuntu's software repository or removed, and the sources disabled.

b) (along with 'a') is proprietary drivers for graphics, networking or printers -> back to open source drivers

And then of course, make sure that the system is fully updated;
And finally that the screensaver is disabled.

As close to default as possible -> expect no problem in the release upgrade.

[INDENT][INDENT]workie great last long time
[/INDENT][/INDENT]

---

### Post by gregor9 on 2014-08-28
I have no proprietary drivers and and I have only standard PPA sources in sources list.

---

### Post by Bashing-om on 2014-08-28
gregor9; Hokay !

Let's check and make sure:
```

lsb_release -a
sudo lshw -C display
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

If all that is at default, and you are fully updated, I expect the release-upgrade to happen.

[INDENT][INDENT]with all due respects
[/INDENT][/INDENT]

---

### Post by gregor9 on 2014-08-28
Here is result of the commands.
```

root@odin:/etc/apt/sources.list.d# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

root@odin:/etc/apt/sources.list.d# lshw -C display
  *-display UNCLAIMED
       description: VGA compatible controller
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller
       configuration: latency=0
       resources: memory:fd000000-fdffffff memory:febd0000-febd0fff memory:febc0000-febcffff

root@odin:/etc/apt/sources.list.d# cat -n /etc/apt/sources.list
     1  #
     2
     3  # deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/main/binary-i386/
     4  # deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/restricted/binary-i386/
     5  # deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ precise main restricted
     6
     7  # deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/main/binary-i386/
     8  # deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/restricted/binary-i386/
     9  # deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ precise main restricted
    10
    11  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    12  # newer versions of the distribution.
    13  deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    14  deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    15
    16  ## Major bug fix updates produced after the final release of the
    17  ## distribution.
    18  deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    19  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    20
    21  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    22  ## team. Also, please note that software in universe WILL NOT receive any
    23  ## review or updates from the Ubuntu security team.
    24  deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    25  deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    26  deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    27  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    28
    29  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    30  ## team, and may not be under a free licence. Please satisfy yourself as to
    31  ## your rights to use the software. Also, please note that software in
    32  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    33  ## security team.
    34  deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    35  deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    36  deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    37  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    38
    39  ## N.B. software from this repository may not have been tested as
    40  ## extensively as that contained in the main release, although it includes
    41  ## newer versions of some applications which may provide useful features.
    42  ## Also, please note that software in backports WILL NOT receive any review
    43  ## or updates from the Ubuntu security team.
    44  deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    45  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    46
    47  deb http://security.ubuntu.com/ubuntu precise-security main restricted
    48  deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    49  deb http://security.ubuntu.com/ubuntu precise-security universe
    50  deb-src http://security.ubuntu.com/ubuntu precise-security universe
    51  deb http://security.ubuntu.com/ubuntu precise-security multiverse
    52  deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    53
    54  ## Uncomment the following two lines to add software from Canonical's
    55  ## 'partner' repository.
    56  ## This software is not part of Ubuntu, but is offered by Canonical and the
    57  ## respective vendors as a service to Ubuntu users.
    58  #deb http://archive.canonical.com/ubuntu precise partner
    59  #deb-src http://archive.canonical.com/ubuntu precise partner
    60
    61  ## Uncomment the following two lines to add software from Ubuntu's
    62  ## 'extras' repository.
    63  ## This software is not part of Ubuntu, but is offered by third-party
    64  ## developers who want to ship their latest software.
    65  # deb http://extras.ubuntu.com/ubuntu precise main
    66  # deb-src http://extras.ubuntu.com/ubuntu precise main
    67
    68  ## Medibuntu - Ubuntu 12.04 "Precise Pangolin"
    69  ## Please report any bug on https://bugs.launchpad.net/medibuntu/
    70  # deb http://packages.medibuntu.org/ precise free non-free
    71  # deb-src http://packages.medibuntu.org/ precise free non-free
    72

root@odin:/etc/apt/sources.list.d# tail -v -n +1 /etc/apt/sources.list.d/*
tail: cannot open `/etc/apt/sources.list.d/*' for reading: No such file or directory

```

---

### Post by Bashing-om on 2014-08-28
gregor9; Well !

I agree;
Beside the fact that there is no graphics driver loaded; I too see no faults.

Let's see what the package manager thinks:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

```
As we prepare for
[INDENT][INDENT][INDENT]that giant leap forward
[/INDENT][/INDENT][/INDENT]

---

### Post by gregor9 on 2014-08-29
Done.

```
root@odin:/# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Bashing-om on 2014-08-29
gregor9; Well !

Again, looks good, package manager appears to be in a happy state.
Let's do this and see:
```

sudo do-release-upgrade

```
and post the output. In context perhaps we can see what the choke point is.

[INDENT][INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT][/INDENT]

---

### Post by gregor9 on 2014-09-01
How can I capture the output. I tried redirecting result to file but no success.

---

### Post by Bashing-om on 2014-09-01
gregor9;

I had in mind to just copy and paste.
See:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by gregor9 on 2014-09-02
Here is last few lines when upgrade crashes.

```
Installing new version of config file /etc/ldap/schema/amavis.schema ...
Installing new version of config file /etc/cron.d/amavisd-new ...
Creating/updating amavis user account...
Starting amavisd: amavisd-new.
Setting up libauthen-sasl-perl (2.1500-1) ...
Setting up pflogsumm (1.1.5-1) ...
Setting up pkg-php-tools (1.11) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up python-software-properties (0.92.37.1) ...
Setting up sa-compile (3.4.0-1ubuntu1) ...
Running sa-compile (may take a long time)
invoke-rc.d: unknown initscript, /etc/init.d/spamassassin not found.
dpkg: error processing package sa-compile (--configure):
 subprocess installed post-installation script returned error exit status 100
No apport report written because MaxReports is reached already
                                                              Setting up kbd (1.15.5-1ubuntu1) ...
Setting up mysql-server (5.5.38-0ubuntu0.14.04.1) ...
Setting up ubuntu-minimal (1.325) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
Processing triggers for ca-certificates (20130906ubuntu2) ...
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....done.
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-35-generic
Processing triggers for php5-fpm (5.5.9+dfsg-1ubuntu4.3) ...
php5-fpm stop/waiting
php5-fpm start/running, process 11735
Processing triggers for sgml-base (1.26+nmu4ubuntu1) ...
Processing triggers for dovecot-core (1:2.2.9-1ubuntu2.1) ...
Errors were encountered while processing:
 sa-compile
Error in function:


A fatal error occurred

Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. The upgrade has aborted.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.

SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)



*** Send problem report to the developers?

After the problem report has been sent, please fill out the form in the
automatically opened web browser.

What would you like to do? Your options are:
  S: Send report (526.9 KB)
  V: View report
  K: Keep report file for sending later or copying to somewhere else
  I: Cancel and ignore future crashes of this program version
  C: Cancel
Please choose (S/V/K/I/C):

```

---

### Post by Bashing-om on 2014-09-02
gregor9; Welp;

I read it that the upgrade is chocking on "spamassissin" (  sa-compile ) .
> 
Package sa-compile

trusty (14.04LTS) (mail): Tools for compiling SpamAssassin rules into C 
3.4.0-1ubuntu1: all


How 'bout we try and remove it ? See if then the upgrade will progress ?
```

sudo apt-get remove --purge spamassassin

```
as we have:
> 
invoke-rc.d: unknown initscript, /etc/init.d/spamassassin not found.

And (RE-)install later .


[INDENT][INDENT]looks reasonable to me
[/INDENT][/INDENT]

---

### Post by gregor9 on 2014-09-03
It worked. I removed spamassassin and reinstalled after upgrade. Thanks for help!

---

### Post by Bashing-om on 2014-09-03
gregor9; Great !

As you are now up on 14.04 Please mark this thread solved - top of post -> thread tools .

Pleased it has worked out.

[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

