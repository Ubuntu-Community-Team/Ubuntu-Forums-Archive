---
title: "First time mail server setup"
date: 2016-07-07
forum: Server Platforms
---

### Post by nhagney on 2016-07-07
I am trying to setup my first E-Mail server. I am using this tut [https://help.ubuntu.com/community/PostfixBasicSetupHowto#Installing_courier_IMAP_and_POP3](https://help.ubuntu.com/community/PostfixBasicSetupHowto#Installing_courier_IMAP_and_POP3) now i'm a small time novice but not completely oblivious to ubuntu. while trying to test the local domain on the local machine i get this. can someone gide me from here sorry for the sloppy post im tired and headed to bed. Thank you for your time!!!

```
nick@nicnetworking:~$ sudo postconf mydestinationmydestination = $myhostname, nicnetworking.com, localhost.com, , localhost
nick@nicnetworking:~$ sudo postconf -e "mydestination = mail.nicnetworking.com, localhost.localdomain, localhost, nicnetworking.com
> sudo postconf -e "mydestination = mail.nicnetworking.com, localhost.localdomain, localhost, nicnetworking.com
postconf: fatal: -e, -X, or -# accepts no multi-line input
nick@nicnetworking:~$ sudo nano postconf
nick@nicnetworking:~$ sudo postconf -e "mydestination = mail.nicnetworking.com, localhost.localdomain, localhost, nicnetworking.com
> postconf -e "mydestination = mail.nicnetworking.com, localhost.localdomain, localhost, nicnetworking.com
postconf: fatal: -e, -X, or -# accepts no multi-line input
nick@nicnetworking:~$ sudo postconf -e "mydestination = mail.nicnetworking.com, localhost.localdomain, localhost, nicnetworking.com"
nick@nicnetworking:~$ sudo postconf -e "mydestination = mail.nicnetworking.com, localhost.localdomain, localhost, nicnetworking.com"
nick@nicnetworking:~$ sudo postconf mydestination
mydestination = mail.nicnetworking.com, localhost.localdomain, localhost, nicnetworking.com
nick@nicnetworking:~$ sudo postconf mynetworks
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
nick@nicnetworking:~$ sudo postconf -e "mynetworks = 127.0.0.0/8, 10.0.0.0/24"
nick@nicnetworking:~$ sudo postconf mynetworks
mynetworks = 127.0.0.0/8, 10.0.0.0/24
nick@nicnetworking:~$ sudo postconf -e "inet_interfaces = all"
nick@nicnetworking:~$ icnetworking.com, localhost.localdomain, localhost, nicnetworking.com
icnetworking.com,: command not found
nick@nicnetworking:~$ nick@nicnetworking:~$ s
nick@nicnetworking:~$: command not found
nick@nicnetworking:~$ sudo  /etc/init.d/postfix restart
[ ok ] Restarting postfix (via systemctl): postfix.service.
nick@nicnetworking:~$ netcat mail.nicnetworking.com 25
220 nicnetworking.com ESMTP Postfix (Ubuntu)
ehlo nicnetworking.com
250-nicnetworking.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: root@nicnetworking.com
250 2.1.0 Ok
rcpt to: fmaster@nicnetworking.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
subject: Test from domain subject


Data in Email!!!
.
250 2.0.0 Ok: queued as 4C1ECC1E4B
quit
221 2.0.0 Bye
nick@nicnetworking:~$ netcat mail.nicnetworking.com 25
220 nicnetworking.com ESMTP Postfix (Ubuntu)
q
502 5.5.2 Error: command not recognized
q
502 5.5.2 Error: command not recognized
quit
221 2.0.0 Bye
nick@nicnetworking:~$ sudo postconf mynetworks
mynetworks = 127.0.0.0/8, 10.0.0.0/24
nick@nicnetworking:~$ netcat mail.nicnetworking.com 24
nick@nicnetworking:~$ netcat mail.nicnetworking.com 25
220 nicnetworking.com ESMTP Postfix (Ubuntu)


500 5.5.2 Error: bad syntax
quit
221 2.0.0 Bye
nick@nicnetworking:~$ netcat mail.nicnetworking.com 24
nick@nicnetworking:~$ netcat mail.nicnetworking.com 25
220 nicnetworking.com ESMTP Postfix (Ubuntu)
mail
501 5.5.4 Syntax: MAIL FROM:<address>
quit
221 2.0.0 Bye
nick@nicnetworking:~$ sudo  /etc/init.d/postfix restart
[ ok ] Restarting postfix (via systemctl): postfix.service.
nick@nicnetworking:~$ netcat mail.nicnetworking.com
This is nc from the netcat-openbsd package. An alternative nc is available
in the netcat-traditional package.
usage: nc [-46bCDdhjklnrStUuvZz] [-I length] [-i interval] [-O length]
          [-P proxy_username] [-p source_port] [-q seconds] [-s source]
          [-T toskeyword] [-V rtable] [-w timeout] [-X proxy_protocol]
          [-x proxy_address[:port]] [destination] [port]
nick@nicnetworking:~$ netcat mail.nicnetworking.com 25
220 nicnetworking.com ESMTP Postfix (Ubuntu)
ehlo nicnetworking.com
250-nicnetworking.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: root@nicnetworking.com
250 2.1.0 Ok
rcpt to: fmaster@nicnetworking.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
subject: domain send


some kind of text
.
250 2.0.0 Ok: queued as AFBA4C1E4B
quit
221 2.0.0 Bye
nick@nicnetworking:~$ su - fmaster
Password:
fmaster@nicnetworking:~$ cd Mailfir/new
-su: cd: Mailfir/new: No such file or directory
fmaster@nicnetworking:~$ MAIL=/home/fmaster/Maildir
fmaster@nicnetworking:~$ MAIL=maildir/new
fmaster@nicnetworking:~$ mail
Cannot open mailbox /home/fmaster/maildir/new: No such file or directory
No mail for fmaster
fmaster@nicnetworking:~$ cd Mailfir/new
-su: cd: Mailfir/new: No such file or directory
fmaster@nicnetworking:~$ ls
dead.letter  Maildir
fmaster@nicnetworking:~$ mail
Cannot open mailbox /home/fmaster/maildir/new: No such file or directory
No mail for fmaster
fmaster@nicnetworking:~$ cd maildir
-su: cd: maildir: No such file or directory
fmaster@nicnetworking:~$ cd maildir/new
-su: cd: maildir/new: No such file or directory
fmaster@nicnetworking:~$ -su: cd: maildir/new: No such file or directory
-su:: command not found
fmaster@nicnetworking:~$ cd home/fmaster/maildir/new
-su: cd: home/fmaster/maildir/new: No such file or directory
fmaster@nicnetworking:~$ cd home
-su: cd: home: No such file or directory
fmaster@nicnetworking:~$ cd home/
-su: cd: home/: No such file or directory
fmaster@nicnetworking:~$ cd maildir/new
-su: cd: maildir/new: No such file or directory
fmaster@nicnetworking:~$ netcat mail.nicnetworking.com
This is nc from the netcat-openbsd package. An alternative nc is available
in the netcat-traditional package.
usage: nc [-46bCDdhjklnrStUuvZz] [-I length] [-i interval] [-O length]
          [-P proxy_username] [-p source_port] [-q seconds] [-s source]
          [-T toskeyword] [-V rtable] [-w timeout] [-X proxy_protocol]
          [-x proxy_address[:port]] [destination] [port]
fmaster@nicnetworking:~$ netcat mail.nicnetworking.com 110
+OK Hello there.
user fmastwer
+OK Password required.


-ERR Invalid command.
pass 
-ERR Temporary problem, please try again later
fmaster@nicnetworking:~$ netcat mail.nicnetworking.com 110
+OK Hello there.
user fmaster
+OK Password required.
pass 
-ERR Temporary problem, please try again later
fmaster@nicnetworking:~$ netcat mail.nicnetworking.com 110
+OK Hello there.
user fmaster
+OK Password required.
pass password
-ERR Temporary problem, please try again later
fmaster@nicnetworking:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp6       0      0 [::]:pop3               [::]:*                  LISTEN
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN
udp        0      0 *:bootpc                *:*
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     16635    /run/user/1000/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     13592    /run/acpid.socket
unix  2      [ ACC ]     SEQPACKET  LISTENING     10674    /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     13594    /run/uuidd/request
unix  2      [ ACC ]     STREAM     LISTENING     28926    /run/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     43918    /run/snapd.socket
unix  2      [ ACC ]     STREAM     LISTENING     61677    private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     61680    private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     61683    private/defer
unix  2      [ ACC ]     STREAM     LISTENING     61686    private/trace
unix  2      [ ACC ]     STREAM     LISTENING     61689    private/verify
unix  2      [ ACC ]     STREAM     LISTENING     61695    private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     61698    private/proxywrite
unix  2      [ ACC ]     STREAM     LISTENING     61701    private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     61704    private/relay
unix  2      [ ACC ]     STREAM     LISTENING     61710    private/error
unix  2      [ ACC ]     STREAM     LISTENING     61713    private/retry
unix  2      [ ACC ]     STREAM     LISTENING     61716    private/discard
unix  2      [ ACC ]     STREAM     LISTENING     61719    private/local
unix  2      [ ACC ]     STREAM     LISTENING     61722    private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     61725    private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     61728    private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     61731    private/scache
unix  2      [ ACC ]     STREAM     LISTENING     61734    private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     61737    private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     61740    private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     61743    private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     61746    private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     61749    private/mailman
unix  2      [ ACC ]     STREAM     LISTENING     10673    /run/lvm/lvmetad.socket
unix  2      [ ACC ]     STREAM     LISTENING     10675    /run/systemd/journal/stdout
unix  2      [ ACC ]     STREAM     LISTENING     10678    /run/systemd/fsck.progress
unix  2      [ ACC ]     STREAM     LISTENING     10679    /run/lvm/lvmpolld.socket
unix  2      [ ACC ]     STREAM     LISTENING     13574    /var/lib/lxd/unix.socket
unix  2      [ ACC ]     STREAM     LISTENING     13591    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     61674    private/tlsmgr
unix  2      [ ACC ]     STREAM     LISTENING     15209    @ISCSIADM_ABSTRACT_NAMESPACE
unix  2      [ ACC ]     STREAM     LISTENING     61663    public/pickup
unix  2      [ ACC ]     STREAM     LISTENING     61667    public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     61670    public/qmgr
unix  2      [ ACC ]     STREAM     LISTENING     61692    public/flush
unix  2      [ ACC ]     STREAM     LISTENING     61707    public/showq
fmaster@nicnetworking:~$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp        0      0 10.0.0.5:ssh            10.0.0.9:49212          ESTABLISHED
tcp        0      0 10.0.0.5:ssh            10.0.0.9:49498          ESTABLISHED
tcp6       0      0 [::]:pop3               [::]:*                  LISTEN
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN
udp        0      0 *:bootpc                *:*
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ]         DGRAM                    16634    /run/user/1000/systemd/notify
unix  2      [ ACC ]     STREAM     LISTENING     16635    /run/user/1000/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     13592    /run/acpid.socket
unix  2      [ ACC ]     SEQPACKET  LISTENING     10674    /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     13594    /run/uuidd/request
unix  3      [ ]         DGRAM                    10662    /run/systemd/notify
unix  2      [ ACC ]     STREAM     LISTENING     28926    /run/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     43918    /run/snapd.socket
unix  2      [ ACC ]     STREAM     LISTENING     61677    private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     61680    private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     61683    private/defer
unix  2      [ ACC ]     STREAM     LISTENING     61686    private/trace
unix  2      [ ACC ]     STREAM     LISTENING     61689    private/verify
unix  2      [ ACC ]     STREAM     LISTENING     61695    private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     61698    private/proxywrite
unix  2      [ ACC ]     STREAM     LISTENING     61701    private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     61704    private/relay
unix  2      [ ACC ]     STREAM     LISTENING     61710    private/error
unix  2      [ ACC ]     STREAM     LISTENING     61713    private/retry
unix  2      [ ACC ]     STREAM     LISTENING     61716    private/discard
unix  2      [ ACC ]     STREAM     LISTENING     61719    private/local
unix  2      [ ACC ]     STREAM     LISTENING     61722    private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     61725    private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     61728    private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     61731    private/scache
unix  2      [ ACC ]     STREAM     LISTENING     61734    private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     61737    private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     61740    private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     61743    private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     61746    private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     61749    private/mailman
unix  23     [ ]         DGRAM                    10668    /run/systemd/journal/dev-log
unix  2      [ ]         DGRAM                    10672    /run/systemd/journal/syslog
unix  2      [ ACC ]     STREAM     LISTENING     10673    /run/lvm/lvmetad.socket
unix  2      [ ACC ]     STREAM     LISTENING     10675    /run/systemd/journal/stdout
unix  7      [ ]         DGRAM                    10676    /run/systemd/journal/socket
unix  2      [ ACC ]     STREAM     LISTENING     10678    /run/systemd/fsck.progress
unix  2      [ ACC ]     STREAM     LISTENING     10679    /run/lvm/lvmpolld.socket
unix  2      [ ACC ]     STREAM     LISTENING     13574    /var/lib/lxd/unix.socket
unix  2      [ ACC ]     STREAM     LISTENING     13591    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     61674    private/tlsmgr
unix  2      [ ACC ]     STREAM     LISTENING     15209    @ISCSIADM_ABSTRACT_NAMESPACE
unix  2      [ ACC ]     STREAM     LISTENING     61663    public/pickup
unix  2      [ ACC ]     STREAM     LISTENING     61667    public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     61670    public/qmgr
unix  2      [ ACC ]     STREAM     LISTENING     61692    public/flush
unix  2      [ ACC ]     STREAM     LISTENING     61707    public/showq
unix  3      [ ]         STREAM     CONNECTED     61661
unix  3      [ ]         STREAM     CONNECTED     61717
unix  3      [ ]         STREAM     CONNECTED     18763    /run/systemd/journal/stdout
unix  2      [ ]         DGRAM                    61988
unix  3      [ ]         STREAM     CONNECTED     61714
unix  3      [ ]         DGRAM                    29046
unix  3      [ ]         STREAM     CONNECTED     18762
unix  3      [ ]         STREAM     CONNECTED     61744
unix  3      [ ]         STREAM     CONNECTED     11482    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     61681
unix  2      [ ]         DGRAM                    44061
unix  3      [ ]         STREAM     CONNECTED     61709
unix  3      [ ]         STREAM     CONNECTED     61697
unix  3      [ ]         STREAM     CONNECTED     61748
unix  3      [ ]         DGRAM                    29047
unix  3      [ ]         STREAM     CONNECTED     42318    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     37985    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     61691
unix  3      [ ]         STREAM     CONNECTED     61720
unix  3      [ ]         STREAM     CONNECTED     61699
unix  3      [ ]         STREAM     CONNECTED     29037
unix  2      [ ]         DGRAM                    58775
unix  2      [ ]         DGRAM                    15201
unix  2      [ ]         DGRAM                    61766
unix  3      [ ]         STREAM     CONNECTED     16583    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     14148
unix  2      [ ]         DGRAM                    54148
unix  2      [ ]         DGRAM                    60889
unix  3      [ ]         DGRAM                    37992
unix  3      [ ]         STREAM     CONNECTED     61672
unix  3      [ ]         STREAM     CONNECTED     61741
unix  3      [ ]         STREAM     CONNECTED     61736
unix  3      [ ]         STREAM     CONNECTED     44057    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     42637    /run/systemd/journal/stdout
unix  2      [ ]         DGRAM                    16625
unix  3      [ ]         STREAM     CONNECTED     61705
unix  3      [ ]         STREAM     CONNECTED     19508
unix  3      [ ]         STREAM     CONNECTED     14234    /run/systemd/journal/stdout
unix  2      [ ]         DGRAM                    14464
unix  3      [ ]         STREAM     CONNECTED     61675
unix  2      [ ]         DGRAM                    16586
unix  2      [ ]         DGRAM                    61779
unix  3      [ ]         STREAM     CONNECTED     61723
unix  3      [ ]         STREAM     CONNECTED     61708
unix  3      [ ]         STREAM     CONNECTED     14527    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     61682
unix  3      [ ]         STREAM     CONNECTED     11481
unix  3      [ ]         STREAM     CONNECTED     61668
unix  3      [ ]         STREAM     CONNECTED     14220
unix  3      [ ]         STREAM     CONNECTED     61745
unix  3      [ ]         STREAM     CONNECTED     52672
unix  3      [ ]         STREAM     CONNECTED     61703
unix  3      [ ]         STREAM     CONNECTED     42636
unix  3      [ ]         STREAM     CONNECTED     61690
unix  3      [ ]         STREAM     CONNECTED     37984
unix  3      [ ]         STREAM     CONNECTED     61733
unix  3      [ ]         STREAM     CONNECTED     61712
unix  3      [ ]         DGRAM                    29044
unix  3      [ ]         STREAM     CONNECTED     61665
unix  3      [ ]         STREAM     CONNECTED     61706
unix  3      [ ]         STREAM     CONNECTED     14235    /run/systemd/journal/stdout
unix  3      [ ]         DGRAM                    37991
unix  2      [ ]         DGRAM                    37987
unix  3      [ ]         STREAM     CONNECTED     28925    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     61730
unix  3      [ ]         STREAM     CONNECTED     61664
unix  2      [ ]         DGRAM                    61826
unix  3      [ ]         STREAM     CONNECTED     61738
unix  2      [ ]         DGRAM                    60650
unix  3      [ ]         STREAM     CONNECTED     14525
unix  3      [ ]         STREAM     CONNECTED     61679
unix  3      [ ]         STREAM     CONNECTED     52671
unix  3      [ ]         STREAM     CONNECTED     61724
unix  2      [ ]         DGRAM                    19472
unix  3      [ ]         STREAM     CONNECTED     61669
unix  3      [ ]         STREAM     CONNECTED     14416
unix  3      [ ]         STREAM     CONNECTED     61739
unix  3      [ ]         STREAM     CONNECTED     61732
unix  3      [ ]         STREAM     CONNECTED     44056
unix  3      [ ]         STREAM     CONNECTED     61750
unix  3      [ ]         STREAM     CONNECTED     61687
unix  3      [ ]         STREAM     CONNECTED     61702
unix  2      [ ]         DGRAM                    58741
unix  3      [ ]         STREAM     CONNECTED     14863
unix  3      [ ]         STREAM     CONNECTED     14002    /run/systemd/journal/stdout
unix  2      [ ]         DGRAM                    61639
unix  3      [ ]         STREAM     CONNECTED     61735
unix  2      [ ]         DGRAM                    53157
unix  2      [ ]         DGRAM                    29040
unix  2      [ ]         DGRAM                    53284
unix  3      [ ]         STREAM     CONNECTED     61751
unix  3      [ ]         STREAM     CONNECTED     61711
unix  2      [ ]         DGRAM                    15215
unix  3      [ ]         STREAM     CONNECTED     61676
unix  3      [ ]         STREAM     CONNECTED     42319
unix  3      [ ]         STREAM     CONNECTED     61715
unix  3      [ ]         STREAM     CONNECTED     61693
unix  3      [ ]         STREAM     CONNECTED     14524
unix  3      [ ]         STREAM     CONNECTED     61694
unix  3      [ ]         STREAM     CONNECTED     13938
unix  3      [ ]         STREAM     CONNECTED     29038    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     14478
unix  3      [ ]         STREAM     CONNECTED     61684
unix  3      [ ]         STREAM     CONNECTED     14864    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     61696
unix  2      [ ]         DGRAM                    13875
unix  3      [ ]         STREAM     CONNECTED     14429    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     42320    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19509
unix  2      [ ]         DGRAM                    14236
unix  3      [ ]         STREAM     CONNECTED     61742
unix  3      [ ]         STREAM     CONNECTED     42317
unix  3      [ ]         STREAM     CONNECTED     28924
unix  3      [ ]         STREAM     CONNECTED     61685
unix  3      [ ]         STREAM     CONNECTED     61662
unix  2      [ ]         DGRAM                    56817
unix  3      [ ]         STREAM     CONNECTED     61688
unix  3      [ ]         STREAM     CONNECTED     61727
unix  3      [ ]         STREAM     CONNECTED     61726
unix  3      [ ]         STREAM     CONNECTED     61718
unix  3      [ ]         STREAM     CONNECTED     61747
unix  3      [ ]         STREAM     CONNECTED     16579
unix  3      [ ]         STREAM     CONNECTED     61671
unix  3      [ ]         STREAM     CONNECTED     61700
unix  2      [ ]         DGRAM                    52636
unix  3      [ ]         DGRAM                    29045
unix  3      [ ]         STREAM     CONNECTED     61721
unix  2      [ ]         DGRAM                    11285
unix  3      [ ]         STREAM     CONNECTED     61729
unix  2      [ ]         DGRAM                    14515
unix  3      [ ]         STREAM     CONNECTED     61678
fmaster@nicnetworking:~$



```

That was my ending point if you guys could guide me in the right direction you would be amazing!! I be on tomorrow . THANKS AGAIN!!! If anyone feels they need more information I can reply asap.

---

### Post by TheFu on 2016-07-07
Comcast blocks inbound/outbound SMTP traffic on residential connections. Must use their outbound gateway and for inbound, a MX relay is needed.  dyn sells this service for $20/yr.

If this is a business connection, there is hope. If residential, someone else will have to help.

BTW, pings and traceroutes are failing to the registered IP.

---

### Post by nhagney on 2016-07-07
I have one setup with GoDaddy. This is a residential line. I didn't know they block SMTP.. are you sure about the IP? Can you send me the lines your seeing?

---

### Post by TheFu on 2016-07-07
```
$ dig mail.nicnetworking.com mx 
$ ping 67.176.195.227
$ traceroute 67.176.195.227
```

The pings worked now, but they definitely failed earlier.
But you won't be able to receive email to any Comcast residential IP.  They started blocking that about a decade ago - plus DHCP subnets are all blacklisted by email servers, so nobody will accept the emails anyway.

---

### Post by nhagney on 2016-07-07
Does anyone know any kind of workaround on this? U would be amazing!!! Ty Thefu. Has any one had success with asking Comcast to allow 25 or 5-- whatever it is?

---

### Post by TheFu on 2016-07-08
> any kind of workaround

There are many solutions, just none that let email be directly sent to or from your home connection. You'll need an intermediary. It can be a bought service OR a store and forward system that you manage.

**Another option**
Many people just use existing email accounts and poll those every 5-15 minutes, pulling any messages to their local machine and forcing all outbound thru 1 of the external email accounts. This is fine for 1 person. With this method, no need for DNS or even a domainname that is yours.

You can have comcast allow SMTP. Get a business account for 30-50% more money every month and 50% less throughput. Running servers on a residential connection is against the ToS. Best not to ask, mention, think about that. Think discussing much more here is not allowed.

[http://ubuntuforums.org/showthread.php?t=2108482](http://ubuntuforums.org/showthread.php?t=2108482) is one previous discussion about emailing (outbound only). There are probably 10 others from the last few years. 

The simplest answer for all of this is a $5/month VPS running postfix for 2-way use, IMHO. This is what I would do. That might not be the "best" answer for you, however.  Hopefully, someone else will respond with some different ideas and opinions. This is opinion, not necessarily fact. Really depends on many things, key is your skill level with Linux, email, networking, tunnels, etc.

Of course, there are a nearly infinite set of combinations with any mix of these things, plus options not proposed.

---

