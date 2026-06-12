---
title: "Add to AD Ubuntu Server 18.04"
date: 2020-04-15
forum: Server Platforms
---

### Post by strigoff on 2020-04-15
[COLOR=#000000]Hello![/COLOR]
[COLOR=#000000]I try add server with Ubuntu Server 18.04.04 in our domain domen.ru, but don't work. Who know what problem?


[/COLOR][COLOR=#000000][I]
[LIST=1]
[*]root@vld_pbx:~# realm join --user=*****@******.ru *******.RU --verbose
 * Resolving: _ldap._tcp.*******.ru
 * Performing LDAP DSE lookup on: 172.26.7.12
 * Performing LDAP DSE lookup on: 192.168.75.11
 * Performing LDAP DSE lookup on: 172.26.127.11
 * Successfully discovered: ******.ru
Password for ******@*******.ru:
 * Unconditionally checking packages
 * Resolving required packages
 * LANG=C /usr/sbin/adcli join --verbose --domain ********.ru --domain-realm *******.RU --domain-controller 192.168.75.11 --login-type user --login-user *******@polymetal.ru --stdin-password
 * Using domain name: *******.ru
 * Calculated computer account name from fqdn: VLD_PBX
 * Using domain realm:*******.ru
 * Sending netlogon pings to domain controller: cldap://192.168.75.11
 * Received NetLogon info from: ******.******.ru
 * Wrote out krb5.conf snippet to /var/cache/realmd/adcli-krb5-awyduy/krb5.d/adcli-krb5-conf-hkn2yS
 ! Couldn't get kerberos ticket for: ******@******.ru: KDC reply did not match expectations
adcli: couldn't connect to *******.ru domain: Couldn't get kerberos ticket for: *******@*******.ru: KDC reply did not match expectations
 ! Failed to join the domain
realm: Couldn't join realm: Failed to join the domain
root@vld_pbx:~#
[/LIST]
[/I][/COLOR]

---

### Post by LHammonds on 2020-04-16
What does this show?
```
ls -l /etc/krb*
```
I'm looking to see if you symlinked that file to Sambas kerberos file which normally happens right after provisioning the domain.

LHammonds

---

