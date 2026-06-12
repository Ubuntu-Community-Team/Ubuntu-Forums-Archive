---
title: "vboxdrv setup fails at compiling modules"
date: 2014-02-18
forum: Virtualisation
---

### Post by Rmy on 2014-02-18
Hello,

I have recently upgraded from 13.04, where everything worked fine, to 13.10, where I cannot get VirtualBox to work any more.
I did some googling but could not find a similar error (all involved explicit compilation issue against bad headers for example, but there seems to be nothing of the like in my situation?).

When trying to setup VirtualBox, I get the following:
> 
-> % sudo /etc/init.d/vboxdrv setup
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMSError! Bad return status for module build on kernel: 3.11.0-15-generic (x86_64)
Consult /var/lib/dkms/vboxhost/4.3.6/build/make.log for more information.
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)


Here are the logs:
vbox-install.log: [http://pastebin.com/6G2awxR5](http://pastebin.com/6G2awxR5)
make.log: [http://pastebin.com/BTXhMGgQ](http://pastebin.com/BTXhMGgQ)

Looking at neither of the mentioned logs revealed nothing useful to me. It seems that the .ko files are not getting generated which prevents the whole operation.
I have been trying both the "virtualbox" package of the ubuntu saucy repository:
> 
-> % apt-cache policy virtualbox
virtualbox:
  Installed: (none)
  Candidate: 4.2.16-dfsg-3
  Version table:
     4.2.16-dfsg-3 0
        500 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) saucy/multiverse amd64 Packages


And the "virtualbox-4.3" package of the specific virtualbox repository:
> 
-> % apt-cache policy virtualbox-4.3
virtualbox-4.3:
  Installed: 4.3.6-91406~Ubuntu~raring
  Candidate: 4.3.6-91406~Ubuntu~raring
  Version table:
 *** 4.3.6-91406~Ubuntu~raring 0
        500 [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) saucy/contrib amd64 Packages
        100 /var/lib/dpkg/status


...but both failed with the same errors.

I am currently running kernel 3.11.0-15:
> 
-> % uname -a
Linux 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Can I please get some help as to how solve this? How would you go about investigating this build issue? I have tried making my way in the Makefiles but it got complicated quite quickly and I'm sure I missed something obvious.

Thanks a lot!

---

### Post by jdeca57 on 2014-02-19
Just a tip, since nobody answers (probably because it always works), did you do apt-get update and upgrade recently? Because my kernel ends with 17 and is from Februari. It would really be strange if you had to modify Makefiles...

---

### Post by Rmy on 2014-02-19
Thanks for the tip!
I had a glimmer of hope when I saw an upgrade was available for the kernel to version 3.11.0-17 which I am now on.
However the error persists :(

---

### Post by Rmy on 2014-02-20
It looks like the failing part really is the end:
> 
root@x:/usr/src/linux-headers-3.11.0-17-generic# find /tmp/vbox.0/.tmp_versions -name '*.mod' | xargs -r grep -h '\.ko$' | sort -u | sed 's/\.ko$/.o/' | scripts/mod/modpost -m -a -i /usr/src/linux-headers-3.11.0-17-generic/Module.symvers -I /tmp/vbox.0/Module.symvers  -o /tmp/vbox.0/Module.symvers -S -w -s -T -
/tmp/vbox.0/vboxdrv.ko: No such file or directory


The funny thing is that the ".ko" characters are colored in the "/tmp/vbox.0/vboxdrv.ko: No such file or directory".

---

### Post by Rmy on 2014-03-06
> **Rmy said:**
> It looks like the failing part really is the end:


The funny thing is that the ".ko" characters are colored in the "/tmp/vbox.0/vboxdrv.ko: No such file or directory".
Hello :)

I did find the problem a little later on.
I had the *not so great idea* to add specify GREP_OPTIONS="--color=always" in my /etc/environment which is why I got colored output.
Unfortunately this colorization being done through special characters, they prevented the scripts from finding the actual file (they were looking for a file with the special characters :x).

Removing the variable did the trick!

---

### Post by Jorge_Palma on 2014-07-20
[FONT=Verdana][FONT=Trebuchet MS]Uninstall - you will not lose existing virtual machines and instances using:

# [COLOR=#38761D]**apt-get purge virtualbox**[/COLOR][/FONT][/FONT]
[FONT=Verdana]reinstall with the last version available: [/FONT]
[FONT=Verdana][FONT=Trebuchet MS]# **[COLOR=#38761D]apt-get install virtualbox-4.2[/COLOR]**[/FONT][/FONT]

---

### Post by QIII on 2014-07-20
13.10 is no longer supported.  Any help provided is moot at this point.

We no longer support threads requesting support for End Of Life (EOL) releases of Ubuntu.  Please see the sticky at [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730).

Thread closed.

---

