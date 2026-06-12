---
title: "Xinetd 754/tcp Kerberos Propagation Port can't open"
date: 2010-04-06
forum: Server Platforms
---

### Post by romeroc24 on 2010-04-06
Hi, I can't open 754/tcp por for kerberos propagation, the service is krb_prop.

The file /etc/xinetd.conf:
```

defaults
{

}

includedir /etc/xinetd.d

```

The file /etc/xinetd.d/krb_prop:

```

service krb_prop
{
        disable         = no
        socket_type     = stream
        protocol        = tcp
        user            = root
        wait            = no
        server          = /usr/sbin/kpropd
}

```

Restaring the service:

```

$sudo /etc/init.d/xinetd restart

```

When I do:

```

$sudo nmap -sU -sT localhost

```

Can see some ports, but no krb_prop 754/tcp.

---

### Post by cdenley on 2010-04-06
```

sudo netstat -tlnp
grep file=/etc/xinetd.d/krb_prop /var/log/syslog
ls -l /usr/sbin/kpropd
dpkg -l krb5-kdc
getent services krb_prop

```

---

### Post by romeroc24 on 2010-04-06
```

$ sudo netstat -tlnp 

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         
State       PID/Program name
tcp        0      0 0.0.0.0:754             0.0.0.0:*               LISTEN      2609/xinetd

$ sudo grep file=/etc/xinetd.d/krb_prop /var/log/syslog

Apr  5 23:47:33 mainserver xinetd[7784]: Reading included configuration file: /etc/xinetd.d/krb_prop [file=/etc/xinetd.d/krb_prop] [line=26]
Apr  6 16:42:38 mainserver xinetd[2609]: Reading included configuration file: /etc/xinetd.d/krb_prop [file=/etc/xinetd.d/krb_prop] [line=26]

$ sudo ls -l /usr/sbin/kpropd
-rwxr-xr-x 1 root root 23144 2009-04-07 15:51 /usr/sbin/kpropd

cromero@mainserver:~$ sudo dpkg -l krb5-kdc
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  krb5-kdc                 1.6.dfsg.4~beta1-5ubuntu MIT Kerberos key server (KDC)

cromero@mainserver:~$ sudo getent services krb_prop

krb_prop              754/tcp krb5_prop hprop

```

Wow!, thank you man, I've forgot the netstat command. It seems to be Okey (if not tell me please):
```

cromero@mainserver:~$ sudo nmap -sU -sT localhost

Starting Nmap 4.76 ( http://nmap.org ) at 2010-04-06 17:36 PET
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 1982 closed ports
PORT     STATE         SERVICE
22/tcp   open          ssh
53/tcp   open          domain
80/tcp   open          http
110/tcp  open          pop3
139/tcp  open          netbios-ssn
143/tcp  open          imap
445/tcp  open          microsoft-ds
631/tcp  open          ipp
749/tcp  open          kerberos-adm
993/tcp  open          imaps
995/tcp  open          pop3s
53/udp   open|filtered domain
123/udp  open|filtered ntp
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
464/udp  open          kpasswd5
4444/udp open|filtered krb524
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.48 seconds
cromero@mainserver:~$ sudo nmap -p 754 localhost

Starting Nmap 4.76 ( http://nmap.org ) at 2010-04-06 17:36 PET
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
PORT    STATE SERVICE
754/tcp open  krb_prop


```

---

### Post by cdenley on 2010-04-06
Yes. It looks like nmap simply doesn't check port 754 by default. It only checks the most commonly used ports.

---

