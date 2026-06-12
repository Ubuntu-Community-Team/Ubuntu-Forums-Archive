---
title: "Data from Rootkit Hunter. Do I need to take any action?"
date: 2018-02-11
forum: Security
---

### Post by anon_private on 2018-02-11
Data from Rootkit Hunter (Edited Data)

[01:53:36]   /usr/bin/curl                                   [ Warning ]

[01:53:38]   /usr/bin/ldd                                    [ Warning ]
[01:53:38] Warning: The file properties have changed:

[01:53:43]   /usr/bin/unhide.rb                              [ Warning ]
[
[01:53:45]   /sbin/ip                                        [ Warning ]
[01:53:45] Warning: The file properties have changed:
[
[01:53:48]   /bin/ip                                         [ Warning ]
[01:53:48] Warning: The file properties have changed:



[01:54:52]   Checking /dev for suspicious file types         [ Warning ]
[01:54:52] Warning: Suspicious file types found in /dev:
[01:54:52]          /dev/.udev/rules.d/root.rules: ASCII text
[01:54:52]   Checking for hidden files and directories       [ Warning ]

PS. Do I need to update this programme. If so, what is the method?

---

### Post by Habitual on 2018-02-12
Yes, you need to take action.
Great Question.
See [To avoid these warnings ]("https://help.ubuntu.com/community/RKhunter") section.

Also scour /etc/rkhunter.conf for very important tips,
like using your own rkhunter settings in /etc/rkhunter.conf.local

Step2: Verify output of /var/log/rkhunter.log 
"To avoid these warnings" will help.


The file properties have changed
indicate a couple of possibles:
You're hacked, or the more likely 
Someone ran an "apt-get" and updated some  software w\OUT running
rkhunter --propupd, afterwards.

---

### Post by anon_private on 2018-02-12
Thank you for responding.

I will read the link you have given.

I get the impression that these warnings are nothing to worry about.

Have I interpreted your response correctly?

Regards

---

### Post by anon_private on 2018-02-12
I note that my rkhunter.conf file has only one of the three (static) commands?


/var/log/rkhunter.log is empty

---

### Post by Habitual on 2018-02-13
When was the last time you ran rkhunter?
Where did
```
[01:53:48] /bin/ip [ Warning ]
[01:53:48] Warning: The file properties have changed:
``` come from?

Is it, or has it been configured?

I got the impression rkhunter was installed but the system has since had upgrades done to it since rkhunter was installed.

Unconfigured rkhunter will issue "Warnings" as per 
```
man rkhunter
```
DESCRIPTION:second paragraph

Does /etc/rkhunter have "more" than "3 static commands"? I read that as "has only 3 lines in it."
mine has > 40 uncommented directives. ;)

[https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter) as a resource.

---

### Post by anon_private on 2018-02-14
> **Habitual said:**
> When was the last time you ran rkhunter?
Where did
```
[01:53:48] /bin/ip [ Warning ]
[01:53:48] Warning: The file properties have changed:
``` come from?

Is it, or has it been configured?

I got the impression rkhunter was installed but the system has since had upgrades done to it since rkhunter was installed.

Unconfigured rkhunter will issue "Warnings" as per 
```
man rkhunter
```
DESCRIPTION:second paragraph

Does /etc/rkhunter have "more" than "3 static commands"? I read that as "has only 3 lines in it."
mine has > 40 uncommented directives. ;)

[https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter) as a resource.

1:53:48 came from the scan I did a few days ago.

I don't think it has been configured

Yes, upgrades from the repository have been installed whenever they have been issued, and certainly since rkhunter was installed.

There are lots of lines in rkhunter, some are uncommented. I gave the ones mentioned in the help page

---

### Post by Habitual on 2018-02-14
> **anon_private said:**
> I don't think it has been configured

See [To avoid these warnings ]("https://help.ubuntu.com/community/RKhunter") section.
and
[https://ubuntuforums.org/showthread.php?t=2351702&p=13603673#post13603673](https://ubuntuforums.org/showthread.php?t=2351702&p=13603673#post13603673)

---

### Post by anon_private on 2018-02-14
[TABLE]
[TR]
[TD]I only have the middle one from this grouping

#ALLOWHIDDENDIR=/dev/.udev
[/TD]
[/TR]
[TR]
[TD]#ALLOWHIDDENDIR=/dev/.static[/TD]
[/TR]
[TR]
[TD]#ALLOWHIDDENDIR=/dev/.initramfs[/TD]
[/TR]
[/TABLE]

Should I add the other two to the file?

---

### Post by anon_private on 2018-02-22
An answer to the above would be appreciated

---

