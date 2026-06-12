---
title: "HOWTO: Disable automounting of portable media and manually control automounting"
date: 2009-09-03
forum: Tutorials
---

### Post by adlibre on 2009-09-03
[SIZE="2"]**Intro**[/SIZE]

This howto will allow you to (1) disable automounting of portable media (e.g. USB and flash drives) and (2) give you manual control over the automounting process, so you can select what partitions mount, where they mount, and what programs start automatically.

This hotplug functionality is achieved with the [[COLOR="Blue"]_ivman_[/COLOR]]("http://ivman.sourceforge.net/") program which uses [[COLOR="Blue"]_HAL_[/COLOR]]("http://www.freedesktop.org/wiki/Software/hal") events to run programs when new hardware changes are detected.  This lets you do more than automount external hard drives; for example you can run a script when a printer is attached, etc.

This howto was tested on Ubuntu Jaunty Jackalope.

[SIZE="2"]**I. Disable automounting**[/SIZE]

Run gconf-editor from the command line:

```
gconf-editor &
```

Go to "apps/nautilus/preferences" and uncheck "media_automount" and "media_automount_open".  The first option disables the automatic mounting of plugged-in media; the second prevents Nautilus from automatically opening the new device.

You can also do the above steps with these two commands:
```

gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount False
gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount_open False

```

[SIZE="2"]**II. Set up fstab**[/SIZE]
You will need to add entries to the fstab file for each device you want to automatically mount.  This will vary depending on what you are trying to mount, but here is a rough guide for those new to fstab.

First find out the device name of your drive/partition (e.g. /dev/sdb2).  One way to do this is to plug the device in and then run dmesg:
```
dmesg
```
Look for clues about what device was just plugged in toward the bottom of the output.
Another way: if you have not turned off automounting yet, you can plug the device in and run these commands for similar device information:
```

mount
df

```

Once you know the name of your device, find out its UUID (Universally Unique Identifier).  This is a unique string that lets you refer to particular drives/partitions which is important when dealing with removable drives (it's better than using /dev/sda2 because those device names may change for removable devices).  To find out the UUID for your device, look in this directory:
```

ls -l /dev/disk/by-uuid

```
and find the long number that links to your device.  You can also do this with the *blkid* command or *sudo vol_id --uuid /dev/sdb2*

Now you can add a new line to your fstab file.  For example:
```

# <file system>                             <mount point>       <type>     <options>                            <dump>  <pass>
UUID=g2398325-60cc-3ac3-b0b2-383209f5380f   /media/myusb        ext3       defaults,noauto,user,exec,noatime    0       0 

```
Here I'm referring to "/dev/sdb2" by its UUID.  This is an ext3 partition; yours may be NTFS (in which case you would use ntfs-3g for read and write support) or something else.  If you don't know the partition type, run something like *sudo cfdisk /dev/sdb* on your device.  Many options are available in fstab.  Here I'm using "noauto" to prevent automounting of a plugged-in device on startup.  You will still be able to allow automounting on startup with the *ivman* program.  I'm also using the "user" option to let an ordinary user mount the device.  The "exec" option is disabled in "user" mode, so I re-enabled it (it lets you execute programs on the drive).  The "noatime" option is for performance gains (also look into the "relatime" option).  For USB flash drives consider the "sync" option for safety reasons (it makes sure that data is written immediately -- in case the USB stick gets unplugged without unmounting first).  You can find out more about these options through *man mount*.

Next create a directory for mounting your device:
```

sudo mkdir /media/myusb

```

Finally check to make sure that you can mount and unmount:
```

mount UUID=g2398325-60cc-3ac3-b0b2-383209f5380f
ls /media/myusb
umount /media/myusb

```

[SIZE="2"]**III. Set up ivman**[/SIZE]
Now install the *ivman* package:
```

sudo apt-get install ivman

```
Run it once so that it can create user configuration files in your home directory:
```

ivman

```
You can then stop it with "Ctrl-C".

Before we start using ivman we will need to do some investigating with HAL.  The *lshal* program lists the items in the HAL database, such as your portable devices.  We can search for your particular device with grep:
```

lshal | grep -A 20 -B 10 "/dev/sdb2"

```
This will will output 20 lines after and 10 lines before the matching "dev/sdb2" line.  You can also search by your volume ID or the UUID.  Now look for the line similar to this one:

*info.udi = '/org/freedesktop/Hal/devices/volume_uuid_g2398325_60cc_3ac3_b0b2_383209f5380f'  (string)*

The UUID should correspond to the one you found earlier, with underscores instead of dashes.  Now you're ready to edit the *ivman* configuration files:
```

gedit ~/.ivman/IvmConfigActions.xml 

```
You will probably want to comment-out the rule that mounts everything:
```

<!-- // commented out
<ivm:Match name="ivm.mountable" value="true">
    <ivm:Option name="mount" value="true" />
</ivm:Match>
-->

```
Now add your own automounting rule:
```

<ivm:Match name="hal.info.udi" value="/org/freedesktop/Hal/devices/volume_uuid_g2398325_60cc_3ac3_b0b2_383209f5380f">
    <ivm:Option name="exec" value="mount UUID=g2398325-60cc-3ac3-b0b2-383209f5380f" />
</ivm:Match>

```
Use the "info.udi" value you found earlier.  Note the use of underscores in the first UUID and dashes in the second.  The "exec" line tells *ivman* what to execute when the device is recognized by HAL.  Here we use a mount command, but you can use any command you wish.  For example, to mount and open the new device in *nautilus* use this line instead:
```

<ivm:Option name="exec" value="mount UUID=g2398325-60cc-3ac3-b0b2-383209f5380f ; nautilus /media/myusb" />

```
You can even run your own custom scripts this way.  For example a script could check if the computer just booted (say through the *uptime* command) and use that to decide whether or not to start up *nautilus* on the plugged-in devices.

Add this line to have *ivman* mount any devices that are already plugged in when it starts.  This is great for automounting your drives on startup if they are plugged in (instead of using the 'auto' option in fstab):
```

<ivm:Option name="checkOnInit" value="true" />

```
Another rule example: open audio CDs in *nautilus*:
```

<ivm:Match name="hal.volume.disc.type" value="cd_rom">
    <ivm:Option name="exec" value="nautilus 'cdda://sr0/'" />
</ivm:Match>

```
where "sr0" is the device name of the cdrom.

You may also want to look at the configuration files in "/etc/ivman/".

Run *ivman* to test the new configuration until you are satisfied with the behavior.  The final step is to run *ivman* on startup.  In GNOME you can go to "System/Preferences/Startup Applications/Add" and add the command "ivman &".

Some more tips.  Look into the *pmount* package to mount drives as user without the need to edit fstab.  See this page for a [[COLOR="Blue"]_quick pmount example_[/COLOR]]("http://productivelinux.com/2009/01/31/how-to-automatically-mount-usb-drives-with-rox-filer-ivman-and-pmount/").

Using UUIDs can get tiresome, so try using labels instead.  You can get/set drive labels for NTFS partitions with *ntfslabel* and ext2/3 partitions with *e2label*.  In fstab simply use "LABEL=mylabel" instead of "UUID=..." and then mount with "mount LABEL=mylabel".  Finally change your IvmConfigActions.xml file to work with labels as well.  Use *<ivm:Match name="hal.volume.label" value="mylabel" />*.  This makes things a lot easier, but of course you'll need to make sure your drive labels are unique and consistent.

To create other rules for custom hardware changes, try this method.  Run "*lshal > out1.txt*" before you plug the device in.  Then run "*lshal > out2.txt*" after you plug it in.  Now compare the two outputs with "*diff out1.txt out2.txt*" and see what has changed.  Try to create a rule around the change and launch your own programs/scripts. See this page for [[COLOR="Blue"]_more *ivman* rule examples_[/COLOR]]("http://www.gentoo-wiki.info/Ivman").

---

### Post by curtistuckr on 2012-12-29
Just wondering, has this procedure been tested on the most recent version of Ubuntu? I'm looking for a utility that will automatically unmount partitions on external USB/FireWire drives at startup.

I just installed Ubuntu 12.10 on a Mac mini (dual boot with OS X Mountain Lion). On the Mac side, I have a utility that automatically unmounts everything except my Time Machine and media library partitions. I prefer to mount these external drives/partitions only when I'm actually using them. It would be helpful if I could find something in Ubuntu that performs the same function.

Your thoughts?

---

