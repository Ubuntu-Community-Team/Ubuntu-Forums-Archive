---
title: "Boot without gui into different runlevel"
date: 2010-07-27
forum: Server Platforms
---

### Post by .09. on 2010-07-27
Hi

I have installed 10.04 LTS server and after that x-window-system-core, gnome-core and gdm. Now it boots to a gui in runlevel 2.

1. How can I set the default runlevel to 3?

and

2. boot into runlevel 3 without a gui?

---

### Post by cdenley on 2010-07-27
So you want GDM to start for runlevels 2,4, and 5? I think this would work.

/etc/init/gdm.conf
```

# gdm - GNOME Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services

description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

start on (filesystem
          and started dbus
          and (graphics-device-added fb0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger)
          **[COLOR="Red"]and runlevel [245] [/COLOR]**)
stop on runlevel [016]

```

I believe the correct place to change the default runlevel for 10.04 is /etc/init/rc-sysinit.conf

---

### Post by sisco311 on 2010-07-27
> **.09. said:**
> Hi

I have installed 10.04 LTS server and after that x-window-system-core, gnome-core and gdm. Now it boots to a gui in runlevel 2.

1. How can I set the default runlevel to 3?

and

2. boot into runlevel 3 without a gui?

Run levels are still emulated, but are kinda deprecated... 

In order to boot without starting the display manager use the **text** kernel parameter.

Edit /etc/default/grub and add the **text** option to the GRUB_CMDLINE_LINUX_DEFAULT variable:
```

...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **text**"
...
```

Remove the **quiet** option to make the boot process verbose. 

Removing the **splash** option to disable the splash screen.

i.e.
```

...
GRUB_CMDLINE_LINUX_DEFAULT="**text**"
...
```


Then run:
```
sudo update-grub
```
to generate a new grub.cfg file.

Or you could create a new *text mode* grub entry, but that's a little bit trickier. :)
[list=i]
[*]backup the /etc/grub.d/10_linux file:
```
sudo cp /etc/grub.d/10_linux{,-backup}
sudo chmod -x /etc/grub.d/10_linux-backup
```

[*]open it for editing:
```
gksu gedit /etc/grub.d/10_linux
```

[*]scroll down to the **linux_entry** function (line ~64), and edit it to look like this:
```

...
linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"

[B]  if [ "${recovery}" = "text" ]; then
    title="$(gettext_quoted "%s, with Linux %s (text mode)")"
  elif ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi[/B]
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
...
```

[*]scroll down to the end of file and call the function with the **text** parameter:
```

...
[B]  linux_entry "${OS}" "${version}" "text" \
      "text ${GRUB_CMDLINE_LINUX}"
[/B]

  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet

  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
        "single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done

```

[*]generate a new grub.cfg file:
```
sudo update-grub
```

[*]check out the /boot/grub/grub.cfg file and see if the new menu entry is generated.
[/list]

If something went wrong, restore the original settings:
```
sudo mv /etc/grub.d/10_linux{-backup,}
sudo chmod +x /etc/grub.d/10_linux
```
```
sudo update-grub
```

---

### Post by .09. on 2010-07-28
I used the text option in grub and it worked, thanks :cool:

---

### Post by dwaltz on 2012-09-27
Thanks I found this thread still useful today, I used the long solution, and at step iii. I had to chang line 96 to read like:
```
if [ "${recovery}" != "text" -a ! ${recovery} ] ; then
```
this in Ubuntu 12, don't know if this script changed from 10 to 12.

At step iv. instead I placed the "text" mode as second option.

regards

---

