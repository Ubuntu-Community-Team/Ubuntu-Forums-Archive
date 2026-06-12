---
title: "panp4i Jaunty upgrade: Broken dpkg status"
date: 2009-04-29
forum: System76 Support
---

### Post by phyzome on 2009-04-29
I dist-upgraded my panp4i from Intrepid to Jaunty last night, which went smoothly. Then I noticed an upgrade for kipi-plugins. When I tried to upgrade, I got several messages. Synaptic said, on startup:
```
W: Encountered status field in a non-version description
```
And then when I tried to apply marked changes, I got a failure message:
```
dpkg: parse error, in file `/var/lib/dpkg/status' near line 448 package `libpth20':
 newline in field name `Vinstalled'
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 448 package `libpth20':
 newline in field name `Vinstalled'
```
Replacing the /var/lib/dpkg-status file with /var/lib/dpkg/status-old just makes dpkg segfault, so I rolled that forward again. (I assume it is dpkg, because both apt and Synaptic are segfaulting.)

[LIST][*] I updated my backup of my system from before the upgrade (though I forgot to use --delete in the rsync command, so I may have some extra files I don't want -- shouldn't hurt, right?), so I could revert everything. (Do I include /sys and /dev in the restore?)
[*] I could wipe the drive, install Jaunty, copy in my home folder again, and try to migrate my Apache and MySQL folders as well. (How would I get my old applications back, besides piecemeal?)
[*] Alternatively, can I somehow fix dpkg? Synaptic does allow me to generate a full listing of installed files.[/LIST]

---

### Post by thomasaaron on 2009-04-29
It could just be that particular update that is hosing stuff. If...

sudo apt-get clean

...doesn't fix it, you may try re-installing dpkg...

sudo apt-get --reinstall install dpkg

I googled the error, and it has popped up occasionally in various Ubuntu versions. Are you running KDE? It seems to pop up mostly with Kubuntu.

---

### Post by phyzome on 2009-04-29
> **thomasaaron said:**
> sudo apt-get clean

The problem remains.

> **thomasaaron said:**
> sudo apt-get --reinstall install dpkg

Tried, but can't, because dpkg itself is in a broken state.

> **thomasaaron said:**
> I googled the error, and it has popped up occasionally in various Ubuntu versions. Are you running KDE? It seems to pop up mostly with Kubuntu.

Nope, regular ol' Ubuntu.

---

### Post by thomasaaron on 2009-04-29
This isn't perfectly clear...

[http://ubuntuforums.org/showthread.php?t=103683](http://ubuntuforums.org/showthread.php?t=103683)

...but you might want to try what that guy tried.

---

### Post by phyzome on 2009-04-29
> **thomasaaron said:**
> This isn't perfectly clear...

[http://ubuntuforums.org/showthread.php?t=103683](http://ubuntuforums.org/showthread.php?t=103683)

...but you might want to try what that guy tried.

What do you think might happen if I remove random packages from dpkg's status file, as suggested by that thread?

For clarity, here's one of the malformed entries:

```
Package: libpth20
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 200
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: pth
Version: 2.0.7-12
Depends: libc6 (>= 2.4)
Description: The GNU Portable Threads
 Pth is a very portable POSIX/ANSI-C based library for Unix platforms which
 provides non-preemptive priority-based scheduling for multiple threatu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: exim4
Vinstalled
Priority: stan address space of the server application, but each thread has its own
 individual program-counter, run-time stack, signal mask and errno variable.
Original-Maintainer: Daniel Baumann <daniel@debian.org>
Homepage: http://www.gnu.org/software/pth/
```

Notice the line "Vinstalled". That's what dpkg barfs on. I think it's the beginning of a "Version" line followed by the end of a "Status" line. The next line appears to be a mix of Priority and Description.

---

### Post by phyzome on 2009-04-29
I tried removing some pieces, but I think there are a *lot* of them. The first was on line 405, the next on 448, and the one after that on 505. For comparison, the file has 47958 lines.

Also, for each chunk I remove, Synaptic gets more and more buggered. The "intelligent package management" can't cope with a broken state.

---

### Post by thomasaaron on 2009-04-29
Here's what mine says for libpth20. Maybe we can just work through them one at a time...

> Package: libpth20
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 200
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: pth
Version: 2.0.7-12
Depends: libc6 (>= 2.4)
Description: The GNU Portable Threads
 Pth is a very portable POSIX/ANSI-C based library for Unix platforms which
 provides non-preemptive priority-based scheduling for multiple threads of
 execution ("multithreading") inside server applications. All threads run in the
 same address space of the server application, but each thread has its own
 individual program-counter, run-time stack, signal mask and errno variable.
Original-Maintainer: Daniel Baumann <daniel@debian.org>
Homepage: [http://www.gnu.org/software/pth/](http://www.gnu.org/software/pth/)

---

### Post by thomasaaron on 2009-04-29
Actually, my status file is attached. You can go through it and use the sections you need.

---

### Post by phyzome on 2009-04-29
> **thomasaaron said:**
> Here's what mine says for libpth20. Maybe we can just work through them one at a time...

Maybe... Here's the next one:

```
Package: exim4-config
Status: install ok installed
Priority: standard
Section: mail
Installed-Size: 1116
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: exim4
Version: 4.69-9ubuntu1
Provides: exim4-config-2
Depends: debconf (>= 0.5) | debconf-2.0, adduser
Conflicts: bash (<< 2.05), courier-mta, esmtp-run, exim, exim-tls, exim4-config, exim4-config-2, exim4-daemon-heavy (<< 4.63), exim4-daemon-light (<< 4.63), hula-mta, masqmail, mta-dummy, nullmailer, postfix, sendmail-bin, smail, ssmtp, xmail, zmailer
Conffiles:
 /etc/exim4/conf.d/auth/00_exim4-config_header d0ee6ea0b33d9796573bb024ffca20d4
 /etc/exim4/conf.d/auth/30_exim4-config_examples 3baef800f00e84410f48c19ccdc2be30
 /etc/exim4/conf.d/main/03_exim4-config_tlsoptions 52bc867dd1e7b20deeb6aa548697d845
 /etc/exim4/conf.d/main/90_exim4-config_log_selector 888348df8f7bd25a0a77d3c05e8fffe3
 /etc/exim4/conf.d/main/02_exonf.d/transport/30_exim4-config_address_reply 9145131105953b0125a228.d/main/01_exim4-config_listmacrosdefs 9ce2f129b98e90b1ebbfa04979b4a335
 /etc/exim4/conf.d/retry/00_exim4-config_header 309f5bf0859ad91e03c5402d6afe6895
 /etc/exim4/conf.d/retry/30_exim4-config e4d46ad94d28d86e58d673a7562880a5
 /etc/exim4/conf.d/acl/20_exim4-config_local_deny_exceptions 516070107501d48a3106d755cb199e95
 /etc/exim4/conf.d/acl/40_exim4-config_check_data d34675c84115949a319b8cd9b4b99029
 /etc/exim4/conf.d/acl/00_exim4-config_header e572a7b9954b20950242db2a92b35044
 /etc/exim4/conf.d/acl/30_exim4-config_check_rcpt a929c526674c4ab42d85debbd2cc3731
 /etc/exim4/conf.d/acl/30_exim4-config_check_mail 715076d5c3a365a6b38425e478fdca83
 /etc/exim4/conf.d/rewrite/00_exim4-config_header d98361da23f34490d191bf2280728dec
 /etc/exim4/conf.d/rewrite/31_exim4-config_rewriting f232e855810d98a45ede134b369faa53
 /etc/exim4/conf.d/transport/30_exim4-config_mail_spool a0f0997e4f06f38afdae0ee79759dfea
 /etc/exim4/conf.d/transport/35_exim4-config_address_directory c2a777e8db8fac4f83c2da0c95952598
 /etc/exim4/conf.d/transport/30_exim4-config_maildir_home 3edfd11b8e9a8919a9a14cbc24637d68
 /etc/exim4/conf.d/transport/00_exim4-config_header 9568ac286553a79b8447c9060fed7798
 /etc/exim4/conf.d/transport/30_exim4-config_address_reply 9145131105953b0125a228ab9b7c6500
 /etc/exim4/conf.d/transport/30_exim4-config_remote_smtp_smarthost e2fbeeeaa7588d1773404f82750402f9
 /etc/exim4/conf.d/transport/30_exim4-config_procmail_pipe 82379d31ca4bf60d9667f408cb55dbbf
 /etc/exim4/conf.d/transport/30_exim4-config_remote_smtp 69955bc4a4999f6f85900a17ccecdf7d
 /etc/exim4/conf.d/transport/30_exim4-config_address_file fe97ddf4165820356e90c05fa744f796
 /etc/exim4/conf.d/transport/10_exim4-config_transport-macros 903d7e9fdbf74069f735a7e67a6a79aa
 /etc/exim4/conf.d/transport/30_exim4-config_address_pipe dfcd9d71f1bb4c55ac29cccead29117e
 /etc/exim4/conf.d/transport/30_exim4-config_maildrop_pipe e04895ab4184472a270ff229de8fbfd3
 /etc/exim4/conf.d/router/800_exim4-config_maildrop ba5474_header c0ecc395e9a49487b484126cac4d9559
 /etc/exim4/conf.d/router/3router/30a5e4f6e23
 /etcc7fc1ba66325f116e
 /etc/exim4/conf.d/router/700_exim4-config_procmail 28ddff8000ba5577c60eed8fabb520b4
 /etc/exim4/conf.d/router/00_exim4-config_header c0ecc395e9a49487b484126cac4d9559
 /etc/exim4/conf.d/router/300_exim4-config_real_local 07c6277988b181918f790ffe68c245da
 /etc/exim4/conf.d/router/100_exim4-config_domain_literal 1c4d00a933df2dcc18b1d0e4a3a4bc3d
 /etc/exim4/conf.d/router/400_exim4-config_system_aliases 7dc0cee575163f1d9761f1cf317f8299
 /etc/exim4/conf.d/router/mmm_mail4root 8a16022dfc39cae4f508dfab20a8f760
 /etc/exim4/conf.d/router/600_exim4-config_userforward 2c63dff568fb6c984c5e4aa3d8142cd8
 /etc/exim4/conf.d/router/900_exim4-config_local_user 20c8ced8346125170242584e575a95ff
 /etc/exim4/conf.d/router/150_exim4-config_hubbed_hosts 1d4a3bab1738f10f931b73ad60c7bb8d
 /etc/exim4/conf.d/router/500_exim4-config_hubuser 42b9467ce27b51394e7eaf3631173728
 /etc/exim4/conf.d/router/200_exim4-config_primary 0ef918a08fe84cc7155c7984559fb35b
 /etc/exim4/passwd.client 4b0013712a87d147c8303fa761e3c771
 /etc/exim4/exim4.conf.template 660c1d28c5ba0a8e4021ee0a5e4f6e23
 /etc/ppp/ip-up.d/exim4 5f4b9cb6696117b19b32aaa8fa7a6de2
 /etc/email-addresses 6bea09fbb18e4676012105fa5fc726c6
Description: configuration for the Exim MTA (v4)
 Exim (v4) is a mail transport agent. exim4-config provides the configuration
 for the exim4 daemon packages. The configuration framework has been split
 off the main package to allow sites to replace the configuration scheme
 with their own without having to change the actual exim4 packages.
 .
 Sites with special configuration needs (having a lot of identically
 configured machines for example) can use this to distribute their own
 custom configuration via the packaging system, using the magic
 available with dpkg's conffile handling, without having to do local
 changes on all of these machines.
 .
 The Debian exim4 packages have their own web page,
 http://pkg-exim4.alioth.debian.org/. There is also e built. The
 very extensive upstream documentation is shipped in
 /e/README.Debian.gz, whican be found in
 /usr/share/doc/exim4-base/README.Debian.gz, which additionally contains
 information about the way the Debian binary packages are built. The
 very extensive upstream documentation is shipped in
 /usr/share/doc/exim4-base/spec.txt.gz. To repeat the debconf-driven
 configuration process in a standard setup, invoke dpkg-reconfigure
 exim4-config. There is a Debian-centered mailing list,
 pkg-exim4-users@lists.alioth.debian.org. Please ask Debian-specific
 questions there, and only write to the upstream exim-users mailing
 list if you are sure that your question is not Debian-specific. You
 can find the subscription web page on
 http://lists.alioth.debian.org/mailman/listinfo/pkg-exim4-users
 .
  Homepage: http://www.exim.org/
Homepage: http://www.exim.org/
Original-Maintainer: Exim4 Maintainers <pkg-exim4-maintainers@lists.alioth.debian.org>

```

---

### Post by thomasaaron on 2009-04-29
I attached my status file above.

---

### Post by phyzome on 2009-04-29
Well, now it's crashed hard: The disk went read-only, and on reboot Grub complains about the filesystem*.  I think the hard drive was corrupted, which caused all of this. (Come to think of it, fsck caught and supposedly fixed some problems just after dist-upgrade rebooted the machine.)

I guess I'll give you a call.

* Grub fails to bring up the bootloader menu, and instead drops me to grub-shell. I enter `root (hd0,0)`, then attempt to tab-complete `kernel /boot/...`, but I get "Error 2: Bad file or directory type".

---

### Post by thomasaaron on 2009-04-29
I'd use a Live CD to see if you can still mount the partition and rescue your data.

---

### Post by phyzome on 2009-04-29
> **thomasaaron said:**
> I'd use a Live CD to see if you can still mount the partition and rescue your data.

I was able to mount my home partition and update that part of the backup. (Wasn't much new, and I didn't need anything from the OS partition.)

I tried to put a fresh Jaunty install on the disk, but it failed, saying there were errors on either the CD or the hard drive.

I ran badblocks against the OS partition, and it found errors.

I ran an integrity check on the CD, and that's fine.

So, what's next, a new hard drive? :-/ Or should I hope that this is not a sign of doom, and try installing again now that badblocks has had a go?

---

### Post by thomasaaron on 2009-04-29
I'd try installing one more time. If that doesn't work... hard drive.

---

### Post by phyzome on 2009-04-29
> **thomasaaron said:**
> I'd try installing one more time. If that doesn't work... hard drive.

Oh, right! Because badblocks has done its work now.

I tried one last time... and it worked!

I'm still having the original problem that led to the one I posted about at the top of this thread, but I see the solution is coming down the pipeline. (Something about kipi-plugins and libkipi0 vs. libkipi6.)

---

### Post by phyzome on 2009-04-30
Well, /dev/sda3 just reported fsck errors (and .bashrc had a "stale NFS file handle".) I restarted, and was dropped into BusyBox. (Mounting /root "failed Stale NFS file handle" & later "Target filesystem doesn't have /sbin/init.")

So... it's gotta be a dead/dying hard drive, OR horribly broken OS code that is smashing random pieces of the filesystem.

---

### Post by thomasaaron on 2009-04-30
Since I've not seen this on any other machines (particularly with a fresh install), I'm voting for a drive that's about to go belly up. 

You're probably still under warranty, right? If so...

Please fill out this brief online form. It goes straight to my inbox and will provide me with the information necessary to proces warranty requests and repair estimates...

[http://system76.com/article_info.php?articles_id=39](http://system76.com/article_info.php?articles_id=39)

---

### Post by phyzome on 2009-05-09
Received the new hard drive, installed and restored. Gonna wipe and send off the old one tonight or tomorrow.

---

