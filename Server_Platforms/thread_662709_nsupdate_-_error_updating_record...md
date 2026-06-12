---
title: "nsupdate - error updating record.."
date: 2008-01-09
forum: Server Platforms
---

### Post by sujathab on 2008-01-09
Hi all,

I have been trying to use nsupdate for dynamic update in my bind server.
The update fails with a message. Please let me know if you can spot some problem. This is what i tried.

- Generate a secret key using
   dnssec-keygen -a HMAC-MD5 -b 128 -n HOST [www.foo.ca](www.foo.ca).
- two files gets created in the current directory with .key and .private extension
- move these keys to /var/named/chroot/etc directory. that is where my named.conf file exists
- Include this statement in named.conf
key  [www.foo.ca](www.foo.ca). {       
        algorithm hmac-md5;
		secret "adsfjiott9054kfahG5+Zg==";
		};
- Update my zone to allow update from this key
zone "foo.ca" in {
	type master;
	file "db.foo.ca";
	allow-transfer { 50.60.70.80; };
	allow-update { key [www.foo.ca.;](www.foo.ca.;) };
	};
- restart the named server
- Run nsupdate command with the following options
nsupdate -k /var/named/chroot/etc/Kwww.foo.ca.+157+55171.key
- this open a prompt
and i enter
   >> update add test.ca. 21600 IN A 127.45.0.1
   >> send

ERROR message which comes back from the above :
; TSIG error with server: tsig indicates error
update failed: NOTAUTH(BADKEY)

Please help me if you know i am doing anything wrong with generating the key and assigning it to the zone. I have been struck in this for two days now.

Any help appreciated.

Thanks in advance

---

