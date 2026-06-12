---
title: "Samba AD, join WinXP error"
date: 2015-11-05
forum: Server Platforms
---

### Post by Rafael_ on 2015-11-05
[COLOR=#222222][FONT=Verdana]Ubuntu Server 14.04LTS x64 updated

[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Windows and Ubuntu are VM, clean install, no antivirus.

[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana] Windows 7 join on domain, but Windows XP machines don't. The error message: 
     [FONT=courier new]Error on try join in domain "ardo"[/FONT][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][FONT=courier new]   Fail on logon user unknown or wrong password 
[/FONT]or simply [FONT=courier new]internal error[/FONT][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]I tried  with ardo.net.br too.

[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]On W7 works with a DHCP from other server, in XP doesn't work with DHCP or static IP (1º DNS server with ADDC IP  )[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]I checked  samba logs in /var/log/samba, but not found information about the error.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]I researched some documents and performed the installation as follows:[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Update and install the dependencies
[/FONT][/COLOR]```

[COLOR=#222222][FONT=Verdana]apt-get update && apt-get upgrade[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]apt-get install build-essential libacl1-dev libattr1-dev libgnutls-dev libblkid-dev libreadline-dev python-dev python-dnspython gdb libpopt-dev pkg-config libldap2-dev dnsutils libbsd-dev attr krb5-user docbook-xsl ntp ntpdate[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]I set the ntp service[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Added the "user_xattr mount, acl, barrier = 1" in /etc/fstab, I rebooted and tested with[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]touch test.txt[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]setfattr -n user.test -v test test.txt[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]setfattr -n security.test -v test2 test.txt[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]getfattr -d test.txt[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]getfattr -n security.test -d test.txt [/FONT][/COLOR]

```[COLOR=#222222][FONT=Verdana]

[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]I set configuration files:
[/FONT][/COLOR]```

[COLOR=#222222][FONT=Verdana]/etc/network/interfaces[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]auto eth0 eth1[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]iface eth0 inet static[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]    address 192.168.1.3[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]    network 192.168.1.0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]    netmask 255.255.255.0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]    gateway 192.168.1.1[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]    broadcast 192.168.1.255[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]    dns-nameservers 192.168.1.1 8.8.8.8 8.8.4.4[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]    dns-search ardo.net.br[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]iface eth1 inet static[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]    address 192.168.0.220[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]    network 192.168.0.0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]    netmask 255.255.255.0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]    broadcast 192.168.0.255[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana] /etc/resolv.conf[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]domain ardo.net.br[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]search ardo.net.br[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nameserver 192.168.1.3[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nameserver 192.168.1.1[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nameserver 8.8.8.8[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nameserver 8.8.4.4[/FONT][/COLOR]

```[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]```

[COLOR=#222222][FONT=Verdana]/etc/hosts[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]127.0.0.1       localhost[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]#127.0.1.1[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]192.168.0.3     ardo3.ardo.net.br ardo3[/FONT][/COLOR]

```[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]```

[COLOR=#222222][FONT=Verdana]/etc/hostname[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ardo3[/FONT][/COLOR]

```
[COLOR=#222222][FONT=Verdana]And installed samba
[/FONT][/COLOR]```

[COLOR=#222222][FONT=Verdana]apt-get install samba smbclient[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]rm /etc/samba/smb.conf [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]samba-tool domain provision --host-name=ARDO3 --realm=ARDO.NET.BR --domain=ARDO --server-role='dc'  --adminpass=123abcd --dns-backend=SAMBA_INTERNAL --function-level=2008_R2 --use-rfc2307[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]cp /var/lib/samba/private/krb5.conf /etc/[/FONT][/COLOR]

```
[COLOR=#222222][FONT=Verdana]And tested:
[/FONT][/COLOR]```

[COLOR=#222222][FONT=Verdana]host -t SRV _ldap._tcp.ardo.net.br.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]_ldap._tcp.ardo.net.br has SRV record 0 100 389 ardo3.ardo.net.br.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]host -t SRV _ldap._tcp.ardo.net.br.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]_ldap._tcp.ardo.net.br has SRV record 0 100 389 ardo3.ardo.net.br.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]root@ardo3:~# host -t SRV _kerberos._udp.ardo.net.br.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]_kerberos._udp.ardo.net.br has SRV record 0 100 88 ardo3.ardo.net.br.

[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]smbclient -L localhost -U%[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Domain=[ARDO] OS=[Unix] Server=[Samba 4.1.6-Ubuntu][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        Sharename       Type      Comment[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        ---------       ----      -------[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        netlogon        Disk[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        sysvol          Disk[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        IPC$            IPC       IPC Service (Samba 4.1.6-Ubuntu)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Domain=[ARDO] OS=[Unix] Server=[Samba 4.1.6-Ubuntu][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        Server               Comment[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        ---------            -------[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        Workgroup            Master[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        ---------            -------[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        ARDO                 BKP[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]        WORKGROUP      ARDO3[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]

```

---

### Post by darkod on 2015-11-05
Can the XP client ping the DC by fqdn? Like:
ping ardo3.ardo.net.br

That should be first clue if it reaches the DC correctly.

For the domain join I think you should always use the fqdn. The short domain name (workgroup) is just the short, better to use the fqdn.

Make sure you are using the correct admin user and pass for the join.

---

### Post by Rafael_ on 2015-11-05
I ping the DC by fqdn(ardo3.ardo.net.br), and the time response is less than 1ms.
I tryed the domain join with the fqdn (ardo.net.br) but doesn't work.
The user is administrator and password i copy and paste.

I saw thats on ran[COLOR=#222222][FONT=Verdana] [FONT=courier new]smbclient -L localhost -U%[/FONT] show 2[/FONT][/COLOR] workgoups (ARDO and WORKGROUP) and 2 Masters, this is a problem?

my smb.conf
```

# Global parameters
[global]
        workgroup = TRANSARDO
        realm = TRANSARDO.NET.BR
        netbios name = ARDO3
        server role = active directory domain controller
        dns forwarder = 192.168.1.1
        idmap_ldb:use rfc2307 = yes

[netlogon]
        path = /var/lib/samba/sysvol/transardo.net.br/scripts
        read only = No

[sysvol]
        path = /var/lib/samba/sysvol
        read only = No

```

---

### Post by darkod on 2015-11-05
Not sure if the realm case can play a role. On my DC in smb.conf the workgroup is uppercase (like in yours) but the realm is lowercase. I think there were instructions about the domain provision command what has to be uppercase or not. In linux use uppercase only when it is strictly needed. Linux is much more sensitive about case than windows. I wonder if that can create issues.

Otherwise it looks good, and you can join win7 client so the domain seems to be provisioned correctly...

---

### Post by Rafael_ on 2015-11-09
I tried change the realm to lowercase, but doesn't  works.
I did a new clean install but the same error happens.
 Maybe if I make a samba with bind9, instead of samba internal dns ?

---

### Post by darkod on 2015-11-09
The internal dns should not be an issue. It works. I have installed DCs like that. But you can try bind if you want to...

I really don't have a clue about your case. Sorry...

---

