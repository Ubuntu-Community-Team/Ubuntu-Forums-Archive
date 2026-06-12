---
title: "Remove SELinux (intrepid) and install apparmor"
date: 2009-02-08
forum: Security
---

### Post by arkticcool on 2009-02-08
I attempted to install SElinux on 8.10 ibex, and was successful with;

```
sudo apt-get install selinu
```

However it wasn't enabled. So I attempted to install a variety of SElinux policies such as 

```
sudo apt-get install selinux-policy-refpolicy
```

However this did not work as it could no longer locate the file in the repositories. Somehow, I can't remember exactly but I ended up installing a policy which changed the policy from refpolicy to mls.

I then typed in;

```
sestatus
```

and it showed the following;

```
SELinux status:                 disabled
```


I then viewed the config file;

```
sudo gedit /etc/selinux/config
```

And this is what it showed;

```
# This example is the file that controls the state of SELinux on the
# system.  It normally resides at /etc/selinux/config and must be
# updated whenever the policy changes.  Use the script
# /usr/sbin/update-selinux-config to change the policy type, and then
# reload the policy for changes to go into effect.

# SELINUX= can take one of these three values:
# enforcing - SELinux security policy is enforced.
# permissive - SELinux prints warnings instead of enforcing.
# disabled - No SELinux policy is loaded.
SELINUX=enforcing

# SELINUXTYPE= can take one of these two values:
# refpolicy-targeted - Only targeted network daemons are protected.
# refpolicy-strict   - Full SELinux protection.
# refpolicy-src      - Custom policy built from source
SELINUXTYPE=mls

# SETLOCALDEFS= Check local definition changes
SETLOCALDEFS=0

```

It states that it is in enforcing mode however sestatus states that it is disabled.

I then followed the instructions on [http://cjacobsen.net/?p=183](http://cjacobsen.net/?p=183) and install sysvinit;

```
sudo apt-get install sysvinit
```

And this is where my problems began. I can no longer reboot or shutdown properly in ubuntu, and whenever I try to remove SElinux;

```
sudo apt-get remove selinux
```

it states the following;

```
:~$ sudo apt-get remove selinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  selinux-utils
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  selinux
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 127kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 200299 files and directories currently installed.)
Removing selinux ...
/var/lib/dpkg/info/selinux.prerm: 55: /etc/init.d/selinux: not found
dpkg: error processing selinux (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 selinux
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How can I remove SElinux and reinstall apparmor.

---

### Post by arkticcool on 2009-02-08
HOLY CRAP!!!

I restarted my box with the restart button on the front because shutdown and reboot commands weren't being registered in terminal.

Boot up the latest kernel in recovery mode. It states it can't find/mount selinux, then states kernel panic, unable to sync.

Boot up an older kernel .9 not .11 and same thing, can't mount selinux and kernel panic.

Help please and fast.

Is there a way to reinstall Ubuntu without wiping the disk.

---

### Post by ptn107 on 2009-02-08
If your /home folder is on a separate partition then you can reinstall Ubuntu to the root '/' partition without losing your files.  Just make sure during the install process you don't format your /home.

---

### Post by movieman on 2009-02-08
I never got SELinux to work on Debian, so I presume it's a pain on Ubuntu too; I eventually put CentOS on that machine because it was the only distribution where I could get SELinux to work reliably.

If you do try to enable it again, the best method is to leave it disabled in the OS and manually set the enforcing state on the kernel line in grub when you reboot so that if there are problems you can simply reboot with it disabled; I wouldn't turn it on permanently in the OS configuration files until you've first verified that it will boot and run by adding it to the grub boot line.

For this particular case, did you label the file system at any point? My non-SELinux Ubuntu machine has no SELinux labelling on the files, so unless the installer labels the file system automatically then it won't have been done. Without that SELinux can't work.

---

### Post by movieman on 2009-02-08
Actually, you could try that anyway: I'm not sure whether disabling SELinux on the grub command line will keep it disabled after the system boots, but it's worth a go.

I think you just need to boot into grub and add selinux=disable (or maybe it's selinux=0) to the end of the boot line. Google should find the details on how to do it.

---

### Post by cjacobsen on 2009-02-08
> **arkticcool said:**
> HOLY CRAP!!!

I restarted my box with the restart button on the front because shutdown and reboot commands weren't being registered in terminal.

Boot up the latest kernel in recovery mode. It states it can't find/mount selinux, then states kernel panic, unable to sync.

Boot up an older kernel .9 not .11 and same thing, can't mount selinux and kernel panic.

Help please and fast.

Is there a way to reinstall Ubuntu without wiping the disk.

Had the same problem. Fixed it by booting up with a livecd, than deleted the directories /selinux and /etc/selinux

Then rebooted as normal, and it has worked ever since.

As I mentioned on my blog, I've never got SElinux working on Ubuntu 8.10. However, it works well on Ubuntu 8.04.

---

### Post by HermanAB on 2009-02-08
Unless you work for the government and you have to process data with different classification levels, SELinux is best avoided.

Cheers,

Herman

---

### Post by arkticcool on 2009-02-09
YES

To fix a bricked computer (kernel panic due to SElinux not mounting/being installed properly etc.) simply boot up 8.10 LiveCD then open up terminal and format your delete your ext3, linux-swap, and extended partition. (I backed up /home to another parition -- dual boot vista/Ubuntu). Then simply install Ubuntu again, using the option guided - use largest continuous space.

Learnt my lesson, don't mess with the kernel/stuff around it.

Yet anyway.

---

### Post by bodhi.zazen on 2009-02-09
My advice is to use AppArmor if you use Ubuntu.

If you wish to use SELinux, why not use Fedora or Centos ?

To remove SELinux I believe all you need do is sudo apt-get install apparmor

Since you can not run both selinux and apparmor at the same time, selinux will be removed.

I have also had problems installing SELinux on Ubuntu.

---

### Post by brandon88tube on 2009-02-10
Is it true that they are trying to integrate SElinux into future Ubuntu installs?

---

### Post by bodhi.zazen on 2009-02-10
> **brandon88tube said:**
> Is it true that they are trying to integrate SElinux into future Ubuntu installs?

No. Ubuntu uses Apparmor.

There is a security team on launchpad that has been working on selinux, but as has been mentioned several times on this thread selinux does not seem to work on 8.10. I have not tried it on 9.04 Alpha.

IMO id you wish to use Ubuntu you should learn apparmor. IMO if you want selinux go with Feodra or Centos (both very fine distros with both advantages and disadvantages).

---

### Post by brandon88tube on 2009-02-10
Just curious, because I didn't want to start learning AppArmor and then have SELinux take its place.

---

