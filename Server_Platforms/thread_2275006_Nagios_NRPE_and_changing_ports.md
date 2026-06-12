---
title: "Nagios NRPE and changing ports"
date: 2015-04-23
forum: Server Platforms
---

### Post by ghughes on 2015-04-23
Good afternoon, all!

I have a working Nagios Core 3.2.3 installation from the repositories.  I need to change the sending/listening port for nrpe.  I can change the port in nrpe.cfg on the remote server and run the command by hand from the central server using the -p option successfully, which shows that the remote host listens and executes the command.  However, when I edit command.cfg on the central servers to specify the new port none of the targets respond.  If I change the remote server back to the default port 5666 the commands run successfully.  

I've hunted for where another command.cfg with the default port might exist but don't have any luck in finding one.  Changing the check_nrpe.cfg in /etc/nagios-plugins/config was also not helpful.

Any help in finding where this can be changed in 12.04 (central server) and 14.04 (remote) would be very much appreciated!

Thanks to all for looking!

Gregg

---

### Post by ghughes on 2015-04-23
OK, think I found it.

/etc/nagios-plugins/config - I went back to that check_nrpe.cfg and changed the port setting in there, then waited for the next check to succeed.  It failed, so I went back to the target remote server and changed the server_port there to the new value and again waited to succeed or fail. The new port setting suceeded, I have no idea why it failed the first time I tried that fix.  

Linux - try, try again because it might not take the first time......


G

---

