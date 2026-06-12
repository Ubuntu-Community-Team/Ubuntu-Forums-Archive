---
title: "openvpn: error revoking certificate"
date: 2008-04-17
forum: Server Platforms
---

### Post by Underpants on 2008-04-17
Trying to revoke a cert per the openvpn.net howto. Getting this error. Anyone know what's up?


```


root@boxen:/usr/share/doc/openvpn/examples/easy-rsa/2.0# ./revoke-full client1
Using configuration from /usr/share/doc/openvpn/examples/easy-rsa/2.0/openssl.cnf
error on line 282 of config file '/usr/share/doc/openvpn/examples/easy-rsa/2.0/openssl.cnf'
13088:error:0E065068:configuration file routines:STR_COPY:variable has no value:conf_def.c:629:line 282
Using configuration from /usr/share/doc/openvpn/examples/easy-rsa/2.0/openssl.cnf
error on line 282 of config file '/usr/share/doc/openvpn/examples/easy-rsa/2.0/openssl.cnf'
13089:error:0E065068:configuration file routines:STR_COPY:variable has no value:conf_def.c:629:line 282
cat: crl.pem: No such file or directory
client1.crt: /C=US/ST=KY/L=Louisville/O=Advanced Business Solutions/CN=client1/emailAddress=admin@admin.com
error 3 at 0 depth lookup:unable to get certificate CRL
root@boxen:/usr/share/doc/openvpn/examples/easy-rsa/2.0#


```

---

### Post by SpaceTeddy on 2008-04-17
> cat: crl.pem: No such file or directory

your crl.pem is missing... either you did not specify it in your config, or you forgot to create it. 

check [here]("http://www.spenneberg.com/talks/fc_vpn/text19.html")

best thing i could find in this short time. Thing is, i don't remeber how i set it up, but i KNOW i use it :)

btw - never ever work in the doc dirs.. those are examples. copy the easy-rsa somewhere else and do it there... so you don't loose your examples in case something goes wrong :)

---

### Post by letic on 2008-07-21
Hey Underpants,

I came accross your post while looking for something else. Don't know if you still have the issue but the solution is simple

```
vi openssl.cnf
```
and comment out :
```
#[ pkcs11_section ]
#engine_id = pkcs11 	
#dynamic_path = /usr/lib/engines/engine_pkcs11.so
#MODULE_PATH = $ENV::PKCS11_MODULE_PATH
#PIN = $ENV::PKCS11_PIN
#init = 0
```

Hope this help :)

---

