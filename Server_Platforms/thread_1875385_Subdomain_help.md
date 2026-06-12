---
title: "Subdomain help"
date: 2011-11-04
forum: Server Platforms
---

### Post by richard.moreton on 2011-11-04
Hello, I am new to the forums and I have currently ran into some trouble with my server setup. Everything I setup works just fine(Apache2,php,mysql,ssh,ftp,bind9,etc.) but when I try to make my own subdomain it doesn't seem to work. I run my own server at home from a Dell Poweredge that I found in the garbage and repaired. It works rather decent so I decided to use it for my own use for my small business I am in the process of making. At the moment I am in the process of learning linux and how it works, got a pretty decent grasp on the commands now and a good handle on how to make things work except subdomains...

But to get to my actual problem I am having, I own the domain rawcomputertech.com and a few others that point to the same site(rawct.com,rawcomptech.com,rawcomputertechnologies.com) but I use rawcomputertech.com as my primary one. Anyways! Their hosted on [http://www.1and1.com](http://www.1and1.com) and they only allow 5 subdomains so I thought maybe I could just how my own through the same server my site is running on. I have tried countless times to get this working and I cannot seem to figure it out... Right now I am in the process of making a subdomain [http://scripts.rawcomputertech.com/](http://scripts.rawcomputertech.com/) which will point to a folder where I am going to test some of my scripts I am working on as I freelance Web development as well.

This is my current BIND9 configuration file for the [http://www.rawcomputertech.com](http://www.rawcomputertech.com) I don't think the other domain configuration files are relevant but if so I can post them.

```

;
; BIND data file for rawcomputertech.com
;
$TTL    604800
@       IN      SOA     rawcomputertech.com. root.rawcomputertech.com. (
                       11110412         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
rawcomputertech.com.    IN      NS      ns1.rawcomputertech.com.
rawcomputertech.com.    IN      MX      10      mail.rawcomputertech.com.
rawcomputertech.com.    IN      PTR     scripts.rawcomputertech.com.
rawcomputertech.com.    IN      A       192.168.1.169

www     IN      A       rawcomputertech.com.
ns1     IN      A       192.168.1.169
mail    IN      A       192.168.1.169
scripts IN      A       192.168.1.169

scripts.rawcomputertech.com.    CNAME   rawcomputertech.com.

```
As you can see I am also trying to setup a mail.rawcomputertech.com for my mail server and a nameserver but neither of them are working either. So I think once I figure this out I can get my others working as well. I think I can host my own nameservers correct? Anyways

Apache2 configuration:
```

<VirtualHost *:80>
        ServerAdmin richard.moreton@rawcomputertech.com

        ServerName scripts.rawcomputertech.com
        DocumentRoot /Path/To/Dir
        ServerAlias scripts.*

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /Path/To/Dir>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

Not sure what other file is relevant to figuring this out but let me know and I will post whatever information I have failed to post this time. Also here are the dig command outputs for the urls.

[http://www.rawcomputertech.com](http://www.rawcomputertech.com)
```


; <<>> DiG 9.7.3 <<>> rawcomputertech.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11616
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;rawcomputertech.com.           IN      A

;; ANSWER SECTION:
rawcomputertech.com.    85613   IN      A       24.210.92.67

;; Query time: 25 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Fri Nov  4 18:14:56 2011
;; MSG SIZE  rcvd: 53

```

[http://scripts.rawcomputertech.com](http://scripts.rawcomputertech.com)
```


; <<>> DiG 9.7.3 <<>> scripts.rawcomputertech.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 42202
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;scripts.rawcomputertech.com.   IN      A

;; AUTHORITY SECTION:
rawcomputertech.com.    3967    IN      SOA     ns51.1and1.com. hostmaster.1and1.com. 2011110201 28800 7200 604800 86400

;; Query time: 49 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Fri Nov  4 18:16:10 2011
;; MSG SIZE  rcvd: 103

```

Please let me know if you need any other information. Thanks in advanced for the help.

---

### Post by robvas on 2011-11-04
Just have 1and1 host your DNS, and point scripts.rawcomputertech.com to your servers IP address (create an A record in DNS)

---

### Post by richard.moreton on 2011-11-05
I can't do much via the 1and1 control panel it looks like this:
[IMG]http://www.rawcomputertech.com/1and1.png[/IMG]

I can change the Name Server from 1and1 name server to my name server it looks like this:

[IMG]http://www.rawcomputertech.com/1and1-2.png[/IMG]

and since I don't have my own name server not sure what to put in there? So I am unsure of how to add this record to my dns? Thanks.

---

### Post by richard.moreton on 2011-11-05
Well I just realized my domains work without BIND even running so I assume that's the reason why I cannot get sub-domains working? I think I have to set something on 1and1 but not sure what to set and where...? If I try to set the name server to my domain name then the URL becomes unreachable... So I guess my next question is, how do I setup my own name server to use on 1and1 and maybe then BIND may work correctly then I can setup my own sub-domains?

---

### Post by richard.moreton on 2011-11-07
Anyone..? Need some help setting this up please. Do I just set the name servers on 1and1 to my domain address since it points towards my ipaddress anyways? or where can I move my domains that would allow me to edit the records..? Thanks.

---

### Post by richard.moreton on 2011-11-17
Alright so... Since no one has answered me. I figured out my BIND9 problem and have gotten sub-domains working... But only internally. For some reason my domains resolve to 192.168.1.169 and not my public ip address... Any idea why? Do I have to edit my BIND9 zones and replace my private ip with my public one? or what...?

---

### Post by Jonathan L on 2011-11-18
> **richard.moreton said:**
> Alright so... Since no one has answered me. I figured out my BIND9 problem and have gotten sub-domains working... But only internally. For some reason my domains resolve to 192.168.1.169 and not my public ip address... Any idea why? Do I have to edit my BIND9 zones and replace my private ip with my public one? or what...?

Hi Richard

Unless you're doing it for the education or the branding, running DNS on your own servers is not the most rewarding of tasks: it's a lot of effort for very little business value.  And not necessarily even the best idea: most especially if you have only one connection to the internet, and most especially especially if your DNS server is on the same link as your services.  If you make a mistake you can easily saw off the branch you're sitting on., as you really need good connectivity to run DNS well.  Most ISPs run decent DNS, as do the domain suppliers and the DNS service companies, or AWS for $0.50/mo.

Nevertheless you might want to do it: it's your choice.  If you're giving technology advice it certainly puts your money where your mouth is.

I see you have your server working, and yes, it's delivering 192.168.1.169 private addresses.  To fix this you need to put your public addresses in your zonefile.  But you probably need to have the private addresses for your local LAN access to work: this is the "inside/outside problem", and perhaps you'll find my post about [Split DNS]("http://ubuntuforums.org/showpost.php?p=11458757&postcount=3") userful.

I'm confused because you say you're running bind but "I don't have my own name server": if you're running bind, you certain do have a name server.  Once you have it running satisfactorily you can change the delegation at 1&1.

NB: although technically you are absolutely correct in calling scripts.rawcomputertech.com a subdomain of rawcomputertech.com, most people would call it a host inside rawcomputertech.com. The word subdomain normally being used when you have a level of organisation like [www.europe.rawcomputertech.com]("http://www.europe.rawcomputertech.com") and [www.asia.rawcomputertech.com]("http://www.asia.rawcomputertech.com"), where europe and asia would subdomains of rawcomputertech.com and would typically be administered by different people in those regions: that's why you normally only see it for large companies, universities and so on.  In terms of resource records, the normal usage means that a host has an A record while a subdomain has NS records and quite probably an MX record.  If it has an SOA then it's a subzone because the person responsible for it is different from the person responsible for the parent domain.  Sometimes, usually for mail or web purposes, you put host records (A) on domains which have NS and SOA records: eg ubuntuforums.org.  When we speak of subdomains we are normally thinking about it from point of view of the parent domain: just like we only sometimes speak of directories as subdirectories -- obviously rawcomputertech.com must be a subdomain of com, and com is a subdomain of the root domain "." (called "dot").

Hope that helps: DNS can be confusing!  Let us know how you get on and if you need any further help.

Kind regards,
Jonathan.

---

### Post by richard.moreton on 2011-11-18
> **Jonathan L said:**
> Hi Richard

Unless you're doing it for the education or the branding, running DNS on your own servers is not the most rewarding of tasks: it's a lot of effort for very little business value.  And not necessarily even the best idea: most especially if you have only one connection to the internet, and most especially especially if your DNS server is on the same link as your services.  If you make a mistake you can easily saw off the branch you're sitting on., as you really need good connectivity to run DNS well.  Most ISPs run decent DNS, as do the domain suppliers and the DNS service companies, or AWS for $0.50/mo.

Nevertheless you might want to do it: it's your choice.  If you're giving technology advice it certainly puts your money where your mouth is.

I see you have your server working, and yes, it's delivering 192.168.1.169 private addresses.  To fix this you need to put your public addresses in your zonefile.  But you probably need to have the private addresses for your local LAN access to work: this is the "inside/outside problem", and perhaps you'll find my post about [Split DNS]("http://ubuntuforums.org/showpost.php?p=11458757&postcount=3") userful.

I'm confused because you say you're running bind but "I don't have my own name server": if you're running bind, you certain do have a name server.  Once you have it running satisfactorily you can change the delegation at 1&1.

NB: although technically you are absolutely correct in calling scripts.rawcomputertech.com a subdomain of rawcomputertech.com, most people would call it a host inside rawcomputertech.com. The word subdomain normally being used when you have a level of organisation like [www.europe.rawcomputertech.com]("http://www.europe.rawcomputertech.com") and [www.asia.rawcomputertech.com]("http://www.asia.rawcomputertech.com"), where europe and asia would subdomains of rawcomputertech.com and would typically be administered by different people in those regions: that's why you normally only see it for large companies, universities and so on.  In terms of resource records, the normal usage means that a host has an A record while a subdomain has NS records and quite probably an MX record.  If it has an SOA then it's a subzone because the person responsible for it is different from the person responsible for the parent domain.  Sometimes, usually for mail or web purposes, you put host records (A) on domains which have NS and SOA records: eg ubuntuforums.org.  When we speak of subdomains we are normally thinking about it from point of view of the parent domain: just like we only sometimes speak of directories as subdirectories -- obviously rawcomputertech.com must be a subdomain of com, and com is a subdomain of the root domain "." (called "dot").

Hope that helps: DNS can be confusing!  Let us know how you get on and if you need any further help.

Kind regards,
Jonathan.


Thank you that was very educational for me. I got it working and so far it seems to be working alright for all my domains except for rawcomputertech.com until it refreshes/updates. I did figure out that since I had bind I did have my own name server, thanks. I now have my domains primary name server point towards my name server and their secondary name server pointing to 1and1s name server. So far my sub domains work and everything is working alright. I enjoy being able to run my own things without having to worry about third party programs/services. I realize it can be a pain to run everything yourself but to me that is the only way to learn how things work and how to keep them working. I appreciate all the help.

Thanks!

---

### Post by Trismegister on 2012-05-31
Richard, would you be kind enough to list the steps you took -- from your first posting to successfully propagating the 'subdomains' from your own name server on your 1&1 hosted server. This would be tremendously helpful to me and others I am sure.

My bind9 zone file is - unsurprisingly - not unlike yours; the correct ports are open and syslog reports named (bind9) is running and that my secondary name servers (on XNames.org) are notified.. but my subdomains are not being propagated.

Many thanks!

---

