---
title: "DNS - domain name doesn't work"
date: 2014-03-30
forum: Server Platforms
---

### Post by jacksmith on 2014-03-30
Hi, 

I'm using ubuntu 12.04 server + ISP config3 on a server call alpha.d132.com

I've create a first zone call for example d132.com with ns1.d132.com (and on the same server ns2.d132.com)
It's possible to ping d132.com & ns1.d132.com from anywhere.
d132.com is also working


Then, I've create another zone : fixxxx.com and tell it that ns is ns1.d132.com.


When login on the server alpha.d132.com, it's possible to ping fixxxx.com.
Yet, from outside, it's not possible to ping fixxxx.com ....

Does somebody have an idea ???

I've search and search again during hours :-(

Thanks in advance.

---

### Post by SeijiSensei on 2014-03-30
[Whois reports]("http://www.networksolutions.com/whois/results.jsp?domain=fixxxx.com") that fixxxx.com is registered to Bernd Christian of Munich.  However the nameservers that handle that domain are 

Name Server: BUY.INTERNETTRAFFIC.COM
Name Server: SELL.INTERNETTRAFFIC.COM

Are you Bernd Christian?  If so, you need to have the registrar change the nameservers.

---

### Post by jacksmith on 2014-03-30
Hi, I'm stupid, I put d132.com and fixxxx.com as example1.com & example2.com. 

Should be : 

I'm using ubuntu 12.04 server + ISP config3 on a server call alpha.exemple1.com

I've create a first zone call for example example1.com with ns1.example1.com (and on the same server ns2.example1.com)
It's possible to ping example1.com & ns1.example1.com from anywhere.
example1.com is also working


Then, I've create another zone : example2.com and tell it that ns is ns1.example1.com


When login on the server alpha.example1.com, it's possible to ping example2.com.
Yet, from outside, it's not possible to ping example2.com ....

Does somebody have an idea ???

---

### Post by jacksmith on 2014-03-30
Informations in files are :
**file /etc/bind/named.conf.local : **
> zone "example2.com" {
        type master;
        allow-transfer {none;};
        file "/etc/bind/pri.example2.com";
};

**file /etc/bind/pri.example1.com.err**
> $TTL        3600
@       IN      SOA     ns1.example1.com. somebody.gmail.com. (
                        2014032902       ; serial, todays date + todays serial #
                        7200              ; refresh, seconds
                        540              ; retry, seconds
                        604800              ; expire, seconds
                        86400 )            ; minimum, seconds
;

example1.com. 3600 A        xxx.xxx.xxx.xxx ; IP adress in the real file is ok
example1.com. 3600      MX    10   mail.example1.com.
example1.com. 3600      NS        ns1.example1.com.
example1.com. 3600      NS        ns2.example1.com.
mail 3600 A        xxx.xxx.xxx.xxx ; IP adress in the real file is ok
www 3600 A        xxx.xxx.xxx.xxx ; IP adress in the real file is ok


@ IN NS ns1.example1.com
ns1 IN A xxx.xxx.xxx.xxx; IP adress in the real file is ok

**file /etc/bind/pri.example1.com :**

> $TTL        3600
@       IN      SOA     ns1.example1.com. somebody.gmail.com. (
                        2014032901       ; serial, todays date + todays serial #
                        7200              ; refresh, seconds
                        540              ; retry, seconds
                        604800              ; expire, seconds
                        86400 )            ; minimum, seconds
;

example2.com. 3600 A        xxx.xxx.xxx.xxx ; IP adress in the real file is ok
example2.com. 3600      MX    10   mail.example2.com.
example2.com. 3600      NS        ns1.example1.com.
example2.com. 3600      NS        ns2.example1.com.
mail 3600 A        xxx.xxx.xxx.xxx ; IP adress in the real file is ok
www 3600 A        xxx.xxx.xxx.xxx ; IP adress in the real file is ok


---

