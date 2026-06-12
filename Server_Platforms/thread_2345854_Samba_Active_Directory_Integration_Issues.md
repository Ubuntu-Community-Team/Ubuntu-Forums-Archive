---
title: "Samba Active Directory Integration Issues"
date: 2016-12-08
forum: Server Platforms
---

### Post by grotmos on 2016-12-08
Hey Folks,

Long time dabbler of Ubuntu. I can normally fix most of my issues with a few good Google searches but I have repeatedly come up empty handed with this one. 
So I recently set up a Ubuntu server at work that has a samba SMB share on it for an office copier that can scan to a network drive.
(Its a copy of ubuntu 16.04 with the samba set-up.) 
 
I was able to do that with this guide : [https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)

I had the copier sending scans to it no problem. Everything was great, but we needed to lock it down with Active directory for secuirity. I found this article on the samba wiki to help me out: [https://wiki.samba.org/index.php/Setup_Samba_as_an_AD_Domain_Member](https://wiki.samba.org/index.php/Setup_Samba_as_an_AD_Domain_Member)

I manged to set up everything up with the DNS and Kerberos. I joined AD and am able to see users and group, with **[FONT=courier new]wbinfo -u[/FONT]** and **[FONT=courier new]wbinfo -g[/FONT]** I can ping things with their FQDN. I can use **[FONT=courier new]kinit[/FONT]** and **[FONT=courier new]klist[/FONT]** to see that I'm getting tickets from the kerberos server. 

But I can not for the life of me get **[FONT=courier new]id user[/FONT]** or **[FONT=courier new]getent passwd user[/FONT]** to show users.

I'm pretty sure it has something to do with ldap and my nsswitch.cong but I've been poking around the internet and have not been able to find a solution.

```
# /etc/nsswitch.conf#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.


passwd: files ldap
group: files ldap
shadow: files ldap
gshadow:        files


hosts:          dns files
networks:       nis files


protocols:      db files
services:       db files
ethers:         nis files
rpc:            db files


netgroup: nis



```

---

### Post by volkswagner on 2016-12-08
Here's what I have on Ubuntu 14.04 member of SAMBA4 AD

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat winbind
group:          compat winbind
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

---

### Post by grotmos on 2016-12-08
@volkswagner

I just updated mine and rebooted the system and restarted winbind, smbd, and nmbd. Still in the same situation. id username returns user not found. 

Any troubleshooting ideas?

---

### Post by volkswagner on 2016-12-08
Can you post additional details of your environment.

Active Directory DC operating system?

smb.conf
```
testparm -s
```

krb5.conf
```
cat /etc/krb5.conf
```

---

### Post by grotmos on 2016-12-08
AD is running in Windows Server 2012.

TESTPARM
```
# Global parameters
[global]
	workgroup = EXAMPLE
	realm = EXAMPLE.NET
	server string = %h server (Samba, Ubuntu)
	server role = member server
	security = ADS
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 100000
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap uid = 50-99999999999
	idmap gid = 50-99999999999
	idmap config * : range = 50-99999999999
	idmap config * : backend = tdb
	directory mask = 0775
	directory mode = 0775




[scans]
	comment = Scanner SMB Share
	path = /srv/samba/scans
	read only = No
	create mask = 0755
	guest ok = Yes




[TEST]
	comment = TEST
	path = /srv/samba/scans/Technology\ Dept/
	read list = @TECHNOLOGYDEPT @Technology
	write list = @TECHNOLOGYDEPT @Technology




[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No




[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers



```

```

[libdefaults]
	default_realm = EXAMPLE.NET
[realms]
  EXAMPLE.NET = {
   kdc = 10.100.236.246
   admin_server = DC.EXAMPLE.net
   kpasswd_server = 10.100.236.246
   }
WORKGROUP = {
	kdc = 10.100.236.246
	admin_server = DC.EXAMPLE.net
	default_domain = EXAMPLE.NET
	}


# The following krb5.conf variables are only for MIT Kerberos.
	krb4_config = /etc/krb.conf
	krb4_realms = /etc/krb.realms
	kdc_timesync = 1
	ccache_type = 4
	forwardable = true
	proxiable = true


# The following encryption type specification will be used by MIT Kerberos
# if uncommented.  In general, the defaults in the MIT Kerberos code are
# correct and overriding these specifications only serves to disable new
# encryption types as they are added, creating interoperability problems.
#
# Thie only time when you might need to uncomment these lines and change
# the enctypes is if you have local software that will break on ticket
# caches containing ticket encryption types it doesn't know about (such as
# old versions of Sun Java).


#	default_tgs_enctypes = des3-hmac-sha1
#	default_tkt_enctypes = des3-hmac-sha1
#	permitted_enctypes = des3-hmac-sha1


# The following libdefaults parameters are only for Heimdal Kerberos.
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


[realms]
	ATHENA.MIT.EDU = {
		kdc = kerberos.mit.edu:88
		kdc = kerberos-1.mit.edu:88
		kdc = kerberos-2.mit.edu:88
		admin_server = kerberos.mit.edu
		default_domain = mit.edu
	}
	MEDIA-LAB.MIT.EDU = {
		kdc = kerberos.media.mit.edu
		admin_server = kerberos.media.mit.edu
	}
	ZONE.MIT.EDU = {
		kdc = casio.mit.edu
		kdc = seiko.mit.edu
		admin_server = casio.mit.edu
	}
	MOOF.MIT.EDU = {
		kdc = three-headed-dogcow.mit.edu:88
		kdc = three-headed-dogcow-1.mit.edu:88
		admin_server = three-headed-dogcow.mit.edu
	}
	CSAIL.MIT.EDU = {
		kdc = kerberos-1.csail.mit.edu
		kdc = kerberos-2.csail.mit.edu
		admin_server = kerberos.csail.mit.edu
		default_domain = csail.mit.edu
		krb524_server = krb524.csail.mit.edu
	}
	IHTFP.ORG = {
		kdc = kerberos.ihtfp.org
		admin_server = kerberos.ihtfp.org
	}
	GNU.ORG = {
		kdc = kerberos.gnu.org
		kdc = kerberos-2.gnu.org
		kdc = kerberos-3.gnu.org
		admin_server = kerberos.gnu.org
	}
	1TS.ORG = {
		kdc = kerberos.1ts.org
		admin_server = kerberos.1ts.org
	}
	GRATUITOUS.ORG = {
		kdc = kerberos.gratuitous.org
		admin_server = kerberos.gratuitous.org
	}
	DOOMCOM.ORG = {
		kdc = kerberos.doomcom.org
		admin_server = kerberos.doomcom.org
	}
	ANDREW.CMU.EDU = {
		kdc = kerberos.andrew.cmu.edu
		kdc = kerberos2.andrew.cmu.edu
		kdc = kerberos3.andrew.cmu.edu
		admin_server = kerberos.andrew.cmu.edu
		default_domain = andrew.cmu.edu
	}
	CS.CMU.EDU = {
		kdc = kerberos.cs.cmu.edu
		kdc = kerberos-2.srv.cs.cmu.edu
		admin_server = kerberos.cs.cmu.edu
	}
	DEMENTIA.ORG = {
		kdc = kerberos.dementix.org
		kdc = kerberos2.dementix.org
		admin_server = kerberos.dementix.org
	}
	stanford.edu = {
		kdc = krb5auth1.stanford.edu
		kdc = krb5auth2.stanford.edu
		kdc = krb5auth3.stanford.edu
		master_kdc = krb5auth1.stanford.edu
		admin_server = krb5-admin.stanford.edu
		default_domain = stanford.edu
	}
        UTORONTO.CA = {
                kdc = kerberos1.utoronto.ca
                kdc = kerberos2.utoronto.ca
                kdc = kerberos3.utoronto.ca
                admin_server = kerberos1.utoronto.ca
                default_domain = utoronto.ca
	}


[domain_realm]
	.mit.edu = ATHENA.MIT.EDU
	mit.edu = ATHENA.MIT.EDU
	.media.mit.edu = MEDIA-LAB.MIT.EDU
	media.mit.edu = MEDIA-LAB.MIT.EDU
	.csail.mit.edu = CSAIL.MIT.EDU
	csail.mit.edu = CSAIL.MIT.EDU
	.whoi.edu = ATHENA.MIT.EDU
	whoi.edu = ATHENA.MIT.EDU
	.stanford.edu = stanford.edu
	.slac.stanford.edu = SLAC.STANFORD.EDU
        .toronto.edu = UTORONTO.CA
        .utoronto.ca = UTORONTO.CA


[login]
	krb4_convert = true
	krb4_get_tickets = false



```

---

### Post by grotmos on 2016-12-08
SIDE NOTE: If I use user@workgroup for id username or getent passwd username, that works.

---

### Post by volkswagner on 2016-12-09
> **grotmos said:**
> SIDE NOTE: If I use user@workgroup for id username or getent passwd username, that works.

So it is working, just not without adding domain name?

You can try specify use default domain in smb.conf

```
winbind use default domain = Yes
```

For testing purposes you can also add the following to smb.conf
```
	winbind enum users = Yes
	winbind enum groups = Yes
```


Did you get error message when running testparm


Your krb5.conf looks a little different than mine, but I struggled with config as well. I'm not sure if mine is standard.

Here's what I have for krb5.conf:
```
[logging]
    default = FILE:/var/log/krb5libs.log
    kdc = FILE:/var/log/krb5kdc.log
    admin_server = FILE:/var/log/kadmind.log
		 
[libdefaults]
    default_realm = HOME.LOCAL
    ticket_lifetime = 24h
    forwardable = yes


[realms]
    HOME.LOCAL = {
        kdc = dc1.home.local
        admin_server = dc1.home.local
        default_domain = HOME.LOCAL
    }

[domain_realm]
    .home.local = HOME.LOCAL
    home.local = HOME.LOCAL		 


[appdefaults]
    pam = {
        debug = false
        ticket_lifetime = 36000
        renew_lifetime = 36000
        forwardable = true
        krb4_convert = false
    } 
```

---

### Post by grotmos on 2016-12-09
Appreciate the help Volkswagner.

I updated accordingly, things are still where they were yesterday. However when I added [COLOR=#000000][FONT=&amp]winbind use default domain = Yes [/FONT][/COLOR] to my smbd.conf id username@domain stopped working until I removed it again. 

I am confused about the [Domain_realm] part in your krb5.conf file.

---

### Post by volkswagner on 2016-12-09
I'm no expert ;)

The [Domain_realm] in krb5.conf is there because I saw it used in the MIT examples.

What isn't working? Isn't username@domain an acceptable syntax?
Can users authenticate and access your samba server?

---

### Post by grotmos on 2016-12-13
Sorry for the late response, this got away from me over the weekend. I was under the impression that you can't use the username@domain syntax for ads security.

example:
```

read list = username@domain
write list = username@domain

```

At least for me that doesn't seem to work.(Admittedly I do need to read more about samba ads security)

---

### Post by volkswagner on 2016-12-13
Unfortunately I can't be more help. I don't have any system with the same behavior.

In smb.conf you could try:

```
read list = 'username@domain'
write list = 'username@domain'
```

or

```
read list = "username@domain"
write list = "username@domain"
```

---

