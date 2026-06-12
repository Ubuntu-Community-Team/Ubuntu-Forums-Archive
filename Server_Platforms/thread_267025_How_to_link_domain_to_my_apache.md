---
title: "How to link domain to my apache?"
date: 2006-09-28
forum: Server Platforms
---

### Post by Josh1 on 2006-09-28
Hi,
I bought a domain a couple of months ago from dynadot.com. Now I want to setup a dnsserver/nameserver on my ubuntu, so I can then link my domain to my ubuntu box, setup subdomains for myself and such.
Cept, I have no idea how to do this :(.
Could anyone link me toa  guide on how to do this?
Thanks,
Josh

---

### Post by quad3d@work on 2006-09-28
[SIZE=4]**I am under assumption you have a static IP!**[/SIZE]

```
ifconfig
```Write down your NIC IP. For this example: 111.222.333.321.

```
cat /etc/hostname
```Write this down as well. This is your 'hostname'.

Have dynadot.com register your nameserver. Not sure if they have on-line panel that allows you to do that... usually you have to call or email. Just have them register a nameserver with the IP you jogged down to "dns1.domain.tld" (Of course, replace domain.tld with your domain name). Also tell them to create a DNS PTR record for you as well (PTR is kind of... optional... usually you can get by without it).

```
sudo apt-get install bind9
```Above installs BIND DNS server. djsbdns is also another good choice, but BIND is a bit more human-readable IMO. If you want to use djbdns I can help you set that up too.

```
nano /etc/bind/named.conf.local
```Edit above file and insert what's below into it.
```

zone "[COLOR=Red]domain.tld[/COLOR]" {
        type master;
        file "/etc/bind/zones/[COLOR=Red]YOURDOMAIN.COM[/COLOR].db";
};
zone "[COLOR=Red]333.222.111[/COLOR].in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.[COLOR=Red]333.222.111[/COLOR].in-addr.arpa";
};

```Replace domain.tld and YOURDOMAIN.COM with your registered domain name. Replace 333.222.111 with first three octet of your IP you wrote down in first step but in reverse order.

```
mkdir /etc/bind/zones
```This is where all your BIND domains configuration files will reside.

```
nano /etc/bind/zones/rev.[COLOR=Red]333.222.111[/COLOR].in-addr.arpa
```And insert the following... (Replace 333.222.111 again)
```

;
; [COLOR=Red]domain.tld[/COLOR] reverse-lookup
;
[COLOR=Red] 333.222.111[/COLOR].in-addr-arpa. IN      SOA     dns1.[COLOR=Red]doamin.tld[/COLOR]. admin.[COLOR=Red]domain.tld[/COLOR]. (
                        2006091901      ; Serial no., based on date
                        21600           ; Refresh after 6 hours
                        3600            ; Retry after 1 hour
                        604800          ; Expire after 7 days
                        3600            ; Minimum TTL of 1 hour
)
[COLOR=Red] 321[/COLOR]                     IN      PTR     [COLOR=Red]YOURHOSTNAME[/COLOR]
@                       IN      NS      dns1.[COLOR=Red]doamin.tld[/COLOR].

```Replace 333.222.111 with first three octet of your IP again but in reverse order. Replace domain.tld with your domain name. Replace YOURHOSTNAME with hostname you wrote down earlier. Replace 321 with last octet of your actual IP.

```
nano /etc/bind/zones/[COLOR=Red]domain.tld[/COLOR]
```Make your domain zone file and insert the following...
```

;
; [COLOR=Red]domain.tld[/COLOR]
;
[COLOR=Red] domain.tld[/COLOR].             IN      SOA     dns1.[COLOR=Red]domain.tld[/COLOR]. admin.[COLOR=Red]domain.tld[/COLOR]. (
                        2006091901      ; Serial no., based on date
                        21600           ; Refresh after 6 hours
                        3600            ; Retry after 1 hour
                        604800          ; Expire after 7 days
                        3600            ; Minimum TTL of 1 hour
)
[COLOR=Red] YOURHOSTNAME[/COLOR]        IN      A       [COLOR=Red]111.222.333.321[/COLOR]
dns1                  IN      CNAME    @
www                   IN      CNAME   @
ftp                     IN      CNAME   @
mail                    IN      CNAME   @
@                       IN      NS      dns1.[COLOR=Red]domain.tld[/COLOR].

```Replace domain.tld with your domain name. Replace 111.222.333.321 with your IP address you wrote down. Replace YOURHOSTNAME with your hostname.

```
/etc/init.d/bind9 restart
```Restarts BIND DNS server to read your configuration/zone files.

Pray dynadot.com registers your nameserver fast and wait few hours before the world gets populated with your DNS records.

---

### Post by bluefrog on 2006-09-28
you could have a look at [http://tldp.org/](http://tldp.org/) and search their site for dns

James

---

### Post by isme_tze on 2006-09-28
Hi, 

I am also having some problem with my DNS setting too. I followed the same as what you suggested but the dig command return "status: SERVFAIL". The dnsstuff.com return "Server failure.  There's a problem with the DNS server for my-domain.com.au"

I got one static IP from my ISP (used on netgear router) and configure the router to forward all the dns tracfic (port 53) to my server.

I got a static IP (111.222.333.123) and domain name (example.com.au) from different isp. my server (call server) is installed as DNS, Apache, FTP, and Mail server with an internal IP 192.168.0.4, and my question is:
1. do i have to ask my isp and dns provider to do some setting on their dns server?
2. in the zone file, which ip should use? the internal or the external?
3. do i have to configure the dns forwarder ip address? if yes which one should i use? the dns provider or isp provider?

I really need help in this. Thank you in advance.

Regards
Tze

---

### Post by Josh1 on 2006-09-28
> **quad3d@work said:**
> [SIZE=4]**I am under assumption you have a static IP!**[/SIZE]

```
ifconfig
```Write down your NIC IP. For this example: 111.222.333.321.

```
cat /etc/hostname
```Write this down as well. This is your 'hostname'.

Have dynadot.com register your na/etc/init.d/bind9 restartmeserver. Not sure if they have on-line panel that allows you to do that... usually you have to call or email. Just have them register a nameserver with the IP you jogged down to "dns1.domain.tld" (Of course, replace domain.tld with your domain name). Also tell them to create a DNS PTR record for you as well (PTR is kind of... optional... usually you can get by without it).

```
sudo apt-get install bind9
```Above installs BIND DNS server. djsbdns is also another good choice, but BIND is a bit more human-readable IMO. If you want to use djbdns I can help you set that up too.

```
nano /etc/bind/named.conf.local
```Edit above file and insert what's below into it.
```

zone "[COLOR=Red]domain.tld[/COLOR]" {
        type master;
        file "/etc/bind/zones/[COLOR=Red]YOURDOMAIN.COM[/COLOR].db";
};
zone "[COLOR=Red]333.222.111[/COLOR].in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.[COLOR=Red]333.222.111[/COLOR].in-addr.arpa";
};

```Replace domain.tld and YOURDOMAIN.COM with your registered domain name. Replace 333.222.111 with first three octet of your IP you wrote down in first step but in reverse order.

```
mkdir /etc/bind/zones
```This is where all your BIND domains configuration files will reside.

```
nano /etc/bind/zones/rev.[COLOR=Red]333.222.111[/COLOR].in-addr.arpa
```And insert the following... (Replace 333.222.111 again)
```

;
; [COLOR=Red]domain.tld[/COLOR] reverse-lookup
;
[COLOR=Red] 333.222.111[/COLOR].in-addr-arpa. IN      SOA     dns1.[COLOR=Red]doamin.tld[/COLOR]. admin.[COLOR=Red]domain.tld[/COLOR]. (
                        2006091901      ; Serial no., based on date
                        21600           ; Refresh after 6 hours
                        3600            ; Retry after 1 hour
                        604800          ; Expire after 7 days
                        3600            ; Minimum TTL of 1 hour
)
[COLOR=Red] 321[/COLOR]                     IN      PTR     [COLOR=Red]YOURHOSTNAME[/COLOR]
@                       IN      NS      dns1.[COLOR=Red]doamin.tld[/COLOR].

```Replace 333.222.111 with first three octet of your IP again but in reverse order. Replace domain.tld with your domain name. Replace YOURHOSTNAME with hostname you wrote down earlier. Replace 321 with last octet of your actual IP.

```
nano /etc/bind/zones/[COLOR=Red]domain.tld[/COLOR]
```Make your domain zone file and insert the following...
```

;
; [COLOR=Red]domain.tld[/COLOR]
;
[COLOR=Red] domain.tld[/COLOR].             IN      SOA     dns1.[COLOR=Red]domain.tld[/COLOR]. admin.[COLOR=Red]domain.tld[/COLOR]. (
                        2006091901      ; Serial no., based on date
                        21600           ; Refresh after 6 hours
                        3600            ; Retry after 1 hour
                        604800          ; Expire after 7 days
                        3600            ; Minimum TTL of 1 hour
)
[COLOR=Red] YOURHOSTNAME[/COLOR]        IN      A       [COLOR=Red]111.222.333.321[/COLOR]
dns1                  IN      CNAME    @
www                   IN      CNAME   @
ftp                     IN      CNAME   @
mail                    IN      CNAME   @
@                       IN      NS      dns1.[COLOR=Red]domain.tld[/COLOR].

```Replace domain.tld with your domain name. Replace 111.222.333.321 with your IP address you wrote down. Replace YOURHOSTNAME with your hostname.

```
/etc/init.d/bind9 restart
```Restarts BIND DNS server to read your configuration/zone files.

Pray dynadot.com registers your nameserver fast and wait few hours before the world gets populated with your DNS records.

Thanks alot man!
I have a router, so i put my computer ip (192.168.1.2/2.1.168.192) in the IP's right.
And hostname as josh, right?:-k 
And then the dns would be dns1.203.121.199.18 ? Will I need to forward any ports?
Thanks alot!
- Josh

---

### Post by chrisfay on 2006-09-28
If you're not familiar with Bind, [Webmin]("http://webmin.com") makes administering so much easier.....

---

### Post by quad3d@work on 2006-09-29
> **Josh1 said:**
> Thanks alot man!
I have a router, so i put my computer ip (192.168.1.2/2.1.168.192) in the IP's right.
And hostname as josh, right?:-k 
And then the dns would be dns1.203.121.199.18 ? Will I need to forward any ports?
Thanks alot!
- Josh

192.168.* is private addresses... so I guess you don't have static IP. We can do this 2 ways.

Log into your router and acquire the "external" IP, the one your ISP assigned to your router and change out accordingly to my instructions.

Or... use [http://zoneedit.com/](http://zoneedit.com/). I still uses Zoneedit for few of my domains, and it works quite well. Whenever you have an IP change it's faster with zoneedit to get the world to re-populate your new IP.

Oh, and for DNS server... IP address cannot be used. That's why you have to get your domain registrar to register a nameserver to IP for you. If your IP changes a lot this is going to be painful in future... just a warning.

---

### Post by quad3d@work on 2006-09-29
> **isme_tze said:**
> 
I got a static IP (111.222.333.123) and domain name (example.com.au) from different isp. my server (call server) is installed as DNS, Apache, FTP, and Mail server with an internal IP 192.168.0.4, and my question is:
1. do i have to ask my isp and dns provider to do some setting on their dns server?
2. in the zone file, which ip should use? the internal or the external?
3. do i have to configure the dns forwarder ip address? if yes which one should i use? the dns provider or isp provider?

I really need help in this. Thank you in advance.

Regards
Tze

1. No, if everything is setup correctly their DNS server will automatically cache your DNS server.

2. For less painful setup I recommend you put your server in DMZ in your router. But yea... you want to use external IP. I have feeling that DNS would not work w/o DMZ, I could be wrong.

3. You don't need to set up forwarder DNS IP. From what I understand forwarder is for replications and stuff.

Now my question is... did you have the company who registered example.com.au for you register a nameserver for you? Have them register dns1.example.com.au to static IP "111.222.333.123" for you.

Servfail means no DNS servers anywhere in the world have your domain records. Also could meaning something on your side is setup wrong.

---

### Post by Josh1 on 2006-09-29
> **quad3d@work said:**
> 192.168.* is private addresses... so I guess you don't have static IP. We can do this 2 ways.

Log into your router and acquire the "external" IP, the one your ISP assigned to your router and change out accordingly to my instructions.

Or... use [http://zoneedit.com/](http://zoneedit.com/). I still uses Zoneedit for few of my domains, and it works quite well. Whenever you have an IP change it's faster with zoneedit to get the world to re-populate your new IP.

Oh, and for DNS server... IP address cannot be used. That's why you have to get your domain registrar to register a nameserver to IP for you. If your IP changes a lot this is going to be painful in future... just a warning.

My external IP is static, hasn't changed (I love my ISP, they only offer static, and thats fine be me! :D), and my network IP is 192.168.1.2. This does not change either. :D.
And for the dynadot thing, I can set any name server etc, its very good, so would i just set it myself? (dns1.203.121.199.18?)
Thanks,
Josh
P.S: Thats alot for your help, i'm learning alot :D.

---

### Post by chrisfay on 2006-09-29
> And for the dynadot thing, I can set any name server etc, its very good, so would i just set it myself? (dns1.203.121.199.18?)

You can not register a nameserver using an IP. You need to create an ns1.subdomain.tld that points to your public IP 203.121.199.18. You will also, more than likely, have to create a second nameserver:

ns1.subdomain.tld
ns2.subdomain.tld

You can create them both pointing to your public ip. Although this defeats the purpose of having backup name servers due to them both being on the same IP/physical location, some registrars require two.

---

### Post by Johnsie on 2006-11-21
The easiest way is to use zoneedit.com and have your registrar point your domain to the zonedit nameserver.

This isn't exactly how it works but it'll give you an idea:
Webbrowser---->Zonedit--->Your IP


Zoneedit merely forwards the domain to your ip without you having to set up complex dns servers.

---

### Post by tturrisi on 2006-11-22
Dynadot.com
Domain Registration Highlights
  Low price of $7.99, registration & renewal
  Free domain parking
  Free domain forwarding, regular & stealth
  Free email forwarding (catch-all)
  Free basic dns, up to 3 subhosts & 3 MX records
  Free ownership changes
  Account management tools (screenshot

Use the Domain Forwarding service they provide, it's free.  No need for your own dns or bind.

---

