---
title: "Citadel"
date: 2008-03-20
forum: Server Platforms
---

### Post by dantheman3212 on 2008-03-20
I've been having some problems with my Citadel server. i'm running Ubuntu 7.10 server with bind9 and apache running to do domain resolving, and that it working perfectly. I decided to install Citadel to run as an Internet Mail server, and went the path of doing the easy install. Everything seems to be working fine, and i can log into citadel, create users, etc., and send mail to different users in the same domain, but when I try to send or receive mail from outside servers, such as through hotmail, gmail, or yahoo mail, it wont receive, and when i try and send mail out, in the SMTP que is just says 'Connection timed out".

Now I know you have to edit your DNS host names and reverse zones to get citadel to talk to the outside world, but I am unable to find anyone who is in my position who has figured it out. Let me give you some information.


```

vpssolutions.com. IN SOA vpsserver.vpssolutions.com. admin.vpssolutions.com. (

2006081401
28800
3600
604800
38400 )

vpssolutions.com. IN NS vpsserver.vpssolutions.com.
IN A 24.117.5.71
vpssolutions.com. IN MX 10 vpssolutions.com.

vpssolutions.com IN A 24.117.5.71
www IN A 24.117.5.71
mail IN A 24.117.5.71:2000
ns1 IN A 24.117.5.71
@ IN A 24.117.5.71

```


thats my main zone .db file, and that all resolves fine. I can access vpssolutions.com outside the network without any problems.

Here is my reverse.


```



@ IN SOA vpssolutions.com. admin.vpssolutions.com. (
2006081401;
28800;
604800;
604800;
86400 );

IN NS vpsserver.vpssolutions.com.
71 IN PTR vpssolutions.com.



```

i've read that I need a PTR entry for citadel to work, but Citadel is running of the same IP address as the DNS server is, do I need another PTR entry?


P.S. I can also telnet ports 110, 143, and 25 through my server, and it says it is working. If anyone can help, please let me know, and if you need additional information, i can give it out. Thanks alot.

---

### Post by ctyc on 2008-03-23
yes the PTR record in needed for a real mail server.
But you do not have MX records and you have no NS records.

This is what your domain looks like to the internet.

A records
[www.vpssolutions.com](www.vpssolutions.com).   7200    IN      A       74.200.220.215
ftp.vpssolutions.com.   7200    IN      A       74.200.220.215
mail.vpssolutions.com.  7200    IN      A       74.200.220.215
smtp.vpssolutions.com.  7200    IN      A       74.200.220.215
pop.vpssolutions.com.   7200    IN      A       74.200.220.215
imap.vpssolutions.com.  7200    IN      A       74.200.220.215

MX and SOA Details
vpssolutions.com.       3600 IN SOA . hostmaster.nameserver. (
                                1          ; serial
                                28800      ; refresh (8 hours)
                                7200       ; retry (2 hours)
                                604800     ; expire (1 week)
                                5          ; minimum (5 seconds)
                                )

---

### Post by HermanAB on 2008-03-24
Yup, most problems with Citadel are due to a bad DNS and hostname configuration.

You must have A, PTR and MX records and your Citadel server host name must be a FQDN and it must resolve.  Otherwise it won't work - simple as that...

---

