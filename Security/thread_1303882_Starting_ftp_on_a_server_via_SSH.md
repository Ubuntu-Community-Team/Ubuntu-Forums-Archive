---
title: "Starting ftp on a server via SSH ?"
date: 2009-10-28
forum: Security
---

### Post by kartal on 2009-10-28
Hi

I have a working SSH and FTP setup. I want to connect to my SSH server and start stop Ftp server on demand. This is just a convenience thing for me. The reason I am asking is that the ftp server that I is Gadmin-Proftp(gui+server)will ask me to be root at all times to run it?

thanks

---

### Post by Lars Noodén on 2009-10-29
> **kartal said:**
> Hi

I have a working SSH and FTP setup. I want to connect to my SSH server and start stop Ftp server on demand. This is just a convenience thing for me. The reason I am asking is that the ftp server that I is Gadmin-Proftp(gui+server)will ask me to be root at all times to run it?

thanks

I'm going from the package 'proftpd-basic' with the below suggestions.  You can substitute another script if I've guessed wrong:

First make a group to help with starting and stopping FTP, and put the users that need to be able to start or stop the FTP server in that group.  

If you are running proftpd as a standalone server (it listens by itself) then you need to set something like the following in /etc/sudoers to allow anyone in the group to use the proftpd script:

```

# YMMV, test it before you break sudo
%ftpteam     ALL=(ALL) PASSWD: /etc/init.d/proftpd start, \
                               /etc/init.d/proftpd status, \
                               /etc/init.d/proftpd force-start, \
                               /etc/init.d/proftpd stop, \
                               /etc/init.d/proftpd force-stop, \
                               /etc/init.d/proftpd reload, \
                               /etc/init.d/proftpd restart, \
                               /etc/init.d/proftpd force-reload, \
                               /etc/init.d/proftpd check-config 

```

Then starting or stopping proftp does not need full root access only prepend 'sudo'. e.g.

sudo /etc/init.d/proftpd restart

If you are using xinetd to launch proftpd, then the solution is more complex.  

Out of curiosity what are you using ftp for that the built-in sftp cannot provide?

---

### Post by kartal on 2009-10-29
Hi

Thank you so much I will try now

---

### Post by kartal on 2009-10-29
> **Lars Noodén said:**
> 

Out of curiosity what are you using ftp for that the built-in sftp cannot provide?

Well It is just convenience. I use key based SSH so providing file-ftp access for non ssh users on the fly is not easy since I need  to create the key pairs put them on the server etc.

---

