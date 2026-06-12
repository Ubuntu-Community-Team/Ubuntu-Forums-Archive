---
title: "Samba server w/ LDAP"
date: 2010-10-24
forum: Server Platforms
---

### Post by Toast2120 on 2010-10-24
Making a Samba Server with LDAP authentication. Will post as I go along. Found these sources, anything/hiccups I should know before jumping in? Figure would follow the official documentation then check the others for comparative errors.

[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
[https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)
[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

Also

Do other computers that want access to server also need samba installed (or just client)?

The server is 10.04 and my proposed client is 10.10, does this create problems?

Do I need to use ACL? I see them only in certain places.

Using xfce after Ubuntu install, not sure if this matters.

---

### Post by luvshines on 2010-10-24
> **Toast2120 said:**
> Making a Samba Server with LDAP authentication. Will post as I go along. Found these sources, anything/hiccups I should know before jumping in? Figure would follow the official documentation then check the others for comparative errors.

[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
[https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)
[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

Well, you shud go ahead and give it a try :) if you need LDAP as backend authentication. In my opinion, LDAP should be used for large number of users who need to be controlled from a centralised location, have to have Samba SID and NFS UID's  accessing the same data, maybe in office environment
For small number of users, Samba itself can be a good authentication alternative, I mean for home usage
Also

> 
Do other computers that want access to server also need samba installed (or just client)?
They would need only client to access

> The server is 10.04 and my proposed client is 10.10, does this create problems?
Should not be a problem I guess. Although I haven't tried 10.10 at all

> Do I need to use ACL? I see them only in certain places.
You mean LDAP ACL's ? I think that will be required for users connecting to LDAP server itself, I guess. If LDAP will only be a backend, then you can avoid that. But most of the time ppl protect the Samba NTLM hashes and user passwords for public viewing

> Using xfce after Ubuntu install, not sure if this matters.
No comment on this one, haven't tried this

I think it should be pretty simple configuration, though I have always done it with slapd.conf and not cn=config method :)
You should also wait for some expert comments on this, since I am still a newbie

Good Luck !! :)

---

### Post by Toast2120 on 2010-10-24
toast@pasta:/etc/init.d$ sudo smbclient -L localhost
Enter root's password: 
Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)

okay! had this error but fix'd my smb.conf using this thread

[http://ubuntuforums.org/showthread.php?t=1488906](http://ubuntuforums.org/showthread.php?t=1488906)

Now I'm getting a 

session setup failed: Call timed out: server did not respond after 20000 milliseconds

hmmmmm, my internet is slow, but not that bad, besides this shouldn't even leave my house right?

---

### Post by Zeosa on 2010-10-24
That has nothing to do with your internet speed.

Make sure you stored your ldap password in samba with smbpasswd -W.  Check your log files for errors and make sure smbd is running (ps aux | grep smbd). (check /var/log/samba/log.smbd etc)

---

### Post by Toast2120 on 2010-10-25
> **Zeosa said:**
> That has nothing to do with your internet speed.

Make sure you stored your ldap password in samba with smbpasswd -W.  Check your log files for errors and make sure smbd is running (ps aux | grep smbd). (check /var/log/samba/log.smbd etc)

Yeah I think Webmin was slowing me down.

Ok, asked a friend about my situation told me to set up Samba first before I include LDAP. Samba starts but Win7 sure doesn't like it, I get

"Windows cannot access"

copied from somewhere else, this is my /etc/samba/smb.conf
```
[global]
    ; General server settings
    netbios name = pasta
    server string =
    workgroup = WORKGROUP
   ; announce version = 5.0
   ; socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

   ; passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/toast/Public
    path = /media/samba
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = toast
    force group = WORKGROUP
```

Both /home/toast/Public and /media/samba have been chmod 777 access

any ideas?

---

### Post by luvshines on 2010-10-25
There should be only one path under one share name, ie under [MyFiles] here
Also the force group has to be some Linux group present on your machine, WORKGROUP will not do, unless you have WORKGROUP as a group defined on your system
If you have not defined any usermaps, you may want to remove username map as well and make sure every directory in your shared path should be readable by the user you are forcing, which is 'toast' here

---

### Post by Toast2120 on 2010-10-26
Okay! Figured out my Samba issues, feels great. 

Here's my /etc/samba/smb.conf for reference

```
[global]
   ; valid users = ALL
    ; hosts allow = ALL
    ; General server settings
    netbios name =
   ; server string =
   workgroup = WORKGROUP
   ; announce version = 5.0
   ; socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

   ; passdb backend = tdbsam
   ; security = user
   ; null passwords = true
   ; username map = /etc/samba/smbusers
   ; name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = ALL
   ; create mode = 0600
   ; directory mode = 0755
    browseable = yes
    read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/samba
    browseable = yes
    read only = no
    guest ok = yes
   ; create mask = 0644
   ; directory mask = 0755
   ; force user = toast
   ; force group = WORKGROUP
```

Now that Samba is working I'm going to use LDAP for authentication.

Here's the guide
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

Plus the how to on authentication (same page)
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html#openldap-auth-config](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html#openldap-auth-config)

This too
[https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)

Any advice cus this is just simple authentication (school project) drop a line

---

### Post by Toast2120 on 2010-11-01
Do I need a FQDN for LDAP?

---

### Post by luvshines on 2010-11-01
> **Toast2120 said:**
> Do I need a FQDN for LDAP?

You mean ldap uri ??
FQDN is not a compulsion, I always use the short name. As long as it is reachable with short name.
One thing which I can remember is, if you have mentioned FQDN while generating certificate for SSL/TLS, then you have to use FQDN for URI too.

---

### Post by Toast2120 on 2010-11-02
Okay, got a lot further today, felt great.:)

Here's where I'm at in this guide
[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

> sudo smbclient -L localhost

But I keep getting a 
> session setup failed: NT_STATUS_LOGON_FAILURE

Same issue when I type>  smbclient //192.168.1.100/media/samba -U <user> % <passwd>


testparm -sp
> [global]
	obey pam restrictions = Yes
	passdb backend = ldapsam:ldap://localhost
	pam password change = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	server signing = auto
	printcap name = cups
	add user script = /usr/sbin/smbldap-useradd -m '%u'
	delete user script = /usr/sbin/smbldap-userdel %u
	add group script = /usr/sbin/smbldap-groupadd -p '%g'
	delete group script = /usr/sbin/smbldap-groupdel '%g'
	add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
	delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
	set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'
	add machine script = /usr/sbin/smbldap-useradd -w '%u'
	logon script = allusers.bat
	logon path = 
	logon home = 
	domain logons = Yes
	os level = 35
	domain master = Yes
	dns proxy = No
	wins support = Yes
	ldap admin dn = cn=admin,dc=mango.dyndns-web,dc=com
	ldap group suffix = ou=Groups
	ldap idmap suffix = ou=Idmap
	ldap machine suffix = ou=Computers
	ldap passwd sync = yes
	ldap suffix = dc=mango.dyndns-web,dc=com
	ldap ssl = no
	ldap user suffix = ou=Users
	panic action = /usr/share/samba/panic-action %d

[homes]
	valid users = ALL
	read only = No

[print$]
	path = /var/lib/samba/printers
	write list = root
	create mask = 0664
	directory mask = 0775
	guest ok = Yes

[printers]
	path = /tmp
	guest ok = Yes
	printable = Yes
	browseable = No
	browsable = No

[MyFiles]
	path = /media/samba
	read only = No
	guest ok = Yes


My issue can't be a sharing violation as I have opened permissions on everything. Getting it to work first.

---

### Post by luvshines on 2010-11-02
Try this:
```

## For listing the shares
smbclient -L 192.168.1.100 -U<username>%<passwd>

## Access won't happen with shared path, only by share name
smbclient //192.168.1.100/MyFiles -U<username>%<passwd>

```

Also, try ldapsearch command:```

## Replace <...> with actual values
ldapsearch -x -h <ldap-server-ip> -b 'dc=mango.dyndns-web,dc=com' -D cn=<username>,ou=users,dc=mango.dyndns-web,dc=com -w <password>

```

---

### Post by Toast2120 on 2010-11-02
Tried both comments, with output

```
smbclient -L //192.168.1.100 -U <user>%<passwd>
session setup failed: NT_STATUS_LOGON_FAILURE
```
```
smbclient -L 192.168.1.100 -U <user>%<passwd>
session setup failed: NT_STATUS_LOGON_FAILURE
```

```
ldapsearch -x -h 192.168.1.100 -b 'dc=mango.dyndns-web,dc=com' -D cn=<user>,ou=users,dc=mango.dyndns-web,dc=com -w <passwd>
ldap_bind: Invalid credentials (49)
```

```
ldapsearch -x -h //192.168.1.100 -b 'dc=mango.dyndns-web,dc=com' -D cn=<user>,ou=users,dc=mango.dyndns-web,dc=com -w <passwd>
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
```


Server is always running. Trying logging in as guest, but that doesn't seem to work and guest is approved.

Did some more looking found to do 

```
ldapsearch mango.dyndns-web.com
SASL/DIGEST-MD5 authentication started
Please enter your password: 
ldap_sasl_interactive_bind_s: Invalid credentials (49)
	additional info: SASL(-13): user not found: no secret in database

```

So I tried adding a user

```
sudo smbldap-useradd -a -m -P <user>
Unable to open /etc/opt/IDEALX/smbldap-tools/smbldap.conf for reading !
Compilation failed in require at /usr/sbin/smbldap-useradd line 30.
BEGIN failed--compilation aborted at /usr/sbin/smbldap-useradd line 30.

```


I tried looking for the /etc/opt/IDEALX/smbldap-tools/smbldap.conf file to troubleshoot, but it doesn't exist!

---

### Post by luvshines on 2010-11-02
**"Invalid credentials"**
Something looks wrong with the user which you are trying to use.

Some questions:

1. Is this user added to LDAP server ? Also, Samba attributes set for this user ?
2. Can you list it with ldapsearch
```

## Replace <...> with proper values
ldapsearch -x -D cn=admin,dc=mango.dyndns-web,dc=com -w <ldap-admin-passwd> -b dc=mango.dyndns-web,dc=com "(|(cn=<user-name>)(uid=<user-name>))"

```

---

### Post by Toast2120 on 2010-11-02
Okay I've realized that I never set a LDAP password. But I did change a password in /etc/ldap/backend.ldif does that file correspond to my LDAP login?

So I tried changing the root password.
```
root@pasta:/etc/ldap# ldappasswd 
SASL/DIGEST-MD5 authentication started
Please enter your password: 
ldap_sasl_interactive_bind_s: Invalid credentials (49)
	additional info: SASL(-13): user not found: no secret in database

```

So I tried adding the user 
```
root@pasta:/etc/ldap# sudo ldapadd -x -D cn=admin,dc=root,dc=local -W -f users.ldif
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)
```

Can't change root password without adding user, can't add user without changing password. I screwed up bad somewhere, probably in a text file.

Think my issue has to do with backend.ldif or frontend.ldif

Is it best for me to start over?

---

### Post by david.garceau on 2010-11-02
Honestly, in my experiences for me atleast... it has been better for me to start over. You realise a lot when you start over and its great to get the experience. Take good notes each time so you know where you messed up :)

---

### Post by luvshines on 2010-11-03
> **Toast2120 said:**
> Okay I've realized that I never set a LDAP password. But I did change a password in /etc/ldap/backend.ldif does that file correspond to my LDAP login?

So I tried changing the root password.
```
root@pasta:/etc/ldap# ldappasswd 
SASL/DIGEST-MD5 authentication started
Please enter your password: 
ldap_sasl_interactive_bind_s: Invalid credentials (49)
	additional info: SASL(-13): user not found: no secret in database

```

So I tried adding the user 
```
root@pasta:/etc/ldap# sudo ldapadd -x -D cn=admin,dc=root,dc=local -W -f users.ldif
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)
```

Can't change root password without adding user, can't add user without changing password. I screwed up bad somewhere, probably in a text file.

Think my issue has to do with backend.ldif or frontend.ldif

Is it best for me to start over?

I have never gone by cn=config way, and has always been using the older method of /etc/ldap/slapd.conf method :)

This link [https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html) explains how to set rootPasswd(ldapmodify command). See if this helps

**PS: And don't reinstall LDAP server plz...**

---

