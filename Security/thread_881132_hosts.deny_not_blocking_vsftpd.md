---
title: "hosts.deny not blocking vsftpd"
date: 2008-08-05
forum: Security
---

### Post by bj0 on 2008-08-05
Hey, I was trying to configure my kubuntu box to allow ftp connections only from certain computers using hosts.deny/allow, but it didn't seem to be doing anything at all.  To test to see if it was even recognizing the daemon name I put 'vsftpd: ALL' in hosts.deny and nothing in hosts.allow, but I can still ftp to the computer from anywhere else.  I tried 'ALL: ALL' in hosts.deny and 'sshd: ALL' in hosts.allow, but I can still ftp to the machine.

I am using the vsftpd from the repositories, and it appears to be compiled against libwrap:
> ldd /usr/sbin/vsftpd |grep libwrap
        libwrap.so.0 => /lib/libwrap.so.0 (0xb7fc5000)

Now if I run:
> tcpdchk -v   
I get an entry that looks like:
daemons:  vsftpd
warning: /etc/hosts.deny, line 20: vsftpd: no such process name in /etc/inetd.conf
clients:  ALL
access:   denied


But there is no initd running, vsftpd is running standalone mode, and the /etc/initd.conf file is empty
> ps -e|grep ftp
  567 ?        00:00:00 vsftpd

What am I missing?  Is there a way to get a list of daemons affected by hosts.deny?

---

### Post by brian_p on 2008-08-05
> **bj0 said:**
> 

What am I missing?  Is there a way to get a list of daemons affected by hosts.deny?

You do have 'listen=yes' in the configuration file?

---

### Post by bj0 on 2008-08-05
> **brian_p said:**
> You do have 'listen=yes' in the configuration file?

In the /etc/vsftpd.conf yes.

---

### Post by brian_p on 2008-08-05
> **bj0 said:**
> In the /etc/vsftpd.conf yes.

Ok. Plan B:

```
man vsftpd.conf
```

The tcp_wrappers option. The default is 'NO'.

---

### Post by bj0 on 2008-08-05
very nice that worked, thanks.  I searched the example vsftpd.conf file, but that option wasn't in it, I guess I should of checked the man page instead.

---

