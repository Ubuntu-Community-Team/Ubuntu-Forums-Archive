---
title: "can send mail, but cannot receive"
date: 2013-02-20
forum: Server Platforms
---

### Post by avaserver on 2013-02-20
Hello everyone.
For several days i have a problem with postfix and bind and that i can`t resolve it..so i`m begging for your help
I had installed Ubuntu Server 12.04,ssh, BIND9, Apache2, MySql, PHP5, postfix, dovecot, webmin and virtualmin. 
I had configure partially bind.
I have a static IP Adrees (no rooter). 
I created my own nameserver called avaserver.ava-design.ro wich point to the ip address of my server.

my named.conf.local is (from etc/bind):
zone "ava-design.ro" {
        type master;
        file "/var/lib/bind/ava-design.ro.hosts";
        allow-transfer {
                127.0.0.1;
                localnets;
                };
        };
zone "238.27.188.in-addr.arpa" {
        type master;
        file "/etc/bind/rev.238.27.188.in-addr.arpa";
};


my ava-design.ro.hosts is(/var/lib/bind/  was created by  virtualmin at installation):

$ttl 38400
@       IN      SOA     avaserver.ava-design.ro. root.avaserver.ava-design.ro. (
                        1176598869
                        10800
                        3600
                        604800
                        38400 )
ava-design.ro.            IN    NS        avaserver.ava-design.ro.
ava-design.ro.            IN    A         188.27.238.208
[www.ava-design.ro](www.ava-design.ro).        IN    A         188.27.238.208
ftp.ava-design.ro.        IN    A         188.27.238.208
m.ava-design.ro.          IN    A         188.27.238.208
avaserver.ava-design.ro.  IN    A         188.27.238.208
localhost.ava-design.ro.  IN    A         127.0.0.1
webmail.ava-design.ro.    IN    A         188.27.238.208
admin.ava-design.ro.      IN    A         188.27.238.208
mail.ava-design.ro.       IN    A         188.27.238.208
ava-design.ro.  IN        MX    10        mail.ava-design.ro
ava-design.ro.  IN        TXT     "v=spf1 a mx a:ava-design.ro ip4:188.27.238.208 ?all"
autoconfig.ava-design.ro. IN     A        188.27.238.208


my reverse zone is (/etc/bind/rev.238.27.188.in-addr.arpa):

;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     avaserver.ava-design.ro. root.avaserver.ava-design.ro. (
2013022050;
28800;
3600;
604800;
38400
);

        IN    NS    avaserver.ava-design.ro.
208     IN    PTR   avaserver.ava-design.ro.
208     IN    MX 10 mail.ava-design.ro


Prolem is, that, when i`m using usermin (the webmail virtualmin client from webmail.ava-design.ro) i can send e-mails but i can`t receive them.
The other problem is that i can`t start BIND Dns Server in Virtualmin, and when i go to "Limits and validation> Validate virtual server" i get the following error:

"BIND DNS domain : This domain has email enabled, but none of the MX records point to it. Either the MX records should be corrected, or the email feature disabled if mail is hosted externally."

Also when i`m trying to send an e-mail from external yahoo address i get:
"No MX or A records for ava-design.ro"
But i allready have this record...

Please help me!

---

### Post by GordThompson on 2013-02-21
From my desktop, when I run the query...

```
dig ava-design.ro ANY
```...it returns, in part...

```
ava-design.ro.        38400    IN    MX    10 mail.ava-design.ro.ava-design.ro.
```...and I don't think that's what you want. (There is no A record for 'mail.ava-design.ro.ava-design.ro'.)

You'll need to tinker with your MX setting until it points to 'mail.ava-design.ro'.

If you want to see what your MX record looks like from the outside world you can use this:

[http://dnsquery.org/dnsquery/ava-design.ro/MX](http://dnsquery.org/dnsquery/ava-design.ro/MX)

Edit: Looking at the examples [here]("http://www.zytrax.com/books/dns/ch8/mx.html"), the fix might simply be to append a period to the end of the current MX line in your 'ava-design.ro.hosts' file.

---

### Post by avaserver on 2013-02-21
I made some modification to ava-design.ro.hosts
Now dig ava-design.ro ANY response:

; <<>> DiG 9.8.1-P1 <<>> ava-design.ro ANY
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26584
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 2

;; QUESTION SECTION:
;ava-design.ro.                 IN      ANY

;; ANSWER SECTION:
ava-design.ro.          38400   IN      MX      10 mail.ava-design.ro.
ava-design.ro.          38400   IN      TXT     "v=spf1 a mx a:ava-design.ro ip4:188.27.238.208 ?all"
ava-design.ro.          38400   IN      SOA     avaserver.ava-design.ro. root.avaserver.ava-design.ro. 1176598869 10800 3600 604800 38400
ava-design.ro.          38400   IN      NS      avaserver.ava-design.ro.
ava-design.ro.          38400   IN      A       188.27.238.208

;; ADDITIONAL SECTION:
mail.ava-design.ro.     38400   IN      A       188.27.238.208
avaserver.ava-design.ro. 38400  IN      A       188.27.238.208

;; Query time: 0 msec
;; SERVER: 188.27.238.208#53(188.27.238.208)
;; WHEN: Tue Apr 17 00:47:56 2007
;; MSG SIZE  rcvd: 229



I also put a "." at the end of the folowin line from rev.238.27.188.in-addr.arpa:

"208     IN    MX 10 ava-design.ro."

Also the [http://dnsquery.org/dnsquery/ava-design.ro/MX](http://dnsquery.org/dnsquery/ava-design.ro/MX) returns:

;;Authority
ava-design.ro. 38400 IN NS avaserver.ava-design.ro
;;Answer
ava-design.ro. 38400 IN MX mail.ava-design.ro
;;Additional
avaserver.ava-design.ro. 38400 IN A 188.27.238.208

I think is ok. Other good working mail servers also return those values. 


But the mail still don`t working.
I guess is a postfix configuration problem. Or dovecot config.
I realy don`t know.

---

### Post by GordThompson on 2013-02-21
DNS changes can sometimes take several hours to propagate around the world. If, for example, Yahoo! has your old DNS settings cached then it may not "see" the new settings until it asks for a refresh. Give it some time before investigating other potential issues.

---

### Post by SeijiSensei on 2013-02-21
If I run "telnet 188.27.238.208 25" I don't see an SMTP server listening there.  I get no connection at all.  I can ping the address however, and nmap shows an array of open ports:

Not shown: 1683 closed ports
PORT      STATE    SERVICE
21/tcp    open     ftp
22/tcp    open     ssh
25/tcp    filtered smtp
53/tcp    open     domain
80/tcp    open     http
110/tcp   open     pop3
143/tcp   open     imap
443/tcp   open     https
548/tcp   open     afpovertcp
587/tcp   open     submission
993/tcp   open     imaps
995/tcp   open     pop3s
1720/tcp  filtered H.323/Q.931
10000/tcp open     snet-sensor-mgmt

SMTP is filtered, perhaps by your provider? Perhaps by you?  Whichever applies, Postfix won't answer the phone for me. 

If 10000 is Webmin, I'd add some firewalling to that port right away.  You should only permit access to Webmin from known addresses, not leave it open for exploitation by anyone on the Internet.  I apply the same logic to port 22 (SSH) as well.

---

### Post by avaserver on 2013-02-21
How can port 25 be filtered by me?
Because i don`t have a firewall installed.
I have installed only spamassasin.

When i try Telnet 188.27.238.208 il loads for 2-3 min
then return:
Connection closed by foreign host.

---

### Post by SeijiSensei on 2013-02-21
Talk to your ISP.  Are you sure that Postfix has the proper "[mynetworks]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from")" setting so that it accepts mail on all the interfaces and not just 127.0.0.1?  The default is to lock down Postfix (and dovecot as well I believe) to listen only on localhost.

---

### Post by avaserver on 2013-02-21
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
# appending .domain is the MUA's job.
append_dot_mydomain = no
# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = avaserver
mydomain = ava-design.ro
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = avaserver, localhost.localdomain, , localhost, avaserver.ava-design.ro, 188.27.238.208, $myhostname
mynetworks = 127.0.0.0/8, 188.27.238.208/29
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
myorigin = $mydomain
mailbox_command = procmail -a "$EXTENSION"
virtual_alias_maps = hash:/etc/postfix/virtual
sender_bcc_maps = hash:/etc/postfix/bcc
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination check_policy_service inet:127.0.0.1:10023
allow_percent_hack = no
sender_dependent_default_transport_maps = hash:/etc/postfix/dependent
relayhost =
inet_interfaces = localhost, $myhostname


Is this ok?

---

### Post by avaserver on 2013-02-21
root@avaserver:/etc# nmap -sS -O 188.27.238.208

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2007-04-17 02:55 EEST
Nmap scan report for avaserver.ava-design.ro (188.27.238.208)
Host is up (0.000017s latency).
Not shown: 986 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
25/tcp    open  smtp
53/tcp    open  domain
80/tcp    open  http
110/tcp   open  pop3
143/tcp   open  imap
443/tcp   open  https
548/tcp   open  afp
587/tcp   open  submission
993/tcp   open  imaps
995/tcp   open  pop3s
10000/tcp open  snet-sensor-mgmt
20000/tcp open  unknown

Network Distance: 0 hops

OS detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 12.00 seconds

I think smtp port 25 appear to be open.

---

### Post by SeijiSensei on 2013-02-21
I don't use Postfix but sendmail, so I can't say whether your configuration is correct or not.

On the server itself, what happens if you run "telnet 127.0.0.1 25" and "telnet 188.27.238.208 25"?  Do they both connect?  Neither? Only one?

Another issue might be reverse DNS.  If you run "host 188.27.238.208" on the server, do you get avaserver.ava-design.ro in return?  I know you set up a zone for this address block, but the authoritative provider for the 238.27.188.in-addr.arpa subdomain is your ISP.  Your server could be ignoring your zone file entirely. Out here in public a request for "host 188.27.238.208" returns
> 208.238.27.188.in-addr.arpa domain name pointer 188-27-238-208.rdsnet.ro.

If you don't get avaserver as the reply to a "host 188.27.238.208" request, add an entry to /etc/hosts on avaserver like this:

```
188.27.238.208    avaserver.ava-design.ro   avaserver
```

so that forward and reverse delegation works correctly from the perspective of the server itself.  (To change your publicly-visible reverse entry requires the ISP to do it for you.)

---

### Post by avaserver on 2013-02-21
Punctually:

**1. telnet 127.0.0.1 25 response:**
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
220 mail.ava-design.ro ESMTP Postfix (Ubuntu)
421 4.4.2 mail.ava-design.ro Error: timeout exceeded - This is loading after aprox 3 min
Connection closed by foreign host.

**2. telnet 188.27.238.208 25 response:**
Trying 188.27.238.208...
Connected to 127.0.0.1.
Escape character is '^]'.
220 mail.ava-design.ro ESMTP Postfix (Ubuntu)
421 4.4.2 mail.ava-design.ro Error: timeout exceeded - This is loading after aprox 3 min
Connection closed by foreign host.

**3. host 188.27.238.208:**
208.238.27.188.in-addr.arpa domain name pointer avaserver.ava-design.ro.


**4. cat /etc/hosts:**
127.0.0.1        avaserver  localhost.localdomain  localhost
188.27.238.208   avaserver.ava-design.ro   avaserver
188.27.238.208   mail.ava-design.ro        mail

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
f02::2 ip6-allrouters

---

### Post by SeijiSensei on 2013-02-21
The sessions time out because you didn't type any SMTP commands.  It does look like you can connect to the ethernet port internally, but it's blocked out here.  

If you want to run a test SMTP session you need to type commands like this:

```

220 mail.ava-design.ro ESMTP Postfix (Ubuntu)
ehlo localhost
[server replies]
mail from: you@example.com
[server confirms]
rcpt to: you@ava-design.ro
[server should confirm here, too]
data
[server replies]
this is a test message.
.
[server replies]
quit
[server disconnects]

```

Hold down Ctrl and type "]" to leave the telnet session.

---

### Post by avaserver on 2013-02-21
my isp told me that the port 25 is not filtered.
5 minute ago i was able to send a mail from [email]director@ava-design.ro[/email]  to a gmail address . 

It arives to my gmail address with the following error:


This is an automatically generated Delivery Status Notification

 THIS IS A WARNING MESSAGE ONLY.

 YOU DO NOT NEED TO RESEND YOUR MESSAGE.

 Delivery to the following recipient has been delayed:

      [email]director@ava-design.ro[/email]

 Message will be retried for 2 more day(s)

 Technical details of temporary failure:
 DNS Error: Domain name not found

 ----- Original message -----


Tell me something please:
If somewone trying to send me an e-mail at [email]director@ava-design.ro[/email] that means that it cannot find the [email]director@ava-design.ro[/email] under my ip address (188.27.238.208) so that means that my error comes from my forward zone (var/lib/bind/ava-design.ro.hosts) right?

---

### Post by avaserver on 2013-02-21
I had run SMTP test:

root@avaserver:/# telnet 188.27.238.208 25

Trying 188.27.238.208...
Connected to 188.27.238.208.
Escape character is '^]'.
220 mail.ava-design.ro ESMTP Postfix (Ubuntu)
mail from: [email]airineivladpaul@gmail.com[/email]
250 2.1.0 Ok
rcpt to: [email]director@ava-design.ro[/email]
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
this is a test mail.
.
250 2.0.0 Ok: queued as 2998665D25

---

### Post by GordThompson on 2013-02-21
> **SeijiSensei said:**
> If I run "telnet 188.27.238.208 25" I don't see an SMTP server listening there.  I get no connection at all.  I can ping the address however, and nmap shows an array of open ports:

Not shown: 1683 closed ports
PORT      STATE    SERVICE
21/tcp    open     ftp
22/tcp    open     ssh
25/tcp    filtered smtp
53/tcp    open     domain
80/tcp    open     http
110/tcp   open     pop3
143/tcp   open     imap
443/tcp   open     https
548/tcp   open     afpovertcp
587/tcp   open     submission
993/tcp   open     imaps
995/tcp   open     pop3s
1720/tcp  filtered H.323/Q.931
10000/tcp open     snet-sensor-mgmt

SMTP is filtered, perhaps by your provider? Perhaps by you?  Whichever applies, Postfix won't answer the phone for me.
You might want to try your test on port 25 again just to be sure, but it could be that *your *ISP is blocking your request. I can't connect from home (same as you) because my home ISP *does *block traffic on port 25 to anything except their mail server. However, I just tried from a server at work and it could connect to 'mail.ava-design.ro' on port 25 and get a response back from Postfix.

---

### Post by GordThompson on 2013-02-21
> **avaserver said:**
> 5 minute ago i was able to send a mail from [EMAIL="director@ava-design.ro"]director@ava-design.ro[/EMAIL]  to a gmail address . 

It arives to my gmail address with the following error:


This is an automatically generated Delivery Status Notification

 THIS IS A WARNING MESSAGE ONLY.

 YOU DO NOT NEED TO RESEND YOUR MESSAGE.

 Delivery to the following recipient has been delayed:

      [EMAIL="director@ava-design.ro"]director@ava-design.ro[/EMAIL]

 Message will be retried for 2 more day(s)

 Technical details of temporary failure:
 DNS Error: Domain name not found

 ----- Original message -----
That doesn't quite make sense. If you sent a message **from **director@ava-design.ro **to **something@gmail.com then what appears in your Gmail inbox should either be 1) the actual message you sent, or 2) nothing at all.

What you quoted was a bounce message for an email you tried to send from Gmail to [EMAIL="director@ava-design.ro"]director@ava-design.ro[/EMAIL] (i.e, the other direction). Did you try such a test earlier?

---

### Post by avaserver on 2013-02-21
from a putty :

root@avaserver:/# nmap -sS -O 127.0.0.1

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2007-04-17 06:34 EEST
Nmap scan report for avaserver (127.0.0.1)
Host is up (0.000013s latency).
Not shown: 983 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
25/tcp    open  smtp
53/tcp    open  domain
80/tcp    open  http
110/tcp   open  pop3
143/tcp   open  imap
443/tcp   open  https
548/tcp   open  afp
587/tcp   open  submission
631/tcp   open  ipp
783/tcp   open  spamassassin
993/tcp   open  imaps
995/tcp   open  pop3s
3306/tcp  open  mysql
10000/tcp open  snet-sensor-mgmt
20000/tcp open  unknown


Sometimes i can send mails, sometimes not.
For example 2 h ago i was able to send the mail described above (to a gmail with error and to a yahoo mail without any error).
2 min ago i was not able to send any mails (neither to yahoo, neither to gmail).
Sincerly i realy don`t know what is going on.

I called my isp twice this evening and he assured me that port 25 is opened. 
My ISP is the bigest provider from my country giving bussines internet plans for company`s. A lot of those companies are hosting providers, so i don`t believe is an ISP problem.

Sincerly i realy don`t know what to do :( I have this problem for a week and i cant solve it. :(


Also for the ip: 188.27.238.208:

root@avaserver:/# nmap -sS -O 188.27.238.208
Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2007-04-17 06:47 EEST
Nmap scan report for avaserver.ava-design.ro (188.27.238.208)
Host is up (0.000013s latency).
Not shown: 986 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
25/tcp    open  smtp
53/tcp    open  domain
80/tcp    open  http
110/tcp   open  pop3
143/tcp   open  imap
443/tcp   open  https
548/tcp   open  afp
587/tcp   open  submission
993/tcp   open  imaps
995/tcp   open  pop3s
10000/tcp open  snet-sensor-mgmt
20000/tcp open  unknown


What command should i use in cmd for verify the open port remotely?

---

### Post by GordThompson on 2013-02-21
> **avaserver said:**
> What command should i use in cmd for verify the open port remotely?
One way to test would be to use one of the many free web-based mail server testing tools. I did a Google search for 'mail server test' and got a bunch of them. The first one on the list was

[http://mxtoolbox.com/diagnostic.aspx](http://mxtoolbox.com/diagnostic.aspx)

and when I entered 'mail.ava-design.ro' I got the results listed here

[http://mxtoolbox.com/SuperTool.aspx?action=smtp%3amail.ava-design.ro]("http://mxtoolbox.com/SuperTool.aspx?action=smtp%3amail.ava-design.ro")

They indicate that your mail server is responding correctly to connections from the outside world.

-----

Note that the above is a test to help determine if you should be able to *receive *mail on that server. If you are now having problems *sending *mail from that server then some things to check would be

1) Is [EMAIL="director@ava-design.ro"]director@ava-design.ro[/EMAIL] receiving any bounce messages for the emails that are not being delivered?

2) Are there any entries in the Postfix log(s) that indicate what might be going wrong?

3) You could run your static IP address through an RBL checker like...

[http://multirbl.valli.org/](http://multirbl.valli.org/)

...which I just did, and found that your static IP is in several blocklists, including two Barracuda lists and two Spamhaus lists. 

At Spamhaus, the IP address range 188.27.0.0/16 is on the Policy Block List (PBL) because:

"This IP range has been identified by Spamhaus as not  meeting our policy for IPs permitted to deliver unauthenticated  'direct-to-mx' email to PBL users."

See [this page]("http://www.spamhaus.org/pbl/query/PBL702258") for more information, including options for getting removed from the PBL.

---

### Post by SeijiSensei on 2013-02-21
I was the one being blocked.  I thought I was connecting from one my machines in the cloud, but it was the one in my home which has outbound port 25 traffic blocked.  Sorry for the confusion I created.

So now, if I connect from a server in the cloud, I can connect to the SMTP server and issue the "ehlo" and "mail from" commands.  However when I try to send the message to "director@ava-design.ro" I get this result:

```

mail from: someone@example.com
250 2.1.0 Ok
rcpt to: director@ava-design.ro
451 4.3.0 <director@ava-design.ro>: Temporary lookup failure

```

That's not the same result that you show up in [post #14](http://ubuntuforums.org/showpost.php?p=12522374&postcount=14).

---

### Post by GordThompson on 2013-02-21
> ```
rcpt to: director@ava-design.ro
451 4.3.0 <director@ava-design.ro>: Temporary lookup failure
```Maybe the receiving server is greylisting...?

[http://en.wikipedia.org/wiki/Greylisting](http://en.wikipedia.org/wiki/Greylisting)

---

### Post by avaserver on 2013-02-21
Seiji, i realy dont know what to say...
My last telnet procedure worked for me.
Gord gave me a utility tool site where i was been able to have an mx lookup and it looks like smtp is good.

When i came back home i found more than 20 mails in my yahoo inbox. 
It seems that all the mails that i`ve sent from [email]director@ava-design.ro[/email] to my yahoo email address had arived but with delay (couple of hours delay).

My imap still not work. 
I also try 

mutt -f imap://director@ava-design.ro

This certificate belongs to:
   avaserver  [email]root@avaserver.ava-design.ro[/email]
   Dovecot mail server
   avaserver


This certificate was issued by:
   avaserver  [email]root@avaserver.ava-design.ro[/email]
   Dovecot mail server
   avaserver


This certificate is valid
   from Mon, 18 Feb 2013 11:20:32 UTC
     to Sat, 18 Feb 2023 11:20:32 UTC
SHA1 Fingerprint: 763D AFA0 D279 FA5B A1D3 F8C1 EAC8 52E6 98F7 E4FD
MD5 Fingerprint: 9F3C B499 9119 2111 AF72 0AA7 2CE7 CA8B

WARNING: Server certificate is not yet valid
WARNING: Server hostname does not match certificate


I accept
Then it ask for password. I enter my password, then it gives me the following error:

Authenticating (PLAIN)...
Logging in...
Login failed.

This is the password of the user mail that i`ve created in virtualmin right?

---

### Post by avaserver on 2013-02-21
I tryed to install roundcube.
But when i access: [www.ava-design.ro/roundcube](www.ava-design.ro/roundcube) 
popup with "save as" appears the popup with "Downloading file" default (3,6 kb):(

---

