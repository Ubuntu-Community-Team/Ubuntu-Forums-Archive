---
title: "apache2 not working after dist-upgrade"
date: 2005-08-25
forum: Server Platforms
---

### Post by istoyanov on 2005-08-25
Today I did a routine dist-upgrade on a Ubuntu server, but after the upgrade apache2 could not start again :(

Here is a log of the process:
```

Reading Package Lists... Done
Building Dependency Tree... Done
Calculating Upgrade... Done
The following packages will be upgraded:
  apache2 apache2-common apache2-mpm-worker gnupg libapr0 libpcre3
  linux-image-2.6.8.1-5-386
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.8MB/18.5MB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue? [Y/n]
<snip>
Fetched 15.9MB in 20m18s (13.0kB/s)

Preconfiguring packages ...
(Reading database ... 23508 files and directories currently installed.)
Preparing to replace libpcre3 4.5-1.1 (using .../libpcre3_4.5-1.1ubuntu0.4.10.1_i386.deb) ...
Unpacking replacement libpcre3 ...
Preparing to replace gnupg 1.2.4-4ubuntu2 (using .../gnupg_1.2.4-4ubuntu2.1_i386.deb) ...
Unpacking replacement gnupg ...
Preparing to replace libapr0 2.0.50-12ubuntu4.3 (using .../libapr0_2.0.50-12ubuntu4.4_i386.deb) ...
Unpacking replacement libapr0 ...
Preparing to replace apache2-mpm-worker 2.0.50-12ubuntu4.3 (using .../apache2-mpm-worker_2.0.50-12ubuntu4.4_i386.deb) ...
 * Stopping web server (Apache2)...                                      [ ok ]
Unpacking replacement apache2-mpm-worker ...
Preparing to replace apache2-common 2.0.50-12ubuntu4.3 (using .../apache2-common_2.0.50-12ubuntu4.4_i386.deb) ...
Unpacking replacement apache2-common ...
Preparing to replace apache2 2.0.50-12ubuntu4.3 (using .../apache2_2.0.50-12ubuntu4.4_i386.deb) ...
Unpacking replacement apache2 ...
Preparing to replace linux-image-2.6.8.1-5-386 2.6.8.1-16.20 (using .../linux-image-2.6.8.1-5-386_2.6.8.1-16.21_i386.deb) ...
The directory /lib/modules/2.6.8.1-5-386 still exists. Continuing as directed.
Unpacking replacement linux-image-2.6.8.1-5-386 ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.8.1-5-386.dpkg-tmp
Found kernel: /boot/vmlinuz-2.6.8.1-5-386
Found kernel: /boot/vmlinuz-2.6.8.1-4-386
Found kernel: /boot/vmlinuz-2.6.8.1-3-386
Updating /boot/grub/menu.lst ... done

Setting up libpcre3 (4.5-1.1ubuntu0.4.10.1) ...

Setting up gnupg (1.2.4-4ubuntu2.1) ...
Setting up libapr0 (2.0.50-12ubuntu4.4) ...

Setting up apache2-common (2.0.50-12ubuntu4.4) ...

Setting up apache2-mpm-worker (2.0.50-12ubuntu4.4) ...
 * Forcing reload of web server (Apache2)...
Syntax error on line 16 of /etc/apache2/conf.d/proxy.conf:
 *gex could not be compiled                                              [fail]
invoke-rc.d: initscript apache2, action "force-reload" failed.

Setting up apache2 (2.0.50-12ubuntu4.4) ...
Setting up linux-image-2.6.8.1-5-386 (2.6.8.1-16.21) ...
Not touching initrd symlinks since we are being reinstalled (2.6.8.1-16.20)
Not updating image symbolic links since we are being updated (2.6.8.1-16.20)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.8.1-5-386
Found kernel: /boot/vmlinuz-2.6.8.1-4-386
Found kernel: /boot/vmlinuz-2.6.8.1-3-386
Updating /boot/grub/menu.lst ... done

```

Line 16 of /etc/apache2/conf.d/proxy.conf is
```

<ProxyMatch http://localhost:[0-9]{2,}?[8|9]0/.*>

```

In the official announcement [http://ubuntuforums.org/showthread.php?t=59294](http://ubuntuforums.org/showthread.php?t=59294)
I found the following text, but I cannot understand what WOULD BE SUFFICIENT:
> 
A standard system upgrade is NOT SUFFICIENT to effect the necessary
changes! If you can afford to reboot your machine, this is the easiest
way to ensure that all services using this library are restarted
correctly. If not, please manually restart all server processes (exim,
Apache, PHP, etc.). It is advised to also restart your desktop
session.
I rebooted the machine, but apache didn't start as usual at boot, and after a ```
/etc/init.d/apache2 restart
``` I get ```
 * Restarting web server (Apache2)...
Syntax error on line 16 of /etc/apache2/conf.d/proxy.conf:
 *gex could not be compiled                                              [fail]

```
Is there a way to compile "gex" manually?

Any help wold be GREALY appreciated!!!

Thank you in advance!

---

### Post by gruepig on 2005-08-25
Hmm ... Try running '/usr/sbin/apache2 -t' to check your syntax.  It probably won't tell you anything new, but it couldn't hurt.  It sounds to me like either mod_proxy isn't loaded (check in /etc/apache2/mods-enabled/) or that the config syntax has changed between versions.

---

### Post by istoyanov on 2005-08-26
The output of ```
/usr/sbin/apache2 -t
``` is ```
Syntax OK
```

I also have "proxy.load" in /etc/apache2/mods-enabled.

BTW, I couldn't find anything about "compiling gex" on the web. Does anybody know what "gex" is?

Anyway, thanks **gruepig** for the reply!

---

### Post by gruepig on 2005-08-29
"gex" sounds suspiciously like the last three letters of "regex" to me, as in the regular expression for the proxymatch.

---

### Post by istoyanov on 2005-08-30
Anyway, after another routine apt-get dist-upgrade that said ```
The following packages will be upgraded:
  apache2 apache2-common apache2-mpm-worker libapr0
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

``` everything went back to normal :)

Cheers!

---

### Post by istoyanov on 2005-08-31
[http://ubuntuforums.org/showthread.php?goto=newpost&t=61020](http://ubuntuforums.org/showthread.php?goto=newpost&t=61020) describes everything :)

---

