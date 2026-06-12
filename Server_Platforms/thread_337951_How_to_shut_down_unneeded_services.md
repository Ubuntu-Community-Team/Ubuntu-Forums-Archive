---
title: "How to shut down unneeded services"
date: 2007-01-13
forum: Server Platforms
---

### Post by larka06 on 2007-01-13
I have read and there seems to be two programs to shutdown unneeded services, bum and sysv-rc-conf.  I am trying to setup a DNS server and only want that much of the server programs to run.  I so far have been unable to find a way to stop the unneeded services.  Trying to install either of the optional programs will not work, they maybe just for GUIs'.  If someone could guide me through how to do this I would greatly appreciate the help
Thanks
Larka06

---

### Post by Pollywoggy on 2007-01-13
> **larka06 said:**
> I have read and there seems to be two programs to shutdown unneeded services, bum and sysv-rc-conf.  I am trying to setup a DNS server and only want that much of the server programs to run.  I so far have been unable to find a way to stop the unneeded services.  Trying to install either of the optional programs will not work, they maybe just for GUIs'.  If someone could guide me through how to do this I would greatly appreciate the help
Thanks
Larka06

I am not familiar with "bum" or the file you mention, but the first place to look is /etc/default/
There you might find a file with the name of the service to which it applies and in the file, a means of stopping it.   If you don't find that, you can cd to /etc/init.d/ and services which start at boot time have their startup files there.  Just put 

exit 0 

near the top of the file but UNDER the shebang line #!/bin/sh

You can also disable the startup file with something like:

update-rc.d -f portmap remove  

   if you are trying to disable portmap, but the best thing to try is the 'exit 0' method because it is easy to undo.

Some services (daemons) start from /etc/inetd.conf or /etc/xinetd.conf and I just noticed that I have some unwanted services there, talk and ntalk.  I will comment them out and restart inetd and that should take care of that.

---

### Post by Gouki on 2007-01-14
I have learned that *rcconf* can be really useful. Maybe you can give it a try.

---

