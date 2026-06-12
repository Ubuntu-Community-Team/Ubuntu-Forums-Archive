---
title: "unable to shutdown with acpi"
date: 2016-07-30
forum: Virtualisation
---

### Post by asgard2 on 2016-07-30
Hi,

I can not shutdown with acpi my lubuntu 16.04 guest since the xenial upgrade.

The host has xubuntu 14.04 (now 16.04 - same problem).

Host:
```
ii  virtualbox                                    5.0.24-dfsg-0ubuntu1.16.04.1                                amd64        x86 virtualization solution - base binaries
ii  virtualbox-dkms                               5.0.24-dfsg-0ubuntu1.16.04.1                                all          x86 virtualization solution - kernel module sources for dkms
ii  virtualbox-guest-dkms                         5.0.24-dfsg-0ubuntu1.16.04.1                                all          x86 virtualization solution - guest addition module source for dkms
ii  virtualbox-guest-utils                        5.0.24-dfsg-0ubuntu1.16.04.1                                amd64        x86 virtualization solution - non-X11 guest utilities
ii  virtualbox-guest-x11                          5.0.24-dfsg-0ubuntu1.16.04.1                                amd64        x86 virtualization solution - X11 guest utilities
ii  virtualbox-qt                                 5.0.24-dfsg-0ubuntu1.16.04.1                                amd64        x86 virtualization solution - Qt based user interface

```

Guest:
```
ii  virtualbox                            5.0.24-dfsg-0ubuntu1.16.04.1             amd64        x86 virtualization solution - base binaries
ii  virtualbox-dkms                       5.0.24-dfsg-0ubuntu1.16.04.1             all          x86 virtualization solution - kernel module sources for dkms
ii  virtualbox-guest-additions-iso        5.0.24-0ubuntu1.16.04.1                  all          guest additions iso image for VirtualBox
ii  virtualbox-guest-dkms                 5.0.24-dfsg-0ubuntu1.16.04.1             all          x86 virtualization solution - guest addition module source for dkms
ii  virtualbox-guest-utils                5.0.24-dfsg-0ubuntu1.16.04.1             amd64        x86 virtualization solution - non-X11 guest utilities
ii  virtualbox-guest-x11                  5.0.24-dfsg-0ubuntu1.16.04.1             amd64        x86 virtualization solution - X11 guest utilities
ii  virtualbox-qt                         5.0.24-dfsg-0ubuntu1.16.04.1             amd64        x86 virtualization solution - Qt based user interface


```
```

$ ps -e | grep acpi
   48 ?        00:00:00 acpi_thermal_pm
 1794 ?        00:00:00 acpid

```

What is wrong?

---

### Post by MAFoElffen on 2016-07-31
It's a Newer version of VirtualBox "thing..."

On your Lubuntu 16.04 guest, (Any recent ubuntu guest)
```

dpkg -l | grep acpid

```
If the output is blank (returns back to the prompt without any output), then install it
```

sudo apt-get install acpid

```

FYI to others using Win10 guests, there is an acpi shutdown workaround for them also
```

Control Panel > Power Options > Choose what the power buttons do> When I press the Power Button > Select "Shutdown"

```

---

### Post by asgard2 on 2016-07-31
Acpi deamon is running (#1), and of course it is installed at the guest.
```

$ dpkg -l | grep acpi
ii  acpid                                 1:2.0.26-1ubuntu2                        amd64        Advanced Configuration and Power Interface event daemon

```[URL="https://ubuntuforums.org/showthread.php?t=2332331&p=13524727#post13524727"]
[/URL]

---

### Post by MAFoElffen on 2016-07-31
Since verified as installed, next step would be to edit /etc/default/grub and go to this line:
```

 GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;

```
Edit it by like this
```

 GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash [COLOR=#b22222]acpi=force[/COLOR]&#8221;

```
After a save and quit, then pickup the changes via
```

sudo update-grub

```
Reboot for the change to take affect.

Then tell me if it's behavior for that acts any different(?)

---

### Post by asgard2 on 2016-07-31
Sadly no, acpi shutdown ist not working. :(

---

### Post by Bashing-om on 2016-07-31
@MAFoElffen; Hello

Reckon it might be beneficial to update the Differentiated Services Description Table (DSDT) ?

And tell the kernel to use the latest ?
To that do 
```

sudo strings /sys/firmware/acpi/tables/DSDT | grep -i windows

```
and identify the latest Windows version listed; then make the grub edit.

[INDENT][INDENT]mind yall
[INDENT][INDENT]just a thought
[/INDENT][/INDENT][/INDENT][/INDENT]

---

