---
title: "Send and receive mail problem"
date: 2007-10-31
forum: Server Platforms
---

### Post by satimis on 2007-10-31
Hi folks,


Ubuntu 7.04 server amd64 (Host OS)
VMWare Server
Postfix 2.3.8-2

1)
On testing sendmail to Internet encounting following problem;

$ telnet localhost 25```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
ehlo xyg.com


```
It hung here after hitting [Enter]

$ netstat -l | grep tcp```

tcp        0      0 *:vmware-authd          *:*                     LISTEN     
tcp        0      0 localhost.localdo:mysql *:*                     LISTEN     
tcp        0      0 *:8333                  *:*                     LISTEN     
tcp        0      0 *:www                   *:*                     LISTEN     
tcp        0      0 192.168.213.1:domain    *:*                     LISTEN     
tcp        0      0 172.16.77.1:domain      *:*                     LISTEN     
tcp        0      0 *:ftp                   *:*                     LISTEN     
tcp        0      0 192.168.0.10:domain     *:*                     LISTEN     
tcp        0      0 localhost.locald:domain *:*                     LISTEN     
tcp        0      0 192.168.0.10:ssh        *:*                     LISTEN     
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp        0      0 localhost.localdoma:953 *:*                     LISTEN     
tcp        0      0 *:https                 *:*                     LISTEN     
tcp        0      0 *:8222                  *:*                     LISTEN     
tcp6       0      0 *:imaps                 *:*                     LISTEN     
tcp6       0      0 *:pop3s                 *:*                     LISTEN     
tcp6       0      0 *:pop3                  *:*                     LISTEN     
tcp6       0      0 *:imap2                 *:*                     LISTEN     
tcp6       0      0 *:domain                *:*                     LISTEN     
tcp6       0      0 *:smtp                  *:*                     LISTEN     
tcp6       0      0 ip6-localhost:953       *:*                     LISTEN     
```

Sending mails on Intranet/locally on the same PC without problem.


2)
All mails sent on yahoo.com/gmail.com to this server returned saying users NOT found.  However the respective users including Maildir have been created.  Mails sent to them on Intranet w/o problem.

Please advise where shall I check?  TIA


B.R.
satimis

---

### Post by MJN on 2007-10-31
Install Postfix - there's very little Sendmail experience on this board.
 
Edit: I see you say you're using Postfix, so where does Sendmail come into it (or was it a slip of the tongue?)?
 
Can you elaborate on what you are able to do? That telnet output suggests nothing is happening given the lack of welcome banner of response to EHLO so I am curious as to how 3rd parties are able to get as far as determining there are no such users for their attempted mail deliveries.
 
What's the domain name?
 
Mathew

---

### Post by satimis on 2007-10-31
> **MJN said:**
> 
Can you elaborate on what you are able to do? That telnet output suggests nothing is happening given the lack of welcome banner of response to EHLO so I am curious as to how 3rd parties are able to get as far as determining there are no such users for their attempted mail deliveries.

$ telnet localhost 25```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
ehlo satimis.com

```
It hung here.

$ netstat -l grep tcp```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:vmware-authd          *:*                     LISTEN     
tcp        0      0 localhost.localdo:mysql *:*                     LISTEN     
tcp        0      0 *:8333                  *:*                     LISTEN     
tcp        0      0 *:www                   *:*                     LISTEN     
tcp        0      0 172.16.77.1:domain      *:*                     LISTEN     
tcp        0      0 192.168.213.1:domain    *:*                     LISTEN     
tcp        0      0 *:ftp                   *:*                     LISTEN     
tcp        0      0 192.168.0.10:domain     *:*                     LISTEN     
tcp        0      0 localhost.locald:domain *:*                     LISTEN     
tcp        0      0 192.168.0.10:ssh        *:*                     LISTEN     
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp        0      0 localhost.localdoma:953 *:*                     LISTEN     
tcp        0      0 *:https                 *:*                     LISTEN     
tcp        0      0 *:8222                  *:*                     LISTEN     
tcp6       0      0 *:imaps                 *:*                     LISTEN     
tcp6       0      0 *:pop3s                 *:*                     LISTEN     
tcp6       0      0 *:pop3                  *:*                     LISTEN     
tcp6       0      0 *:imap2                 *:*                     LISTEN     
tcp6       0      0 *:domain                *:*                     LISTEN     
tcp6       0      0 *:smtp                  *:*                     LISTEN     
tcp6       0      0 ip6-localhost:953       *:*                     LISTEN     
udp        0      0 *:32768                 *:*                                
udp        0      0 *:syslog                *:*                                
udp        0      0 172.16.77.1:domain      *:*                                
udp        0      0 192.168.213.1:domain    *:*                                
udp        0      0 192.168.0.10:domain     *:*                                
udp        0      0 localhost.locald:domain *:*                                
udp        0      0 192.168.0.10:ntp        *:*                                
udp        0      0 localhost.localdoma:ntp *:*                                
udp        0      0 *:ntp                   *:*                                
udp6       0      0 *:32769                 *:*                                
udp6       0      0 *:domain                *:*                                
udp6       0      0 ip6-localhost:ntp       *:*                                
udp6       0      0 fe80::20e:a6ff:fef9:ntp *:*                                
udp6       0      0 *:ntp                   *:*                                
raw        0      0 *:icmp                  *:*                     7          
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     16431    /tmp/.font-unix/fs7100
unix  2      [ ACC ]     STREAM     LISTENING     17063    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     17164    /tmp/scim-socket-frontend-satimis
unix  2      [ ACC ]     STREAM     LISTENING     17183    /tmp/scim-helper-manager-socket-satimis
unix  2      [ ACC ]     STREAM     LISTENING     17187    /tmp/scim-panel-socket:0-satimis
unix  2      [ ACC ]     STREAM     LISTENING     16663    /var/run/vmware/root/5094/server-fd
unix  2      [ ACC ]     STREAM     LISTENING     16665    /var/run/vmware/root/5094/vmx-fd
unix  2      [ ACC ]     STREAM     LISTENING     16667    /var/run/vmware/root/5094/server-vcvmdb-fd
unix  2      [ ACC ]     STREAM     LISTENING     16669    /var/run/vmware/root/5094/server-vmdb-fd
unix  2      [ ACC ]     STREAM     LISTENING     16671    /var/run/vmware/root/5094/server-vmxvmdb-fd
unix  2      [ ACC ]     STREAM     LISTENING     16673    /var/run/vmware/root/5094/nfc-fd
unix  2      [ ACC ]     STREAM     LISTENING     16675    /var/run/vmware/root/5094/fsserver-fd
unix  2      [ ACC ]     STREAM     LISTENING     16267    public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     16274    private/tlsmgr
unix  2      [ ACC ]     STREAM     LISTENING     16278    private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     16282    private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     16286    private/defer
unix  2      [ ACC ]     STREAM     LISTENING     16290    private/trace
unix  2      [ ACC ]     STREAM     LISTENING     16294    private/verify
unix  2      [ ACC ]     STREAM     LISTENING     16298    public/flush
unix  2      [ ACC ]     STREAM     LISTENING     16302    private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     16306    private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     16310    private/relay
unix  2      [ ACC ]     STREAM     LISTENING     16314    public/showq
unix  2      [ ACC ]     STREAM     LISTENING     16318    private/error
unix  2      [ ACC ]     STREAM     LISTENING     16322    private/discard
unix  2      [ ACC ]     STREAM     LISTENING     16326    private/local
unix  2      [ ACC ]     STREAM     LISTENING     14412    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     16330    private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     16334    private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     16338    private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     15951    /var/run/courier/authdaemon/socket.tmp
unix  2      [ ACC ]     STREAM     LISTENING     16342    private/scache
unix  2      [ ACC ]     STREAM     LISTENING     16346    private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     16350    private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     16354    private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     16358    private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     16362    private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     16366    private/mailman
unix  2      [ ACC ]     STREAM     LISTENING     16398    /var/spool/postfix/var/run/saslauthd/mux
unix  2      [ ACC ]     STREAM     LISTENING     15757    /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     14430    @/var/run/hald/dbus-CpzOM3g72b
unix  2      [ ACC ]     STREAM     LISTENING     16536    /var/run/proftpd/proftpd.sock
unix  2      [ ACC ]     STREAM     LISTENING     14431    @/var/run/hald/dbus-y00yqu5dgJ
unix  2      [ ACC ]     STREAM     LISTENING     18610    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     16634    /var/run/vmnat.5089

```

That are all I have.

> 
What's the domain name?

satimis.com


B.R.
satimis

---

### Post by MJN on 2007-10-31
It's more what you meant by *'All mails sent on yahoo.com/gmail.com to this server returned saying users NOT found. However the respective users including Maildir have been created. Mails sent to them on Intranet w/o problem*.'
 
The last bit in particular needs expanding - what do you mean?
 
The yahoo.com/gmail.com bit could be a red herring - you've got three mail exchangers listed in your DNS for satimis.com so it's likely that they are going to the other two given the lack of response from yours. Are the others configured for accepting your mail?
 
Post your Postfix config and we can take a look, as well as your Postfix log (mail.log) showing what happens when you restart the Postfix service as well as when you attempt to connect with telnet.
 
Mathew
 
P.S. As I've warned you elsewhere, if you even *think* about grepping these files for the bits you think are of interest instead of posting it unaltered then I swear I'll hunt you down... ;)

---

### Post by satimis on 2007-10-31
> **MJN said:**
> It's more what you meant by *'All mails sent on yahoo.com/gmail.com to this server returned saying users NOT found. However the respective users including Maildir have been created. Mails sent to them on Intranet w/o problem*.'
 
The last bit in particular needs expanding - what do you mean?

I can send mails to users on the same PC w/o problem by running "telnet localhost 25".  The mails are delivered to their /Maildir/new directory.

>  
The yahoo.com/gmail.com bit could be a red herring - you've got three mail exchangers listed in your DNS for satimis.com so it's likely that they are going to the other two given the lack of response from yours. Are the others configured for accepting your mail?

All others have Maildir with their names on /etc/aliases.


> 
Post your Postfix config and we can take a look, as well as your Postfix log (mail.log) showing what happens when you restart the Postfix service as well as when you attempt to connect with telnet.

$ cat /etc/postfix/main.cf```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ubuntu.satimis.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ubuntu.satimis.com, satimis.com, localhost.satimis.com, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8, 192.168.1.0/24
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
virtual_maps = hash:/etc/postfix/virtusertable

```

$ sudo tail /var/log/mail.log```

Oct 31 07:52:58 ubuntu postfix/master[4880]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct 31 07:53:58 ubuntu postfix/smtpd[6542]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Oct 31 07:53:59 ubuntu postfix/master[4880]: warning: process /usr/lib/postfix/smtpd pid 6542 exit status 1
Oct 31 07:53:59 ubuntu postfix/master[4880]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct 31 07:54:59 ubuntu postfix/smtpd[6544]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Oct 31 07:55:00 ubuntu postfix/master[4880]: warning: process /usr/lib/postfix/smtpd pid 6544 exit status 1
Oct 31 07:55:00 ubuntu postfix/master[4880]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct 31 07:56:00 ubuntu postfix/smtpd[6611]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Oct 31 07:56:01 ubuntu postfix/master[4880]: warning: process /usr/lib/postfix/smtpd pid 6611 exit status 1
Oct 31 07:56:01 ubuntu postfix/master[4880]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

```


satimis

---

### Post by MJN on 2007-10-31
> **satimis said:**
> I can send mails to users on the same PC w/o problem by running "telnet localhost 25". The mails are delivered to their /Maildir/new directory.
 
Something doesn't quite add up - in your first post you said that telnet localhost 25 wasn't working and showed the output that it just hangs...
 
> 1)
On testing sendmail to Internet encounting following problem;
 
```
$ telnet localhost 25 
Code:
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
ehlo xyg.com
```
It hung here after hitting [Enter]
 
Can you clarify?
 
Sorry for all these questions but we've got to know exactly where we stand before we can get anywhere.
 
Mathew

---

### Post by satimis on 2007-10-31
> **MJN said:**
> Something doesn't quite add up - in your first post you said that telnet localhost 25 wasn't working and showed the output that it just hangs...

It was the firewall blocking it.  After stopping iptables, "telnet localhost 25" works w/o problem. 

>  
Can you clarify?

Running;

$ telnet localhost 25 ```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.

```
It worked w/o problem.

Then I continued typing```

ehlo satimis.com

```
It hung there.

---

### Post by MJN on 2007-10-31
So which is it?! Does it work or not?
 
Let's crack on regardless as we're not making any progress otherwise.
 
Your logs states 'fatal: open database /etc/postfix/virtusertable.db: No such file or directory'
 
Does the file exist?
 
Either way, try recreating it with **sudo postmap /etc/posfix/virtusertable** and restarting Postfix.
 
Post fulls logs again showing the restart and an attempt at a manual mail submission with telnet.
 
Meanwhile I'm off for a lie down in a dark room...
 
Mathew

---

### Post by satimis on 2007-10-31
> **MJN said:**
> So which is it?! Does it work or not?
 
Let's crack on regardless as we're not making any progress otherwise.
 
Your logs states 'fatal: open database /etc/postfix/virtusertable.db: No such file or directory'
 
Does the file exist?
 
Either way, try recreating it with **sudo postmap /etc/posfix/virtusertable** and restarting Postfix.
 
Post fulls logs again showing the restart and an attempt at a manual mail submission with telnet.

Now I can send mails to yahoo.com after running;

$ sudo touch /etc/postfix/virtusertable
$ sudo postmap /etc/postfix/virtusertable 
$ sudo /etc/init.d/postfix restart


But still can't receive mail.  Mails sent on yahoo.com to users on this server returned immediately.


satimis




 
..

---

### Post by MJN on 2007-10-31
I've just sent a few test message (to postmaster) and they seemed to have been accepted.
 
What users are you having trouble with? Do they exist?
 
What's in your virtusertable file?
 
And what do your logs say when a message comes in? (I keep asking you this!)
 
Mathew
 
P.S. You also seem to have 3 MX records all pointing ultimate to the same machine - howcome? (That's nothing to do with this problem but something you may want to address later)

---

### Post by satimis on 2007-10-31
> **MJN said:**
> I've just sent a few test message (to postmaster) and they seemed to have been accepted.
 
What users are you having trouble with? Do they exist?

Yes, satimis, fmaster and administrator,


>  
What's in your virtusertable file?

$ cat /etc/postfix/virtusertable
No printout.  It is empty.

> 
And what do your logs say when a message comes in? 
 
$ sudo tail /var/log/mail.log ```

Oct 31 22:19:12 ubuntu postfix/master[4880]: terminating on signal 15
Oct 31 22:19:12 ubuntu postfix/master[7070]: daemon started -- version 2.3.8, configuration /etc/postfix
Oct 31 22:19:36 ubuntu postfix/smtpd[7076]: connect from localhost.localdomain[127.0.0.1]
Oct 31 22:21:28 ubuntu postfix/smtpd[7076]: C0781DF01AE: client=localhost.localdomain[127.0.0.1]
Oct 31 22:22:06 ubuntu postfix/cleanup[7080]: C0781DF01AE: message-id=<20071101052128.C0781DF01AE@ubuntu.satimis.com>
Oct 31 22:22:06 ubuntu postfix/qmgr[7074]: C0781DF01AE: from=<satimis@satimis.com>, size=396, nrcpt=1 (queue active)
Oct 31 22:22:07 ubuntu postfix/smtp[7081]: C0781DF01AE: host d.mx.mail.yahoo.com[216.39.53.2] said: 451 Resources temporarily not available - Please try again later [#4.16.5]. (in reply to end of DATA command)
Oct 31 22:22:09 ubuntu postfix/smtpd[7076]: disconnect from localhost.localdomain[127.0.0.1]
Oct 31 22:22:10 ubuntu postfix/smtp[7081]: C0781DF01AE: to=<satimis@yahoo.com>, relay=f.mx.mail.yahoo.com[209.191.88.247]:25, delay=64, delays=59/0.01/2.7/1.6, dsn=2.0.0, status=sent (250 ok dirdel)
Oct 31 22:22:10 ubuntu postfix/qmgr[7074]: C0781DF01AE: removed

```


$ sudo tail /var/log/mail.err ```

Oct 31 21:48:49 ubuntu postfix/smtpd[6837]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Oct 31 21:49:50 ubuntu postfix/smtpd[6839]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Oct 31 21:50:51 ubuntu postfix/smtpd[6841]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Oct 31 21:51:52 ubuntu postfix/smtpd[6846]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Oct 31 21:52:53 ubuntu postfix/smtpd[6848]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Oct 31 21:53:54 ubuntu postfix/smtpd[6861]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Oct 31 21:54:55 ubuntu postfix/smtpd[6863]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Oct 31 21:55:56 ubuntu postfix/smtpd[6879]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Oct 31 21:56:57 ubuntu postfix/smtpd[6882]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Oct 31 21:57:58 ubuntu postfix/smtpd[6894]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory

```


>  
P.S. You also seem to have 3 MX records all pointing ultimate to the same machine - howcome? (That's nothing to do with this problem but something you may want to address later)
Sorry I don't follow.  Whether you meant on the Registrar's site


satimis

---

### Post by MJN on 2007-10-31
I hate to say it but this is getting too painful to debug.

I'm assuming you followed a HowTo as the virtual_maps directive doesn't exist by default (indeed it looks like Postfix 2 doesn't use it anymore). I suggest going back to the HowTo and retracing your steps.

I have sent you a couple of test e-mails and they seem to have gone through okay - post your logs showing the period around 17:52 GMT on 31/10/2007 as from this end it looks like the mail was accepted.

When connecting from a different machine it looks like you are blocking connections with an RBL - are you? I can't help debug if you've got things like this in place... indeed you shouldn't even think about such measure until you've got a basic server up and running.

Don't take this the wrong but I'm close to giving up as it's getting like pulling teeth I'm afraid!

Your DNS is configured as:

```
$ dig satimis.com mx

; <<>> DiG 9.3.2 <<>> satimis.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22705
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;satimis.com.                   IN      MX

;; ANSWER SECTION:
satimis.com.            3600    IN      MX      0 smtp.satimis.com.
satimis.com.            3600    IN      MX      0 smtp.secureserver.net.
satimis.com.            3600    IN      MX      10 mailstore1.secureserver.net.

;; ADDITIONAL SECTION:
mailstore1.secureserver.net. 1898 IN    A       64.202.166.11

;; Query time: 180 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Wed Oct 31 18:56:47 2007
;; MSG SIZE  rcvd: 130

```Tell me your IP is 64.202.166.11 AND 64.202.166.12 as this is what the names ultimately resolve to. Who set the DNS up? It is wrong, and in violation of the RFCs.

Are you sure your ISP allows you to run an SMTP server? It's beginning to look like they're intercepting port 25 and responding on your behalf.

Mathew

---

### Post by satimis on 2007-10-31
> **MJN said:**
> I hate to say it but this is getting too painful to debug.
It is a time consuming task.  Much appreciated for your assistance.


> 
I'm assuming you followed a HowTo as the virtual_maps directive doesn't exist by default (indeed it looks like Postfix 2 doesn't use it anymore). I suggest going back to the HowTo and retracing your steps.

First I followed;
The Perfect Setup - Ubuntu Feisty Fawn (Ubuntu 7.04)
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

building this Ubuntu server as Host OS on this virtural machine running VMWare.

Now I'm following;
PostfixBasicSetupHowto
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

further tuning this server.  After finish I'll follow;
PostfixVirtualMailBoxClamSmtpHowto
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

for further learning the technique on setup a virtual mail box.


> 
I have sent you a couple of test e-mails and they seem to have gone through okay - post your logs showing the period around 17:52 GMT on 31/10/2007 as from this end it looks like the mail was accepted.

Sorry I haven't informed you that this server is for testing only which will be turned off when not in use.  I just have it switched on.


I have a different output on running;
$ dig satimis.com mx```


; <<>> DiG 9.3.4 <<>> satimis.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 14911
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 2, ADDITIONAL: 3

;; QUESTION SECTION:
;satimis.com.                   IN      MX

;; ANSWER SECTION:
satimis.com.            3600    IN      MX      0 smtp.satimis.com.
satimis.com.            3600    IN      MX      0 smtp.secureserver.net.
satimis.com.            3600    IN      MX      10 mailstore1.secureserver.net.

;; AUTHORITY SECTION:
satimis.com.            3600    IN      NS      NS6.secureserver.net.
satimis.com.            3600    IN      NS      NS5.secureserver.net.

;; ADDITIONAL SECTION:
mailstore1.secureserver.net. 2617 IN    A       64.202.166.11
NS5.secureserver.net.   1623    IN      A       208.109.78.180
NS6.secureserver.net.   2354    IN      A       208.109.80.75

;; Query time: 470 msec
;; SERVER: 202.14.67.4#53(202.14.67.4)
;; WHEN: Thu Nov  1 10:02:35 2007
;; MSG SIZE  rcvd: 198

```


> 
When connecting from a different machine it looks like you are blocking connections with an RBL - are you? I can't help debug if you've got things like this in place... indeed you shouldn't even think about such measure until you've got a basic server up and running.

Whether you meant:- 
Realtime Blackhole List (RBL)

No, I haven't gone so advanced.


> 
Don't take this the wrong but I'm close to giving up as it's getting like pulling teeth I'm afraid!

I'm sorry to hear it.  I'm really appreciated for your effort and time in assisting me.


> 
Tell me your IP is 64.202.166.11 AND 64.202.166.12 as this is what the names ultimately resolve to. Who set the DNS up? It is wrong, and in violation of the RFCs.

I'm running ISP's  DNS server.

$ cat /etc/resolv.conf ```

nameserver 202.14.67.4
nameserver 202.14.67.14

```

A further thought how to check whether I have installed DNS packages on this server?


> 
Are you sure your ISP allows you to run an SMTP server? It's beginning to look like they're intercepting port 25 and responding on your behalf.

Yes, I'm paying fixed IP plan.  At the beginning ISP blocked port 25.  I can't send mails.  Upon my request ISP uplift its blocking.


satimis

---

### Post by MJN on 2007-11-01
So your mail server isn't even connected to the Internet and reference by the DNS? It's no wonder you're not getting any e-mail from yahoo etc.
 
I'm afraid I will have to bow out and let someone else take over - I can't really afford the time to debug HowTo's that you may have followed and there are so many uncertaintites surrounding your configuration, setup and intent that it's proving impossible to progress . I suggest either restarting a HowTo from scratch (don't follow two in parallel - that's a recipe for disaster) and/or getting in touch with the authors of the HowTo's to request their help, perhaps they were announced in a forum thread in which case you could direct your questions there.
 
Sorry...
 
Mathew

---

### Post by satimis on 2007-11-01
> **MJN said:**
> So your mail server isn't even connected to the Internet and reference by the DNS? It's no wonder you're not getting any e-mail from yahoo etc.

I suppose the problem is on Registrar's site.  I just discovered that all settings on the DNS Control Panel: satimis.com has been reset to default.  Unfortunately I haven't taken down the working settings.  It also took me sometime to set them previously.  I only use this domain for testing NOT for production.

I sent an email to the Registrar for advice on resetting the data but met with refusal, saying that they won't support customer to setup the DNS Control Panel.


The Default setting of the DNS Control Panel is as follows;```


3 Tables

1)
A (Host)	
 v  Host	Points To
[ ] @		IP address	


2)
CNAMES (Aliases)
 v  Host	Points To
[ ] email	email.secureserver.net
[ ] mail	pop.secureserver.net
[ ] webmail	webmail.secureserver.net
[ ] pop		pop.secureserver.net
[ ] e		email,secureserver.net
[ ] smtp	smtp.secureserver.net
[ ] ftp		@
[ ] www		@
[ ] mobilemail	mobilemail-v01.prod.mesa1.secureserver.net
[ ] pda		mobilemail-v01.prod.mesa1.secureserver.net


3)
MX (Mail Exchange)

 v  Priority	Host	Goes To
[ ] O		@	smtp.secureserver.net
[ ] O		@	smtp.secureserver.net
[ ] 10		@	mailstore1.secureserver.net 	

TXT (Text)
SRV (Service)
AAAA (IPV6 Host)

```

[ ] is for a tick "v"

My request to Registrar for adivce is as follows:```


A
Point To
(my fixed IP)



CNAMES (Aliases)
email	email.satimis.com
(or just satimis.com)
mail	pop.satimis.com
(OR just satimis.com)
webmail
(I don't have webmail)
pop	pop.satimis.com
(OR just satimis.com)
(what is the difference of mail and pop?  Settings are the same?)
e	email.satimis.com
(OR just satimis.com)
(what is the difference of e and email?  Settings are the same?)
smtp	smtp.satimis.com
(OR just satimis.com)
www	@satimis.com
(OR just satimis.com)

(I don't have ftp, mobilemail and pda.  I'll leave them default?)



MX (Mail Exchange)
	Priority	Host	Goes To			TTL	Action
check	0		@	smtp.satimis.com	1 hour
box	0		@	smtp.secureserver.net	1 hour
box	10		@	mailstore1.secureserver.net	1 hour
(Shall I make any change here?)

```

The technical support of my Registrar refused providing me advice.


Can you shed me some light.  I'll try changing the settings myself.  TIA


satimis

---

