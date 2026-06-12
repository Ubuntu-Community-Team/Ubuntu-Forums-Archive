---
title: "How to start binary"
date: 2011-02-25
forum: Server Platforms
---

### Post by geohei on 2011-02-25
Hi.

I need to start a binary when Ubuntu 10.04 server boots.
In which script should I insert the line to start this binary correctly according to Ubuntu policies?

Thanks,

---

### Post by scorp123 on 2011-02-25
> **geohei said:**
> 
I need to start a binary when Ubuntu 10.04 server boots.

You could place it into this file:
**/etc/rc.local**

I myself have a stupid old Acer SCSI scanner and I can't use it unless I remember to change its permissions from "root" to something else, and I need to do this everytime I boot my desktop. So I added the necessary lines here. My "/etc/rc.local" now looks like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Really make sure /tmp is cleaned:
# rm -rf /tmp/*
/usr/bin/find /tmp -amin +60 -exec /bin/rm -rf {} \;

# Reset scanner's (usually on /dev/sg10) permissions
/bin/chgrp disk `/usr/bin/lsscsi -g | /bin/grep "FlatbedScanner_9" | /usr/bin/awk '{ print $7 }'`
/bin/chmod 664 `/usr/bin/lsscsi -g | /bin/grep "FlatbedScanner_9" | /usr/bin/awk '{ print $7 }'`

exit 0
```

If you compare that with your default /etc/rc.local file you will easily see that the lower 7 lines above "exit 0" were added by me.

Important:

Please make sure that the binary you are going to add in there knows how to exit cleanly. If the binary gets stuck or is waiting for input or some such thing then putting it in there may hang your boot process. In that case it might be a wise choice to have it sent to the background upon boot? You can achieve that by adding a "&" after calling it. Example:

```
/path/to/your/binary &
```

This will launch it in the background and will prevent it from hanging the boot process ... 

Everything you put into **/etc/rc.local** will be executed as superuser "root" (so there's no need for using "sudo" here). If you need a different user you'd need to construct something using "su", e.g. something like this:

```
/bin/su -c '/path/to/your/command' name-of-non-root-user-here
```

This should work. But only do this if you need it.


I hope this helped?

---

### Post by geohei on 2011-02-28
Hi.

It did. It solved the problem completely!

Thanks a lot!

---

