---
title: "Possible malicious activity found by Tiger"
date: 2015-10-10
forum: Security
---

### Post by alberto28 on 2015-10-10
Hi.

I am running a web server with Ubuntu Server 14.04.2 LTS , Nginx, PHP and MySql. i do use psad in auto IDS mode, tripwire for file integrity check, Tiger to monitor possibly security breaches and Rkhunter to check for rootkits. 

Last night i noticed this in Tiger logs:

```

--ALERT-- [fsys006a] Unexpected device files found:
lrwxrwxrwx 1 root root 9 Aug 31 15:13 /etc/udev/rules.d/80-net-name-slot.rules -> /dev/null
lrwxrwxrwx 1 root root 9 Aug 31 15:13 /etc/udev/rules.d/80-net-setup-link.rules -> /dev/null

```

Syslinks pointing to /dev/null.....?

I did some researches and it seems they have nothing to do with networking, at least in Ubuntu. I wonder what these files are, i wonder if they may be a security breach and, last but not least, if i can remove them. 

Thank you.

---

### Post by QDR06VV9 on 2015-10-10
I too have seen changes like that, But found that mine at least were due to some system updates.
More Info Here 
[http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)
[https://wiki.gentoo.org/wiki/Udev/Upgrade_Guide](https://wiki.gentoo.org/wiki/Udev/Upgrade_Guide)
Other posters might have some good news for you also.
Regards

---

### Post by alberto28 on 2015-10-10
> **runrickus said:**
> I too have seen changes like that, But found that mine at least were due to some system updates.
More Info Here 
[http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)
[https://wiki.gentoo.org/wiki/Udev/Upgrade_Guide](https://wiki.gentoo.org/wiki/Udev/Upgrade_Guide)
Other posters might have some good news for you also.
Regards

Thank you for those documents. [Here]("http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/") i read: 
> [h=2][SIZE=2][FONT=arial]I don't like this, how do I disable this?[/FONT][/SIZE][/h][SIZE=2][FONT=arial]You basically have four options:[/FONT][/SIZE]

[LIST=1]
[*][SIZE=2][FONT=arial]You disable the assignment of fixed names, so that the unpredictable kernel names are used again. For this, simply mask udev's rule file for the default policy: ln -s /dev/null /etc/udev/rules.d/80-net-setup-link.rules (since v209: this file was called 80-net-name-slot.rules in release v197 through v208)[/FONT][/SIZE]
[*][FONT=arial][...][/FONT]
[*][SIZE=2][FONT=arial][...][/FONT][/SIZE]
[*][SIZE=2][FONT=arial][/FONT][/SIZE][FONT=arial][...][/FONT]
[/LIST]


The first option is exactly what is enforced in my system.** Should i consider those files safe then?** 

Moreover, could you help me in go a 'bit deeper into this fact?

**My udev version:**
```

udevadm --version
204

```

Considering [this]("https://wiki.gentoo.org/wiki/Udev/Upgrade_Guide") and considering that the output of the command ```
sysctl -a | grep net.ifnames
``` is blank, i should have Predictable Network Interface Names enabled **at kernel level**. **Right?** Then.. those 2 files pointing to /dev/null are actually disabling the feature **at system level**. [B]Right?

[/B]Well.. therefore.. the best thing would be add ```
net.ifnames=0
``` to my sysctl.conf . [B]Right?

[/B]Thank you for your time.

---

### Post by Doug S on 2015-10-11
In my opinion this interface names stuff is a mess and inconsistent between server and desktop Ubuntu editions. So much so that we do not actually know how to fix the [Ubuntu server guide]("https://bugs.launchpad.net/serverguide/+bug/1312785") for the subject. (there are links to other references in that bug report).

Where I ended up was with this is my grub line:```
GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=1 biosdevname=0"
```

---

