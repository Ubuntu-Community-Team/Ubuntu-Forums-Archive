---
title: "SAMBA Can't join domain:"
date: 2008-12-16
forum: Server Platforms
---

### Post by muckv on 2008-12-16
Hey guys, This samba config is driving me NUTS

I have to join our domain because I need amanda to pull files from  domain xp computers

I'll start with smb.conf

```


[global]

security = ads
password server = PDC ip ,DC ip, DC ip
encrypt passwords = yes
domain master = no
local master = no
enhanced browsing = yes
idmap uid = 10000-20000
idmap gid = 10000-20000
use spnego = yes
wins server = 172.X.X.X



workgroup = XDOMAIN
realm = XDOMAIN.COM

winbind use default domain = yes
winbind enum groups = yes
winbind enum users = yes
winbind trusted domains only = no


[homes]

comment = Home Directories
browseable = yes
writeable = yes


```

Here is the krb5.conf


```

[libdefaults]
	default_realm = XDOMAIN.COM
	krb4_config = /etc/krb.conf
	krb4_realms = /etc/krb.realms
	kdc_timesync = 1
	ccache_type = 4
	forwardable = true
	proxiable = true
	v4_instance_resolve = false
	v4_name_convert = {
		host = {
			rcmd = host
			ftp = ftp
		}
		plain = {
			something = something-else
		}
	}
	fcc-mit-ticketflags = true
	default_tgs_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
	default_tkt_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
	preferred_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
	dns_lookup_kdc = true


[realms]
	XDOMAIN.COM = {

		auth_to_local = DEFAULT		
		kdc = HOSTNAMEPDC
		kdc = HOSTNAMEBDC
		kdc = HOSTNAMEBDC
		kdc = HOSTNAMEBDC
		default_domain = XDOMAIN.COM
		admin_server = HOSTNAMEPDC
		
	
[domain_realm]
	
	.xdomain.com =	XDOMAIN.COM
	xdomain.com = XDOMAIN.COM

[login]
	krb4_convert = true
	krb4_get_tickets = false


```


Here is the Kinit admin ouput

```

Default principal: admin@XDOMAIN.COM

Valid starting     Expires            Service principal
12/16/08 15:51:00  12/17/08 01:51:04  krbtgt/XDOMAIN.COM@XDOMAIN.COM
	renew until 12/17/08 15:51:00


Kerberos 4 ticket cache: /tmp/tkt0
klist: You have no tickets cached


```

here is my hosts file

```


127.0.0.1	localhost
127.0.1.1	amandasrv.xdomain.com	                amandasrv
172.X.X.X       PDC.xdomain.com		                PDC
172.X.X.X       BDC.xdomain.com			        BDC
172.X.X.X   	BDC.xdomain.com			        BDC
172.X.X.X   	BDC.xdomain.com			        BDC



```

```

and finally my resolv.conf

domain xdomain.com
search xdomain.com
nameserver 198.X.X.X
nameserver 198.X.X.X

```


Here is the output of 
sudo net join ads [email]-Uadmin@XDOMAIN.COM[/email]

```

Enter admin@XDOMAIN.COM's password:
Failed to join domain: failed to find DC for domain ads
ADS join did not work, falling back to RPC...
Unable to find a suitable server
Unable to find a suitable server
root@bdpamandasrv:/home/bram# 



```

Any ideas?

---

### Post by asommer on 2008-12-16
Not sure if your familiar with likewise-open, but it takes the pain out of joining an AD domain:

[https://help.ubuntu.com/8.10/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.10/serverguide/C/likewise-open.html)

That's the guide for Intrepid, but likewise-open is also available for Hardy.  You might give it a try and see how it goes.

---

### Post by muckv on 2008-12-18
I joined the domain with likewise, thanks

Suppose I want to make a backup of a ntfs drive on an xp computer
with amanda.

DO I have to make the backup as a domain admin, if so then winbind should be configured accodingly right?

---

### Post by asommer on 2008-12-18
It would depend on the permissions that are set on the drive that you want to setup, as far as using a Domain Admin.  If you are wanting to backup every file on the drive a domain admin should have rights to access all the files.

Winbind shouldn't need to be configured to do anything special.  likewise-open has it's own winbind daemon, which should be configured once you join the domain.

---

