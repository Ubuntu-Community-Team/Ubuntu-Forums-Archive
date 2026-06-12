---
title: "Set up an internal mail server"
date: 2012-11-16
forum: Server Platforms
---

### Post by sbjaved on 2012-11-16
My home network is like this:

5-6 devices (wirelessly) -----> Router ---> ISP Modem ---> Internet
File server-Ubuntu 12.04 (wired)--^

All devices are part of the same workgroup. I'm interested in learning more about networking and I would like to set up an internal mail server that allows all devices to send emails to each other.

I've found some good tutorials on the web but most are too advanced for my needs. I don't need to receive email from outside, just internally... for starters. I found this one [tutorial]("http://forums.pcper.com/showthread.php?448351-Howto-A-simple-internal-mail-server-using-postfix-and-dovecot") which seems fit for my needs but its 5 years old. Also I'm a little confused about domains. In order to use email internally, do I need to register a domain? And it seems I'd have to set up a DNS server (probably on the file server)...won't that screw up the internet access to the network if I set up my own DNS server?

I'm just experimenting since these things interest me, so if you can be patient and explain...please help.

---

### Post by Bachstelze on 2012-11-16
Email is strongly tied to DNS and the Internet, a strictly internal mail server is possible but far from trivial. (Email itself is far from trivial to begin with, even for a "standard" mail sever, I suggest you find something else to experiment with like HTTP/FTP.)

---

### Post by kennethconn on 2012-11-16
I would have a read of that article you cited again, if I were you.

Actually, I think the postfix installer in Ubuntu server has an option to select local only (open to correction on that as it has been a while).

Would nervously disagree with Bachstelze (that's an awful lot of posts you have racked up) about the internal only mail server for your domain-only mail, but certainly take the point on a practical level (i.e. you should focus on setting up a fully functional "standard" mail server only once you are more comfortable with the concepts). 

Also, as Bachstelze mentioned, look at setting up a web server first, as you should have a better understanding of other related concepts (such as networking, DNS) before you tackle the mail server project.

---

### Post by sbjaved on 2012-11-16
Thanks for your responses. I've already fiddled with an setting up an FTP server (vsftp). That was pretty easy. I haven't set up a web server yet. I'll look into that.

---

### Post by sbjaved on 2012-11-17
After some [reading]("http://www.aboutdebian.com/dns.htm") i've gathered that I can set up an internal domain and DNS server with the ability to forward internet requests to ISP's DNS servers. That was what I wanted to know. If i'm able to set up the DNS server properly, I think I'll try setting up a mail server as well.

I'm going to install ubuntu 12.04 server on spare old desktop and experiment with BIND on it, so that my current network setup (and file server) isn't disturbed if I make a mistake. Any and all pointers are welcome.

---

### Post by SeijiSensei on 2012-11-17
You do not even need a domain as I recall if all you want to do is deliver mail to local users.  You'd just need Postfix and Dovecot, though you'll need to change the Postfix configuration to allow mail to be sent to the Ethernet interface.  But you should be able to address mail to a local user name without a domain and have it delivered to that person's mailbox.

---

### Post by sbjaved on 2012-11-17
I found a tutorial about setting up an internal only mail server (I linked it in my first post) and that required setting up a domain. If you can link to any tutorials or posts for an internal only mail server w/o setting up a domain, that would be great because all the guides I found were using domains and were for full blown mail servers.

---

### Post by darkod on 2012-11-17
Sensei can correct me if I'm wrong, but I think you are looking at the domain thing the wrong way. For an email to be delivered it will have to have a domain, but it doesn't have to be a public (real) one. Also, your local machines will have to have their first DNS choice set up to be your server, not a public DNS.

And your server will also have to have DNS service running, so that it keeps all emails sent to your local domain.

Always sit down to think and follow to flow of information:
1. A machine in your network will send an email to [email]user@mydomain.local[/email]
2. Your machines will have your server as DNS server, and will ask him where is mydomain.local. The reply will be your local server IP and the message will be sent there.
3. The mailserver running on your server will be configured to accept mydomain.local and will accept the message and deliver it to the user mailbox.
4. For all other DNS queries of your machines, your server will just forward them to the public servers you specify, and the local machines will get their reply.

That should be the line of thought in my opinion. The domain doesn't need to be public or registered if your only need is to work locally.

---

### Post by Cheesemill on 2012-11-17
I know that it's for Debian but for a good basic understanding of mail servers you should at least read through this guide:
[http://workaround.org/ispmail/squeeze](http://workaround.org/ispmail/squeeze)

Even if you don't follow it then reading it will give you a good background in how all the various pieces of a mail server fit together.

---

### Post by kennethconn on 2012-11-17
You do not need to go near DNS for your requirements.

[https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html)

If you have read and understood this, you should be able to get this set-up working (again, based on your requirements).

---

### Post by darkod on 2012-11-17
> **kennethconn said:**
> You do not need to go near DNS for your requirements.

[https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html)

If you have read and understood this, you should be able to get this set-up working (again, based on your requirements).

Pardon my ignorance, but what is the idea here? Using the local hosts file can help relate hostname with local IP, but wouldn't the email sending require MX record information? How can you implement that without your own DNS server in this case when you are working only with local domain??

---

### Post by kennethconn on 2012-11-17
It is dealt with in the Postfix configuration, to the best of my knowledge. Let me see if I can find that particular configuration file (internal mail server scenario) for the OP.

---

### Post by sbjaved on 2012-11-17
> **kennethconn said:**
> It is dealt with in the Postfix configuration, to the best of my knowledge. Let me see if I can find that particular configuration file (internal mail server scenario) for the OP.
That would be great because i've been googling and i've found random threads here and there but not a full postfix tutorial for internal mail server w/o setting up a domain.

---

### Post by darkod on 2012-11-18
If the DNS part is where you are getting stuck, and if you want to try it, here is a tutorial about quick DNS setup on ubuntu:
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/](http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/)

I don't think configuring DNS with a local domain should be stopping you.

---

### Post by sbjaved on 2012-11-18
> **darkod said:**
> If the DNS part is where you are getting stuck, and if you want to try it, here is a tutorial about quick DNS setup on ubuntu:
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/](http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/)

I don't think configuring DNS with a local domain should be stopping you.
If Postfix can be configured to deliver mail locally without setting up a DNS server and a domain, I'd like to try that first.

---

### Post by sbjaved on 2012-11-18
I installed debian 6 in vmware player, set network to bridge mode. Selected both **mail server** and **dns server** during installation. It asked for a domain name during installation which I set to **javed.local**. 
After that I installed postfix and dovecot and selected "local only" during postfix configuration setup.
I followed the debian wiki instructions for postfix and sent a test email from root@localhost to saad@localhost. That worked. Now how do I extend it to send email to other machines on the network (none of which are a part of **javed.local** domain). Like I want to send an email from saad@debian (machine 1) to saad@ubuntu (machine 2)... 

Here is the postfix config file:

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
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

myhostname = debian.javed.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = debian.javed.local, localhost.javed.local, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
default_transport = error
relay_transport = error
```

---

### Post by kennethconn on 2012-11-18
My understanding of internal mail server is that everybody from your organisation can send email internally to each other. So you have two users on your local network like [email]saad@javed.local[/email] and [email]user2@javed.local[/email] that can send and receive email. I have got this up and running in the past purely as a learning exercise (but it was a long time ago and I thought I had the config files saved for future reference, can't seem to locate them at the moment).

What you wish to do sounds a bit cumbersome going forward. I think you need to research a bit more before you start actually configuring. SeijiSensei and darkod have made relevant points in their posts, and I'd imagine they have a lot more experience with configuring mail servers.

---

### Post by darkod on 2012-11-18
I still think you can't do this without your own local DNS, which I guess you didn't install yet. But I might be wrong.

It's own thing to select 'local' when installing postfix, but I don't see how that can tell other machines on your network where to find the mailserver. Only DNS service can do that, of any kind. You can use bind9, dnsmasq, or any other similar service, but they need to know where to find the mailserver.

Right now your machines are using public DNS, or the router as DNS which is the same thing, and the public DNS servers have no clue what javed.local is.

---

### Post by sbjaved on 2012-11-18
These are postfix config values I collected from google searches about setting up postfix w/o a domain. Since I have no clue what they actually mean...I thought i'd post them here. Would they work?

```
myhostname = debian
mydomain = javed.local
myorigin = $mydomain
inet_interfaces = all
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
mynetworks = 192.168.0.100/24, 127.0.0.0/8
relay_domains = 
home_mailbox = Maildir/
[B]append_dot_mydomain = no
disable_dns_lookups = yes[/B]

```

saad@ubuntu <-----------------> saad@debian
(192.168.0.103)--------------------(192.168.0.106)
Laptop--------------------------------Server   

Can I specify in postfix config different destination addresses like deliver mail to saad@ubuntu at 192.168.0.103? I have 4 machines on the network so i could easily specify addresses manually.

@darkod If there is any hope to do this w/o setting up a DNS Server, I'll chase it because BIND looks mighty scary. If it doesn't work....I'll set up a DNS Server then :)

---

### Post by darkod on 2012-11-18
I think the network needs to be specified as 192.168.0.0/24, the whole subnet. The 192.168.0.100 might be the server IP but the whole network definition is 192.168.0.0/24.

In my opinion, you are looking at the domain thing in a wrong way. The point is not whether or not the server is part of a domain.

The point is how will the client computers know where the server is to deliver mail to it?

I see the hostname is debian, so do a quick test. From any of the other machines on the network, try to ping the server:
ping debian.javed.local

I bet it won't find it, because it doesn't know where javed.local is. That's why you need local DNS to tell the other computers:

1. The MX record for the domain javed.local points to debian.javed.local
2. That debian.javed.local is at 192.168.0.100

You don't need a domain network installed, but you do need DNS resolution that is able to identify the MX record and the server IP.

---

### Post by sbjaved on 2012-11-18
I understand your point...but SeijiSensei and KennethConn seem to think there is a way to do this w/o setting up a DNS server...

---

### Post by sbjaved on 2012-11-19
Experimenting with BIND/DNS on the debian VM. I've run into some errors. I've posted the config files and error below.

**/etc/bind/named.conf**

```

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
```

**/etc/bind/named.conf.local**

```
//
// Do any local configuration here
//

zone "javed.local" {
    type master;
	file "/etc/bind/db.javed.local";
};

zone "0.168.192.in-addr.arpa" {
    type master;
	file "/etc/bind/db.0.168.192";
};

// Consider adding the 1918 zones here, if they are not used in your
// organization
include "/etc/bind/zones.rfc1918";
```

**/etc/bind/named.conf.options**

```
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow multiple
	// ports to talk.  See http://www.kb.cert.org/vuls/id/800113

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	forwarders {
		192.168.15.1;
	};

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};

```

**/etc/bind/db.javed.local (forward-lookup)**

```
$TTL 86400
javed.local.            IN     SOA    debian.javed.local. (
                   2004011522     ; Serial no., based on date
                        21600     ; Refresh after 6 hours
                         3600     ; Retry after 1 hour
                       604800     ; Expire after 7 days
                         3600     ; Minimum TTL of 1 hour
                      )
beast                 IN     A       192.168.0.104
home-server           IN     A       192.168.0.105
debian                IN     A       192.168.0.106
@                     IN     NS      debian
@                     IN     MX      10 debian
debian                IN     CNAME   @

```

**/etc/bind/db.0.168.192 (reverse lookup)**

```
$TTL 86400
@                     IN     SOA    debian.javed.local. (
                   2004011522     ; Serial no., based on date
                        21600     ; Refresh after 6 hours
                         3600     ; Retry after 1 hour
                       604800     ; Expire after 7 days
                         3600     ; Minimum TTL of 1 hour
                      )
104                    IN     PTR     beast
105                    IN     PTR     home-server
106                    IN     PTR     debian
@                      IN     NS      debian

```

**Error:**

```

saad@debian:~$ sudo named-checkconf -z
dns_rdata_fromtext: /etc/bind/db.javed.local:7: near eol: unexpected end of input
dns_master_load: /etc/bind/db.javed.local:14: debian.javed.local: CNAME and other data
zone javed.local/IN: loading from master file /etc/bind/db.javed.local failed: unexpected end of input
zone javed.local/IN: not loaded due to errors.
_default/javed.local/IN: unexpected end of input
dns_rdata_fromtext: /etc/bind/db.0.168.192:7: near eol: unexpected end of input
zone 0.168.192.in-addr.arpa/IN: loading from master file /etc/bind/db.0.168.192 failed: unexpected end of input
zone 0.168.192.in-addr.arpa/IN: not loaded due to errors.
_default/0.168.192.in-addr.arpa/IN: unexpected end of input
zone 10.in-addr.arpa/IN: loaded serial 1
zone 16.172.in-addr.arpa/IN: loaded serial 1
zone 17.172.in-addr.arpa/IN: loaded serial 1
zone 18.172.in-addr.arpa/IN: loaded serial 1
zone 19.172.in-addr.arpa/IN: loaded serial 1
zone 20.172.in-addr.arpa/IN: loaded serial 1
zone 21.172.in-addr.arpa/IN: loaded serial 1
zone 22.172.in-addr.arpa/IN: loaded serial 1
zone 23.172.in-addr.arpa/IN: loaded serial 1
zone 24.172.in-addr.arpa/IN: loaded serial 1
zone 25.172.in-addr.arpa/IN: loaded serial 1
zone 26.172.in-addr.arpa/IN: loaded serial 1
zone 27.172.in-addr.arpa/IN: loaded serial 1
zone 28.172.in-addr.arpa/IN: loaded serial 1
zone 29.172.in-addr.arpa/IN: loaded serial 1
zone 30.172.in-addr.arpa/IN: loaded serial 1
zone 31.172.in-addr.arpa/IN: loaded serial 1
zone 168.192.in-addr.arpa/IN: loaded serial 1
zone localhost/IN: loaded serial 2
zone 127.in-addr.arpa/IN: loaded serial 1
zone 0.in-addr.arpa/IN: loaded serial 1
zone 255.in-addr.arpa/IN: loaded serial 1
```

I've mainly followed instructions from here:
[http://www.aboutdebian.com/dns.htm]("http://www.aboutdebian.com/dns.htm")

---

### Post by darkod on 2012-11-19
I think you should take a look at the link I posted earlier, about settings up DNS in ubuntu the easy way. It has exact and precise insructions.
Here is the link again:
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/](http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/)

Alternatively, you can use a very simple DNS with dnsmasq because that's all you need. If you want to try that, stop the bind daemon (service), and install dnsmasq in the VM:
sudo apt-get install dnsmasq

After that, edit /etc/hosts and add your server there, which seems to have hostname 'debian', so make it something like:
192.168.0.100 debian.javed.local

Use the correct IP for the server if it's not 192.168.0.100. dnsmasq will use the hosts in /etc/hosts so adding the server host there will make it use it in DNS queries.

Finally, open the /etc/dnsmasq.conf file and look for mx-host (it's towards the middle of the file, there are many rows to scroll, the file is big). If you use nano to edit, you can search inside the file with Ctrl+W and look for mx-host.
When you find the line, remove the # at front and edit the line to something like:
mx-host=javed.local,debian.javed.local,10

If I'm not mistaken that should return debian.javed.local (the server host) for the MX queries on the javed.local domain.

After saving and closing the file, restart the dnsmasq service.

That should be it. Don't forget that the primary DNS for the local machines should be your server, either by setting it up manually or adding the option in the router dhcp settings.

If everything worked fine, if you now try:
ping debian.javed.local

from any machine it should return a reply.

And the MX query should work fine too.

---

### Post by sbjaved on 2012-11-19
I set it up like you explained. Changed nameserver 192.168.0.106 in /etc/resolv.conf on a client machine (beast), and pinged debian. 

```
saad@beast:~$ ping debian.javed.local
ping: unknown host debian.javed.local

saad@beast:~$ ping debian
PING debian.javed.local (192.168.0.106) 56(84) bytes of data.
64 bytes from debian.javed.local (192.168.0.106): icmp_req=1 ttl=64 time=0.289 ms
64 bytes from debian.javed.local (192.168.0.106): icmp_req=2 ttl=64 time=0.390 ms
64 bytes from debian.javed.local (192.168.0.106): icmp_req=3 ttl=64 time=0.387 ms
64 bytes from debian.javed.local (192.168.0.106): icmp_req=4 ttl=64 time=0.424 ms
64 bytes from debian.javed.local (192.168.0.106): icmp_req=5 ttl=64 time=0.161 ms
^C
--- debian.javed.local ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 0.161/0.330/0.424/0.096 ms

saad@beast:~$ dig debian.javed.local

; <<>> DiG 9.8.1-P1 <<>> debian.javed.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45297
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;debian.javed.local.		IN	A

;; ANSWER SECTION:
debian.javed.local.	0	IN	A	192.168.0.106
debian.javed.local.	0	IN	A	127.0.1.1

;; Query time: 1 msec
;; SERVER: 192.168.0.106#53(192.168.0.106)
;; WHEN: Mon Nov 19 15:44:54 2012
;; MSG SIZE  rcvd: 68

```

Does the client (beast) have to be a part of the javed.local domain for ping to work? it is pinging debian but not debian.javed.local ...

---

### Post by darkod on 2012-11-19
No, it doesn't.

What is the IP of the server, 100 or 106?

---

### Post by sbjaved on 2012-11-19
```
saad@beast:~$ dig mx javed.local

; <<>> DiG 9.8.1-P1 <<>> mx javed.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37927
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 2

;; QUESTION SECTION:
;javed.local.			IN	MX

;; ANSWER SECTION:
javed.local.		0	IN	MX	10 debian.javed.local.

;; ADDITIONAL SECTION:
debian.javed.local.	0	IN	A	127.0.1.1
debian.javed.local.	0	IN	A	192.168.0.106

;; Query time: 1 msec
;; SERVER: 192.168.0.106#53(192.168.0.106)
;; WHEN: Mon Nov 19 16:11:22 2012
;; MSG SIZE  rcvd: 95

```

---

### Post by sbjaved on 2012-11-19
> **darkod said:**
> No, it doesn't.

What is the IP of the server, 100 or 106?
debian is at 192.168.0.106

---

### Post by darkod on 2012-11-19
I didn't notice in your earlier reply that it work with ping debian. I wasn't sure whether you need to add the domain in the ping command since the clients are not in the domain.

Looks to me like it's working.

You are getting a correct DNS reply with dig, including the MX reply. And the ping is working.

Try sending email now.

---

### Post by sbjaved on 2012-11-19
How should I do that?...before I followed wiki instructions for postfix.

saad@debian:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 debian.javed.local ESMTP Postfix (Debian/GNU)
mail from: saad@debian
250 2.1.0 Ok
rcpt to: saad@beast
550 5.1.1 <saad@beast>: Recipient address rejected: beast

---

### Post by darkod on 2012-11-19
Instead of localhost, when doing it from another machine use the server host, debian.javed.local (or only debian, I'm not sure). Like:
telnet debian.javed.local 25

But you won't be able to send email to saad@beast. The email system is not used to send from the mailserver to any machine, it's used to send from any machine (email client) to the mailserver.

So, on the beast machine try something like:
telnet debian.javed.local 25

And then try sending from user [email]saad@javed.local[/email] to another user that is created on the mailserver and has a mailbox.

If you add dovecot to postfix, you can use email clients to do this, not the command line.

In any case, all users have to be created on the server and have their own mailboxes in order to receive mail. You can't try sending email to some mailbox that doesn't exist, right?

---

### Post by sbjaved on 2012-11-19
```
saad@beast:~$ telnet debian.javed.local 25
telnet: could not resolve debian.javed.local/25: Name or service not known
saad@beast:~$ telnet debian 25
Trying 127.0.1.1...
Trying 192.168.0.106...
telnet: Unable to connect to remote host: Connection refused
saad@beast:~$ telnet javed.local 25
telnet: could not resolve javed.local/25: Name or service not known

```

---

### Post by darkod on 2012-11-19
OK, so telnet debian 25 worked but the connection was refused.

I am not an expert on mailservers, it seems something in the configuration is blocking you. I remember in one of the postfix config files you seem to have enabled secure connection (encryption). Not sure how it should work.

The DNS configuration looks OK to me since you can ping debian and dig returns expected results. Now you need to take a look at the email configuration, and maybe consider installing dovecot so you can use email clients.

Testing with email clients would be much better than in the command line. After all, you expect people to use email clients, not just to set up a test system where they can only send emails at the command line.

---

### Post by sbjaved on 2012-11-19
Thanks for all the help Darkod. I'm going to figure this out.

---

### Post by sbjaved on 2012-11-19
Been playing with postfix config. Like solving a rubik's cube. Messing with one option after another....

---

### Post by darkod on 2012-11-19
Since this is a VM, if you have a snapshot of the VM with only debian installed, I suggest you go back to that snapshot and try with postfix again. Try with the official documentation and for a start keep it simple, no SSL, nothing.
It doesn't look complicated in the official documentation:
[https://help.ubuntu.com/12.04/serverguide/postfix.html](https://help.ubuntu.com/12.04/serverguide/postfix.html)

After each important step, make a snapshot that you can go back to.

Now that you know how to do the dnsmasq DNS service, I suggest you make a clean debian install (or restore a snapshot if you have it), do the dnsmasq again, and make a snapshot of that situation to keep it. Then continue with postfix.

---

### Post by SeijiSensei on 2012-11-20
I skimmed the last couple of days of postings, and one question kept popping up, how will the client machines find the mailserver.

The answer is simply how you define the SMTP server in the client email software.  Have all the clients use the server's IP address, or its hostname since it looks like you have DNS running now.

[noparse]Also there seemed to be some notion that mail from user1@host1 addressed to user2@host2 will somehow appear on host2.  All the mailboxes are on the server.  Mail should be addressed to user@javed.local.[/noparse]

---

### Post by sbjaved on 2012-11-20
> **SeijiSensei said:**
> I skimmed the last couple of days of postings, and one question kept popping up, how will the client machines find the mailserver.

The answer is simply how you define the SMTP server in the client email software.  Have all the clients use the server's IP address, or its hostname since it looks like you have DNS running now.

[noparse]Also there seemed to be some notion that mail from user1@host1 addressed to user2@host2 will somehow appear on host2.  All the mailboxes are on the server.  Mail should be addressed to user@javed.local.[/noparse]

Just to update you: debian is a VM installation i set up to test dns and postfix. it asked for a domain name during installation so i gave it one:**javed.local**. No other machine on the network is part of javed.local or any domain.

What i'm confused about is that pinging debian works ... even on systems where debian(192.168.0.106) is not set as the nameserver in resolv.conf... I think its because all of them are in the same workgroup... but pinging debian.javed.local does not work from anywhere...is it because none of the machines are in javed.local domain?
i.e.

beast(192.168.0.104) nameserver 192.168.0.106 in /etc/resolv.conf
--->ping debian WORKS
--->ping debian.javed.local NOT FOUND

home-server(192.168.0.105) nameserver 127.0.0.1 in /etc/resolv.conf
--->ping debian WORKS
--->ping debian.javed.local NOT FOUND

So I can't send email to anybody because no computer on the network is able to see debian.javed.local...

---

### Post by sbjaved on 2012-11-20
Okay I haven't yet figured out the ping thing. But on debian, I edited /etc/hosts which was:
```
127.0.0.1	localhost
127.0.1.1	debian.javed.local	debian
192.168.0.106	debian.javed.local	

```
I changed it to:
```
127.0.0.1	localhost
**#**127.0.1.1	debian.javed.local	debian
192.168.0.106	debian.javed.local	**debian**

```

After that I tried sending an email from saad@beast(192.168.0.104) to saad@debian(192.168.0.106)
```
saad@beast:~$ telnet debian 25
Trying 192.168.0.106...
Connected to debian.javed.local.
Escape character is '^]'.
220 debian.javed.local ESMTP Postfix (Debian/GNU)
mail from: saad@beast
250 2.1.0 Ok
rcpt to: saad@debian
550 5.1.1 <saad@debian>: Recipient address rejected: debian
rcpt to: saad@debian.javed.local
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
Subject: Test

Hi,
This is a test 
.
250 2.0.0 Ok: queued as DEA444AF71
quit
221 2.0.0 Bye
Connection closed by foreign host.

```
It WORKED :)
Here is the postfix conf I used:
```
myhostname = debian.javed.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = **debian.javed.local, localhost.javed.local, localhost**
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128, **192.168.0.0/24**
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = **all**
default_transport = error
relay_transport = error

```
I also commented out all the TLS parameters in the postfix conf.

Now how do I send an email from saad@debian(192.168.0.106) to saad@beast(192.168.0.104)??

---

### Post by darkod on 2012-11-20
As I and Sensei already mentioned, email sending is NOT machine to machine. It's mailbox to mailbox.

You don't send email from @debian to @beast.

You send it from [email]user1@javed.local[/email] to [email]user2@javed.local[/email]. By the way, when sending email you should use @javed.local not @debian.

The users will access their mailbox with email clients and they could do that from any machine in your network. So, you need something like dovecot to provide POP3 and IMAP access, and some email client on the machines.

---

### Post by sbjaved on 2012-11-20
> **darkod said:**
> As I and Sensei already mentioned, email sending is NOT machine to machine. It's mailbox to mailbox.

You don't send email from @debian to @beast.

You send it from [email]user1@javed.local[/email] to [email]user2@javed.local[/email]. By the way, when sending email you should use @javed.local not @debian.

The users will access their mailbox with email clients and they could do that from any machine in your network. So, you need something like dovecot to provide POP3 and IMAP access, and some email client on the machines.
I see. All mailbox accounts will be on debian and users will access their mailboxes.
But the problem is I can't seem to send email to [email]saad@javed.local[/email]

```
saad@debian:~$ telnet debian.javed.local 25
Trying 192.168.0.106...
Connected to debian.javed.local.
Escape character is '^]'.
220 debian.javed.local ESMTP Postfix (Debian/GNU)
mail from: **root@javed.local**       
250 2.1.0 Ok
rcpt to: **saad@javed.local**
550 5.1.1 <saad@javed.local>: Recipient address rejected: javed.local
rcpt to: saad@debian.javed.local
250 2.1.5 Ok

```

---

### Post by darkod on 2012-11-20
But you see, it worked with sender [email]root@javed.local[/email]. As long as the mailbox exists, it should work.

But I don't have in depth knowledge of mailservers, maybe Sensei will jump back in.

---

