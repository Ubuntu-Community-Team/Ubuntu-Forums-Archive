---
title: "Samba member server in Windows ActiveDirectory authentication issue"
date: 2015-02-02
forum: Server Platforms
---

### Post by Matze_Woody on 2015-02-02
I want to setup a Ubuntu 14.04 LTS server as a samba member server and want to set permissions with Windows. The DC is a Windows 2012 R2 server. I could successfully join the domain. The setup seems to be well, however accessing the samba share from other systems doesnt work and even logon attempts via ssh fail:

[B][SUP]Authentication test from Win7-machine[/SUP]
[/B]```
[SUP]C:\Windows\system32>net use \\artemis\ipc$ /u:UCNET\m.woody[/SUP]
[SUP]The password or user name is invalid for \\artemis\ipc$.[/SUP]
 
[SUP]Enter the password for 'UCNET\m.woody' to connect to 'artemis'[/SUP]
[SUP]System error 1326 has occurred.[/SUP]
 
[SUP]Logon failure: unknown user name or bad password.[/SUP]
```
 
**[SUP]SSH logon attempt from another Linux box[/SUP]**
```
[SUP]ssh -l m.woody 192.168.100.110[/SUP]
[SUP]m.woody@192.168.100.110's password:[/SUP]
[SUP]Permission denied, please try again.[/SUP]
```

Hopefully someone can help me fixing this issue. 

Output of misc commands and config files:
[B]
[SUP]smbclient -L //localhost -Um.woody[/SUP][/B]
```
[SUP]Enter m.woody's password:[/SUP]
[SUP]Domain=[UCNET] OS=[Unix] Server=[Samba 4.1.6-Ubuntu][/SUP]
 
[SUP]        Sharename       Type      Comment[/SUP]
[SUP]        ---------       ----      -------[/SUP]
[SUP]        IPC$            IPC       IPC Service (MyFiler)[/SUP]
[SUP]        data            Disk      Sambashare[/SUP]
[SUP]Domain=[UCNET] OS=[Unix] Server=[Samba 4.1.6-Ubuntu][/SUP]
 
[SUP]        Server               Comment[/SUP]
[SUP]        ---------            -------[/SUP]
[SUP]        ARTEMIS              MyFiler[/SUP]
 
[SUP]        Workgroup            Master[/SUP]
[SUP]        ---------            -------[/SUP]
[SUP]        UCNET[/SUP]

``` 
[SUP]
**kinit -V administrator**[/SUP]```
[SUP]Using default cache: /tmp/krb5cc_0[/SUP]
[SUP]Using principal: administrator@INTERN.UTURN-CONCEPTS.DE[/SUP]
[SUP]Password for administrator@INTERN.UTURN-CONCEPTS.DE:[/SUP]
[SUP]Authenticated to Kerberos v5[/SUP]
```

[SUP][B]klist
[/B][/SUP]```

[SUP]Ticket cache: FILE:/tmp/krb5cc_0[/SUP]
[SUP]Default principal: administrator@INTERN.UTURN-CONCEPTS.DE[/SUP]
 
[SUP]Valid starting       Expires              Service principal[/SUP]
[SUP]02/02/2015 23:16:40  02/03/2015 05:56:34  krbtgt/INTERN.UTURN-CONCEPTS.DE@INTERN.UTURN-CONCEPTS.DE[/SUP]
[SUP]        renew until 02/09/2015 23:16:34[/SUP]
```
 
[SUP][B]klist -ke
[/B][/SUP]```

[SUP]Keytab name: FILE:/etc/krb5.keytab[/SUP]
[SUP]klist: No such file or directory while starting keytab scan[/SUP]
```
 
**[SUP]net ads info[/SUP]**
```
[SUP]LDAP server: 192.168.100.112[/SUP]
[SUP]LDAP server name: DC1.intern.uturn-concepts.de[/SUP]
[SUP]Realm: INTERN.UTURN-CONCEPTS.DE[/SUP]
[SUP]Bind Path: dc=INTERN,dc=UTURN-CONCEPTS,dc=DE[/SUP]
[SUP]LDAP port: 389[/SUP]
[SUP]Server time: Mon, 02 Feb 2015 23:46:21 CET[/SUP]
[SUP]KDC server: 192.168.100.112[/SUP]
[SUP]Server time offset: -3573[/SUP]
```
 
[SUP][B]wbinfo -u
[/B][/SUP]```

[SUP]ARTEMIS/woody[/SUP]
[SUP]ARTEMIS/m.woody[/SUP]
[SUP]administrator[/SUP]
[SUP]guest[/SUP]
[SUP]krbtgt[/SUP]
[SUP]m.woody[/SUP]
```
 
[SUP]**wbinfo -g**
[/SUP]```

[SUP]winrmremotewmiusers__[/SUP]
[SUP]domain computers[/SUP]
[SUP]domain controllers[/SUP]
[SUP]schema admins[/SUP]
[SUP]enterprise admins[/SUP]
[SUP]cert publishers[/SUP]
[SUP]domain admins[/SUP]
[SUP]domain users[/SUP]
[SUP]domain guests[/SUP]
[SUP]group policy creator owners[/SUP]
[SUP]ras and ias servers[/SUP]
[SUP]allowed rodc password replication group[/SUP]
[SUP]denied rodc password replication group[/SUP]
[SUP]read-only domain controllers[/SUP]
[SUP]enterprise read-only domain controllers[/SUP]
[SUP]cloneable domain controllers[/SUP]
[SUP]protected users[/SUP]
[SUP]dnsadmins[/SUP]
[SUP]dnsupdateproxy[/SUP]
[SUP]uc_gf[/SUP]
[SUP]uc_projects[/SUP]
[SUP]uc_verwaltung[/SUP]
[SUP]uc_all[/SUP]
[SUP]linuxadmins[/SUP]
[SUP]testgroup[/SUP]
```
 
[SUP][B]getent passwd
[/B][/SUP]```

[SUP]root:x:0:0:root:/root:/bin/bash[/SUP]
[SUP]daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin[/SUP]
[SUP]bin:x:2:2:bin:/bin:/usr/sbin/nologin[/SUP]
[SUP]sys:x:3:3:sys:/dev:/usr/sbin/nologin[/SUP]
[SUP]...[/SUP]
[SUP]xrdp:x:119:128::/var/run/xrdp:/bin/false[/SUP]
[SUP]administrator:*:10500:10513:Administrator:/home/administrator:/bin/bash[/SUP]
[SUP]guest:*:10501:10514:Guest:/home/guest:/bin/bash[/SUP]
[SUP]krbtgt:*:10502:10513:krbtgt:/home/krbtgt:/bin/bash[/SUP]
[SUP]m.woody:*:11105:10513:Matthias Woody:/home/m.woody:/bin/bash[/SUP]
```
 
[B][SUP]getent group[/SUP]
[/B]```
[SUP]root:x:0:[/SUP]
[SUP]daemon:x:1:[/SUP]
[SUP]bin:x:2:[/SUP]
[SUP]sys:x:3:[/SUP]
[SUP]adm:x:4:syslog,woody,Administrator[/SUP]
[SUP]tty:x:5:[/SUP]
[SUP]sambashare:x:107:woody,administrator[/SUP]
[SUP]...[/SUP]
[SUP]xrdp:x:128:[/SUP]
[SUP]winrmremotewmiusers__:x:2000:[/SUP]
[SUP]domain computers:x:1515:[/SUP]
[SUP]domain controllers:x:1516:[/SUP]
[SUP]schema admins:x:1518:administrator[/SUP]
[SUP]enterprise admins:x:1519:administrator[/SUP]
[SUP]cert publishers:x:1517:[/SUP]
[SUP]domain admins:x:1512:m.woody,administrator[/SUP]
[SUP]domain users:x:10513:[/SUP]
[SUP]domain guests:x:10514:[/SUP]
[SUP]group policy creator owners:x:1520:administrator[/SUP]
[SUP]ras and ias servers:x:1553:[/SUP]
[SUP]allowed rodc password replication group:x:1571:[/SUP]
[SUP]denied rodc password replication group:x:1572:krbtgt[/SUP]
[SUP]read-only domain controllers:x:1521:[/SUP]
[SUP]enterprise read-only domain controllers:x:1498:[/SUP]
[SUP]cloneable domain controllers:x:1522:[/SUP]
[SUP]protected users:x:1525:[/SUP]
[SUP]dnsadmins:x:2102:[/SUP]
[SUP]dnsupdateproxy:x:2103:[/SUP]
[SUP]uc_gf:x:2106:m.woody[/SUP]
[SUP]uc_projects:x:2107:[/SUP]
[SUP]uc_verwaltung:x:2108:[/SUP]
[SUP]uc_all:x:11112:m.woody[/SUP]
[SUP]linuxadmins:x:11115:[/SUP]
 
[SUP]net rpc rights list accounts -Uadministrator[/SUP]
[SUP]Enter administrator's password:[/SUP]
[SUP]BUILTIN\Print Operators[/SUP]
[SUP]No privileges assigned[/SUP]
 
[SUP]BUILTIN\Account Operators[/SUP]
[SUP]No privileges assigned[/SUP]
 
[SUP]BUILTIN\Backup Operators[/SUP]
[SUP]No privileges assigned[/SUP]
 
[SUP]BUILTIN\Server Operators[/SUP]
[SUP]No privileges assigned[/SUP]
 
[SUP]UCNET\Domain Admins[/SUP]
[SUP]SeDiskOperatorPrivilege[/SUP]
 
[SUP]BUILTIN\Administrators[/SUP]
[SUP]SeMachineAccountPrivilege[/SUP]
[SUP]SeTakeOwnershipPrivilege[/SUP]
[SUP]SeBackupPrivilege[/SUP]
[SUP]SeRestorePrivilege[/SUP]
[SUP]SeRemoteShutdownPrivilege[/SUP]
[SUP]SePrintOperatorPrivilege[/SUP]
[SUP]SeAddUsersPrivilege[/SUP]
[SUP]SeDiskOperatorPrivilege[/SUP]
[SUP]SeSecurityPrivilege[/SUP]
[SUP]SeSystemtimePrivilege[/SUP]
[SUP]SeShutdownPrivilege[/SUP]
[SUP]SeDebugPrivilege[/SUP]
[SUP]SeSystemEnvironmentPrivilege[/SUP]
[SUP]SeSystemProfilePrivilege[/SUP]
[SUP]SeProfileSingleProcessPrivilege[/SUP]
[SUP]SeIncreaseBasePriorityPrivilege[/SUP]
[SUP]SeLoadDriverPrivilege[/SUP]
[SUP]SeCreatePagefilePrivilege[/SUP]
[SUP]SeIncreaseQuotaPrivilege[/SUP]
[SUP]SeChangeNotifyPrivilege[/SUP]
[SUP]SeUndockPrivilege[/SUP]
[SUP]SeManageVolumePrivilege[/SUP]
[SUP]SeImpersonatePrivilege[/SUP]
[SUP]SeCreateGlobalPrivilege[/SUP]
[SUP]SeEnableDelegationPrivilege[/SUP]
 
[SUP]Everyone[/SUP]
[SUP]No privileges assigned[/SUP]

``` 

I tried SSSD, however removed it. Surprisingly it still lists with realm  list. SSSD however is removed and there is no such process running.

[B][SUP]realm list[/SUP]
[/B]```
[SUP]intern.uturn-concepts.de[/SUP]
[SUP]  type: kerberos[/SUP]
[SUP]  realm-name: INTERN.UTURN-CONCEPTS.DE[/SUP]
[SUP]  domain-name: intern.uturn-concepts.de[/SUP]
[SUP]  configured: kerberos-member[/SUP]
[SUP]  server-software: active-directory[/SUP]
[SUP]  client-software: winbind[/SUP]
[SUP]  required-package: winbind[/SUP]
[SUP]  required-package: libpam-winbind[/SUP]
[SUP]  login-formats: %U[/SUP]
[SUP]  login-policy: allow-any-login[/SUP]
[SUP]intern.uturn-concepts.de[/SUP]
[SUP]  type: kerberos[/SUP]
[SUP]  realm-name: INTERN. UTURN-CONCEPTS.DE[/SUP]
[SUP]  domain-name: intern.uturn-concepts.de[/SUP]
[SUP]  configured: kerberos-member[/SUP]
[SUP]  server-software: active-directory[/SUP]
[SUP]  client-software: sssd[/SUP]
[SUP]  required-package: sssd-tools[/SUP]
[SUP]  required-package: sssd[/SUP]
[SUP]  required-package: libnss-sss[/SUP]
[SUP]  required-package: libpam-sss[/SUP]
[SUP]  required-package: adcli[/SUP]
[SUP]  login-formats: %U@intern.uturn-concepts.de[/SUP]
[SUP]  login-policy:[/SUP]

``` 
[B][SUP]
dig -t SRV _kerberos._tcp.intern.uturn-concepts.de[/SUP]
[/B]```
[SUP]; <<>> DiG 9.9.5-3ubuntu0.1-Ubuntu <<>> -t SRV _kerberos._tcp.intern.uturn-concepts.de[/SUP]
[SUP];; global options: +cmd[/SUP]
[SUP];; Got answer:[/SUP]
[SUP];; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21730[/SUP]
[SUP];; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 2[/SUP]
 
[SUP];; OPT PSEUDOSECTION:[/SUP]
[SUP]; EDNS: version: 0, flags:; udp: 4000[/SUP]
[SUP];; QUESTION SECTION:[/SUP]
[SUP];_kerberos._tcp.intern.uturn-concepts.de. IN SRV[/SUP]
 
[SUP];; ANSWER SECTION:[/SUP]
[SUP]_kerberos._tcp.intern.uturn-concepts.de. 600 IN SRV 0 100 88 dc1.intern.uturn-concepts.de.[/SUP]
 
[SUP];; ADDITIONAL SECTION:[/SUP]
[SUP]dc1.intern.uturn-concepts.de. 3600 IN A   192.168.100.112[/SUP]
 
[SUP];; Query time: 3 msec[/SUP]
[SUP];; SERVER: 192.168.100.112#53(192.168.100.112)[/SUP]
[SUP];; WHEN: Tue Feb 03 00:40:51 CET 2015[/SUP]
[SUP];; MSG SIZE  rcvd: 144[/SUP]

``` 
[B][SUP]
/etc/nsswitch.conf[/SUP]
[/B]```
[SUP]# /etc/nsswitch.conf[/SUP]
[SUP]#[/SUP]
[SUP]# Example configuration of GNU Name Service Switch functionality.[/SUP]
[SUP]# If you have the `glibc-doc-reference' and `info' packages installed, try:[/SUP]
[SUP]# `info libc "Name Service Switch"' for information about this file.[/SUP]
 
[SUP]passwd:         compat winbind[/SUP]
[SUP]group:          compat winbind[/SUP]
[SUP]shadow:         compat[/SUP]
 
[SUP]hosts:          files mdns4_minimal [NOTFOUND=return] dns[/SUP]
[SUP]networks:       files[/SUP]
 
[SUP]protocols:      db files[/SUP]
[SUP]services:       db files[/SUP]
[SUP]ethers:         db files[/SUP]
[SUP]rpc:            db files[/SUP]
 
[SUP]netgroup:       nis sss[/SUP]
[SUP]sudoers:        files[/SUP]

``` 

My guess is that the pam files are the cause:

[B][SUP]/etc/pam.d/common-auth[/SUP]
[/B]```
[SUP]account [success=3 new_authtok_reqd=done default=ignore]        pam_unix.so[/SUP]
[SUP]account [success=2 new_authtok_reqd=done default=ignore]        pam_winbind.so[/SUP]
[SUP]account [success=1 default=ignore]      pam_ldap.so[/SUP]
[SUP]account requisite                       pam_deny.so[/SUP]
[SUP]account required                        pam_permit.so[/SUP]

``` 

[B][SUP]/etc/pam.d/common-password[/SUP]
[/B]```
[SUP]password        requisite                       pam_pwquality.so retry=3[/SUP]
[SUP]password        [success=3 default=ignore]      pam_unix.so obscure use_authtok try_first_pass sha512[/SUP]
[SUP]password        [success=2 default=ignore]      pam_winbind.so use_authtok try_first_pass[/SUP]
[SUP]password        [success=1 user_unknown=ignore default=die]     pam_ldap.so use_authtok try_first_pass[/SUP]
[SUP]password        requisite                       pam_deny.so[/SUP]
[SUP]password        required                        pam_permit.so[/SUP]
[SUP]password        optional                        pam_smbpass.so nullok use_authtok use_first_pass[/SUP]
[SUP]password        optional        pam_gnome_keyring.so[/SUP]

``` 

[B][SUP]/etc/pam.d/common-auth[/SUP]
[/B]```
[SUP]auth    sufficient      pam_unix.so nullok_secure[/SUP]
[SUP]auth    sufficient      pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login use_first_pass[/SUP]
[SUP]auth    requisite                       pam_deny.so[/SUP]
[SUP]auth    required                        pam_permit.so[/SUP]
[SUP]auth    optional        pam_mount.so[/SUP]
[SUP]auth    optional                        pam_smbpass.so migrate[/SUP]
[SUP]auth    optional                        pam_cap.so[/SUP]

``` 

[SUP][B]/etc/pam.d/common-session
[/B][/SUP]```

[SUP]session [default=1]                     pam_permit.so[/SUP]
[SUP]session requisite                       pam_deny.so[/SUP]
[SUP]session required                        pam_permit.so[/SUP]
[SUP]session optional                        pam_umask.so[/SUP]
[SUP]session required        pam_unix.so[/SUP]
[SUP]session optional                        pam_winbind.so[/SUP]
[SUP]session optional        pam_mount.so[/SUP]
[SUP]session optional                        pam_ldap.so[/SUP]
[SUP]session optional        pam_systemd.so[/SUP]
```
 
[SUP][B]/etc/krb5.conf
[/B][/SUP]```

[SUP][libdefaults][/SUP]
[SUP]ticket_lifetime = 24000[/SUP]
[SUP]default_realm = INTERN.UTURN-CONCEPTS.DE[/SUP]
[SUP]default_tgs_entypes = rc4-hmac des-cbc-md5[/SUP]
[SUP]default_tkt_enctypes = rc4-hmac des-cbc-md5[/SUP]
[SUP]permitted_enctypes = rc4-hmac des-cbc-md5[/SUP]
[SUP]renew_lifetime = 7d[/SUP]
[SUP]rdns = false[/SUP]
[SUP]forwardable = yes[/SUP]
[SUP]dns_lookup_realm = true[/SUP]
[SUP]dns_lookup_kdc = true[/SUP]
[SUP]dns_fallback = yes[/SUP]
 
[SUP][realms][/SUP]
[SUP] INTERN.UTURN-CONCEPTS.DE = {[/SUP]
[SUP]  kdc = dc1:88[/SUP]
[SUP]  admin_server = dc1:464[/SUP]
[SUP]  default_domain = intern.uturn-concepts.de[/SUP]
[SUP] }[/SUP]
 
[SUP][domain_realm][/SUP]
[SUP] .intern.uturn-concepts.de = INTERN.UTURN-CONCEPTS.DE[/SUP]
[SUP] intern.uturn-concepts.de = INTERN. UTURN-CONCEPTS.DE[/SUP]
 
[SUP][appdefaults][/SUP]
[SUP] pam = {[/SUP]
[SUP]   debug = false[/SUP]
[SUP]   ticket_lifetime = 36000[/SUP]
[SUP]   renew_lifetime = 36000[/SUP]
[SUP]   forwardable = true[/SUP]
[SUP]   krb4_convert = false[/SUP]
[SUP] }[/SUP]
 
[SUP][logging][/SUP]
[SUP] default = FILE:/var/log/krb5libs.log[/SUP]
[SUP] kdc = FILE:/var/log/krb5kdc.log[/SUP]
[SUP] admin_server = FILE:/var/log/kadmind.log[/SUP]
```
 
[SUP][B]testparm
[/B][/SUP]```

[SUP]Load smb config files from /etc/samba/smb.conf[/SUP]
[SUP]rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)[/SUP]
[SUP]Processing section "[data]"[/SUP]
[SUP]Loaded services file OK.[/SUP]
[SUP]Server role: ROLE_DOMAIN_MEMBER[/SUP]
[SUP]Press enter to see a dump of your service definitions[/SUP]
 
[SUP][global][/SUP]
[SUP]        workgroup = UCNET[/SUP]
[SUP]        realm = INTERN.UTURN-CONCEPTS.DE[/SUP]
[SUP]        server string = MyFiler[/SUP]
[SUP]        security = ADS[/SUP]
[SUP]        allow trusted domains = No[/SUP]
[SUP]        log file = /var/log/samba/samba.log[/SUP]
[SUP]        client signing = if_required[/SUP]
[SUP]        socket options = TCP_noDELAY SO_RCVBUF=8192 SO_SNDBUF=8192[/SUP]
[SUP]        load printers = No[/SUP]
[SUP]        printcap name = /dev/null[/SUP]
[SUP]        disable spoolss = Yes[/SUP]
[SUP]        os level = 0[/SUP]
[SUP]        local master = No[/SUP]
[SUP]        domain master = No[/SUP]
[SUP]        dns proxy = No[/SUP]
[SUP]        template homedir = /home/%U[/SUP]
[SUP]        template shell = /bin/bash[/SUP]
[SUP]        winbind separator = /[/SUP]
[SUP]        winbind enum users = Yes[/SUP]
[SUP]        winbind enum groups = Yes[/SUP]
[SUP]        winbind use default domain = Yes[/SUP]
[SUP]        winbind refresh tickets = Yes[/SUP]
[SUP]        idmap config *:range = 70000-90000[/SUP]
[SUP]        idmap config * : backend = rid[/SUP]
[SUP]        valid users = "@UCNET/Domain Users"[/SUP]
[SUP]        hosts allow = 192.168.110.0/255.255.255.128, 127.[/SUP]
[SUP]        hosts deny = 0.0.0.0/0.0.0.0[/SUP]
[SUP]        map acl inherit = Yes[/SUP]
[SUP]        printing = bsd[/SUP]
[SUP]        print command = lpr -r -P'%p' %s[/SUP]
[SUP]        lpq command = lpq -P'%p'[/SUP]
[SUP]        lprm command = lprm -P'%p' %j[/SUP]
[SUP]        store dos attributes = Yes[/SUP]
[SUP]        vfs objects = acl_xattr[/SUP]
 
[SUP][data][/SUP]
[SUP]        comment = Sambashare[/SUP]
[SUP]        path = /var/samba[/SUP]
[SUP]        read only = No[/SUP]
[SUP]        create mask = 0660[/SUP]
[SUP]        force create mode = 0660[/SUP]
[SUP]        directory mask = 0770[/SUP]
[SUP]        force directory mode = 0770[/SUP]
```
 
**[SUP]ls -la /var[/SUP]**
```
[SUP]drwxrwx---+  2 root root     4096 Jan 29 21:23 samba/[/SUP]
```
 
**[SUP]getfacl /var/samba[/SUP]**
```
[SUP]getfacl /var/samba[/SUP]
[SUP]getfacl: Removing leading '/' from absolute path names[/SUP]
[SUP]# file: var/samba[/SUP]
[SUP]# owner: root[/SUP]
[SUP]# group: root[/SUP]
[SUP]user::rwx[/SUP]
[SUP]group::r-x[/SUP]
[SUP]group:uc_all:rwx[/SUP]
[SUP]mask::rwx[/SUP]
[SUP]other::---[/SUP]
[SUP]default:user::rwx[/SUP]
[SUP]default:user:10512:rwx[/SUP]
[SUP]default:user:uc_all:rwx[/SUP]
[SUP]default:group::r-x[/SUP]
[SUP]default:group:10512:rwx[/SUP]
[SUP]default:group:uc_all:rwx[/SUP]
[SUP]default:mask::rwx[/SUP]
[SUP]default:other::r-x[/SUP]
```
 
**[SUP]/etc/resolv.conf[/SUP]**
```
[SUP]nameserver 192.168.100.112[/SUP]
[SUP]search intern.uturn-concepts.de[/SUP]
```
 
[SUP][B]/etc/hosts
[/B][/SUP]```

[SUP]127.0.0.1       localhost[/SUP]
[SUP]127.0.1.1       artemis artemis.intern.uturn-concepts.de[/SUP]
[SUP]192.168.100.112 dc1 dc1.intern.uturn-concepts.de[/SUP]
 
[SUP]# The following lines are desirable for IPv6 capable hosts[/SUP]
[SUP]::1     localhost ip6-localhost ip6-loopback[/SUP]
[SUP]ff02::1 ip6-allnodes[/SUP]
[SUP]ff02::2 ip6-allrouters[/SUP]
```
 
**[SUP]/etc/network/interfaces[/SUP]**
```
[SUP]# This file describes the network interfaces available on your system[/SUP]
[SUP]# and how to activate them. For more information, see interfaces(5).[/SUP]
 
[SUP]# The loopback network interface[/SUP]
[SUP]auto lo[/SUP]
[SUP]iface lo inet loopback[/SUP]
 
[SUP]# The primary network interface[/SUP]
[SUP]auto eth0[/SUP]
[SUP]iface eth0 inet static[/SUP]
[SUP]        address 192.168.100.110[/SUP]
[SUP]        netmask 255.255.255.128[/SUP]
[SUP]        network 192.168.100.0[/SUP]
[SUP]        broadcast 192.168.100.127[/SUP]
[SUP]        gateway 192.168.100.1[/SUP]
[SUP]        dns-search intern.uturn-concepts.de[/SUP]
[SUP]        dns-nameservers 192.168.100.112[/SUP]
```

---

