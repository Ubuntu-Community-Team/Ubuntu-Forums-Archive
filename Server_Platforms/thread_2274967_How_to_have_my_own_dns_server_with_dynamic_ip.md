---
title: "How to have my own dns server with dynamic ip"
date: 2015-04-23
forum: Server Platforms
---

### Post by rhandy2 on 2015-04-23
I´m trying to do one litle dns server

I don´t have fixed Ip Adrress, I use afraid.org Dynamic DNS. "You could say !!! Why You don´t put all domains in afraid??? Because have free limits"

Ok first thing I try, I register 2 free domains for testing.

One I put directly on afraid
[TABLE="align: center"]
[TR]
[TD="colspan: 4"]10 subdomains
[/TD]
[/TR]
[TR]
[TD="colspan: 4"]
[TABLE="width: 100%"]
[TR]
[TD]domainteste123.tk
[/TD]
[TD][[ add ]]("http://freedns.afraid.org/subdomain/edit.php?edit_domain_id=1081804")
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][domainteste123.tk]("http://freedns.afraid.org/subdomain/edit.php?data_id=14329075") (**G**)
[/TD]
[TD]A
[/TD]
[TD]88.114.119.171
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][domainteste123.tk]("http://freedns.afraid.org/subdomain/edit.php?data_id=14329073") (**G**)
[/TD]
[TD]MX
[/TD]
[TD]10:domainteste123.tk
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][dns1.domainteste123.tk]("http://freedns.afraid.org/subdomain/edit.php?data_id=14330003") (**G**)
[/TD]
[TD]A
[/TD]
[TD]88.114.119.171
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][dns2.domainteste123.tk]("http://freedns.afraid.org/subdomain/edit.php?data_id=14330007") (**G**)
[/TD]
[TD]A
[/TD]
[TD]88.114.119.171
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][ftp.domainteste123.tk]("http://freedns.afraid.org/subdomain/edit.php?data_id=14329199") (**G**)
[/TD]
[TD]CNAME
[/TD]
[TD]domainteste123.tk
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][ftp2.domainteste123.tk]("http://freedns.afraid.org/subdomain/edit.php?data_id=14329998") (**G**)
[/TD]
[TD]A
[/TD]
[TD]88.114.119.171
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][mail.domainteste123.tk]("http://freedns.afraid.org/subdomain/edit.php?data_id=14329072") (**G**)
[/TD]
[TD]CNAME
[/TD]
[TD]domainteste123.tk
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][ns1.domainteste123.tk]("http://freedns.afraid.org/subdomain/edit.php?data_id=14329999") (**G**)
[/TD]
[TD]CNAME
[/TD]
[TD]dns1.domainteste123.tk
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][ns2.domainteste123.tk]("http://freedns.afraid.org/subdomain/edit.php?data_id=14330011") (**G**)
[/TD]
[TD]CNAME
[/TD]
[TD]dns2.domainteste123.tk
[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][www.domainteste123.tk]("http://freedns.afraid.org/subdomain/edit.php?data_id=14329188") (**G**)
[/TD]
[TD]CNAME
[/TD]
[TD]domainteste123.tk
[/TD]
[/TR]
[/TABLE]

**[SIZE=3]AFTER I register other domain LIKE - MYNAME.TK and I put DNS server on registrar as [dns1.domainteste123.tk]("http://freedns.afraid.org/subdomain/edit.php?data_id=14330003") and [dns2.domainteste123.tk]("http://freedns.afraid.org/subdomain/edit.php?data_id=14330003")[/SIZE]**

$ttl 38400
myname.tk.       IN           SOA       myname.tk. nobody.myname.tk. (
                                               1429793530
                                               10800
                                               3600
                                               604800
                                               38400 )
myname.tk.       IN           NS          myname.tk.
myname.tk.       IN           A             88.114.119.171
[www.myname.tk]("http://www.myname.tk").          IN           A             88.114.119.171
ftp.myname.tk.               IN           A             88.114.119.171
ns1.myname.tk.              IN           A             88.114.119.171
ns2.myname.tk.              IN           A             88.114.119.171
ns1.myname.tk.              IN           NS          myname.tk
ns2.myname.tk.              IN           NS          ns2.myname.tk.
myname.tk.       IN           MX         10 mail.myname.tk.
mail.myname.tk.             IN           A             89.114.119.17


__________________________


**for security reasons, please understand, domains and Ip are not my real. but config is the same.**



[SIZE=3]IS POSSIBLE PUT THIS THINK WORK. ON MY LOCAL NETWORK IT WORKS. 

I DONT KNOW IF IS ONLY ONE QUESTION OF TIME FOR PROPAGATION OR IF IS NOT POSSIBLE DO THE THINGS ON THIS WAY.

OTHER QUESTION, IS HOW I CAN DYNAMIC UPDATE MY IP 89.114.119.17 ON DNS CONFIG[/SIZE]

LIKE TODAY IS
 myname.tk.       IN           A             88.114.119.171

WHEN IP CHANGE 

myname.tk.       IN           A             88.114.119.172

IF i CAN USE ONE VARIABLE LIKE  IN PHP 
> $ip = getenv('HTTP_CLIENT_IP')?:
getenv('HTTP_X_FORWARDED_FOR')?:
getenv('HTTP_X_FORWARDED')?:
getenv('HTTP_FORWARDED_FOR')?:
getenv('HTTP_FORWARDED')?:
getenv('REMOTE_ADDR');

and make some like

```
myname.tk.       IN           A             $ip

```

---

### Post by rhandy2 on 2015-04-23
Ok! 

First thing! Configuration Works!!!:guitar: Is just a Time for propagation!

Second, How I can update dinamic update Bind conf???

---

### Post by rhandy2 on 2015-04-24
After lots of google search s And some hours trying I finaly found one solution.

**Dynamic DNS updates with nsupdate and BIND 9**

   
  I first saw nsupdate mentioned on the devops-toolchain mailing list as a  tool for dynamically updating DNS zone files from the command line.  Since this definitely beats manual editing of zone files, I'd thought  I'd give it a try. My setup is BIND 9 on Ubuntu 10.04. I won't go into  the details of setting up BIND 9 on Ubuntu -- see a good article about  this [here]("https://help.ubuntu.com/community/BIND9ServerHowto").

It took me a while to get nsupdate to work. There are lots of resources  out there, but as usual it's hard to separate the grain from the chaff.  When everything was said and done, the solution was relatively simple.  Here it is.

**Generate [TSIG]("http://www.bind9.net/manual/bind/9.3.2/Bv9ARM.ch04.html#tsig") keys**

[FONT=Courier New][COLOR=black]# [/COLOR][COLOR=black]dnssec-keygen [/COLOR][COLOR=black]-r /dev/urandom [/COLOR][COLOR=black]-a HMAC-MD5 -b 512 -n HOST myzone.com[/COLOR][/FONT]

 [COLOR=black][FONT=Arial]
[/FONT][/COLOR]
  [COLOR=black][FONT=Arial]This generates 2 files of the form:[/FONT][/COLOR]
  [FONT=Arial]
[/FONT][FONT=Courier New][COLOR=black]-rw-------   1 root bind   122 2012-03-21 15:47 Kmyzone.com.+157+02058.key[/COLOR]
[COLOR=black]-rw-------   1 root bind   229 2012-03-21 15:47 Kmyzone.com.+157+02058.private[/COLOR][/FONT]
  [COLOR=black][FONT=Arial]
[/FONT][/COLOR]
  [COLOR=black][FONT=Arial]Note that I specified /dev/urandom as the source of randomness, which may not meet your security requirements. When I didn't specify the -r /dev/urandom parameter, the dnssec-keygen command appeared to hang.[/FONT][/COLOR]
  [COLOR=black][FONT=Arial]
[/FONT][/COLOR]
  [COLOR=black][FONT=Arial]Also note that the type of the key needs to be HOST (specified via -n HOST). [/FONT][/COLOR]
  [COLOR=black][FONT=Arial]
[/FONT][/COLOR]
  [COLOR=black][FONT=Arial]**Add key to DNS master server configuration and allow updates**[/FONT][/COLOR]
  [COLOR=black][FONT=Arial]
[/FONT][/COLOR]
  [FONT=Arial]I modified /etc/bind/named.conf.local and added a 'key' section:[/FONT]
  [FONT=Arial]
[/FONT]
  [FONT=Courier New][COLOR=black]key "myzone.com." {[/COLOR]
[COLOR=black]  algorithm hmac-md5;[/COLOR]
[COLOR=black]  secret "JKlA76FvmGboEQ8R2yoc9AtpFqkIncH5yf2mXY+s8m6a/RRC0thUVGnqrJSO1QKhzlnkbxTjmArap+WuVW9iLQ==";[/COLOR]
[COLOR=black]};[/COLOR][/FONT]
  [FONT=Arial]
[/FONT]
  [FONT=Arial]The key name can be anything you want. The secret is the actual key, which can be found in both of the files generated by dnssec-keygen.[/FONT]
  [FONT=Arial]
[/FONT]
  [FONT=Arial]I also added an allow-update directive to the zone that I wanted to modify via nsupdate. This is still in /etc/bind/named.conf.local:[/FONT]
  [FONT=Arial]
[/FONT]
  [FONT=Courier New]zone "myzone.com" {[/FONT]
   [FONT=Courier New][COLOR=black]        type master;[/COLOR]
[COLOR=black]        file "/var/lib/bind/myzone.com.db";[/COLOR]
[COLOR=black]        allow-update { key "myzone.com."; };[/COLOR]
[COLOR=black]};


After this I found this script

```
#!/bin/bash

# Servers: http://dynupdate.no-ip.com/ip.php, http://www.antedes.com/getip.php, ..?
# Less straifghtforward: http://checkip.dyndns.org/, ...
IPS=http://dynupdate.no-ip.com/ip.php

DNSP=/home/nuno
while true; do

# First, retrieve IP address
CURIP=`curl -s $IPS | awk '{ print $1 }'`
OLDIP=`cat $DNSP/oldip`

# Compare to previously saved IP
[ "$CURIP" == "$OLDIP" ] && continue
echo $CURIP > $DNSP/oldip

# If different, tell DNS
echo "server MYDOMAIN.COM" > $DNSP/MYDOMAINZONEUPDATE.txt
echo "zone MYDOMAIN.COM" >> $DNSP/MYDOMAINZONEUPDATE.txt
echo "update delete MYDOMAIN.COM A" >> $DNSP/MYDOMAINZONEUPDATE.txt
echo "update add MYDOMAIN.COM 14400 A $CURIP" >> $DNSP/MYDOMAINZONEUPDATE.txt


/usr/bin/nsupdate -k KMYDOMAIN.COM.tk.XXXXXXX.private -v MYDOMAINZONEUPDATE.txt


# Sleeeeeeep I tell you
# 1800 = 30 minutes
#sleep 1800
done
```


I dont know why this script is very very slow. some times give error, "could not read rdata".

If I comment
#[FONT=Courier New][COLOR=black]/usr/bin/nsupdate -k KMYDOMAIN.COM.tk.XXXXXXX.private -v MYDOMAINZONEUPDATE.txt

Script save the file [FONT=Courier New][COLOR=black][FONT=Courier New][COLOR=black]MYDOMAINZONEUPDATE.txt,

AND AFTER BY HAND I EXECUTE
[FONT=Courier New][COLOR=black][FONT=Courier New][COLOR=black]/usr/bin/nsupdate -k KMYDOMAIN.COM.tk.XXXXXXX.private -v MYDOMAINZONEUPDATE.txt


Is must faster.

[B]Anyone could help me do some script better.
[/B]
Thanks.[/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT]

[/COLOR][/FONT]

---

### Post by amerinde on 2015-04-24
i also use afraid.. but i go through a router. I also bought my own name.

Doesnt matter where u get them from, just link the name(where u got them) in your admin page. To the 4 afraid dns servers. i deleted all the others that were auto set up.

If you are using a router, hopefully it has DaynamicDNS updating.  Many  routers allow only default servers, but some allow a user to configure it..  pick USER defined.

first you must allow DNS updates in the router.

then for the update URL... freedns.affraid.org
domain name.. (of coarse) is your domain name.. [www.your.domain](www.your.domain)
then it probably wants your user name and password to access the domain, so inter it accordingly.

note... you also have to open the ports you want to access to the pc/server u want to use
also, for my domain, i dont use [www.my.name](www.my.name) only my.name   (so try both ways)

---

### Post by rhandy2 on 2015-04-24
Hello

I know that, but isn´t I want.
I want have my own dns server. I can had multiple domains on it, And Have just one in Afraid.

---

### Post by amerinde on 2015-04-24
are u connected direct to the internet or through a router

btw, afraid also gives you the option to make a dns server under your own name

but your router, if you have one, must allow access to the ports

---

### Post by rhandy2 on 2015-04-24
I connect throught router! I have ports open. Only I dont know How I can make Dns in Afraid.

---

### Post by rhandy2 on 2015-04-25
Ok I write other script using nsuptade. And its working Good!

---

### Post by andrei29 on 2016-02-12
I think that you might try to have a sub-domain with a NS record on afraid for example [ns111.chickenkiller.com]("http://freedns.afraid.org/subdomain/edit.php?data_id=15651711") and this will be registered to TLD and will point on you name server (that will be authoritative for you actual TLD domain or domains). You name server will have dynamic IP address and will be updated with nsupdate or afraid utility on [ns111.chickenkiller.com]("http://freedns.afraid.org/subdomain/edit.php?data_id=15651711") (in my exemple).
 
Tell me if it make any sense what I wrote :)

---

