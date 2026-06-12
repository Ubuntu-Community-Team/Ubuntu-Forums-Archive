---
title: "Strongswan &amp; Playbook issues."
date: 2012-04-12
forum: Server Platforms
---

### Post by zinv on 2012-04-12
Alright im trying to set up strongswan on my ubuntu 10.04 box to my blackberry playbook. WHen attempting to connect to the vpn server i get a timeout error on my playbook. Below is the log.

```
Apr 12 12:17:04 ZORO charon: 01[DMN] Starting IKEv2 charon daemon (strongSwan 4.3.2)
Apr 12 12:17:04 ZORO charon: 01[LIB] loading plugin 'sha1' failed: /usr/lib/ipsec/plugins/libstrongswan-sha1.so: cannot open shared object file: No such file or directory
Apr 12 12:17:04 ZORO charon: 01[LIB] loading plugin 'fips-prf' failed: /usr/lib/ipsec/plugins/libstrongswan-fips-prf.so: cannot open shared object file: No such file or directory
Apr 12 12:17:04 ZORO charon: 01[KNL] listening on interfaces:
Apr 12 12:17:04 ZORO charon: 01[KNL]   eth1
Apr 12 12:17:04 ZORO charon: 01[KNL]     192.168.1.104
Apr 12 12:17:04 ZORO charon: 01[KNL]     fe80::a00:27ff:fe92:7943
Apr 12 12:17:04 ZORO charon: 01[KNL]   ppp0
Apr 12 12:17:04 ZORO charon: 01[KNL]     192.168.1.104
Apr 12 12:17:04 ZORO charon: 01[CFG] loading ca certificates from '/etc/ipsec.d/cacerts'
Apr 12 12:17:04 ZORO charon: 01[CFG] loading aa certificates from '/etc/ipsec.d/aacerts'
Apr 12 12:17:04 ZORO charon: 01[CFG] loading ocsp signer certificates from '/etc/ipsec.d/ocspcerts'
Apr 12 12:17:04 ZORO charon: 01[CFG] loading attribute certificates from '/etc/ipsec.d/acerts'
Apr 12 12:17:04 ZORO charon: 01[CFG] loading crls from '/etc/ipsec.d/crls'
Apr 12 12:17:04 ZORO charon: 01[CFG] loading secrets from '/etc/ipsec.secrets'
Apr 12 12:17:04 ZORO charon: 01[CFG]   loaded IKE secret for %any
Apr 12 12:17:04 ZORO charon: 01[CFG]   loaded EAP secret for zinv
Apr 12 12:17:04 ZORO charon: 01[LIB] loading plugin 'sql' failed: /usr/lib/ipsec/plugins/libstrongswan-sql.so: cannot open shared object file: No such file or directory
Apr 12 12:17:04 ZORO charon: 01[LIB] loading plugin 'attr' failed: /usr/lib/ipsec/plugins/libstrongswan-attr.so: cannot open shared object file: No such file or directory
Apr 12 12:17:04 ZORO charon: 01[CFG] no RADUIS secret defined
Apr 12 12:17:04 ZORO charon: 01[CFG] RADIUS plugin initialization failed
Apr 12 12:17:04 ZORO charon: 01[LIB] loading plugin 'eapradius' failed: plugin_create() returned NULL
Apr 12 12:17:04 ZORO charon: 01[CFG] mediation database URI not defined, skipped
Apr 12 12:17:04 ZORO charon: 01[LIB] loading plugin 'medsrv' failed: plugin_create() returned NULL
Apr 12 12:17:04 ZORO charon: 01[CFG] mediation client database URI not defined, skipped
Apr 12 12:17:04 ZORO charon: 01[LIB] loading plugin 'medcli' failed: plugin_create() returned NULL
Apr 12 12:17:04 ZORO charon: 01[LIB] loading plugin 'resolv-conf' failed: /usr/lib/ipsec/plugins/libstrongswan-resolv-conf.so: cannot open shared object file: No such file or directory
Apr 12 12:17:04 ZORO charon: 01[DMN] loaded plugins: curl ldap random x509 pubkey openssl xcbc hmac agent gmp kernel-netlink stroke updown eapidentity eapmd5 eapgtc eapaka eapmschapv2 nm 
Apr 12 12:17:04 ZORO charon: 01[JOB] spawning 16 worker threads
Apr 12 12:17:04 ZORO charon: 03[CFG] received stroke: add connection 'rem'
Apr 12 12:17:04 ZORO charon: 03[CFG] added configuration 'rem'
Apr 12 12:17:04 ZORO charon: 03[CFG] adding virtual IP address pool 'rem': 192.168.1.120/24
Apr 12 12:17:04 ZORO charon: 08[CFG] received stroke: initiate 'rem'
Apr 12 12:17:04 ZORO charon: 08[IKE] unable to initiate to %any
Apr 12 12:17:13 ZORO charon: 13[NET] received packet: from 75.99.83.90[500] to 192.168.1.104[500]
Apr 12 12:17:13 ZORO charon: 13[ENC] parsed IKE_SA_INIT request 0 [ SA KE No N(NATD_S_IP) N(NATD_D_IP) ]
Apr 12 12:17:13 ZORO charon: 13[IKE] 75.99.83.90 is initiating an IKE_SA
Apr 12 12:17:13 ZORO charon: 13[IKE] local host is behind NAT, sending keep alives
Apr 12 12:17:13 ZORO charon: 13[IKE] remote host is behind NAT
Apr 12 12:17:13 ZORO charon: 13[ENC] generating IKE_SA_INIT response 0 [ SA KE No N(NATD_S_IP) N(NATD_D_IP) N(MULT_AUTH) ]
Apr 12 12:17:13 ZORO charon: 13[NET] sending packet: from 192.168.1.104[500] to 75.99.83.90[500]
Apr 12 12:17:33 ZORO charon: 14[IKE] sending keep alive
Apr 12 12:17:33 ZORO charon: 14[NET] sending packet: from 192.168.1.104[500] to 75.99.83.90[500]
Apr 12 12:17:43 ZORO charon: 15[JOB] deleting half open IKE_SA after timeout
```


Below this are my configuration files:


strongswan.conf

```

# strongswan.conf - strongSwan configuration file

charon {
   	dns1 = 192.168.1.104	
	# number of worker threads in charon
	threads = 16
	
	# plugins to load in charon
	# load = aes des sha1 md5 sha2 hmac gmp random pubkey xcbc x509 stroke
#	load = curl ldap aes des sha1 sha2 md5 random x509 pubkey pkcs1 pgp dnskey pem openssl fips-prf xcbc hmac agent gmp attr kernel-netlink socket-raw  stroke updown eap-identity eap-aka eap-md5 eap-gtc eap-mschapv2 dhcp resolve

	plugins {

		sql {
			# loglevel to log into sql database
			loglevel = -1
			
			# URI to the database
			# database = sqlite:///path/to/file.db
			# database = mysql://user:password@localhost/database
		}
	}
	
	# ...
}

pluto {

	# plugins to load in pluto
	# load = aes des sha1 md5 sha2 hmac gmp random pubkey
	
}

libstrongswan {

	#  set to no, the DH exponent size is optimized
	#  dh_exponent_ansi_x9_42 = no
}

```

ipsec.conf

```

config setup
	strictcrlpolicy=no
	plutostart=no
conn %default
	ikelifetime=60m
	keylife=20m
	rekeymargin=3m
	keyingtries=1
	keyexchange=ikev2
	dpdaction=clear
	dpddelay=300s
conn rem
	left=192.168.1.104
	leftsubnet=0.0.0.0/0
	leftauth=psk
	leftid=zinv@zinvnix.co.cc
	right=%any
	rightsourceip=192.168.1.120/24
	rightauth=eap-mschapv2
	rightsendcert=never
	eap_identity=zinv
	auto=start

```

Id also like to add that im running a pptp vpn on the same box. Could this be interfering with the strongswan connection?

---

