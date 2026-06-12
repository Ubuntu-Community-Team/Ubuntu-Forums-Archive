---
title: "can't access ldap server OR client isn't conf'ed correctly..."
date: 2012-02-02
forum: Server Platforms
---

### Post by alsdkjhf23465 on 2012-02-02
Hello everyone,
I seem to be in a complete stall as to how or why I can't seem to get a client pc to connect to an LDAP server....

ubuntu version is  11.10.
I started off using this tutorial
[https://help.ubuntu.com/11.10/serverguide/C/openldap-server.html]("https://help.ubuntu.com/11.10/serverguide/C/openldap-server.html")

which helped in setting up the LDAP server on a server machine.
I also added TLS support (chapter "TLS") but i didn't follow chapters "replication" or "replication and TLS".

Then I went on to configure the client (chapter "LDAP Authentication").

I followed the steps again and again , reconfigured the package ldap-auth-config but had no luck..

since yesterday I have read/tried countless tutorials, (for different versions of ubuntu, different distros).. but I haven't managed to get the command
> getent passwd
to fetch some ldap users that exist only in the ldap server DIT.

The thing is I don't know if there is a problem with the client config of some problem with the LDAP server (btw -firewalls are down on both the ldap server and client), and I can't find a single tutorial to help me give me some sort of command that does ldap queries from the client side, just to see if the server responds to it!!

what's more, I am extremely confused at this point at the differences between libnss-ldap, libpam-ldap, libpam-ldapd, libnss-ldapd (if that thing even exists - i can't remember all the different options for authentication I came across) and the list can go on.

where should files be located in the client? /etc/ or /etc/ldap/ ?
how should they be called? libnss-ldap.conf? libpam-ldap.conf? something else? what else is needed?

Can someone help with checking the contents of my client config files? As I have very ZERO experience with pam, nss, and ldap ...

Thank you for your help

here are some of the relevant files (ask for it if I forgot something)

> nass@server00:/etc$ ls -l /etc/lib*
-rw-r--r-- 1 root root   76 2012-02-02 13:10 libnss-ldap.conf
-rw-r--r-- 1 root root   76 2012-02-02 13:06 libnss-ldap.conf-dpkg.old
-r--r----- 1 root root    6 2012-02-02 13:06 libnss-ldap.secret


as well as

> nass@server00:/etc$ sudo ls -l /etc/ld* 
-rw-r--r-- 1 root root  9136 2012-02-02 13:08 /etc/ldap.conf
-rw------- 1 root root     6 2012-02-02 13:08 /etc/ldap.secret

> nass@server00:/etc$ sudo ls -l /etc/pam*
-rw-r--r-- 1 root root  552 2011-08-19 04:05 /etc/pam.conf
-rw-r--r-- 1 root root   76 2012-02-02 13:10 /etc/pam_ldap.conf
-r--r----- 1 root root    6 2012-02-02 13:11 /etc/pam_ldap.secret
drwxr-xr-x 2 root root 4096 2012-02-02 14:01 pam.d


and the file contents are 
> nass@server00:/etc$ cat /etc/libnss-ldap.conf
host ldap
base dc=da,dc=asfa,dc=gr
rootbinddn cn=admin,dc=da,dc=asfa,dc=gr 

/etc/libnss-ldap.conf is the same as /etc/pam_ldap.conf
the relevant .secret files are the same too (contain only the plain text LDAP root user password (why should that exist on a client pc, i don't know - but the ncurses dpkg-reconfigure ldap-auth-config asked for it)

also,
```
nass@server00:/etc$ cat /etc/ldap.conf | egrep -v '^(#|$)' 
base dc=da,dc=asfa,dc=gr
uri ldapi:///da.asfa.gr
ldap_version 3
rootbinddn cn=admin,dc=da,dc=asfa,dc=gr
pam_password exop
nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,colord,daemon,games,gnats,hplip,irc,kernoops,libuuid,lightdm,list,lp,mail,man,messagebus,mysql,news,nslcd,proxy,pulse,root,rtkit,saned,speech-dispatcher,sshd,sync,sys,syslog,usbmux,uucp,www-data

```

the /etc/pam.d/common-* files
> nass@server00:/etc$ cat /etc/pam.d/common-* | egrep -v '^(#|$)' 
account [success=2 new_authtok_reqd=done default=ignore]        pam_unix.so 
account [success=1 default=ignore]      pam_ldap.so 
account requisite                       pam_deny.so
account required                        pam_permit.so
auth    [success=2 default=ignore]      pam_unix.so nullok_secure
auth    [success=1 default=ignore]      pam_ldap.so use_first_pass
auth    requisite                       pam_deny.so
auth    required                        pam_permit.so
password        [success=2 default=ignore]      pam_unix.so obscure sha512
password        [success=1 user_unknown=ignore default=die]     pam_ldap.so use_authtok try_first_pass
password        requisite                       pam_deny.so
password        required                        pam_permit.so
session [default=1]                     pam_permit.so
session requisite                       pam_deny.so
session required                        pam_permit.so
session optional                        pam_umask.so
session required        pam_unix.so 
session optional                        pam_ldap.so 
session [default=1]                     pam_permit.so
session requisite                       pam_deny.so
session required                        pam_permit.so
session optional                        pam_umask.so
session required        pam_unix.so 
session optional                        pam_ldap.so 


I think that's about it.
If you need something else, let me know,
If there is any command that I can use on the client side to check connectivity to LDAP server, please let me know!!!!

Thank you very much for your help.
Nass

---

### Post by luvshines on 2012-02-04
Assuming that the server has been setup properly (in basic mode, no TLS etc security).

To check that client is able to contact ldap server you can use> nc -zv <ldap-server-name> 389 ## This is assuming that you'll be using standard 389 port for LDAP
## Also if it's not reachable by name, then try IP there 

If that works then you'll need to setup your libnss file, like you have done it already (make sure if you use name in uri, the server was reachable by it's name with 'nc' command). In my setups it has always been ldap:// or ldaps://

In your setup what I think missing is ldap in /etc/nsswitch.conf file. What does following say> egrep '^passwd|^group' /etc/nsswitch.conf

---

