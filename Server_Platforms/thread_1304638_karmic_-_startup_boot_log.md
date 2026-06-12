---
title: "karmic - startup boot log"
date: 2009-10-29
forum: Server Platforms
---

### Post by infinitezero on 2009-10-29
Can someone tell me where upstart puts the boot log?

Thanks,
iz

---

### Post by swdinesh on 2009-11-15
Is not automatically enabled by default.
You have to enable it 
edit as root (with sudo) the file: "/etc/default/bootlogd"
gives this option:

"Run bootlogd at startup ?
BOOTLOGD_ENABLE=No"

Changing to "yes" save and close.

than you have to enable bootlogdaemon

sudo update-rc.d bootlogd defaults

at next reboot it will be enabled

bye
Alex

---

### Post by robhauge on 2009-11-16
This did not work.

The only thing I got inn boot.log is some entries from the shutdown. 

I got this error message when I ran sudo update-rc.d bootlogd defaults

update-rc.d: warning: bootlogd start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (S)
update-rc.d: warning: bootlogd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)


And it realy sucs that I as an admin should use 2-3 hour&#8217;s of my day to find out how to enable this. On a server this should be enabled as default.

---

### Post by robhauge on 2009-11-16
> **swdinesh said:**
> Is not automatically enabled by default.
You have to enable it 
edit as root (with sudo) the file: "/etc/default/bootlogd"
gives this option:

"Run bootlogd at startup ?
BOOTLOGD_ENABLE=No"

Changing to "yes" save and close.

than you have to enable bootlogdaemon

sudo update-rc.d bootlogd defaults

at next reboot it will be enabled

bye
Alex

Please check the relevance before you post.
Your solution does not work

---

### Post by pivert on 2010-02-28
OK,

I found the boot logs in the /var/log/syslog. Loos like it's there by default, without needed the bootlogd

Regards,

---

