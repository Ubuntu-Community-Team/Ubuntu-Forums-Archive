---
title: "Squid proxy for Windows environment"
date: 2009-09-28
forum: Server Platforms
---

### Post by florpc on 2009-09-28
Hi guys,
 
As a little project for school I've set up a Windows Server 2008 R2 server with AD installed, an Ubuntu 9.04 Server and Windows XP clients in a "lab environment".
 
I installed the packages:
```
apt-get install squid samba ntp bind9 winbind krb5-user krb5-config
```
 
/etc/network/interfaces
```

[LEFT][FONT=LiberationSans]auto lo[/FONT]
[FONT=LiberationSans]iface lo inet loopback[/FONT][/LEFT]
 
[LEFT][FONT=LiberationSans]auto eth2[/FONT]
[FONT=LiberationSans]iface eth2 inet dhcp[/FONT][/LEFT]
 
[LEFT][FONT=LiberationSans]auto eth1[/FONT]
[FONT=LiberationSans]iface eth1 inet static[/FONT]
[FONT=LiberationSans]address 192.168.0.50[/FONT]
[FONT=LiberationSans]netmask 255.255.255.0[/FONT]
[FONT=LiberationSans]gateway 192.168.0.50[/FONT]
[FONT=LiberationSans]dns-search davinci.local[/FONT][/LEFT]
 
[FONT=LiberationSans]dns-nameservers 192.168.0.50 83.143.245.36[/FONT]

```
 
 
[LEFT][FONT=LiberationSans]/etc/hosts[/FONT][/LEFT]
```

 
[LEFT][FONT=LiberationSans]127.0.0.1 localhost[/FONT]

[FONT=LiberationSans]127.0.1.1 srv1[/FONT][/LEFT]

 
 
[LEFT][FONT=LiberationSans]192.168.0.50 srv1 srv1.davinci.local[/FONT]
192.168.0.51 dc1 dc1.davinci.local[/LEFT]

```
 
[LEFT]My firewall script loaded through rc.local:[/LEFT]
```

 
[LEFT][FONT=LiberationSans]iptables -F[/FONT]

[FONT=LiberationSans]iptables -t nat -F[/FONT]
[LEFT][FONT=LiberationSans]iptables --delete-chain[/FONT]
[FONT=LiberationSans]iptables --table nat --delete-chain[/FONT][/LEFT]
[/LEFT]

 
 
 
 
[LEFT][FONT=LiberationSans]iptables -P INPUT DROP[/FONT]

[FONT=LiberationSans]iptables -P FORWARD DROP[/FONT]
[LEFT][FONT=LiberationSans]iptables -P OUTPUT ACCEPT[/FONT][/LEFT]
[/LEFT]

 
 
 
 
[LEFT][FONT=LiberationSans]iptables -A INPUT -m state --state INVALID -j DROP[/FONT]

[FONT=LiberationSans]iptables -A FORWARD -m state --state INVALID -j DROP[/FONT]
[LEFT][FONT=LiberationSans]iptables -A OUTPUT -m state --state INVALID -j DROP[/FONT][/LEFT]
[/LEFT]

 
 
 
 
[LEFT][FONT=LiberationSans]iptables -A INPUT -i lo -j ACCEPT[/FONT]

[FONT=LiberationSans]iptables -A OUTPUT -o lo -j ACCEPT[/FONT][/LEFT]

 
 
 
 
[LEFT][FONT=LiberationSans]iptables -A FORWARD -i eth1 -o eth2 -j ACCEPT[/FONT]

[FONT=LiberationSans]iptables -A FORWARD -i eth2 -o eth1 -j ACCEPT[/FONT][/LEFT]

 
 
 
 
[LEFT][FONT=LiberationSans]iptables -A INPUT -i eth1 -j ACCEPT[/FONT][/LEFT]
 
 
 
[LEFT][FONT=LiberationSans]iptables -A INPUT -i eth2 -m state --state ESTABLISHED,RELATED -j ACCEPT[/FONT][/LEFT]
 
 
 
[LEFT][FONT=LiberationSans]iptables -t nat -A POSTROUTING -o eth2 -j MASQUERADE[/FONT][/LEFT]
 

```
 
[LEFT]My internal interface is eth1. And eth2 connects to the modem.
Ofcourse, IPv4 forwarding is enabled.[/LEFT]
 
[LEFT]I editted the squid.conf file:[/LEFT]
```

 
[LEFT][FONT=LiberationSans]# OPTIONS FOR AUTHENTICATION[/FONT]

[FONT=LiberationSans]# Active Directory configuration[/FONT]
[LEFT][FONT=LiberationSans]auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp --requiremembership-of=DAVINCI.LOCAL+Internet[/FONT]
[FONT=LiberationSans]auth_param ntlm children 30[/FONT]
[FONT=LiberationSans]auth_param ntlm keep_alive on[/FONT][/LEFT]
[/LEFT]

 
 
 
 
[LEFT][FONT=LiberationSans](...)[/FONT][/LEFT]
 
 
 
[LEFT][FONT=LiberationSans][FONT=LiberationSans]# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS[/FONT][/FONT][/LEFT]

[FONT=LiberationSans][LEFT][FONT=LiberationSans]acl our_networks src 192.168.0.0/24[/FONT]
[LEFT][FONT=LiberationSans]acl to_webserver dst 192.168.0.50[/FONT]
[FONT=LiberationSans]acl good url_regex "/home/samba/writable/admin/data/squid-allow.acl"[/FONT]
[FONT=LiberationSans]acl bad url_regex "/home/samba/writable/admin/data/squid-block.acl"[/FONT]
[FONT=LiberationSans]acl ad_users proxy_auth REQUIRED[/FONT]
[FONT=LiberationSans]http_access deny bad[/FONT]
[FONT=LiberationSans]http_access allow to_webserver[/FONT]
[FONT=LiberationSans]http_access allow good[/FONT]
[FONT=LiberationSans]http_access allow localhost[/FONT]
[FONT=LiberationSans]http_access allow ad_users[/FONT][/FONT][/LEFT]
[/LEFT]

 
 
[LEFT][FONT=LiberationSans][FONT=LiberationSans]http_access deny al[/FONT][/LEFT]
 
[LEFT][FONT=LiberationSans](...)[/FONT][/LEFT]
 
 
[LEFT][FONT=LiberationSans][FONT=LiberationSans]cache_effective_user proxy[/FONT][/FONT][/LEFT]
 
[LEFT][FONT=LiberationSans][FONT=LiberationSans]cache_effective_group squid[/FONT][/LEFT]
[/FONT][/FONT]
```
 
 
[LEFT]I've alse set permissions:[/LEFT]
 
```

 
[LEFT][FONT=LiberationSans]groupadd squid[/FONT]

[FONT=LiberationSans]chown proxy:squid /var/run/samba/winbindd_privileged[/FONT][/LEFT]

 
 
[LEFT][FONT=LiberationSans]chmod 750 /var/run/samba/winbindd_privileged[/FONT][/LEFT]

```
 
 
[LEFT]/etc/samba/smb.conf[/LEFT]
 
```

 
[LEFT][FONT=LiberationSans][global][/FONT]

[FONT=LiberationSans]netbios name = srv1[/FONT]
[LEFT][FONT=LiberationSans]realm =DAVINCI.LOCAL[/FONT]
[FONT=LiberationSans]workgroup = DAVINCI[/FONT]
[FONT=LiberationSans]security = ADS[/FONT]
[FONT=LiberationSans]#security = user[/FONT]
[FONT=LiberationSans]password server = dc1.davinci.local[/FONT]
[FONT=LiberationSans]socket options = TCP_NODELAY SO_RCVBUF=16384 SO_SNDBUF=16384[/FONT]
[FONT=LiberationSans]idmap uid = 10000-20000[/FONT]
[FONT=LiberationSans]winbind enum users = yes[/FONT]
[FONT=LiberationSans]winbind uid = 10000-20000[/FONT]
[FONT=LiberationSans]winbind gid = 10000-20000[/FONT]
[FONT=LiberationSans]winbind separator = +[/FONT]
[FONT=LiberationSans]winbind use default domain = yes[/FONT]
[FONT=LiberationSans]encrypt passwords = yes[/FONT][/LEFT]
[/LEFT]

 
 
[LEFT][FONT=LiberationSans]log level = 3 passdb:5 auth:10 winbind:5[/FONT][/LEFT]

```
 
 
[LEFT]/etc/krb5.conf[/LEFT]
 
```

 
[LEFT][libdefaults]

ticket_lifetime = 600
[LEFT]default_realm = DAVINCI.LOCAL
dns_lookup_realm = false
dns_lookup_kdc = false
[realms]
DAVINCI.LOCAL = {
kdc = dc1.davinci.local:88
admin_server = dc1.davinci.local:749
default_domain = DAVINCI.LOCAL
}
[domain_realm]
.davinci.local = dc1.davinci.local
davinci.local = dc1.davinci.local
[kdc]
profile = /etc/krb5kdc/kdc.conf
[logging]
kdc = FILE:/var/log/krb5kdc.log
admin_server = FILE:/var/log/kadmin.log[/LEFT]
[/LEFT]

 
 
[LEFT]default = FILE:/var/log/krb5lib.log[/LEFT]

```
 
 
[LEFT]Joining the domain... DNS updates failed??[/LEFT]
 
```

 
[LEFT]net ads join -U Administrator -S dc1.davinci.local

Enter Administrator's password:
[LEFT]Using short domain name -- DAVINCI
Joined 'SRV1' to realm 'davinci.local'
[2009/09/28 18:50:18,  0] utils/net_ads.c:net_update_dns_internal(1064)
net_update_dns_internal: Failed to connect to our DC!
DNS update failed![/LEFT]
[/LEFT]

 
 

```
 
```

 
[LEFT]wbinfo -t

checking the trust secret via RPC calls succeeded[/LEFT]

 
 

```
 
```

 
[LEFT]wbinfo -u

[...]
[LEFT]Administrator
TestUser[/LEFT]
[/LEFT]

 
 

```
 
 
[LEFT][FONT=LiberationSans]But the test for the helper-protcol failed:[/FONT][/LEFT]
 
```

 
[LEFT]ntlm_auth --helper-protocol=squid-2.5-basic[/LEFT]
 
[LEFT]DAVINCI.LOCAL+testUser testPassword159[/LEFT]
 
[LEFT][2009/09/28 18:45:49,  3] utils/ntlm_auth.c:check_plaintext_auth(328)

NT_STATUS_PIPE_DISCONNECTED: Named pipe dicconnected (0xc00000b0)
[LEFT]ERR[/LEFT]
[/LEFT]

 
 
 

```
 
 
[LEFT]I really don't have much Ubuntu/Linux experience, but I'm trying to get this working for days.[/LEFT]
 
 
[LEFT]Any suggestions? Thanks![/LEFT]

---

### Post by Lars Noodén on 2009-09-29
Which existing documentation have you tried to follow?

[http://www.linuxmail.info/squid-active-directory-integration/](http://www.linuxmail.info/squid-active-directory-integration/)

(After solving squid, you may want to look at radmind or puppet)
[http://www.linuxjournal.com/article/10046](http://www.linuxjournal.com/article/10046)
[http://www.informit.com/articles/article.aspx?p=1315435&seqNum=3&rll=1](http://www.informit.com/articles/article.aspx?p=1315435&seqNum=3&rll=1)

Unfortunately AD is **not** designed for interoperability, rather the opposite.  If it were intended to work, it would have used regular Kerberos and LDAP.  usually Windows admins *.....censored....* unhelpful *.....censored....*  However, be that as it may, since you have full access to the problem machine you have half the problem solved if you can find documentation.

---

### Post by bmcc on 2009-09-29
Hi florpc
 
We are in exactly the same boat. I have configured a centos 5.3 box which hosts our website and vle. I can do all you can with wbinfo but nothing with ntlm_auth
 
when I run ntlm_auth --diagnostics --username=big-foot
 
i get this
 
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test LM failed!
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test LM and NTLM failed!
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test NTLM failed!
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test NTLM in LM failed!
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test NTLM in both failed!
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test NTLMv2 failed!
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test NTLMv2 and LMv2 failed!
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test LMv2 failed!
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test NTLMv2 and LMv2, LMv2 broken failed!
Named pipe dicconnected (0xc00000b0)
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test NTLM and LM, LM broken failed!
Named pipe dicconnected (0xc00000b0)
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test Plaintext failed!
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test Plaintext LM broken failed!
Named pipe dicconnected (0xc00000b0)
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:56, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test Plaintext NT only failed!
Named pipe dicconnected (0xc00000b0)
[2009/09/29 20:18:57, 1] utils/ntlm_auth_diagnostics.c:diagnose_ntlm_auth(599)
  Test Plaintext LM only failed!
 
We too are running a Windows 2008 R2 domain which seems to be the common denominator
 
Good luck
 
Mark

---

### Post by bmcc on 2009-09-30
Hi guys

I finally fixed our problem. It is relating to samba and server 2008 R2. Apparently MS have actually made R2 adhere to standards and samba has had to change to talk properly to it.

We were running a stable 3.0 version of samba from the centos repos. I added the sernet samba repo [http://enterprisesamba.org/index.php?id=125](http://enterprisesamba.org/index.php?id=125) which has 3.4 and all is good.

We have our SSO working for moodle. yay

Good luck

MArk

---

### Post by florpc on 2009-09-30
Thanks! I'm going to try that as well.
 
But how do I install SerNet on Ubuntu? I'm a linux-newbie, you know..
Can I use apt-get for this?

---

### Post by Krijk on 2009-09-30
> **florpc said:**
> 
 
But how do I install SerNet on Ubuntu? I'm a linux-newbie, you know..
Can I use apt-get for this?

apt-get won't work. 

You can download the package from [http://ftp.sernet.de/pub/samba/debian/](http://ftp.sernet.de/pub/samba/debian/) and choose the deb you require.

from the GUI opening it will start the installer, from CLI go to the directory where you downloaded it and do:
 dpkg <packagename>

---

### Post by florpc on 2009-09-30
Great! I'm downloading right now.
 
BTW: It was actually quite obvious, I admit ](*,)

---

### Post by florpc on 2009-10-08
Hi,
 
I still didn't succeed on installing the packages. It says the dependencies are not met.
The refer to other packages, but I cannot install them togheter it seems??

---

### Post by zero_1984 on 2009-10-23
Hi All,

I'm having the same issues as all listed here, espcially like the MP.

we're also running windows 2008 AD servers but the function level is still at a 2003 level.

when trying to install the package mentioned in this post, i recieve the following errors..

```
user@Proxy:~$ sudo dpkg --install sernet-samba_3.2.15-24_i386.deb
(Reading database ... 43119 files and directories currently installed.)
Unpacking sernet-samba (from sernet-samba_3.2.15-24_i386.deb) ...
dpkg: dependency problems prevent configuration of sernet-samba:
 sernet-samba depends on sernet-samba-common (= 3.2.15-24); however:
  Package sernet-samba-common is not installed.
 sernet-samba depends on libcupsys2-gnutls10 (>= 1.1.23-1); however:
  Package libcupsys2-gnutls10 is not installed.
 sernet-samba depends on libdm0; however:
  Package libdm0 is not installed.
 sernet-samba depends on libfam0c102; however:
  Package libfam0c102 is not installed.
 sernet-samba depends on libldap2 (>= 2.1.17-1); however:
  Package libldap2 is not installed.
 sernet-samba depends on sernet-libwbclient0; however:
  Package sernet-libwbclient0 is not installed.
dpkg: error processing sernet-samba (--install):

```

so im guessing i am missing dependencies.. or perhaps i am installing in the wrong order. can anybody help me as to what i need to install first or what i actually need to install to get this going?

---

### Post by zero_1984 on 2009-10-24
anybody here able to help me with this? its doing my head in >.>

---

### Post by zero_1984 on 2009-10-25
Ok so i've decided to refine my question, hopefully it makes more sense.

Im having a similiar situation with active directory/NTLM authentication. the error i am getting is that winbind is not authorized to access the squid cache, and i get a "access denied" when trying to authenticate to my squid box using my AD credentials.

Are there any up to date step by step guides on how to set this up using ubuntu squid and samba?

Thanks,

---

### Post by cariboo on 2009-10-25
Just download all the files in the directory and install them using dpkg eg:

```
sudo dpkg -i sernet-cifs-mount_3.2.15-24_i386.deb 
```

---

