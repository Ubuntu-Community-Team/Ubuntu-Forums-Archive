---
title: "[SOLVED] SELinux disabled at boot?"
date: 2007-08-23
forum: Server Platforms
---

### Post by southernman on 2007-08-23
I was scanning some log messages and found it odd to see: SELinux disabled at boot. So I dug into dmesg and found it there too.

I then ran whereis SELinux and got nothing back... just dumped me back to the prompt.

One would think that even a default server installation would have selinux compiled into the kernel and the required packages installed... wouldn't one? :p

None the less, it isn't on my system. Will I need to recompile the kernel and add it in, or do I just need to install the packages.

FWIW, I also checked out [this thread]("http://ubuntuforums.org/showthread.php?t=507136") with no conclusion found therein.

Thank you!

Edited -
Running 6.06.1 server
System Specs:
Dell Dimension v350 (PII 350)
which of course exceeds the ACPI cutoff of 2000! :p

---

### Post by southernman on 2007-08-23
After a little more digging I see that it is compiled into the kernel according to the config file however, this line concerns me:

CONFIG_SECURITY_SELINUX_BOOTPARAM_VALUE=0

---

### Post by ruibernardo on 2007-08-23
Hi southerman,

I'm not a great helper about your question. I've never installed SElinux in Dapper and, as you could see in the thread you pointed, couldn't help, but at least I give you the little I know about it.

in Dapper the installation of SElinux is a bit complicated, as its integration [was declined for Dapper]("https://blueprints.launchpad.net/ubuntu/+spec/selinux"). But in the following releases, SElinux can be installed in an easer way.
 
The kernel options for it are already compiled [since Ubuntu 5.10 Breezy]("https://wiki.ubuntu.com/SELinux") ([although it was planed to Hoary]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/13502/comments/6")), but the SElinux package installation was a bit complicated until 6.10 Edgy arrived. 

Check [this thread]("http://ubuntuforums.org/showthread.php?t=521534") about SElinux on  7.04 Feisty (did not tested it but should work on 6.10 Edgy too).

SElinux in Dapper is an unanswered question in this forum. It would be great that you, if you get it to work, or somebody that got it to work, to reply a solution.

---

### Post by southernman on 2007-08-23
Hi there epimeteo,

I appreciate your reply none-the-less... it does help to some extent. Doing an apt-cache search pulls 14 packages (various but all relating to SELinux). I'll do some more digging around the internet and the links you gave. IF nothing more turns up definitively, I'll do another backup and install what is in the repos now to give it a try.

If I come up with anything important or not, I'll post back with the findings.

Thanks again.

---

### Post by southernman on 2007-08-23
Well, the only thing I found really quick was [this]("http://www.cse.psu.edu/~lstclair/Howtos/selinux_on_ubuntu.html"). Looks (reads as) as if the Ubuntu teams are leaning more towards AppArmor although it seems as if they are still working to get SELinux in order as well.

One mailing list I read through talked about (at the breezy stage) it would take a year or more to get policy working properly. Of course there were some rather heated exchanges mixied in... that was the crux of the end results.

No worries.. We'll survive! ;)

---

### Post by ruibernardo on 2007-08-24
Yeah, you're right, we will survive :)

The link you posted is the "complicated" way to install selinux (and it refers to post-dapper versions of Ubuntu, as it talks about upstart).

I took a deep cup of coffee and installed Dapper on a vmware machine, just to try.

The "easy" way to get SElinux working on Dapper is more or less this.

1. Edit the file /boot/grub/menu.lst and on the line that starts with "# kopt=", add "selinux=1 permissive=1". Save and exit.

2. Run "sudo update-grub" to update grub kernel options.

3. Install the packages "checkpolicy policycoreutils selinux-utils".

4. Restart.

5. Install the policy package: selinux-policy-default. In the end of the installation of the package, it will relabel the files and if you type "sestatus", the output says it's working.

But that's it. If you reboot, you will get the error of the thread [http://ubuntuforums.org/showthread.php?t=507136](http://ubuntuforums.org/showthread.php?t=507136)

I saw a message saying "NB if you use an initrd you may need to recreate it before rebooting.". I've installed the package "initrd-tools" and run "sudo update-initramfs -u -k $(uname -r)" to update the initrd, rebooted and selinux was gone.

SElinux on Dapper is a dead end, folks. If you really want to use a Ubuntu server with SElinux, I advise you not to use Dapper. Instead use Feisty and wait until the next LTS (gusty+1 / 8.04) comes up.

To me too, this Dapper/SElinux thing is "solved".

---

### Post by southernman on 2007-08-24
Thanks for the update.

---

