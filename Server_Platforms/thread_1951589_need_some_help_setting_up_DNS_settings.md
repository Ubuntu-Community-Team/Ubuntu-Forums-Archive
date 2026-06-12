---
title: "need some help setting up DNS settings"
date: 2012-04-02
forum: Server Platforms
---

### Post by 51B0RG on 2012-04-02
I have Ubuntu 11.10 running an apache2 web server. i have bind9 installed for dns. I have followed many different tutorials on how to setup dns but i can't seem to get it right specifically for my details.

could someone either set it up for me via SSH or i can pm you my details and can make the file information for me.

I used to run an admin panel that made DNS a lot easier but after a few days apache won't start so i'm no longer using it. it was callec ISPConfig 3.


Cheers!
-Andrew

---

### Post by rubylaser on 2012-04-02
Why don't you post your config and ask for help?  Since, you are going to be responsible for this and managing it in the future, it would be much better to understand how / why Bind works than to just have someone do it for you.  When something goes awry, or you'd like a change, you wouldn't have a clue what to do.

---

### Post by 51B0RG on 2012-04-02
ok, but my problem is mainly i'm not 100% sure im using the correct information.

my IP address is 98.237.188.138 it has been publicly used before i don't care that much about it being in the open.
*NOT behind a router

The isp domain for it is c-98-237-188-138.hsd1.wa.comcast.net

the domain i am attempting to use is subaveragegamers.com registered with godaddy.com

nameservers redirected through godaddy ns1.subaveragegamers.com and ns2.subaveragegamers.com



this is my current /etc/bindnamed.conf.local
```
zone "subaveragegamers.com" {
	type master;
        file "/etc/bind/db.subaveragegamers.com";
};
zone "188.237.98.in-addr.arpa" {
        type master;
        file "/etc/bind/db.98";
};

```

my Zone file
```
; BIND db file for subaveragegamers.com

$TTL 86400

@       IN      SOA     ns1.subaveragegamers.com.      d3xkn0w5.rocketmail.com. (
                        2012040301	; serial number YYMMDDNN
                        28800           ; Refresh
                        7200            ; Retry
                        864000          ; Expire
                        86400           ; Min TTL
			)

                NS      ns1.subaveragegamers.com. 
                NS      ns2.subaveragegamers.com. 

                MX      10 mail.subaveragegamers.com.


$ORIGIN subaveragegamers.com.

```

my Reverse zone file
```
;
; BIND reverse data file for local loopback interface
;
$TTL	604800
@	IN	SOA	ns1.subaveragegamers.com. d3xkn0w5.rocketmail.com. (
			      2		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ns1.
10	IN	PTR	ns1.subaveragegamers.com.

```

I also own the domains subaveragegamers.org, subaveragegamers.net and subaveragegamers.info i haven't looked into zoning these but i'm most likely just going to redirect them to the main .com domain

---

### Post by webservervideos on 2012-04-02
> **51B0RG said:**
> 

The isp domain for it is c-98-237-188-138.hsd1.wa.comcast.net

this is my current /etc/bindnamed.conf.local
```
zone "subaveragegamers.com" {
    type master;
        file "/etc/bind/db.subaveragegamers.com";
};
zone "188.237.98.in-addr.arpa" {
        type master;
        file "/etc/bind/db.98";
};

```my Zone file

**[COLOR=Sienna]perhaps you should name it 138.188.237.98,,, I think that would help a lot.[/COLOR]**

```
; BIND db file for subaveragegamers.com

$TTL 86400

@       IN      SOA     ns1.subaveragegamers.com.      d3xkn0w5.rocketmail.com. (
                        2012040301    ; serial number YYMMDDNN
                        28800           ; Refresh
                        7200            ; Retry
                        864000          ; Expire
                        86400           ; Min TTL
            )

                NS      ns1.subaveragegamers.com. 
                NS      ns2.subaveragegamers.com. 

                MX      10 mail.subaveragegamers.com.


$ORIGIN subaveragegamers.com.

```my Reverse zone file

_**[COLOR=Sienna]I usually use something like www or something else to signify more than just the mail and nameservers.[/COLOR]**_


```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@    IN    SOA    ns1.subaveragegamers.com. d3xkn0w5.rocketmail.com. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns1.
10    IN    PTR    ns1.subaveragegamers.com.

```I also own the domains subaveragegamers.org, subaveragegamers.net and subaveragegamers.info i haven't looked into zoning these but i'm most likely just going to redirect them to the main .com domain

the reverse should look more like this
[COLOR=Black]
126.135.204.199.in-addr.arpa.    IN      SOA [/COLOR](since your file name is not right, nor is the zone file listing right, thus the ip is never reversed)

that 10 by mail is not needed. in either file


So, I think your arpa is messed up....

---

### Post by 51B0RG on 2012-04-03
After doing what you said, altering the serials, messing with the names of the files (got confused but re-read and fixed)and restarting bind, I now have NOERROR when i dig the domain.

Thanks!

---

### Post by 51B0RG on 2012-04-03
now it is having a problem finding the domain.
when i use dig subaveragegamers.com i get noerror but when i attempt to connect via a web browser it can't find it.
i can still connect via the ip address though.

---

### Post by 51B0RG on 2012-04-03
i keep messing it up, i think it would be best if someone just set it up for me, because i keep getting it wrong and screwing it up.

---

