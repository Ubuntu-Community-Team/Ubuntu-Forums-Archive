---
title: "[Kerberos] KDC outputs no errors to the log, but still cannot be found by kinit"
date: 2009-12-10
forum: Server Platforms
---

### Post by kuchumovn on 2009-12-10
I've installed Kerberos today on my machine.
But when I restart KDC it says "[fail]", but outputs nothing erroneous to the logs.
On my machine I have a running BIND, which provides the "vostrets.ru" (and "kerberos.vostrets.ru") domain name.

The KDC says "[fail]" on restart, and kinit cannot find KDC...
Can you somehow help me in this situation?
Please, tell me, if you need a shell account - I can give it to you...

Oh, and we have a router, which firewalls us from the Internet.
Can it be the cause of the problem?

**dig kerberos.vostrets.ru**
```

; <<>> DiG 9.5.1-P2.1 <<>> kerberos.vostrets.ru
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17535
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 0

;; QUESTION SECTION:
;kerberos.vostrets.ru.          IN      A

;; ANSWER SECTION:
kerberos.vostrets.ru.   86400   IN      A       79.120.48.23

;; AUTHORITY SECTION:
vostrets.ru.            86400   IN      NS      ns1.vostrets.ru.
vostrets.ru.            86400   IN      NS      ns4.nic.ru.
vostrets.ru.            86400   IN      NS      ns8.nic.ru.

;; Query time: 22 msec
;; SERVER: 190.170.1.1#53(190.170.1.1)
;; WHEN: Fri Dec 11 01:46:31 2009
;; MSG SIZE  rcvd: 112

```**default log**
```

Dec 11 01:28:38 syberia krb524d[29013](info): No dictionary file specified, continuing without one.
krb524d: service entry `krb524' not found, using 4444
krb524d: Address already in use - binding main socket

```[B]KDC log
[/B]```

Dec 11 01:12:13 syberia krb5kdc[18523](info): setting up network...
Dec 11 01:12:13 syberia krb5kdc[18523](info): skipping unrecognized local address family 17
Dec 11 01:12:13 syberia krb5kdc[18523](info): listening on fd 8: udp 190.170.1.123.88
Dec 11 01:12:13 syberia krb5kdc[18523](info): listening on fd 9: udp 190.170.1.123.750
Dec 11 01:12:13 syberia krb5kdc[18523](info): listening on fd 10: udp fe80::223:54ff:fe69:5072%eth0.88
Dec 11 01:12:13 syberia krb5kdc[18523](info): listening on fd 11: udp fe80::223:54ff:fe69:5072%eth0.750
Dec 11 01:12:13 syberia krb5kdc[18523](info): set up 4 sockets
Dec 11 01:12:13 syberia krb5kdc[18524](info): commencing operation

```**sudo lsof -i :88**
```

krb5kdc 2822 root    8u  IPv4 6557634       UDP syberia:kerberos
krb5kdc 2822 root   10u  IPv6 6557638       UDP [fe80::223:54ff:fe69:5072]:kerberos

```**general config**
```

  [logging]
    default = FILE:/var/log/krb5.log
    kdc = FILE:/var/log/krb5kdc.log
    admin_server = FILE:/var/log/kadmin.log

  [libdefaults]
    dns_lookup_kdc = true 
    default_realm = VOSTRETS.RU

  ...

  [realms]
    VOSTRETS.RU = {
        kdc = kerberos.vostrets.ru:88
        admin_server = kerberos.vostrets.ru:749
        default_domain = vostrets.ru
    }

  ...

  [domain_realm]
    .vostrets.ru = VOSTRETS.RU
    vostrets.ru = VOSTRETS.RU

  ...

  [login]
    krb4_convert = false
    krb4_get_tickets = false

```**KDC config**
```

  [realms]
    VOSTRETS.RU = {
        ...
    }

  ...

  [logging]
    kdc = FILE:/var/log/kdc.log
    admin_server = FILE:/var/log/kadmin.log

```**sudo /etc/init.d/krb5-kdc restart**
```

* Restarting Kerberos KDC krb5kdc                                  [COLOR=Red][fail]
[/COLOR]
```**sudo kinit**
```

kinit(v5): Cannot contact any KDC for realm 'VOSTRETS.RU' while getting initial credentials

```

---

### Post by kuchumovn on 2009-12-11
Hmmm, i've rebooted my PC, and now KDC is restarting normally (it says "[OK]").
and the error "krb524d: Address already in use - binding main socket" has gone..
But it is still not found by kinit..

---

### Post by kuchumovn on 2009-12-11
I guess then, the kerberos daemon goes to krb5.conf, reads that "KDC is listening on kerberos.vostrets.ru on port 88" and tries to contact it.
But for some reason the 88th port appears to be closed on my machine:

```

kuchumovn@syberia:~$ **nmap kerberos.vostrets.ru**

Starting Nmap 4.76 ( http://nmap.org ) at 2009-12-11 14:47 MSK
Interesting ports on localhost (127.0.0.1):
Not shown: 983 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
53/tcp    open  domain
80/tcp    open  http
139/tcp   open  netbios-ssn
389/tcp   open  ldap
445/tcp   open  microsoft-ds
631/tcp   open  ipp
749/tcp   open  kerberos-adm
3920/tcp  open  unknown
4848/tcp  open  unknown
5432/tcp  open  postgresql
6881/tcp  open  bittorrent-tracker
7676/tcp  open  unknown
8080/tcp  open  http-proxy
8181/tcp  open  unknown
16001/tcp open  unknown

``````

kuchumovn@syberia:~$ [B]sudo nmap -sU kerberos.vostrets.ru
[/B]
Starting Nmap 4.76 ( http://nmap.org ) at 2009-12-11 14:53 MSK
Interesting ports on localhost (127.0.0.1):
Not shown: 992 closed ports
PORT     STATE         SERVICE
53/udp   open|filtered domain
68/udp   open|filtered dhcpc
123/udp  open|filtered ntp
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
464/udp  open          kpasswd5
4444/udp open|filtered krb524
5353/udp open|filtered zeroconf

```So, nobody seems to be listening either 88th TCP or 88th UDP.

But the "lsof" utility says, that somebody is still listening at least on the 88th UDP

```

kuchumovn@syberia:~$ **sudo lsof -i :88**
COMMAND   PID USER   FD   TYPE DEVICE SIZE NODE NAME
krb5kdc 30022 root    8u  IPv4 110143       UDP syberia:kerberos
krb5kdc 30022 root   10u  IPv6 110147       UDP [fe80::223:54ff:fe69:5072]:kerberos

```And in my /etc/services there are directives to listen both on TCP and UDP:
```

kerberos    88/tcp        kerberos5 krb5 kerberos-sec    # Kerberos v5
kerberos    88/udp        kerberos5 krb5 kerberos-sec    # Kerberos v5

```

I guess it's my lack of UNIX knowledge now...
I'll go google something then...
Or maybe you can tell me, why aren't the 88th ports listening, and how can I tell them to listen?

---

### Post by kuchumovn on 2009-12-11
So, what I've understood by now, is that, though it says "[OK]", KDC doesn't start listening on 88th TCP port, and listens only on 88th UDP port.
Maybe it is supposed to do so...
But still I'm not sure, that it even listens on 88th UDP port, because **sudo nmap -sU kerberos.vostrets.ru **shows no 88 port at all...
**netstat --all --numeric --udp | grep "LISTEN "** shows nothing, and just **netstat --all --numeric --udp** shows that something's on 88th UDP port, but it is blank - it is neither LISTEN, nor ESTABLISHED...
just some weird utility **sudo lsof -i :88** shows that there is KDC on UDP, but I don't know how can it help, because it is named "list of files"...
So, to sum it up, KDC still does some business on 88th UDP port, but it is not a LISTENing business...
And no errors in logs...
How am I supposed to debug it with such a level of logging?..

---

### Post by kuchumovn on 2009-12-11
I decided to uninstall MIT and try Heimdal:

```

sudo aptitude remove krb5-kdc krb5-admin-server krb5-user

sudo aptitude install heimdal-kdc heimdal-servers hemdal-servers-x heimdal-clients heimdal-clients-x heimdal-lib heimdal-libskrb5-config

 sudo kate /etc/krb5.conf
  ====================================================
  [logging]
    default = FILE:/var/log/krb5.log
    kdc = FILE:/var/log/krb5kdc.log
    admin_server = FILE:/var/log/kadmin.log

  [libdefaults]
    dns_lookup_kdc = true 
    default_realm = VOSTRETS.RU

  ...

  [realms]
    VOSTRETS.RU = {
        kdc = kerberos.vostrets.ru:88
        admin_server = kerberos.vostrets.ru:749
        default_domain = vostrets.ru
    }

  ...

  [domain_realm]
    .vostrets.ru = VOSTRETS.RU
    vostrets.ru = VOSTRETS.RU

  ...

  [login]
    krb4_convert = false
    krb4_get_tickets = false
  ====================================================

 sudo kate /etc/heimdal-kdc/kdc.conf
  ====================================================
  [kdc]
        enable-kerberos4 = false

  [libdefaults]
             default_realm = VOSTRETS.RU

  [realms]
             VOSTRETS.RU = {
                     kdc = kerberos.vostrets.ru:88
             }

  [domain_realm]
             .vostrets.ru = VOSTRETS.RU
  ====================================================
 sudo mkdir /var/heimdal
 sudo kstash
 sudo kadmin -l
  kadmin> init VOSTRETS.RU
  kadmin> add kuchumovn
  kadmin> exit
 sudo /etc/init.d/heimdal-kdc restart
 kinit kuchumovn
 klist
 kadmin check VOSTRETS.RU
  if kadmin outputs "Connection refused" error, reboot
 sudo kate /etc/heimdal-kdc/kadmind.acl
  ====================================================
  administrator/admin@VOSTRETS.RU    all  
  *@VOSTRETS.RU                      cpw 
  ====================================================

```Now it does listen on 88th TCP.
The tickets now are being issued, and i can see them through **klist**.
But **kadmin check VOSTRETS.RU **outputs "Connection failed" error:

```

kadmin check VOSTRETS.RU
kadmin: connect(kerberos.vostrets.ru): Connection refused
kadmin: failed to contact kerberos.vostrets.ru
krbtgt/VOSTRETS.RU@VOSTRETS.RU doesn't exist, are you sure VOSTRETS.RU is a realm in your database

```but such a principal exists:

```

klist
Credentials cache: FILE:/tmp/krb5cc_1000
        Principal: kuchumovn@VOSTRETS.RU

  Issued           Expires          Principal
Dec 11 19:43:33  Dec 12 05:43:33  krbtgt/VOSTRETS.RU@VOSTRETS.RU

```I'll see if I can fix it... Or I won't fix it at all..
But again, the tickets seem to be working.

===========================

Update: the error "Couldn't connect" appeared because of the kerberos admin server not listening on 749th TCP port.
I've rebooted my PC, and now it seems to be working.

===========================

If you get such an error:

```
kadmin: kadm5_create_principal: Need to use PA-ENC-TIMESTAMP/PA-PK-AS-REQ
kadmin: adding HTTP/vostrets.ru: Need to use PA-ENC-TIMESTAMP/PA-PK-AS-REQ
```when executing, for example, this:

```

kadmin --principal=administrator/admin --keytab=/etc/heimdal-kdc/administrator_key.tab --realm=VOSTRETS.RU add --use-defaults --random-key HTTP/vostrets.ru

```Then you should chmod the keytab file to be readable by the current user

For example, to be able to add users to Kerberos from a Java application, execute this script:

```

sudo chown glassfish /etc/heimdal-kdc/administrator_key.tab

```or replace *glassfish* with whatever username you are logged in.

If still getting errors, try to reboot...

Then, at last, in your J2EE application:

```

import java.io.InputStream;
...
String cmd = "kadmin --principal=administrator/admin
--keytab=/etc/heimdal-kdc/administrator_key.tab --realm=VOSTRETS.RU add
--use-defaults --password=PASSWORD USERNAME/vostrets.ru"; // this is the command to execute in the Unix shell
// create a process for the shell
ProcessBuilder pb = new ProcessBuilder("bash", "-c", cmd);
pb.redirectErrorStream(true); // use this to capture messages sent to stderr
Process shell = pb.start();
InputStream shellIn = shell.getInputStream(); // this captures the output from the command
int shellExitStatus = shell.waitFor(); // wait for the shell to finish and get the return code
// at this point you can process the output issued by the command
// for instance, this reads the output and writes it to System.out:
int c;
while ((c = shellIn.read()) != -1) {System.out.write(c);}
// close the stream
try {shellIn.close();} catch (IOException ignoreMe) {}

```===========================================================

not to mention that this Kerberos broke my vsFTPd, it is broken again...
that's what it says now:

```

kadmin: kadm5_create_principal: Operation requires `add' privilege
kadmin: adding homer/vostrets.ru: Operation requires `add' privilege

```i guess the database somehow got ******...
maybe i'll try to reinitialize it, or even reinstall the whole thing...

===============================================================

I've reinstalled the whole thing, and still the error remained, and you know what it was?
At first I used *"administrator/admin"* in *kadmind.acl*.
Then I changed it to *"*/admin"*.
And it appeared that It just didn't understand *"*/admin"* rule, though it surely should have supported wildcard symbols like *MIT Kerberos* does it...
so, i changed *kadmind.acl* to this:

```

  administrator/admin           all  
  *@VOSTRETS.RU                 change-password

```and it seems to work now for *"administrator/admin"*...

---

