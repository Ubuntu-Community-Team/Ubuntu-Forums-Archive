---
title: "serval serp4 9.10 upgrade issues"
date: 2009-11-11
forum: System76 Support
---

### Post by majoridiot on 2009-11-11
like an idiot, i decided to upgrade to 9.10 in the hope of fixing minor issues that were nagging.  

unfortunately, the upgrade has caused more problems than it fixed.  most have been sorted, 
but a few fairly major ones remain.  

1. nvidia driver 185 inverts video colors.  other colors are fine, but video is inverted. reverting 
back to 173 fixed the problem, but running an older driver seems counterproductive.

2. the laptop refuses to go into either suspend (preferred) or hibernate.  i have tried everything 
recommended in other threads, including changing the appropriate lines in /etc/default/acpi-support 
to read:

```
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=standby
```

however, it is also noted in that file that acpi-support is deprecated and the current config is 
to use:

```
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"
```

so, i'm not sure what path to take, given the "preferred" method fails.

3. some apps (notably cgmail) refuse to use sound, even though it is configured and works in other apps.

if anyone has pointers on resolving these issues- primarily the suspend method, it is much appreciated.  
i'm trying to obviate the need to re-install a fresh version of intrepid or jaunty.

this is, without a doubt, the most bug-laden release yet and a real disappointment from the normally 
reliable ubuntu devs...

EDIT: changing

```
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"
```

to ```
SUSPEND_METHODS="acpi-support"
```

made no difference in suspend or hibernate.

---

### Post by thomasaaron on 2009-11-11
> 1. nvidia driver 185 inverts video colors. other colors are fine, but video is inverted. reverting
back to 173 fixed the problem, but running an older driver seems counterproductive.

Actually, I don't think it is the nVidia driver. If you open Movie Player and go to Edit > Prefs and set the Hue to the center, it should fix that (in other applications as well).

> 2. the laptop refuses to go into either suspend (preferred) or hibernate. i have tried everything
recommended in other threads, including changing the appropriate lines in /etc/default/acpi-support
to read:

I'd put acpi-support back to it's default settings. Then post the output of...

swapon -a

cat /etc/fstab

...and load gparted (Partition Editor) and right-click on the swap partition and click properties. Record the UUID.
> 
3. some apps (notably cgmail) refuse to use sound, even though it is configured and works in other apps.

Not sure about that. Let's get the others worked out first.
> 
this is, without a doubt, the most bug-laden release yet and a real disappointment from the normally
reliable ubuntu devs...

Not really. It's actually pretty stable, and quite nice, if you do a clean install. However, the upgrade *process* was rough this time around. Come to think of it, last time around it was darn bad too.

---

### Post by majoridiot on 2009-11-11
> **thomasaaron said:**
> Actually, I don't think it is the nVidia driver. If you open Movie Player and go to Edit > Prefs and set the Hue to the center, it should fix that (in other applications as well).



no, it was definitely the driver.  possibly from a bad update, but it was the driver.  color inversion 
was consistent across all media players and hue/color settings were correct for all players. video
colors are correct using 173.

> **thomasaaron said:**
> I'd put acpi-support back to it's default settings. Then post the output of...

swapon -a

cat /etc/fstab


```
$ swapon -a
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc	/proc	proc	defaults	0	0
# /dev/sda1
UUID=6c814527-5db0-4129-b3bc-f41a16213147	/	ext3	relatime,errors=remount-ro	0	1	# /dev/sda1
# /dev/sda3
UUID=5aea32d9-f557-461a-958a-011fe718ac27	/home	ext3	relatime	02	# /dev/sda3
# /dev/sda2
UUID=3d13dcef-1b8c-41d9-bada-a585b4022a2d	none	swap	sw	0	0# /dev/sda2
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0
```

> **thomasaaron said:**
> ...and load gparted (Partition Editor) and right-click on the swap partition and click properties. Record the UUID.

per gparted, the swap UUID is 3d13dcef-1b8c-41d9-bada-a585b4022a2d, which matches fstab.

> **thomasaaron said:**
> Not really. It's actually pretty stable, and quite nice, if you do a clean install. However, the upgrade *process* was rough this time around. Come to think of it, last time around it was darn bad too.

maybe overstated on this end, if 9.10 is running fine on other servals from a clean install.

perhaps backing everything up and trying a clean install is wise...?

---

### Post by thomasaaron on 2009-11-11
> no, it was definitely the driver. possibly from a bad update, but it was the driver. color inversion
was consistent across all media players and hue/color settings were correct for all players. video
colors are correct using 173.

Not to kick a dead horse, but if it is the driver, it will be the first case like it that I've seen. Is there any way you could reload the 185 driver and check out the hue setting in Totem Movie Player.

My shop machine isn't inverting colors with the 185 driver unless I mess up the hue settings. It's no big deal, as you're all fixed now. But if there's another problem out there, I'd sure like to verify it in case I run into it again.


> per gparted, the swap UUID is 3d13dcef-1b8c-41d9-bada-a585b4022a2d, which matches fstab.

I'm sorry. I had you run swapon -a when I really needed you to run swapon -s. Could you make sure that swapon -s says /dev/sda2?

> perhaps backing everything up and trying a clean install is wise...? 

It wouldn't hurt. But your system doesn't seem that hosed. I'm happy to keep helping you with it.

---

### Post by majoridiot on 2009-11-12
> **thomasaaron said:**
> Not to kick a dead horse, but if it is the driver, it will be the first case like it that I've seen. Is there any way you could reload the 185 driver and check out the hue setting in Totem Movie Player.

My shop machine isn't inverting colors with the 185 driver unless I mess up the hue settings. It's no big deal, as you're all fixed now. But if there's another problem out there, I'd sure like to verify it in case I run into it again.

re-enabled 185, checked hue settings and colors were still inverted in all media players.

> **thomasaaron said:**
> I'm sorry. I had you run swapon -a when I really needed you to run swapon -s. Could you make sure that swapon -s says /dev/sda2?

no worries.  -s showed the correct swap partition.

> **thomasaaron said:**
> It wouldn't hurt. But your system doesn't seem that hosed. I'm happy to keep helping you with it.

it turned out to be more hosed than it first appeared.  major flakiness abounds.

reformatting and reinstalling 9.10 right now.  will let you know if issues persist after a clean install.

thanks...

---

### Post by majoridiot on 2009-11-12
i installed 9.10 from a clean format.  it was *extremely* flaky, until i managed to wrangle updates, which seemed to fix the usb issues i was having.

it was a trick to get restricted drivers to find the devices, but once it did, nvidia 185 installed fine, with no video issues.

i still had to change /etc/default/acpi-support from:

```
ACPI_SLEEP_MODE=mem
```

to:

```
ACPI_SLEEP_MODE=standby
```

to get it to go into standy, when the lid is closed.

it seems to be running ok at the moment, so i'm keeping my fingers crossed.  lesson learned about upgrading.  ;)

thanks for the help, thomas!

---

