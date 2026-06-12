---
title: "Server login problem"
date: 2010-06-06
forum: Server Platforms
---

### Post by DazEllerington on 2010-06-06
Hello. Not sure If I have the same problem but my Ubuntu 10.04 64 bit server has a login problem:

When I login, on either tty0 or over ssh, it does nothing up to a point when it says login timed out after 60 seconds.

This server (mainly a samba server) has no internet access. 

sometimes, a few more tries and I can login, other times the expensive server becomes a paperweight.

Is this the same issue or something else someone can shed light on?

Thank you.

Darren.

---

### Post by cariboo on 2010-06-06
Moved to a thread of it's own.

---

### Post by steveroot on 2010-06-07
Same thing here, I have:

Fresh install of 10.04 Server 32 bit on VMWare ESXi 4

On the console, Start is quick to the login prompt, accepts username and asks for password. Then nothing happens and it eventually gives message "login timed out after 60 seconds"

Connecting via SSH, nothing happens after the password.  Server responds instantly to pings though.

The server is not busy(CPU/disk/network) during this login delay.  After about 5 minutes or so login works.

If anyone has any suggestions of logs that might shed light on the problem I'd appreciate it.
Thanks,
Steve

---

### Post by zorglubx on 2010-06-07
Have you installed vmware tools properly?

---

### Post by DazEllerington on 2010-06-10
My Ubuntu server is installed stand alone so I don't think it's anything to do with vmware.

Steveroot, exactly the same! Except, sometimes it's 5 mins and other times, like right now, it's over an hour.

Can anyone help?

Thanks.

---

### Post by gsgleason on 2010-06-10
See if this helps: [http://www.refreshinglyblue.com/2007/05/18/long-delay-before-ssh-authentication/](http://www.refreshinglyblue.com/2007/05/18/long-delay-before-ssh-authentication/)

[EDIT]
And/or this: [http://britg.com/2008/10/23/getting-rid-of-ssh-or-sftp-delay/](http://britg.com/2008/10/23/getting-rid-of-ssh-or-sftp-delay/)

---

