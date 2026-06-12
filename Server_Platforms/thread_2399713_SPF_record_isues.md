---
title: "SPF record isues"
date: 2018-08-29
forum: Server Platforms
---

### Post by johngreen2 on 2018-08-29
Hi All,
I am completely new to both linux and networking, but have inherited a server that is running Ubuntu server with a  web server and associated apps, and also a postfix/courier service installed on it.
I have spent months trying to get it up to scratch, and still have issues that I can't solve, currently working getting the mail server more secure, at the moment, I'm trying to get SPF records working, so I can continue on to get dmarc installed.
I've tried so many things that I'm now chasing myself around in circles and am getting no where, I'm hoping you guys can assist me.
Here is my current configuration files and mxtoolbox test results (Last night I finally got local reverse lookups working, but I don't know if is correct now, as per the mxtoolbox results).
IP addesses have been changed of course :)


 Mxtoolbox mail server response (last change was about 16 hours ago – current config)

  

         dmarc  safesec.com.au       DNS Record not found        ** not installed yet **

         mx     safesec.com.au       No DMARC Record found       ** not installed yet **

         spf    safesec.com.au       DNS Record not found        ** ?? **

         http   safesec.com.au       The underlying connection was closed: Could not establish trust relationship for the SSL/TLS secure channel. ([http://safesec.com.au](http://safesec.com.au)) ** site safesec.com.au does not exist so that’s fair enough I guess **

         dns    safesec.com.au       Local NS list does not match Parent NS list ** ?? **

         dns    safesec.com.au       Name Servers are on the Same Subnet ** only one name server explains this? **

         dns    safesec.com.au       SOA Expire Value out of recommended range (does it matter?

         smtp   mail.safesec.com.au  Reverse DNS is not a valid Hostname ** ?? maybe because 1.2.3.245 is safesecurity, not mail.safesec.com.au? **

  
  

  Server settings:

  Ubuntu 15.04 server IP address: 1.2.3.245 (local name: safesecurity)

       Hosting [www.safesecuritysytems.com.au]("http://www.safesecuritysytems.com.au") website

       Hosting postfix/courier? email server
     Hosting own DNS server

FYI, its an old version of Ubuntu, as at the moment I'm not confident in upgrading, I've upgraded by I think 2 versions recently by myself (yay for me :)), but stalled while getting other things working.

  
```

  named.conf.local

  //

  // Do any local configuration here
  //
  

  // Consider adding the 1918 zones here, if they are not used in your

  // organization
  //include "/etc/bind/zones.rfc1918";
  //
  // Do any local configuration here
  //
  

  // Consider adding the 1918 zones here, if they are not used in your

  // organization
  //include "/etc/bind/zones.rfc1918";
  
  zone "safesecuritysystems.com.au" {
          type master;
          file "/etc/bind/db.safesecuritysystems.com.au";

  };

  zone "safesec.com.au" {
          type master;
          file "/etc/bind/db.safesec.com.au";
  };
  zone "3.2.1.in-addr.arpa" IN {
       type master;

       file "/etc/bind/0.136.10.in-addr.arpa";

  };
  
  
  db.safesec.com.au
  ;
  ; BIND data file for local loopback interface

  ;

  $TTL    604800
  @       IN      SOA     safesec.com.au. root.safesec.com.au. (
                               13         ; Serial
                           604800         ; Refresh
                            86400         ; Retry
                          2419200         ; Expire

                           604800 )       ; Negative Cache TTL

  ;
  @       IN      NS      safesec.com.au.
  @    IN   MX   10 mail.safesec.com.au.
  @       IN      A       1.2.3.245
  @       IN      AAAA    ::1
  mail    IN      A       1.2.3.245

  www  IN   A    1.2.3.245

  simprocloud.com. IN TXT "v=spf1 +a:chi-web-01.simprocloud.com +include:_spf.google.com +a +mx ~all"
  safesec.com.au. IN   TXT  "v=spf1 a mx ~all"
  safesec.com.au. IN      SPF     "v=spf1 a mx ~all"
  mail.safesec.com.au. IN TXT "v=spf1 a mx ~all"
  mail.safesec.com.au. IN SPF "v=spf1 a mx ~all"
   

  db.safesecuritysystems.com.au

  ;
  ; BIND data file for local loopback interface
  ;
  $TTL    604800
  @       IN      SOA     safesecuritysystems.com.au. root.safesecuritysystems.com.au. (

                               11         ; Serial

                           604800         ; Refresh
                            86400         ; Retry
                          2419200         ; Expire
                           604800 )       ; Negative Cache TTL
  ;
  @       IN      NS      safesecuritysystems.com.au.

  @    IN   MX   10 mail.safesec.com.au.

  @       IN      A       1.2.3.245
  @       IN      AAAA    ::1
  www     IN      A       1.2.3.245
  mail IN   A    1.2.3.245
  r1      IN      A       1.2.3.254
  enterprise      IN      A       1.2.3.248

  nas     IN      A       1.2.3.170

  server  IN      A       1.2.3.208
  mobile  IN      A       1.2.3.208
  safeptz IN      A       1.2.3.203
  safe.test  IN   A    1.2.3.246
  enterprise.test IN   A    1.2.3.247

  safesec.com.au. IN   TXT  "v=spf1 a mx ~all"

  
   
  3.2.1.in-addr.arpa
  ;
  ; BIND data file for local loopback interface
  ;

  $TTL 604800

  @       IN SOA  safesec.com.au.  admin.safesec.com.au. (
                        3         ; Serial
                   604800         ; Refresh
                    86400         ; Retry
                  2419200         ; Expire

                   604800    ; Negative Cache TTL

  )

  ;
       IN   NS   safesec.com.au.
  245  IN   PTR  safesec.com.au.
  245  IN  PTR   mail.safesec.com.au.
  208  IN   PTR  safesecurity.safesec.com.au.
  

   
```

  Thank you in advance for any help or direction at all.

---

### Post by lisati on 2018-08-29
*Thread moved to **Server Platforms** for a better fit.* 

15.04 is way past it's end-of-life date, and keeping it updated with security patches is likely to be difficult.

---

### Post by johngreen2 on 2018-08-29
Thank you, I am aware - it took me a bit to upgrade to this point, just want to get this fixed first before continuing on...

---

### Post by darkod on 2018-08-29
IMHO... I admire your enthusiasm and that you got so far, but you shouldn't have even tried upgrading a version so old and out of support... Besides even if you reach 16.04 LTS, what is your plan? To keep it for X years more? Or upgrade to 18.04 LTS?

Your end result should be 18.04 LTS and since you still have a lot to get there, I suggest simply deploying a new clean 18.04 LTS and migrate the necessary data/config. DNS is fairly easy to migrate, web files should be too (unless using some special developed site), and mail is also rather easy in its basic form (if no special setups are present). Think about it...

Apart from the above, lets start with the easy part first...

1. You can delete and forget about the reverse zone 3.2.1.in-addr.arpa. Only the provider that actually owns that public range can control it. What ever you put in your BIND about it, is worthless to the world. Your local clients could use it, but is that what you want? Tell your provider to set up reverse DNS on that IP, with value that you choose to be your mail server FQDN. For example, mail.safesecurity.com.au. That way real public reverse DNS will work, and believe me, many mail servers would not even consider receiving mails from your server if it's reverse DNS does not match. Don't forget, you can use the same mail server for multiple domains, so no need to have a public mail.safesec.com.au. You can simply use mail.safesecurity.com.au as MX for both domains.

2. About the spf record, even though bind now seems to accept SPF type records, there are much more examples for TXT so I would stick to that. You don't need both. And as far as I know, you only set it up on the base domain (you don't need TXT record for mail.domain.com, only for domain.com):
```
safesec.com.au.   IN   TXT   "v=spf1 a mx ~all"
```

That would be your SPF for that domain, nothing else... Remove the rest. Similar for the other domain, only one TXT record to set up your spf.

Do this and then try putting it more directly and in short what do you need help with... Honestly I got little confused in the first post, too many things thrown in.

---

### Post by secooonder on 2019-05-01
Hello Darkod

i read your answer carefully.Your answer is very useful for me.But i want to ask two questions.
[COLOR=#000000]
1)
My mail server zone in bind server is ;

[/COLOR]```

[COLOR=#000000]*IN MX 10 xxx.abuse.com.tr.*[/COLOR]

[COLOR=#000000]*abuse.com.tr. IN TXT "v=spf1 a mx ip4:212.a.b.c -all"*[/COLOR]
[COLOR=#000000]*abuse.com.tr. IN SPF "v=spf1 a mx ip4:212.a.b.c -all"*[/COLOR]

```

My bind version is ; BIND 9.9.5-3ubuntu0.7-Ubuntu (Extended Support Version)

i tested mx toolbox.i took an error  "[COLOR=#333333][FONT=&amp]The DNS record type 99 (SPF) has been deprecated".
iclicked detail, and i saw

[/FONT][/COLOR]> 
[COLOR=#333333][FONT=&amp]More Information About Spf Record Deprecated[/FONT][/COLOR][SIZE=2][COLOR=#333333][FONT=&amp]Hostname has returned a SPF Record that has been deprecated
[/FONT][/COLOR][/SIZE][COLOR=#333333][FONT=&amp][SIZE=2]The use of alternative DNS RR types that was formerly supported during the experimental phase of SPF was discontinued in 2014. **SPF records must now only** be published as a DNS TXT (type 16) Resource Record (RR) [RFC1035]. See [RFC 7208]("https://tools.ietf.org/html/rfc7208") for further detail on this change.[/SIZE]
[SIZE=2]According to [RFC 7208]("https://tools.ietf.org/html/rfc7208") Section 3.1: During the period when SPF was in development, requirements for assigning a new DNS RR type were more stringent than they are today and support for the deployment of new DNS RR types was not deployed in DNS servers and provisioning systems. The end result was that developers of SPF discovered it was easier and more practical to follow the TXT RR type for S[/SIZE]
[/FONT][/COLOR]

[COLOR=#000000]i deleted abuse.com.tr. IN SPF "v=spf1 a mx ip4:212.a.b.c -all",and finally my zone file is;[/COLOR]


> 
[COLOR=#000000][I]IN MX 10 xxx.abuse.com.tr.
[/I][/COLOR]
[COLOR=#000000]*abuse.com.tr. IN TXT "v=spf1 a mx ip4:212.a.b.c -all"*[/COLOR]

[COLOR=#000000]And the i test mxtoolbox my mail server,i dont took an error.

[/COLOR][COLOR=#000000]But when i saw bind log ; i see ;[/COLOR]
[COLOR=#000000]"abuse.com.tr' found SPF/TXT record but no SPF/SPF record found, add matching type SPF record"

[/COLOR]Which one should i believe ? Which is true ?
[COLOR=#000000]
[/COLOR][COLOR=#000000]
2) Can the Dns server query to rdns itself.?
i did not define a zone related to the dns server itself.i only defined the rdns for mail server in my named server,&#305; have also defined a provider
[/COLOR]

---

