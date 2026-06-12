---
title: "Ubuntu File Server on AD 2003 Network"
date: 2008-09-19
forum: Server Platforms
---

### Post by smirnoff76 on 2008-09-19
I am in the process of setting up an ubuntu file and print server for testing purposes on a windows 2003 server network. 

I have the server authenticating against the domain using Likewise and am now doing the additional work required so that the server can be used as a file server. 

I have just edited the file krb5.con so that it now looks like this (our domain name has been edited for the purpose of this post due to office policy):

-------------------------------------
[libdefaults]
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
	default_realm = MYDOMAIN.LOCAL

#Additional Entry by Admin
#
#
		ticket_lifetime = 600       
		default_realm = YOURDOMAIN         
		default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc         
		default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc  

#End of Admin Entry
#
#

# The following krb5.conf variables are only for MIT Kerberos.

# The following encryption type specification will be used by MIT Kerberos
# if uncommented.  In general, the defaults in the MIT Kerberos code are
# correct and overriding these specifications only serves to disable new
# encryption types as they are added, creating interoperability problems.

#	default_tgs_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5
#	default_tkt_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5
#	permitted_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5

# The following libdefaults parameters are only for Heimdal Kerberos.

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
		kdc = vice28.fs.andrew.cmu.edu
		kdc = vice2.fs.andrew.cmu.edu
		kdc = vice11.fs.andrew.cmu.edu
		kdc = vice12.fs.andrew.cmu.edu
		admin_server = vice28.fs.andrew.cmu.edu
		default_domain = andrew.cmu.edu
	}
	CS.CMU.EDU = {
		kdc = kerberos.cs.cmu.edu
		kdc = kerberos-2.srv.cs.cmu.edu
		admin_server = kerberos.cs.cmu.edu
	}
	DEMENTIA.ORG = {
		kdc = kerberos.dementia.org
		kdc = kerberos2.dementia.org
		admin_server = kerberos.dementia.org
	}
	stanford.edu = {
		kdc = krb5auth1.stanford.edu
		kdc = krb5auth2.stanford.edu
		kdc = krb5auth3.stanford.edu
		admin_server = krb5-admin.stanford.edu
		default_domain = stanford.edu
	}
	MYDOMAIN.Local = {
		auth_to_local = RULE:[1:$0\$1](^DOMAIN\.LOCAL\\.*)s/^DOMAIN\.LOCAL/MY_DOMAIN/
		auth_to_local = DEFAULT
	}

#Additional Entry by Admin
#
	MYDOMAIN.Local = {         
			kdc = 192.168.2.21         
			default_domain = MYDOMAIN.Local         
		}  
#End of entry
 

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
#Additional Entry by Admin
	.MYDOMAIN.Local = MYDOMAIN.Local
	MYDOMAIN.Local = MYDOMAIN.Local
#end of entry

[login]
	krb4_convert = true
	krb4_get_tickets = false
[appdefaults]
	pam = {
   mappings = MY_DOMAIN\\(.*) $1@MYDOMAIN.Local
   forwardable = true
   validate = true
	}
	httpd = {
   mappings = MY_DOMAIN\\(.*) $1@MYDOMAIN.Local
   reverse_mappings = (.*)@DOMAIN\.LOCAL MY_DOMAIN\$1
	}

#Additional Entry by Admin
[kdc]         
		profile = /etc/krb5kdc/kdc.conf  
[logging]         
		kdc = FILE:/var/log/krb5kdc.log         
		admin_server = FILE:/var/log/kadmin.log         
		default = FILE:/var/log/krb5lib.logog  
----------------------------------------

when i go to terminal and use the command kinit Username@DOMAIN i get an error returned KDC Reply did not match expectations while getting initial credentials. 

I know it is talking to the AD server okay as when I type in invalid credentials I get back Preauthentication failed while getting initial credentials. 

Any help would be greatly appreciated!

---

