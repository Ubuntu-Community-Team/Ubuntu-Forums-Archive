---
title: "Kerberos: kadmin not working"
date: 2014-09-21
forum: Server Platforms
---

### Post by vollenweider on 2014-09-21
Hello

I'm trying to set up my Kerberos Realm in order to get kerberos auth for NFS.

As far as I can tell everything seemed to run smoothly. FQDN are assigned properly to the client and the server. NTP is working – they're in sync, and i could also set up krb5-admin-server and can now even kinit on it from either locally on the server or as the client.

```
kinit on the server Server:

adm@server:/# kinit cas/admin
Password for cas/admin@beispiel.net:
adm@fpsrv:/# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: cas/admin@beispiel.net

Valid starting       Expires              Service principal
09/21/2014 19:32:38  09/22/2014 05:32:38  krbtgt/@beispiel.net@beispiel.net
        renew until 09/22/2014 19:32:31

kinit works on the client over net as well:

cas@fpdesk1 ~ $ kinit cas/admin
Password for cas/admin@beispiel.net:
cas@fpdesk1 ~ $ klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: cas/admin@beispiel.net

Valid starting       Expires              Service principal
09/21/2014 19:33:30  09/22/2014 05:33:30  krbtgt/beispiel.net@beispiel.net [COLOR=#000000][FONT=Bitstream Vera Sans Mono]renew until 09/22/2014 19:33:26[/FONT][/COLOR]
```


But with kadmin i have stepped into trouble i didn't manage to find any proper advice with web searching yet:
```

cas@server:~$ kadmin
Authenticating as principal cas/admin@beispiel.net with password.
kadmin: Missing parameters in krb5.conf required for kadmin client while initializing kadmin interface
```

Same answer either on the client or the server, su'ed with any type of user or using kadmin -p cas/admin asf.

And kadmin is also lacking the kindnes of giving me any hints on this. I have no idea what could be wrong with my krb5.conf
[ATTACH]256590[/ATTACH]

If anyone possesses knowledge about how this could be solved here, I'd be very happy if you'd share it with me. 

TIA

just to be complete:
```
root@server:/etc# kadmin.localAuthenticating as principal cas/admin@anonfqdn.net with password.
kadmin.local:  listprincs
K/M@anonfqdn.net
kadmin/admin@anonfqdn.net
kadmin/changepw@anonfqdn.net
kadmin/server.anonfqdn.net@anonfqdn.net
cas/admin@anonfqdn.net
krbtgt/fp.ddns.net@anonfqdn.net
kadmin.local:
```
[ATTACH]256591[/ATTACH]
```
cas@server:~$ sudo netstat -anp | grep krb
udp        0      0 0.0.0.0:750             0.0.0.0:*                           10774/krb5kdc
udp        0      0 0.0.0.0:88              0.0.0.0:*                           10774/krb5kdc
udp6       0      0 fe80::21c:c0ff:fe33:750 :::*                                10774/krb5kdc
udp6       0      0 2001:xxxx:xxxx:0:21:750 :::*                                10774/krb5kdc
udp6       0      0 2001:xxxx:xxxx:0:c5:750 :::*                                10774/krb5kdc
udp6       0      0 fe80::21c:c0ff:fe33::88 :::*                                10774/krb5kdc
udp6       0      0 2001:xxxx:xxxx:0:21c:88 :::*                                10774/krb5kdc
udp6       0      0 2001:xxxx:xxxx:0:c50:88 :::*                                10774/krb5kdc
unix  2      [ ]         DGRAM                    40076    10774/krb5kdc
unix  3      [ ]         STREAM     CONNECTED     40077    10774/krb5kdc
unix  3      [ ]         STREAM     CONNECTED     40078    10774/krb5kdc
cas@server:~$ sudo netstat -anp | grep kadmin
tcp        0      0 0.0.0.0:749             0.0.0.0:*               LISTEN      10496/kadmind
tcp        0      0 0.0.0.0:464             0.0.0.0:*               LISTEN      10496/kadmind
tcp6       0      0 :::749                  :::*                    LISTEN      10496/kadmind
tcp6       0      0 :::464                  :::*                    LISTEN      10496/kadmind
udp        0      0 0.0.0.0:464             0.0.0.0:*                           10496/kadmind
udp6       0      0 fe80::21c:c0ff:fe33:464 :::*                                10496/kadmind
udp6       0      0 2001:xxxx:xxxx:0:21:464 :::*                                10496/kadmind
udp6       0      0 2001:xxxx:xxxx:0:c5:464 :::*                                10496/kadmind
unix  2      [ ]         DGRAM                    39946    10496/kadmind
unix  3      [ ]         STREAM     CONNECTED     39947    10496/kadmind
unix  3      [ ]         STREAM     CONNECTED     39948    10496/kadmind
```

---

### Post by vollenweider on 2014-09-21
Hello

It appears that i just discovered the problem here, and it seems to be even quity silly and trivial.
default_realm = ATHENA.MIT.EDU is casesensitive. I don't knwo if it was automatic configuration or myself that did it lower case, but it seems that this was the problem.
Strange enough, /etc/krb5kdc/kdc.conf WANTS the realm to be lowercase and krb5.conf seems to demand UPPERCASE. Well, strange world, especially if one enters Kerberos' domain. ;-)

So thx for attending. For now I'm finally getting further. :)

---

