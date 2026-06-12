---
title: "How to get winbind working for squid... help"
date: 2009-08-17
forum: Server Platforms
---

### Post by Avinash.Rao on 2009-08-17
Hi,

I am using ubuntu 8.04 server 64-bit edition. I have installed samba 3.0.28a using apt-get command and its configured as a PDC and winxp clients are able to login to the samba domain and use the shared resources. My server also runs squid for proxy.

I am in need to controlling Internet access for the domain users who login to the domain from winXP, say for example they get to access internet only from 6:00-8:00PM and few users from 10-12:00AM. 

I am trying to do this from [http://wiki.squid-cache.org/ConfigExamples/Authenticate/Ntlm](http://wiki.squid-cache.org/ConfigExamples/Authenticate/Ntlm) and in this even before the squid configuration, there is any instruction to check wbinfo.. winbindd process is running..  

The basic winbindd functionality "wbinfo -t": is not successful

wbinfo -t
checking the trust secret via RPC calls failed
error code was NT_STATUS_DOMAIN_CONTROLLER_NOT_FOUND (0xc0000233)
Could not check secret

Even, wbinfo -a mydomain\\myuser%mypasswd is unsuccessful

I don't have a windows NT domain in my network, i only have winxp clients and they are configured to login to the samba domain. How do i get winbind working so that i can start configuring squid, or is it needed at all??

Thanks
Avinash

---

### Post by koenn on 2009-08-17
> **Avinash.Rao said:**
>  I have installed samba 3.0.28a using apt-get command and its configured as a PDC [ ... ]

I don't have a windows NT domain in my network, i only have winxp clients and they are configured to login to the samba domain. How do i get winbind working so that i can start configuring squid, or is it needed at all??


If you have samba as PDC, *that* is your NT domain controller

---

### Post by Avinash.Rao on 2009-08-17
Ya, I realized that and i followed the instructions in [http://www.debian-administration.org/article/Question_Winbind_on_samba_PDC](http://www.debian-administration.org/article/Question_Winbind_on_samba_PDC).

But wbinfo -u still gives error. 
root@human:/etc/squid# wbinfo -u
Error looking up domain users

root@human:/etc/squid# wbinfo -g
BUILTIN\administrators
BUILTIN\users

wbinfo -t
checking the trust secret via RPC calls succeeded

But it doesn't say "secret is good"!


QUOTE=koenn;7801313]If you have samba as PDC, *that* is your NT domain controller[/QUOTE]

---

### Post by koenn on 2009-08-17
does
```
	getent passwd
	getent group

```
produce anything ?

---

### Post by Avinash.Rao on 2009-08-18
gentent passwd and gentent group works.
The first one displays /etc/passwd i guess and the second all the groups.

> **koenn said:**
> does
```
	getent passwd
	getent group

```
produce anything ?

---

### Post by Avinash.Rao on 2009-08-18
hi, 

Thanks for the above information.I have samba and squid on the same machine. Its running on a Ubuntu 8.04 server 64-bit edition. Samba is configured as PDC and there is NO other Windows NT server on the network. I have winXP clients that login to the samba domain. I am trying to make winbind work so that i could control domain users access to internet through [http://wiki.squid-cache.org/ConfigExamples/Authenticate/Ntlm](http://wiki.squid-cache.org/ConfigExamples/Authenticate/Ntlm)


I followed the instructions in the url [http://www.debian-administration.org...d_on_samba_PDC](http://www.debian-administration.org...d_on_samba_PDC) to get winbindd working. After making the changes in /etc/nsswitch.conf file, After making the changes in /etc/nsswitch.conf file, here's what is happening..

wbinfo -t
checking the trust secret via RPC calls succeeded
I don't get the output the 'secret is good' 

what is happening is, after i reboot the server, none of the wbinfo command works, it says access is denied. it worked after i again joined the machine to the domain using net join command. 

How do i solve this?

Thanks
Avinash

---

### Post by koenn on 2009-08-18
> **Avinash.Rao said:**
> gentent passwd and gentent group works.
The first one displays /etc/passwd i guess and the second all the groups.
if you have a domain and winbind, getent would list domain users|groups as well, be it in unux password or unix group format.
I gather that once you have your domain users/groups in a unix format, using them in  squid's acl's wouldn't be too hard. 

do you mention winbind in /etc/nsswitch.conf ?

---

### Post by Avinash.Rao on 2009-08-19
Here's my nsswitch.conf file

passwd:         files winbind
group:          files winbind
shadow:         files winbind 

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 winbind
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

Yes, thats wat i am trying to accomplish, get the windows groups working in unix.. The only difference is i Don't have a Windows NT server, i have one server which runs samba as PDC and Squid... so i am still figuringing out what to do.. 

net rpc group list -Uroot%secret
Could not connect to server 127.0.0.1
Connection failed: NT_STATUS_CONNECTION_REFUSED

Ok tell me something.. I have configured samba as a PDC and i have created users using smbpasswd command, that means i have a populated domain. wbinfo -g gives 
BUILTIN administrators
BUILTIN users

wbinfo -u gives Error looking up domain users
why cant it display the domain users??



> **koenn said:**
> if you have a domain and winbind, getent would list domain users|groups as well, be it in unux password or unix group format.
I gather that once you have your domain users/groups in a unix format, using them in  squid's acl's wouldn't be too hard. 

do you mention winbind in /etc/nsswitch.conf ?

---

### Post by koenn on 2009-08-19
could you post the global section of your smb.conf ?
(& use the code tags; the #-button in the forum reply editor tool bar)

---

### Post by Avinash.Rao on 2009-08-20
```
[global]
    workgroup = abc
    server string = Samba on SUN
    max log size = 1500
    log level = 1
    interfaces = eth2 100.100.100.251
    bind interfaces only = True
    log file = /var/log/samba/log.%m

    domain logons = yes
    os level = 65
    prefered master = yes
    domain master = yes
    local master = yes

    logon home = 
    logon path =
    logon script = logon.bat

    winbind gid = 10000-20000
    winbind use default domain = yes
    idmap uid = 0-20000
    idmap gid = 0-20000 
    add machine script = /usr/sbin/useradd -s /bin/false -d /home/nobody %u
    dns proxy =No
    hosts allow = 127. 10.10.10.
    wins support = Yes
    passdb backend = tdbsam
    
    encrypt passwords = true
    smb passwd file = /etc/samba/smbpasswd
    security = user
    netbios name = sunbox
    username map = /etc/samba/smbusers   

[homes]
    comment = Home Dir
    read only = NO
    browseable = NO
    valid users = %S
    path = %H
    directory mask = 0700
    create mask = 0700
    
[share]
    comment = Common Share
    path = /sambashare
    valid users = nimda
    create mask = 0765

[netlogon]
	comment = The domain logon service
	path = /export/samba/logon
	public = no
	writeable = no
	browsable = no
        root preexec = /export/samba/logon/bckoperator.sh %U %m

```



> **koenn said:**
> could you post the global section of your smb.conf ?
(& use the code tags; the #-button in the forum reply editor tool bar)

---

