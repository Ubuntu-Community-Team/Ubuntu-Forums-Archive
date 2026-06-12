---
title: "Ubuntu LDAP Client"
date: 2010-06-05
forum: Server Platforms
---

### Post by custangro on 2010-06-05
Okay I'm trying to set up my Ubuntu machine to be an LDAP Client but running into trouble...

Here is my */etc/ldap.conf* file...

```

root@canary:~# egrep -v '^#|^$' /etc/ldap.conf 
base dc=rtps,dc=com
uri ldapi:///ldap-lax1.rtps.com
uri ldapi:///ldap-lax2.rtps.com
ldap_version 3
pam_password md5
nss_initgroups_ignoreusers backup,bin,daemon,games,gnats,irc,landscape,libuuid,list,lp,mail,man,news,proxy,root,sshd,sync,sys,syslog,uucp,www-data

```Here is my */etc/nssswitch.conf* file...

```

root@canary:~# egrep -v '^#|^$' /etc/nsswitch.conf 
passwd: files ldap
group: files ldap
shadow: files ldap
hosts:          files dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup: nis

```But when I look for a user...it returns nothing :(

```

root@canary:~# getent passwd chrish
root@canary:~#

```I know it's not my LDAP server because I have 25+ RHEL/CENTOS servers set up as a clients and they work great (why oh why Ubuntu doesn't have *system-config-authentication* I will never know...I mean...I thought Ubuntu was supposed to be "easy" but it's been nothing but trouble since I added it to our network...anyway I'm ranting now)...

Seems to be that it looks like I'm missing something...

Any help would be greatly appreciated :)

---

### Post by custangro on 2010-06-06
Did some debugging...

```

root@canary:~# iptables -F
root@canary:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@canary:~# ldapsearch -x
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
root@canary:~# telnet ldap-gln1 389
Trying 192.168.11.29...
Connected to ldap-gln1.rtps.com.
Escape character is '^]'.

```

And the LDAP server IS accepting connections...like I said...I have 25+ RHEL/CENTOS servers as ldap clients...

```

root@canary:~# nmap ldap-gln1

Starting Nmap 5.00 ( http://nmap.org ) at 2010-06-06 11:01 PDT
Interesting ports on ldap-gln1.rtps.com (192.168.11.29):
Not shown: 989 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
111/tcp  open  rpcbind
**389/tcp  open  ldap**
514/tcp  open  shell
1022/tcp open  unknown
5801/tcp open  vnc-http-1
5901/tcp open  vnc-1
6001/tcp open  X11:1
8443/tcp open  https-alt

```

Just this stubborn Ubuntu box isn't cooperating :(

---

