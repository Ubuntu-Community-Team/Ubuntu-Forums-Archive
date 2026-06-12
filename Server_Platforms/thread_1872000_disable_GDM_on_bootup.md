---
title: "disable GDM on bootup"
date: 2011-10-29
forum: Server Platforms
---

### Post by patryk_w on 2011-10-29
i'm running ubuntu 11.10 server with installed gnome.
how can i make my system to boot into command line instead of GDM?

setting GRUB_CMDLINE_LINUX to "text" in /etc/default/grub doesn't do the trick like in previous distros... any ideas? ;)

---

### Post by volkswagner on 2011-10-30
EDIT:
I think you may have edited the wrong line in Grub,

Here is mine for a pc running a gui which I forced not to load.

```

GRUB_CMDLINE_LINUX_[COLOR="Red"]DEFAULT[/COLOR]="quiet acpi=force text"

```

NOTICE the word DEFAULT

[endEDIT]

I don't have any versions greater than 10.04 running.  I'm not sure why that does not work.

Take a look inside /etc/init/rc-sysinit.conf.

Check out what my run level looks like for server no GUI installed.  Perhaps you can force your run level to '2' in this file.



```

############## Partial /etc/init/rc-sysinit.conf  ################

# Default runlevel, this may be overriden on the kernel command-line
# or by faking an old /etc/inittab entry
env DEFAULT_RUNLEVEL=2

```

---

### Post by lswb on 2011-10-30
> **patryk_w said:**
> i'm running ubuntu 11.10 server with installed gnome.
how can i make my system to boot into command line instead of GDM?

setting GRUB_CMDLINE_LINUX to "text" in /etc/default/grub doesn't do the trick like in previous distros... any ideas? ;)
I am running 10.4, not 11.10, but... after making a change to /etc/default/grub it is necessary to run ```

sudo update-grub

```
for the changes to take effect.

---

### Post by patryk_w on 2011-10-31
i've change entry in /etc/defalt/grub to 'GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force text"'
default runlevel is set to 2...
still no luck
(yes i know grub needs to be updated;) )

---

### Post by ubu_dynamite on 2011-10-31
Maybe this will work
[http://linux.koolsolutions.com/2009/07/24/tip-disable-gdm-kdm-or-xdm-from-starting-up-automatically/](http://linux.koolsolutions.com/2009/07/24/tip-disable-gdm-kdm-or-xdm-from-starting-up-automatically/)

---

### Post by patryk_w on 2011-10-31
> **ubu_dynamite said:**
> Maybe this will work
[http://linux.koolsolutions.com/2009/07/24/tip-disable-gdm-kdm-or-xdm-from-starting-up-automatically/](http://linux.koolsolutions.com/2009/07/24/tip-disable-gdm-kdm-or-xdm-from-starting-up-automatically/)

no luck here either. bizarre...

---

### Post by volkswagner on 2011-10-31
Did you setup any automatic login for any users inside Gnome?

---

### Post by patryk_w on 2011-10-31
> **volkswagner said:**
> Did you setup any automatic login for any users inside Gnome?

no i didn't

---

### Post by lswb on 2011-10-31
Have you verified that your changes are actually being propagated to the kernel command line at boot? if you ```
cat /proc/cmdline
```do they show up there?

---

### Post by sisco311 on 2011-10-31
In 11.10 you have to use a [.override]("http://upstart.ubuntu.com/cookbook/#disabling-a-job-from-automatically-starting") file to disable an Upstart job:
[http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

---

### Post by patryk_w on 2011-10-31
> **lswb said:**
> Have you verified that your changes are actually being propagated to the kernel command line at boot? if you ```
cat /proc/cmdline
```do they show up there?

i think so....
```

root@atom:~# cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.0.0-12-server root=/dev/mapper/atom-root ro text quiet acpi=force text


```

---

### Post by patryk_w on 2011-10-31
> **sisco311 said:**
> In 11.10 you have to use a [.override]("http://upstart.ubuntu.com/cookbook/#disabling-a-job-from-automatically-starting") file to disable an Upstart job:
[http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

that worked for me. but after i boot the system i need to press ctrl+alt+F1 to get login prompt.
is there a way to fix it? ;)

---

### Post by lswb on 2011-10-31
> **patryk_w said:**
> that worked for me. but after i boot the system i need to press ctrl+alt+F1 to get login prompt.
is there a way to fix it? ;)

It's a kludge but try putting this command in /etc/rc.local
```

chvt 1

```

Change 1 to 2,3, etc. to log in on a different VT. Unable to test but I believe it will work. If you sometimes run X or GDM you may want to include a test of your kernel command line and skip the chvt command if "text" is not present.

---

### Post by lswb on 2011-10-31
> **patryk_w said:**
> that worked for me. but after i boot the system i need to press ctrl+alt+F1 to get login prompt.
is there a way to fix it? ;)

It's a kludge but try putting this command in /etc/rc.local
```

chvt 1

```

Change 1 to 2,3, etc. to log in on a different VT. Unable to test but I believe it will work. If you sometimes boot direclty into gdm or X you may want to include a test of your kernel command line and skip the chvt command if "text" is not present.

---

### Post by patryk_w on 2011-11-01
worked like a charm. thank u guys ;)

---

