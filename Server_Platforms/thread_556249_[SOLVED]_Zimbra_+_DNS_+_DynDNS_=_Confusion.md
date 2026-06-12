---
title: "[SOLVED] Zimbra + DNS + DynDNS = Confusion"
date: 2007-09-21
forum: Server Platforms
---

### Post by mlissner on 2007-09-21
Can somebody please help me? I've been looking all over, but I can't figure this out, and unfortunately until I do, my mail is officially bouncing.

For the past week, I've been trying to install Zimbra on my server in my house, but every time I try, I have problems with DNS, and it fails. 

I'm using dyndns as my dns server because static IP addresses are too expensive for me. 

Something's not right in my configuration. Can somebody figure out what's wrong with this picture:

/etc/hosts:
```
127.0.0.1 localhost.localdomain localhost
70.137.152.208 mail.michaeljaylissner.com       mail

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

hostname -f:
```
mail.michaeljaylissner.com
```

host `hostname:
```
mail.michaeljaylissner.com has address 70.137.138.227
mail.michaeljaylissner.com mail is handled by 5 michaeljaylissner.com.

```

dig mail.michaeljaylissner.com mx:
```
; <<>> DiG 9.3.4 <<>> mail.michaeljaylissner.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61333
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 5, ADDITIONAL: 6

;; QUESTION SECTION:
;mail.michaeljaylissner.com.    IN      MX

;; ANSWER SECTION:
mail.michaeljaylissner.com. 43200 IN    MX      5 michaeljaylissner.com.

;; AUTHORITY SECTION:
michaeljaylissner.com.  86260   IN      NS      ns1.mydyndns.org.
michaeljaylissner.com.  86260   IN      NS      ns2.mydyndns.org.
michaeljaylissner.com.  86260   IN      NS      ns3.mydyndns.org.
michaeljaylissner.com.  86260   IN      NS      ns5.mydyndns.org.
michaeljaylissner.com.  86260   IN      NS      ns4.mydyndns.org.

;; ADDITIONAL SECTION:
michaeljaylissner.com.  60      IN      A       70.137.152.208
ns4.mydyndns.org.       86330   IN      A       213.155.150.206
ns2.mydyndns.org.       86346   IN      A       204.13.249.82
ns5.mydyndns.org.       85401   IN      A       203.62.195.76
ns3.mydyndns.org.       43146   IN      A       204.13.250.82
ns1.mydyndns.org.       84831   IN      A       63.208.196.92

;; Query time: 71 msec
;; SERVER: 68.94.156.1#53(68.94.156.1)
;; WHEN: Fri Sep 21 00:31:11 2007
;; MSG SIZE  rcvd: 258

```

Any ideas are welcome, I'm losing it here...

Thanks.

---

### Post by dmizer on 2007-09-21
if you're behind a router, you won't be able to browse to your external ip.  you'll have to configure your hosts file with your local network ip address like so:

```
127.0.0.1 localhost.localdomain localhost
192.168.1.2 mail.michaeljaylissner.com       mail
```

replace "192.168.1.2" with your server's actual ip address.

---

### Post by Brazen on 2007-09-21
Your mx record is backwards.  It should say this:
"michaeljaylissner.com mail is handled by 5 mail.michaeljaylissner.com"

I went ahead and checked it from my machine:
```
brazen@SERVER01:~$ host michaeljaylissner.com
michaeljaylissner.com has address 70.137.152.208
brazen@SERVER01:~$ host mail.michaeljaylissner.com
mail.michaeljaylissner.com has address 70.137.138.227
mail.michaeljaylissner.com mail is handled by 5 michaeljaylissner.com.
```

I should have been able to do the "host michaeljaylissner.com" and gotten the mx record I listed above.  The mx record should not show up under "host mail.michaeljaylissner.com"

A little explanation:
The thing is, when someone sends email to [email]mikey@michaeljaylissner.com[/email], the mail server checks the dns info for michaeljaylissner.com and sees the mx record which should say that mail for michaeljaylissner.com is handled by the server named mail.michaeljaylissner.com.  It then performs a lookup on mail.michaeljaylissner.com to see what the address is for that server.

Just to clarify, this is what those two commands I ran above SHOULD look like:
```
brazen@SERVER01:~$ host michaeljaylissner.com
michaeljaylissner.com has address 70.137.152.208
michaeljaylissner.com mail is handled by 5 mail.michaeljaylissner.com.
brazen@SERVER01:~$ host mail.michaeljaylissner.com
mail.michaeljaylissner.com has address 70.137.138.227
```

this will need to be reconfigured in your dyndns options.

---

### Post by mlissner on 2007-09-21
OK. I think I've gotten these fixed, but I'm still a bit uncertain it's right. As of now, I've fixed my configuration in /etc/hosts per the first post, and I've updated my information at DYNDNS so that it has 2 A records: michaeljaylissner.com and mail.michaeljaylissner.com. One MX record, with host michaeljaylissner.com and data mail.michaeljaylissner.com. 

Beyond that, I have one CNAME, [www.michaeljaylissner.com](www.michaeljaylissner.com). Does that all add up about right? 

Also, if I want to install Zimbra today, I'm essentially out of luck, right, because these changes are going to take some time to get through the DNS system?

---

### Post by KCPokes on 2007-09-21
Not necessarily.  DNS can take up to 72 hours, but a lot depends on the cache timeout for the different DNS servers.  Of course this means that some will see the updated record while others may not, but typically it is far less then 24 hours for DNS to propagate.

---

### Post by mlissner on 2007-09-22
Well, I've made some progress. Zimbra is now installed, but I can't get it to receive mail, and my woeful ignorance of the ways of DNS/mail routing are driving me crazy. I just don't understand enough to understand where to begin. Can somebody lend me a hand one more time in figuring this out?

Here's the current status of my configuration:
[B]
more /etc/hosts[/B]
```
127.0.0.1 localhost.localdomain localhost
192.168.1.132   mail.michaeljaylissner.com      mail

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


**hostname**
```
mail.michaeljaylissner.com
```

**host `hostname`**
```
mail.michaeljaylissner.com has address 192.168.1.132
```

**dig mail.michaeljaylissner.com mx**
```
; <<>> DiG 9.3.4 <<>> mail.michaeljaylissner.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52430
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.michaeljaylissner.com.    IN      MX

;; AUTHORITY SECTION:
michaeljaylissner.com.  1800    IN      SOA     ns1.mydyndns.org. zone-admin.dyndns.com. 2007091820 10800 1800 604800 1800

;; Query time: 67 msec
;; SERVER: 68.94.156.1#53(68.94.156.1)
;; WHEN: Sat Sep 22 11:56:01 2007
;; MSG SIZE  rcvd: 114

```

**dig michaeljaylissner.com mx**
```
; <<>> DiG 9.3.4 <<>> michaeljaylissner.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57595
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 5, ADDITIONAL: 5

;; QUESTION SECTION:
;michaeljaylissner.com.         IN      MX

;; ANSWER SECTION:
michaeljaylissner.com.  40962   IN      MX      5 mail.michaeljaylissner.com.

;; AUTHORITY SECTION:
michaeljaylissner.com.  51842   IN      NS      ns2.mydyndns.org.
michaeljaylissner.com.  51842   IN      NS      ns1.mydyndns.org.
michaeljaylissner.com.  51842   IN      NS      ns5.mydyndns.org.
michaeljaylissner.com.  51842   IN      NS      ns3.mydyndns.org.
michaeljaylissner.com.  51842   IN      NS      ns4.mydyndns.org.

;; ADDITIONAL SECTION:
ns2.mydyndns.org.       50299   IN      A       204.13.249.82
ns4.mydyndns.org.       50299   IN      A       213.155.150.206
ns3.mydyndns.org.       50299   IN      A       204.13.250.82
ns1.mydyndns.org.       50959   IN      A       63.208.196.92
ns5.mydyndns.org.       50299   IN      A       203.62.195.76

;; Query time: 12 msec
;; SERVER: 68.94.156.1#53(68.94.156.1)
;; WHEN: Sat Sep 22 11:56:43 2007
;; MSG SIZE  rcvd: 242

```

Thanks again for all the help.

---

### Post by MJN on 2007-09-22
Getting there!

However, the A record for mail.michaeljaylissner.com is pointing to your internal (private) IP address - for us (the rest of the world) we need that to resolve to your public IP address.

```

~$ dig michaeljaylissner.com mx

; <<>> DiG 9.3.2 <<>> michaeljaylissner.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2206
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;michaeljaylissner.com.         IN      MX

;; ANSWER SECTION:
michaeljaylissner.com.  43200   IN      MX      5 mail.michaeljaylissner.com.

;; ADDITIONAL SECTION:
mail.michaeljaylissner.com. 60  IN      A       192.168.1.132

;; Query time: 40 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sat Sep 22 20:01:58 2007
;; MSG SIZE  rcvd: 76

```If you don't know what your external IP address is (perhaps it's dynamic) then go to [http://get-myip.com/](http://get-myip.com/) and it'll tell you. However, if you are on a dynamic IP then you'll be wanting to run a client to automatically update the DNS whenever the address changes however let's take this one step at a time.

Edit: I see you mentioned a dynamic IP in which case are you already running such a client? If so you need to ensure it is finding the correct address (what client is it?).

Mathew

---

### Post by deuce868 on 2007-09-22
Just a heads up that running a mail server on a dynamic ip range is going to get you into trouble at some point or another. A lot of other servers out there block or add spam points to known dynamic ranges such as those owned by comcast and other ISPs.

---

### Post by MJN on 2007-09-22
I've run one for several years now with no known problems - simply relay outgoing mail via your ISPs mail server and you're good to go.

Mathew

---

### Post by mlissner on 2007-09-22
See, this is why I'm so confused. 

If I go into the dyndns.com settings and point mail.michaeljaylissner.com to the IP of my mail server, it loads the web server (i.e. [http://www.michaeljaylissner.com/index.php](http://www.michaeljaylissner.com/index.php)). This is not surprising because the web server sits next to the mail server and is on the same IP.

Is there a way for one server to do one thing, and the other server to do the other with both on the same IP? There must be, right?

---

### Post by MJN on 2007-09-23
Your web server will be listening on port 80 and your mail server port 25. This port, in combination with the IP address, thus then makes two uniquely identifiable services. Don't be put off by the DNS perspective that your web and mail records are pointing to the same IP - a connecting client will also specify a port to connect to and hence traffic will hit the right service.

Does that make sense? Have a read of [http://www.tcpipguide.com/free/t_TCPIPPortsTransportLayerTCPUDPAddressing.htm](http://www.tcpipguide.com/free/t_TCPIPPortsTransportLayerTCPUDPAddressing.htm) which gives some good info on the subject.

Have a look at the following:

```

$ telnet www.michaeljaylissner.com 25
Trying 70.137.171.63...
Connected to michaeljaylissner.com.
Escape character is '^]'.
220 mail.michaeljaylissner.com ESMTP Postfix

```See how I've used the name of your web server (or 'service') yet still connected to your mail server/service? That's because I specified the port (25) as any mail server would also do. Of course, in practice no mail server will use the name [www.michaeljaylissner.com]("http://www.michaeljaylissner.com") so you'll still got the point the mail. record correctly.

Mathew

---

### Post by mlissner on 2007-09-23
This makes sense with the ports. I think I pretty much understand ports, and I've got my router set to forward the proper ports for mail to the mail server, and the proper ports for web to the web server sitting next to it. 

I made all the changes people have suggested so far and I think my mail would be going through were it not for the DNS taking time to adapt.

So, the only remaining problem is the web mail aspect: If I go to mail.michaeljaylissner.com, it takes me to [www.michaeljaylissner.com](www.michaeljaylissner.com), rather than the zimbra log in site. On the other hand, if I go to 192.168.1.132, all is well (as would be expected since the web server is on 192.168.1.131. 

Also, before I forget, thanks for all the help. I would truly be stranded and sad without it.

---

### Post by MJN on 2007-09-23
If Zimbra is sat on a seperate physical server then you'll have to either change the port it listens on (so you can forward that port from your router to it) or you could employ a rewrite rule (or proxy pass) from your 'primary' web server to the one hosting Zimbra (again on a non-standard port).

The archives/web should hold some examples for the redirects/proxying or perhaps someone can walk you through their own solution (I don't use it so I'd be learning beside you).

Mathew

P.S. Does Zimbra run under https? It ought to (to protect your password at the very least) and so you could take advantage of this given it'd be running on port 443 hence can be easily seperated from the port 80 traffic to your main web server.

---

### Post by MJN on 2007-09-23
If Zimbra is sat on a seperate physical server then you'll have to either change the port it listens on (so you can forward that port from your router to it) or you could employ a rewrite rule (or proxy pass) from your 'primary' web server to the one hosting Zimbra (again on a non-standard port).

The archives/web should hold some examples for the redirects/proxying or perhaps someone can walk you through their own solution (I don't use it so I'd be learning beside you).

Mathew

P.S. Does Zimbra run under https? It ought to (to protect your password at the very least) and so you could take advantage of this given it'd be running on port 443 hence can be easily seperated from the port 80 traffic to your main web server.

---

### Post by mlissner on 2007-09-25
Well, I was giving it some time to do what it had to do, but alas, my belief that it was working was wrong. 

I have no idea why at this point. Any ideas would be greatly appreciated. The only change since the last time I posted is that I have set up the ddclient to keep dyndns up to date with the IP of the mail server. 

The problem it is having is the same one as ever: incoming mail doesn't get delivered. Outgoing works fine. Any ideas?

---

### Post by MJN on 2007-09-25
Looks to be working fine from here:
 
```

; <<>> DiG 9.2.3 <<>> @dns1.menandmice.com michaeljaylissner.com MX 
;; global options: printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57397
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 5, ADDITIONAL: 0
;; QUESTION SECTION:
;michaeljaylissner.com. IN MX
;; ANSWER SECTION:
michaeljaylissner.com. 42868 IN MX 5 michaeljaylissner.com. 
;; AUTHORITY SECTION:
michaeljaylissner.com. 86068 IN NS ns4.mydyndns.org. 
michaeljaylissner.com. 86068 IN NS ns5.mydyndns.org. 
michaeljaylissner.com. 86068 IN NS ns1.mydyndns.org. 
michaeljaylissner.com. 86068 IN NS ns2.mydyndns.org. 
michaeljaylissner.com. 86068 IN NS ns3.mydyndns.org. 
;; Query time: 205 msec
;; SERVER: 217.151.171.7#53(dns1.menandmice.com)
;; WHEN: Tue Sep 25 08:59:35 2007
;; MSG SIZE rcvd: 157
 
 
 
 
OK, connected to michaeljaylissner.com...
< 220 mail.michaeljaylissner.com ESMTP Postfix
> HELO edit.dnsvr.com
< 250 mail.michaeljaylissner.com
> MAIL FROM:<none@example.com>
< 250 Ok
> RCPT TO:<postmaster@michaeljaylissner.com>
< 250 Ok
> DATA
< 354 End data with <CR><LF>.<CR><LF>
> From: none@example.com
> To: postmaster@michaeljaylissner.com
> Subject: ZoneEdit Automated SMTP Test (michaeljaylissner.com)
> 
> If you received this, then the mail server (michaeljaylissner.com) is probably working.
> Sent at 2007-09-25 01:58:25 by 82.110.109.210 using Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; DII; .NET CLR 1.0.3705; .NET CLR 1.1.4322; InfoPath.1)
> .
< 250 Ok: queued as 609B711003D0

```
 
Mathew

---

### Post by mlissner on 2007-09-25
OK, I think I got it going. Just knowing that it was a local problem helped immensely, so thanks again for all the help. I did a little research, and learned that somehow one of the many ports Zimbra needs wasn't open on my router. 

I opened it up, and wah lah! Mail comes, mail goes. It's like a small miracle. 

Now that it's working, I must say I am impressed with Zimbra. Not only is the web interface pretty darned slick, but the POP and IMAP abilities impress as well, and are already better (more secure) than what I used to use back when somebody else was handling my mail. 

Most excellent. Now I just need to figure out that business about proxy passing you mentioned above.

---

### Post by mlissner on 2007-09-25
Here's the answer to that last bit. 

Change to the zimbra user: su zimbra.

Run zmtlsctl https; zmcontrol stop; zmcontrol start. 

The mail will thus be at [https://example.com](https://example.com). The web will be at [http://example.com](http://example.com)

This will work for a while anyway.

---

