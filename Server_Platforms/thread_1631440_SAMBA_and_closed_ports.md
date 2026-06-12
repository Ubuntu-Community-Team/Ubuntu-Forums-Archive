---
title: "SAMBA and closed ports"
date: 2010-11-26
forum: Server Platforms
---

### Post by Zitan on 2010-11-26
I can't browse my SAMBA shares because ports between 137 to 139 and 445 are closed, but I don't know why. I even turn off iptables

```
root@SERWER:~# iptables -L && smbclient -L localhost -N
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)
```but...

```
root@SERWER:~# echo "hello" | telnet localhost 445
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
root@SERWER:~# echo "hello" | telnet localhost 137
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
root@SERWER:~# echo "hello" | telnet localhost 138
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
root@SERWER:~# echo "hello" | telnet localhost 139
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
root@SERWER:~# echo "hello" | telnet localhost 80
Trying ::1...
Connected to SERWER.PCPR.LAN.
Escape character is '^]'.
Connection closed by foreign host.
```Ports are still closed... why?

ps. sorry for my poor english

---

### Post by Dmitry13 on 2010-11-26
Are you sure that Samba is configured properly?

---

### Post by CharlesA on 2010-11-26
Run nmap against that box instead of trying to use telnet.

---

### Post by Zitan on 2010-11-27
> **Dmitry13 said:**
> Are you sure that Samba is configured properly?
probably... 
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[netlogon]"
Processing section "[homes]"
Processing section "[profiles]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC
Press enter to see a dump of your service definitions

[global]
        dos charset = CP852
        unix charset = ISO8859-2
        workgroup = PCPR
        server string = SERWER
        passdb backend = ldapsam:ldap://serwer.pcpr.lan
        passwd program = /usr/sbin/smbldap-passwd %u
        passwd chat = *New*password* %nn *Retype*new*password* %nn
        log level = 2
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 50
        name resolve order = wins lmhosts host bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192
        add user script = /usr/sbin/smbldap-useradd -m "%u"
        delete user script = /usr/sbin/smbldap-userdel "%u"
        add group script = /usr/sbin/smbldap-groupadd -p "%g"
        delete group script = /usr/sbin/smbldap-groupdel "%g"
        add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
        delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
        set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"
        add machine script = /usr/sbin/smbldap-useradd -w "%u"
        logon script = netlogon.bat OR %U.bat
        logon path = \%Lprofiles%U
        logon drive = U:
        logon home = \%L%U.profile
        domain logons = Yes
        os level = 65
        preferred master = Yes
        domain master = Yes
        dns proxy = No
        wins support = Yes
        ldap admin dn = cn=admin,dc=pcpr,dc=lan
        ldap delete dn = Yes
        ldap group suffix = ou=groups
        ldap machine suffix = ou=machines
        ldap passwd sync = yes
        ldap suffix = dc=pcpr,dc=lan
        ldap ssl = no
        ldap user suffix = ou=users
        hosts allow = 127.0.0.1, 192.168.16.0/24
        hide unreadable = Yes

[netlogon]
        comment = Network Logon Service
        path = /home/samba/netlogon
        browseable = No

[homes]
        comment = HOME Directories
        path = /home/%U
        valid users = %S
        read only = No
        inherit permissions = Yes
        browseable = No

[profiles]
        path = /home/samba/profiles
        valid users = %U, "@Domain Admins"
        read only = No
        create mask = 0600
        directory mask = 0700
        case sensitive = No
        preserve case = No
        short preserve case = No
        hide files = /desktop.ini/ntuser.ini/NTUSER.*/
        browseable = No
        csc policy = disable
```

---

### Post by CharlesA on 2010-11-27
Where did you get that smb.conf? Is your server set up as PDC?

This is what mine looks like and it works fine:

```
charles@thor:~$ testparm -s /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Charles]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string =
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:                                                                                                 * %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[Charles]
        comment = Charles' Folder
        path = /array/charles
        invalid users = clone, htpc
        write list = charles
        create mask = 0660
        directory mask = 0770

```

---

### Post by elico on 2010-11-27
the connection was refused and not just closed of nothing.
it's about some software settings.

first you should try simple small samba share with a guest user allowed.

another question...
what windows OS are you using?

---

### Post by Zitan on 2010-11-27
> **elico said:**
> the connection was refused and not just closed of nothing.
it's about some software settings.

first you should try simple small samba share with a guest user allowed.

You right, It was the first thing I did before writing the post. My first samba configuration was:
```
[global]
workgroup = PCPR
netbios name = Debian
[files]
    revalidate = yes
    public = yes
    path = /home/files&drivers
```> **elico said:**
> 
another question...
what windows OS are you using?

System is Debian

---

### Post by CharlesA on 2010-11-27
Are you using it as a PDC?

---

### Post by Zitan on 2010-11-27
> **CharlesA said:**
> Are you using it as a PDC?

Yes, with ldap server

---

### Post by CharlesA on 2010-11-27
Ok. Have you verified that those ports have a service listening on them?

```
netstat -nl
```

Could also scan it from another box with nmap.

---

### Post by Zitan on 2010-11-28
Now I'm even more confused than before

```
root@SERWER:~# nmap -A serwer.pcpr.lan

Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-28 23:58 CET
Warning: Hostname serwer.pcpr.lan resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on SERWER.PCPR.LAN (127.0.0.1):
Not shown: 988 closed ports
PORT      STATE SERVICE    VERSION
25/tcp    open  smtp       Exim smtpd 4.72
|  smtp-commands: EHLO SERWER.PCPR.LAN Hello localhost [127.0.0.1], SIZE 52428800, PIPELINING, HELP
|_ HELP Commands supported: AUTH HELO EHLO MAIL RCPT DATA NOOP QUIT RSET HELP
53/tcp    open  domain     ISC BIND 9.7.1-P2
80/tcp    open  http       Apache httpd 2.2.16 ((Debian))
|_ html-title: Site doesn't have a title (text/html).
111/tcp   open  rpcbind
|  rpcinfo:
|  100000  2    111/udp  rpcbind
|  100024  1  59169/udp  status
|  100000  2    111/tcp  rpcbind
|_ 100024  1  48532/tcp  status
389/tcp   open  ldap       OpenLDAP 2.2.X
3306/tcp  open  mysql      MySQL 5.1.49-2
|  mysql-info: Protocol: 10
|  Version: 5.1.49-2
|  Thread ID: 97
|  Some Capabilities: Long Passwords, Connect with DB, Compress, ODBC, Transactions, Secure Connection
|  Status: Autocommit
|_ Salt: =m-7j5cwKP2HSFFnt}:E
5222/tcp  open  jabber     jabberd instant messaging server
5269/tcp  open  jabber     jabberd instant messaging server
9091/tcp  open  unknown
9102/tcp  open  jetdirect?
9103/tcp  open  jetdirect?
10000/tcp open  http       Webmin httpd
|_ html-title: Site doesn't have a title (text/html).
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at http://www.insecure.org/cgi-bin/servicefp-submit.cgi :
SF-Port9091-TCP:V=5.00%I=7%D=11/28%Time=4CF2DE8C%P=x86_64-unknown-linux-gnu%r(GenericLines,108,"HTTP/1\.1\x20400\x20Bad\x20Request\r\nContent-Type:\x
SF:20text/html\r\nConnection:\x20close\r\nDate:\x20Sun,\x2028\x20Nov\x2020
SF:10\x2022:58:20\x20GMT\r\nContent-Length:\x20134\r\n\r\n<HTML><HEAD>\n<T
SF:ITLE>400\x20Bad\x20Request</TITLE>\n</HEAD><BODY>\n<H1>Method\x20Not\x2
SF:0Implemented</H1>\nInvalid\x20method\x20in\x20request<P>\n</BODY></HTML
SF:>\n")%r(GetRequest,1AD,"HTTP/1\.0\x20403\x20Forbidden\r\nServer:\x20Tra
SF:nsmission\r\nContent-Type:\x20text/html;\x20charset=ISO-8859-1\r\n\r\n<
SF:h1>403:\x20Forbidden</h1><p>Unauthorized\x20IP\x20Address\.</p><p>Eithe
SF:r\x20disable\x20the\x20IP\x20address\x20whitelist\x20or\x20add\x20your\
SF:x20address\x20to\x20it\.</p><p>If\x20you're\x20editing\x20settings\.jso
SF:n,\x20see\x20the\x20'rpc-whitelist'\x20and\x20'rpc-whitelist-enabled'\x
SF:20entries\.</p><p>If\x20you're\x20still\x20using\x20ACLs,\x20use\x20a\x
SF:20whitelist\x20instead\.\x20\x20See\x20the\x20transmission-daemon\x20ma
SF:npage\x20for\x20details\.</p>")%r(HTTPOptions,108,"HTTP/1\.1\x20400\x20
SF:Bad\x20Request\r\nContent-Type:\x20text/html\r\nConnection:\x20close\r\
SF:nDate:\x20Sun,\x2028\x20Nov\x202010\x2022:58:20\x20GMT\r\nContent-Lengt
SF:h:\x20134\r\n\r\n<HTML><HEAD>\n<TITLE>400\x20Bad\x20Request</TITLE>\n</
SF:HEAD><BODY>\n<H1>Method\x20Not\x20Implemented</H1>\nInvalid\x20method\x
SF:20in\x20request<P>\n</BODY></HTML>\n")%r(RTSPRequest,108,"HTTP/1\.1\x20
SF:400\x20Bad\x20Request\r\nContent-Type:\x20text/html\r\nConnection:\x20c
SF:lose\r\nDate:\x20Sun,\x2028\x20Nov\x202010\x2022:58:20\x20GMT\r\nConten
SF:t-Length:\x20134\r\n\r\n<HTML><HEAD>\n<TITLE>400\x20Bad\x20Request</TIT
SF:LE>\n</HEAD><BODY>\n<H1>Method\x20Not\x20Implemented</H1>\nInvalid\x20m
SF:ethod\x20in\x20request<P>\n</BODY></HTML>\n")%r(Help,108,"HTTP/1\.1\x20
SF:400\x20Bad\x20Request\r\nContent-Type:\x20text/html\r\nConnection:\x20c
SF:lose\r\nDate:\x20Sun,\x2028\x20Nov\x202010\x2022:58:35\x20GMT\r\nConten
SF:t-Length:\x20134\r\n\r\n<HTML><HEAD>\n<TITLE>400\x20Bad\x20Request</TIT
SF:LE>\n</HEAD><BODY>\n<H1>Method\x20Not\x20Implemented</H1>\nInvalid\x20m
SF:ethod\x20in\x20request<P>\n</BODY></HTML>\n");
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.17 - 2.6.28
Network Distance: 0 hops

OS and Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 71.90 seconds
root@SERWER:~# netstat -nl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:9102          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:9103          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:48532           0.0.0.0:*               LISTEN
tcp        0      0 192.168.16.1:53         0.0.0.0:*               LISTEN
tcp        0      0 192.168.0.200:53        0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:51413           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:1410            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:9091            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 192.168.16.1:9101       0.0.0.0:*               LISTEN
tcp6       0      0 :::80                   :::*                    LISTEN
tcp6       0      0 :::5269                 :::*                    LISTEN
tcp6       0      0 :::53                   :::*                    LISTEN
tcp6       0      0 :::51413                :::*                    LISTEN
tcp6       0      0 ::1:25                  :::*                    LISTEN
tcp6       0      0 ::1:953                 :::*                    LISTEN
tcp6       0      0 :::1410                 :::*                    LISTEN
tcp6       0      0 :::389                  :::*                    LISTEN
tcp6       0      0 :::5222                 :::*                    LISTEN
udp        0      0 0.0.0.0:111             0.0.0.0:*
udp        0      0 0.0.0.0:890             0.0.0.0:*
udp        0      0 192.168.0.255:137       0.0.0.0:*
udp        0      0 192.168.0.200:137       0.0.0.0:*
udp        0      0 0.0.0.0:137             0.0.0.0:*
udp        0      0 192.168.0.255:138       0.0.0.0:*
udp        0      0 192.168.0.200:138       0.0.0.0:*
udp        0      0 0.0.0.0:138             0.0.0.0:*
udp        0      0 0.0.0.0:10000           0.0.0.0:*
udp        0      0 0.0.0.0:59169           0.0.0.0:*
udp        0      0 0.0.0.0:54580           0.0.0.0:*
udp        0      0 192.168.16.1:53         0.0.0.0:*
udp        0      0 192.168.0.200:53        0.0.0.0:*
udp        0      0 127.0.0.1:53            0.0.0.0:*
udp        0      0 0.0.0.0:67              0.0.0.0:*
udp        0      0 0.0.0.0:51413           0.0.0.0:*
udp        0      0 0.0.0.0:5353            0.0.0.0:*
udp6       0      0 :::53                   :::*
udp6       0      0 :::47834                :::*
udp6       0      0 :::5353                 :::*
raw        0      0 0.0.0.0:1               0.0.0.0:*               7
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     5555     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     5012     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     6524     /var/run/nslcd/socket
unix  2      [ ACC ]     STREAM     LISTENING     6903     /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     5587     /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     5585     /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     6199     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     5141     /var/run/nscd/socket
unix  2      [ ACC ]     STREAM     LISTENING     2484669  @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     5189     /var/run/slapd/ldapi
unix  2      [ ACC ]     STREAM     LISTENING     2484670  /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     5878     /var/run/avahi-daemon/socket
root@SERWER:~#

```samba does not listens at all

---

### Post by CharlesA on 2010-11-28
Run this:

```
service smbd status
```

```
service nmbd status
```

---

### Post by capscrew on 2010-11-28
It looks like Samba is not running.  There is nothing listening.  Your test was worthwhile.  You should check to see if the *smbd *and *nmbd *daemons are running.   Try this:```
ps -ef|grep mbd
```

This should show 2 instances of *smbd *and 1 of *nmbd*.  

What is curious is this from your scan```
unix  2      [ ACC ]     STREAM     LISTENING     5587     /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     5585     /tmp/.winbindd/pipe
```

It looks as if winbind is running.  Do Samba users authenticate against AD in your network?

---

### Post by CharlesA on 2010-11-28
They set it up as a LDAP server.

---

### Post by capscrew on 2010-11-28
> **CharlesA said:**
> They set it up as a LDAP server.


@CharlesA,

Yes, I saw the references to LDAP.  There is no need to run Winbind just because you are running LDAP as the passdb for Samba.

It appears that Samba is still doing the authentication.  I assume this means UID/GUID.  Winbind is for mapping MS style SID's to UID/GUID's.

If the OP is not in a Windows AD situation then Winbind should be irrelevant.  I my 2 Samba servers authenticate off of there on local passdb's.  I keep them sync'd with each other and with the usernames of the windows clients.  It all works perfectly.  This is not the best way if you have a large amount of users, but it does point out what roll each mechanism provides.

---

### Post by Zitan on 2010-11-28
Hmmm... very strange
```
root@SERWER:~# /etc/init.d/samba restart
Stopping Samba daemons: nmbd.
Starting Samba daemons: nmbd.
root@SERWER:~# service smbd status
smbd: unrecognized service

```So I configured the SAMBA again as daemon.

```
aptitude purge samba && aptitude install samba && dpkg-reconfigure samba
```new password for admin

```
root@SERWER:~# smbpasswd -w my_secret_password
Setting stored password for "cn=admin,dc=pcpr,dc=lan" in secrets.tdb

```and again 

```
 smbclient -L localhost
Enter root's password:
Domain=[PCPR] OS=[Unix] Server=[Samba 3.5.6]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (Samba PDC)
        root            Disk      HOME Directories
Domain=[PCPR] OS=[Unix] Server=[Samba 3.5.6]

        Server               Comment
        ---------            -------
        SERWER               Samba PDC

        Workgroup            Master
        ---------            -------
        PCPR

```It works! finally. Thank you for your help, and for pointing me to a solution.

---

### Post by CharlesA on 2010-11-28
> **capscrew said:**
> @CharlesA,

Yes, I saw the references to LDAP.  There is no need to run Winbind just because you are running LDAP as the passdb for Samba.

It appears that Samba is still doing the authentication.  I assume this means UID/GUID.  Winbind is for mapping MS style SID's to UID/GUID's.

Ah thank you. I just remember that I had a hell of a time getting Samba to authenticate to an Active directory DC. Never did get it to work either.

@Zitan: Don't forget to mark the thread as solved from thread tools.

---

### Post by capscrew on 2010-11-28
@Zitan,

Your welcome.

~~~~~~~~~~~~~~~~~~

> I just remember that I had a hell of a time getting Samba to authenticate to an Active directory DC

@CharlesA

I worked on a proof of concept project way back in the early Samba 3.0 days.  It was overly complex and never worked correctly either.  I sure learned a lot though.

---

