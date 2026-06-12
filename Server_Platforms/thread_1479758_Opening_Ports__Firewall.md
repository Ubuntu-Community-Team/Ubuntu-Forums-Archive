---
title: "Opening Ports / Firewall"
date: 2010-05-11
forum: Server Platforms
---

### Post by LGX on 2010-05-11
ubuntu 10 x64 server

I am new to the ubuntu platform and i can not find a way to have the port 21 open (FTP) using openssh.

==========================================
# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
==========================================
# netstat -an | grep LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
==========================================


Any help would be great.

---

### Post by spynappels on 2010-05-11
You need to tell the SSH daemon to listen on port 21 instead of the default port 22. Any reason you don't want to use 22?

You will need to edit the sshd.conf file to set this variable.

---

### Post by Leppie on 2010-05-11
by default iptables doesn't block any port.
if you want openssh to listen on port 21 instead of the default port 22, you will have to configure this in your /etc/ssh/sshd_config

---

### Post by LGX on 2010-05-11
Thank you for your post.  Here my next question about this.  Is there a way to keep both ports (21-ftp/22-ssh) open so a user can have both options to use?
 
 
I see the file you are talking about.  (  etc/ssh/sshd_config  )
 
 
Another question to this, I know in vsftpd I can chroot the users to their home directory.  Can this be done in Ubuntu Server w/openssh?
 
 
Regards,
LGX

---

### Post by terazen on 2010-05-11
I don't think so.  Do you mean access to modify or view files outside of the home directory?

---

### Post by LGX on 2010-05-11
I know in vsftpd I can chroot the users and keep them to their home directory. Can this be done in Ubuntu Server w/openssh?
 
> **terazen said:**
> I don't think so. Do you mean access to modify or view files outside of the home directory?
 
 
Keeping the user to their home directory (/home/user%) and not allowing them to browse other folders on the box.
 
 
Cheers,
LGX

---

