---
title: "Turning off automatic update on Server 9.04"
date: 2009-09-24
forum: Server Platforms
---

### Post by simplified on 2009-09-24
Hi All

I'm having a bit of a problem in that I must recompile the modules for VMWare every time my Ubuntu Server runs the automatic update. This always seems to happen when I need the server the most so I need to turn off automatic updates so I can then do them manually and have a bit more control over when I can sort out VMWare.

I've looked at modifying the file /etc/cron.daily/apt but to be honest it's a bit above my skill level; there is a post that advises you change the file but doesn't specify exactly what you need to change. I wondered if anyone can point me in the right direction?

TIA, Simplified :)

---

### Post by t3r0 on 2009-09-24
Hi,

in file: ```
/etc/apt/apt.conf.d/50unattended-upgrades
```
comment out update update you don't want to upgrade automatically 
eg: 
```

// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
//        "Ubuntu jaunty-security";
//      "Ubuntu jaunty-updates";
};

```


- Tero

---

### Post by jondkent on 2009-09-24
I was wondering the same thing.  Thanks for the answer

---

### Post by simplified on 2009-09-25
Hi Tero

Thank you for that, I've made the change.

Your help is most appreciated! :)

Cheers, Simplified

---

### Post by rtotheototheb on 2009-10-30
Hi t3r0,

Thanks for the simple and clear answer.

---

### Post by danger89 on 2010-02-16
thx :D

---

### Post by dcstar on 2010-03-06
> **simplified said:**
> Hi All

I'm having a bit of a problem in that I must recompile the modules for VMWare every time my Ubuntu Server runs the automatic update. This always seems to happen when I need the server the most so I need to turn off automatic updates so I can then do them manually and have a bit more control over when I can sort out VMWare.
..........

Or: [http://ubuntuforums.org/showthread.php?t=1418747](http://ubuntuforums.org/showthread.php?t=1418747)

---

### Post by yngens on 2012-04-04
What about just running: 

[HTML]sudo apt-get remove unattended-upgrades[/HTML]

?

---

### Post by loconut on 2012-06-19
> **yngens said:**
> What about just running: 

[HTML]sudo apt-get remove unattended-upgrades[/HTML]

?

That would be a bad idea, at least on Desktop. It may be ok on Server.

root@aurora:/etc/init.d# apt-get remove unattended-upgrades
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-lxml gir1.2-unique-3.0 language-pack-kde-en kde-l10n-engb
  language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  aptdaemon apturl landscape-client-ui-install language-selector
  language-selector-gnome nautilus-share python-aptdaemon
  python-aptdaemon-gtk python-aptdaemon.gtk3widgets
  python-aptdaemon.gtkwidgets python-aptdaemon.pkcompat
  python-software-properties sessioninstaller software-center
  software-properties-gtk ubufox ubuntu-desktop ubuntu-tweak
  ubuntuone-control-panel-common ubuntuone-control-panel-gtk
  ubuntuone-control-panel-qt ubuntuone-installer unattended-upgrades
  xul-ext-ubufox
0 upgraded, 0 newly installed, 24 to remove and 19 not upgraded.
After this operation, 15.1 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
root@aurora:/etc/init.d#



By the way, I found this answer on my own:
root@aurora:/etc/init.d# update-rc.d unattended-upgrades disable
update-rc.d: warning: unattended-upgrades stop runlevel arguments (none) do not match LSB Default-Stop values (0 6)
 Disabling system startup links for /etc/init.d/unattended-upgrades ...
 Removing any system startup links for /etc/init.d/unattended-upgrades ...
   /etc/rc0.d/K20unattended-upgrades
   /etc/rc1.d/K20unattended-upgrades
   /etc/rc2.d/S20unattended-upgrades
   /etc/rc3.d/S20unattended-upgrades
   /etc/rc4.d/S20unattended-upgrades
   /etc/rc5.d/S20unattended-upgrades
   /etc/rc6.d/K20unattended-upgrades
 Adding system startup for /etc/init.d/unattended-upgrades ...
   /etc/rc0.d/K20unattended-upgrades -> ../init.d/unattended-upgrades
   /etc/rc1.d/K20unattended-upgrades -> ../init.d/unattended-upgrades
   /etc/rc6.d/K20unattended-upgrades -> ../init.d/unattended-upgrades
   /etc/rc2.d/K80unattended-upgrades -> ../init.d/unattended-upgrades
   /etc/rc3.d/K80unattended-upgrades -> ../init.d/unattended-upgrades
   /etc/rc4.d/K80unattended-upgrades -> ../init.d/unattended-upgrades
   /etc/rc5.d/K80unattended-upgrades -> ../init.d/unattended-upgrades

---

### Post by nothingspecial on 2012-06-20
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Closed.

---

