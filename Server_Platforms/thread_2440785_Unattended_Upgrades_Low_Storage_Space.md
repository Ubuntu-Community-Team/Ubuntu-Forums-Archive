---
title: "Unattended Upgrades: Low Storage Space"
date: 2020-04-15
forum: Server Platforms
---

### Post by richmbx on 2020-04-15
This is an issue we have been dealing with for some time. Every once in a while we have a server that has an alert that it is running low on disk storage in the /boot partition. When we connect to that system the quickest solution is to do an apt-get autoremove even though we have "Unattended-Upgrade::Remove-Unused-Dependencies "true";" set in /etc/apt/apt.conf.d/50unattended-upgrades. This issue usually occurs with one or two systems a month out of 80+.

Resources we have looked into:
[https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093)
[https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1675079](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1675079)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

We are using Xenial. This most recent system the happened with appears to be an upgrade from Trusty.

After resolution:
> apt-mark showauto 'linux-image-.*'
Show 3 kernels, which I believe is normal. (currently linux-image-4.4.0-176-generic,linux-image-4.4.0-177-generic, linux-image-generic)

> apt-mark showmanual 'linux-image-.*'
Does not show any results.

Like I mentioned, running apt-get autoremove works almost every time. There have been a few instances where packages were broken due to low storage in the /boot directory which needs to be cleaned manually. But unless there was an error there, I would think the unattended-upgrade process would also work.

Is there something I am missing?

---

### Post by TheFu on 2020-04-15
> **richmbx said:**
> 
Is there something I am missing?

We only use 16.04 in production here. We do not auto patch, ever.  Have been burned too many times, so I get up early on Saturdays and run a script that patches all our systems. An incorrect package dependency once removed MariaDB and installed MySQL. That took down our project management server.  Took me a few hours to figure out what happened.  Never, freakin', again!

About once a month, I'll run a different script that does autoremove and autoclean.  During the install, we force /boot/ to be larger than the default size too.
```
/dev/sdb1                         ext2  **720M**  252M  432M  37% /boot

```

Here's the default size:
```
/dev/sdb2                                    ext2  **237M**  105M  120M  47% /boot
```
I need to fix that box. 237MB is just too small.

You could remove file system packages that you don't use. No need for ZFS or brtfs if you don't use those. They just add bloat to the initrd.img files.  

Googling for other options ...
[https://unix.stackexchange.com/questions/270390/how-to-reduce-the-size-of-the-initrd-when-compiling-your-kernel](https://unix.stackexchange.com/questions/270390/how-to-reduce-the-size-of-the-initrd-when-compiling-your-kernel) has some options for reducing the size even if you don't build your own kernels.  
> after all optimizations the size came down from 282 MB to 16 MB!! 
So stripping the unneeded kernel-module symbols and modifying the /etc/initramfs-tools/initramfs.conf can drastically reduce the needed space in /boot/.  I haven't tried either.  Need to try it on a test, non-used system first before I'd touch any production systems.

---

### Post by richmbx on 2020-04-15
I think the issue lies more in line with a bug, order of operations, or a setting. 

The link you posted describes how to compile a kernel which I don't want to go down that road and maintain future patches with our other Ubuntu nodes. The boot size of 237M does seem incredibly small but that is also a default setting that the Ubuntu install imposes - which may not really be an issue if old kernels would get removed like most Ubuntu documentation states.

Aside from the valid concerns and risks associated with automatically removing packages, with this particular exception type, we have good luck with it. I should add, we also use Puppet to ensure specific packages and configuration settings are setup. Additionally, our environment is mostly virtual machines with little or no unique hardware that might require dkms or manual compiles to get modules built in.

The following reasons for a kernel to not get removed seem pretty reasonable (please correct me if I am wrong here or if anything is missing):

[LIST]
[*]Pinned or marked kernel packages set to not be removed
[*]Manually installed
[*]Booted into kernel that is being removed
[*]Errors during update
[*]/etc/apt/apt.conf.d/50unattended-upgrades has [COLOR=#24292E][FONT=SFMono-Regular]Unattended-Upgrade::Remove-Unused-Kernel-Packages uncommented [/FONT][/COLOR]and set to [COLOR=#032F62][FONT=SFMono-Regular]"false"
[/FONT][/COLOR]
[/LIST]
[COLOR=#032F62][FONT=SFMono-Regular]
[/FONT][/COLOR]However, if any of the above were the reason the kernel did not get removed, I would think running apt-get autoremove would also not remove old kernels - which it did.

For reference, this system is running unattended-upgrades 1.1ubuntu1.18.04.7~16.04.6.

---

### Post by TheFu on 2020-04-15
puppet? I'd just automate it.

---

### Post by LHammonds on 2020-04-16
I configure all my servers to NOT use the built-in unattended upgrade schedule.

Instead, I [wrote my own script]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p622") that does the repository update, install and cleanup along with logging everything that it does so if something goes sideways, I can check the log to see what was applied and when.

But if the only problem you are really having is needing the autoremove to run, just schedule that in crontab to run daily.

**EDIT:** Fixed typo "autoclean" -> "autoremove"

LHammonds

---

### Post by richmbx on 2020-04-17
:confused:

I would like to establish whether it is a configuration issue on my end or a bug. 

> **TheFu said:**
> puppet? I'd just automate it.

Puppet is used for automation. Puppet is a configuration management tool that is used for deploying, configuring, and managing servers. For the most part Puppet *is* automation.

> **LHammonds said:**
> 
But if the only problem you are really having is needing the autoclean to run, just schedule that in crontab to run daily.
LHammonds

Autoclean clears the local repository of retrieved package files, but it only removes files that can no longer be downloaded and are useless. I am uncertain how autoclean would resolve anything here. I ran autoremove and it was able to remove the kernel packages. There was not an attempt at using autoclean before hand.



Again, I would like to establish whether it is a configuration issue on my end or a bug. It *seems* like a bug since the documents I have read indicate that it should work the way it is currently configured. It doesn't make sense to circumvent the problem by writing scripts around it or my lack of understanding unless it is a last resort.

---

### Post by TheFu on 2020-04-17
I'm familiar with puppet. That's why it was a suggestion.

Nobody here works for Canonical.  

We are practitioners volunteering suggestions for what may work.  

Calling something a bug doesn't prevent the problem and doesn't mean it will ever be fixed.  If I wanted to find someone with direct Canonical access, I'd use IRC on the #ubuntu-server channel and be patient for a response a few hours.  Then I'd open a bug in landscape for them to explain, track or close.  [https://help.ubuntu.com/lts/serverguide/reporting-bugs.html](https://help.ubuntu.com/lts/serverguide/reporting-bugs.html)

Google found this setting, specific to kernel cleanup in /etc/apt/apt.conf.d/50unattended-upgrades

```
Unattended-Upgrade::Remove-Unused-Kernel-Packages "true";
```
I didn't test it. You've probably seen that setting already.
[https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1267059](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1267059) is still open, so it is doubtful it will ever be fixed for 16.04. A workaround is the only viable option, it seems.

---

### Post by LHammonds on 2020-04-20
> **richmbx said:**
> Autoclean clears the local repository of retrieved package files, but it only removes files that can no longer be downloaded and are useless. I am uncertain how autoclean would resolve anything here. I ran autoremove and it was able to remove the kernel packages. There was not an attempt at using autoclean before hand.
Sorry, that was a typo.  I corrected it.

LHammonds

---

### Post by richmbx on 2020-04-24
Thank you for your help. I think I have a work around for this per your suggestions. I ended up placing a file in kernel/postinst.d/ to run autoremove after kernel operations completed. 

The order of operations seems to be the cause of my issue with the additional factor that the /boot partition size is unusually small on many systems compared to recent Ubuntu installations. Most, I suspect newer, installs have 510M for the boot partition. On the problem systems it is around 230M. 
Order of operations as follows:
1. unattended-install script is run
2. removes packages found in /etc/kernel/postinst.d/apt-auto-removal
3. Installs new kernel
4. creates new /etc/kernel/postinst.d/apt-auto-removal

At this point it does not remove any old packages after the new kernel is installed. However, when unattended-install is run a second time it will remove those packages. This seems like an awkward approach. Ideally, the old kernel packages would get removed the first run of unattended-install. I considered safety concerns in removing older kernels after an update but then it still gets removed on a second run without any checks in place that the new kernel is working (or even rebooted into new kernel). It is also possible there is a setting here that I overlooked that may check for those issues.

I applied a work around in kernel/postinst.d/zzz_autoremove to simply run apt-get autoremove -y a few seconds after kernel updates have completed. This approach is not ideal but functional for this potentially unique issue. That looks something like this:
```
#!/usr/bin/env bash
echo "Telling autoremove to run when existing process is complete."
(sleep 10 && apt-get autoremove -y)&

```

---

