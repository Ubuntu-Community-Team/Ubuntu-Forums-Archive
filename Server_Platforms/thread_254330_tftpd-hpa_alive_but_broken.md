---
title: "tftpd-hpa alive but broken"
date: 2006-09-09
forum: Server Platforms
---

### Post by noven on 2006-09-09
I've got a problem actually using my tftp server. I'm starting it with xinetd and it shows up in my netstat -l as listening {udp:69}. From the local or a remote machine I can log into it but it times out when trying to 'put' or 'get' anything. 

Here is the output of a session:
```


06:31 twdr  ~ $ tftp -v oracle
Connected to oracle (192.168.0.3), port 69
tftp> help
tftp-hpa 0.42
Commands may be abbreviated.  Commands are:

connect         connect to remote tftp
mode            set file transfer mode
put             send file
get             receive file
quit            exit tftp
verbose         toggle verbose mode
trace           toggle packet tracing
status          show current status
binary          set mode to octet
ascii           set mode to netascii
rexmt           set per-packet transmission timeout
timeout         set total retransmission timeout
?               print help information
help            print help information
tftp> put test
putting test to oracle:test [netascii]
Transfer timed out.

tftp> get test
getting from oracle:test to test [netascii]
Transfer timed out.

tftp> binary
mode set to octet
tftp> put test
putting test to oracle:test [octet]
Transfer timed out.

tftp> get test
getting from oracle:test to test [octet]
Transfer timed out.

tftp> quit

```

This was done from a remote client, but the results are exactly the same from the local client. Timeout takes ~30 seconds. The file 'test' exists on both machines, and is a very small sample of data {different on both}

Here is my tftp config:

```

twdr@oracle:~$ cat /etc/xinetd.d/tftp
service tftp
{
   socket_type   = dgram
   protocol   = udp
   wait      = yes
   user      = root
   server      = /usr/sbin/in.tftpd
   server_args   = -c -s /var/lib/tftpboot
   disable      = no
   only_from = 192.168.0.0
   flags        = IPv4
}

```

/var/lib/tftpboot is owned by root:root permissions 755. I tried changing ownership to nobody, and permissions to 777, same result. No firewall exists between the two computers. I have tried both RUN_DAEMON="no" and "yes" in /etc/default/tftpd-hpa.

This really should be a simple service to get operating. Under gentoo and fbsd I never had an issue. Anyone have some ideas as to what sleep-deprived brainless mistake I might be making?

---

### Post by Sladi on 2008-06-10
edit nevermind, it works with root entry


Anybody got a clue why this won't work? 

It works for me as user root when root is specified in xinetd config, but nobody won't work (not even as root). (the tftpboot folder is ownd by nobody)
I guess that's bad when trying to do a netboot from a remote machine, no ?

---

