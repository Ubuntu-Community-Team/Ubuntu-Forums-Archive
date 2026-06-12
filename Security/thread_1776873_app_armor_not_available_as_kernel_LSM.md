---
title: "app armor not available as kernel LSM"
date: 2011-06-06
forum: Security
---

### Post by toolmania1 on 2011-06-06
I had SELinux installed.  I installed app armor like so:

sudo apt-get install app armor

I saw that some SELinux items were to be removed.  I read this in one of Bodhi's posts also.  So, I continued.  I rebooted.  I still cannot start app armor now using this:

sudo /etc/init.d/apparmor start

I get the error message that "apparmor not availble as kernel LSM"

I googled that message and found some closed and new bugs.  The bugs did mention not being able to run SELinux and apparmor at the same time.  I, however, thought that when AppArmor was installed, that SELinux was removed.  Any ideas?

On this page, the first entry is what I saw:

[http://ubuntuforums.org/archive/index.php/t-1063667.html](http://ubuntuforums.org/archive/index.php/t-1063667.html)

---

### Post by toolmania1 on 2011-06-07
[FONT=Calibri]I ended upreinstalling Ubuntu for a second time.  Ihad trouble getting rid of Selinux.  WhenI installed AppArmor, like Bodhi said in one of his posts, SELinux was markedas automatically removed.  But, I am notsure that it was.  When I googled, Ifound many posts that showed issues with removing SELinux and then installing AppArmor. I also found a site that listed the same output I had.  Something about having 0 items installed orit finding 0 items for SELinux when I tried to remove it.  Yet, when I did remove[/FONT]
[FONT=Calibri] [/FONT]
[FONT=Calibri]Sudo apt-get removeselinux[/FONT]
[FONT=Calibri] [/FONT]
[FONT=Calibri]I went through themotions like it was being removed.  So, Idecided to just scrap that install and start over as something did not seemcorrect.  I don't like to keep going at thatpoint.  With google and forums like this,I should be able to understand everything that is happening and I should beable to know that it is correct ( ideally anyways…lol )[/FONT]
[FONT=Calibri]
[/FONT]
[FONT=Calibri]I am not going to install SELinux this time.  I will just install AppArmor.
[/FONT]

---

### Post by dragin33 on 2012-09-07
I got this error after trying to install SELinux on Ubuntu.  I found out that it's more supported to just stick with AppArmor so I tried to uninstall SELinux and reinstall Apparmor.  At that point I got this error.

To Resolve:
First uninstall both selinux and apparmor

I had to edit /etc/default/grub
Where it said security=selinux ; change it to security=apparmor
where is said selinux=1 ; change it to apparmor = 1

reinstall apparmor

---

### Post by cariboo on 2012-09-07
Apt-get remove, only removes the package files. When trying to completely remove a package, either use:

```
apt-get purge <package-name>
```

From man apt-get

> remove
           remove is identical to install except that packages are removed
           instead of installed. Note that removing a package leaves its
           configuration files on the system. If a plus sign is appended to
           the package name (with no intervening space), the identified
           package will be installed instead of removed.

> purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).

Or put your geek pride away and use synaptic instead of the command line. :)

---

