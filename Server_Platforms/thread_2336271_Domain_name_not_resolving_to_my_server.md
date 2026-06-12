---
title: "Domain name not resolving to my server"
date: 2016-09-06
forum: Server Platforms
---

### Post by inadaze on 2016-09-06
Hi all,
I am trying to setup my domain "jadedtonemusic.com" to resolve to my home ubuntu server.  I am using bind9.  I have setup the primary nameserver "ns1.jadedtonemusic.com" to run off the same physical server and a secondary nameserver "ns2.jadedtonemusic.com" to run at [www.namecheap.com](www.namecheap.com).  I have setup my dns settings from the domain company I bought my domain from to point to my two nameservers.  Likewise, I have setup bind to use these nameservers.  When I tests with dig, both nameservers resolve properly to their ip addresses but my domain never does.  I am sure it is a stupid mistake, but I have been trying to fix for a few days and I cannot see my mistake.  I welcome any possible advice.  thank you

Here are my configs:

db.192.222.156 reverse config
```
$ORIGIN 156.222.192.in-addr.arpa.
$TTL    604800
@       IN      SOA     ns1.jadedtonemusic.com. root.jadedtonemusic.com. (
                        20160838        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.jadedtonemusic.com.
@       IN      NS      ns2.jadedtonemusic.com.
10      IN      PTR     jadedtonemusic.com

```

db.jadedtonemusic.com forward config
```

$ORIGIN jadedtonemusic.com.
$TTL    604800
@       IN      SOA     ns1.jadedtonemusic.com. root.jadedtonemusic.com. (
                        20160910        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.jadedtonemusic.com.
@       IN      NS      ns2.jadedtonemusic.com.
;
@       IN      A       192.222.156.xx
ns1     IN      A       192.222.156.xx
ns2     IN      A       199.167.17.xx
```

named.conf.local
```
zone "jadedtonemusic.com" {
        type master;
        file "/etc/bind/db.jadedtonemusic.com";
        allow-transfer { 199.167.17.xx; };
        also-notify { 199.167.17.xx; };

};

zone "156.222.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192.222.156";
        allow-transfer { 199.167.17.xx; };
        also-notify { 199.167.17.xx; };
};
```

named.conf.options
```
options {
        directory "/var/cache/bind";

        forwarders {
                8.8.8.8;
                8.8.4.4;
        };

        allow-transfer {
        };

        dnssec-validation auto;
        recursion yes;
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { none; };
};

```

---

### Post by darkod on 2016-09-06
I don't know what you did at your registrar's control panel (where your domain is registered), but if that's your real domain you didn't set up the nameservers correctly. It doesn't report any nameservers for that domain.

```
C:\Users\darko>dig NS jadedtonemusic.com

; <<>> DiG 9.10.3-P2 <<>> NS jadedtonemusic.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 7262
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;jadedtonemusic.com.            IN      NS


;; Query time: 4052 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Tue Sep 06 21:25:07 Romance Daylight Time 2016
;; MSG SIZE  rcvd: 47
```

So, start to troubleshoot there first. And try dig from another machine, not the very same dns servers. If you use it on the same server it might be resolving locally, not globally. You need to test from the internet.

---

### Post by inadaze on 2016-09-06
Here is my configuration of my domain (not that this will be very helpful I assume):

[ATTACH=CONFIG]271009[/ATTACH]

I contacted them to make sure there are not issues.

---

### Post by darkod on 2016-09-06
Hmmm, it's strange that it lets you enter host names too. Usually it would ask only for IPs of two or more nameservers. And then the hosts of that domain are on those nameservers. Anyway it seems you will have to wait for their reply...

---

### Post by Habitual on 2016-09-07
```
dig jadedtonemusic.com  @ns1.jadedtonemusic.com +short
dig: couldn't get address for 'ns1.jadedtonemusic.com': not found

host ns1.jadedtonemusic.com
Host ns1.jadedtonemusic.com not found: 2(SERVFAIL)

host ns2.jadedtonemusic.com
Host ns2.jadedtonemusic.com not found: 2(SERVFAIL)
```

Likely just needs an A Record for each ns host.

---

### Post by SeijiSensei on 2016-09-07
The SOA for the reverse domain is also wrong.  It should read:

```
@       IN      SOA   156.222.192.in-addr.arpa. root.jadedtonemusic.com. (
```

However it's highly unlikely that you have control over the 156.222.192.in-addr.arpa domain.  Those are almost always managed by the ISP.

---

### Post by inadaze on 2016-09-07
Darkod,
It appears that the issue is indeed with my nameservers.  Support at my registrar says that my hostnames are invalid as they are not returning any NS records. I am not sure how to fix that as I have defined NS records in my config.  Is there a mistake in them?

Habitual,
I thought I had also listed A records for my nameservers in my config.  Have I made a mistake there?

Thanks for your help!
Jason

---

### Post by darkod on 2016-09-07
Yes, your forward zone has an important error. I missed that the first time.
```
@       IN      SOA     ns1.jadedtonemusic.com. root.jadedtonemusic.com. (
```

should be:
```
@       IN      SOA jadedtonemusic.com. root.jadedtonemusic.com. (
```

You need the specify the domain name in the SOA, not the dns server. Except for that I see no other errors.

I assume udp port 53 is allowed in any firewall protecting your dns servers? And the port is forwarded if the servers are not with public IP.

---

### Post by inadaze on 2016-09-09
Unfortunately, even with the changes mentioned made, I am not able to get a response for dig jadedtonemusic.com.  

Question: Are my nameservers set up properly?  dig ns1.jadedtonemusic.com and dig ns2.jadedtonemusic.com respond with A records?  Is that correct or should they be responding with NS records?

cheers,
Jason

---

### Post by darkod on 2016-09-09
What did you do? The dig NS was working and now it's not... You made some change, to the worse...

Can you please post the actual forward zone file and also after every change in it you are restaring the bind service right?

---

### Post by inadaze on 2016-09-09
Damn...  I made two modifications.

1. I modified db.192.222.156 as SeijiSensei suggested (replaced the ns1.jadedtonemusic.com. for 156.222.192.in-addr.arpa. in the SOA record)
2. I modified db.jadedtonemusic.com as darkod suggested (replacing the ns1.jadedtonemusic.com. for jadedtonemusic.com. in the SOA record)
and updated the serial of each file and restarted bind.

My forward zone definition was in my first post.  Am I missing additional configurations?  Do I need a zone definition for my nameserver?

---

### Post by darkod on 2016-09-09
First lets try to configure the basics, adjust it to these instructions: [https://help.ubuntu.com/lts/serverguide/dns-configuration.html](https://help.ubuntu.com/lts/serverguide/dns-configuration.html)

1. Forget about the reverse zone right now, you can't control it. We can explain it later, lets focus on more important things right now.
2. The /etc/bind/named.conf.local on the primary and the secondary server should not be identical. You posted only one copy in post #1 so I assume you made it identical. If you read carefully the link I posted above, it shows the difference between primary and secondary server:
On the primary the named.conf.local should be:
```
zone "jadedtonemusic.com" {
   type master;
   file "/etc/bind/db.jadedtonemusic.com";
   allow-transfer { 199.167.17.xx; };
};
```
On the secondary the named.conf.local should be:
```
[FONT=Verdana]zone "jadedtonemusic.com" {
[/FONT][FONT=Verdana]   type slave;
[/FONT][FONT=Verdana]   file "/etc/bind/db.jadedtonemusic.com";
[/FONT][FONT=Verdana]   masters { 192.222.156.xx; };
[/FONT][FONT=Verdana]};[/FONT]
```
3. Delete both forward and reverse zone file on the secondary server, it will create its own from the primary replication.

4. On the primary server make the forward zone file content:
```
$TTL    604800
@       IN      SOA     jadedtonemusic.com. root.jadedtonemusic.com. (
                        20160910        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.jadedtonemusic.com.
@       IN      NS      ns2.jadedtonemusic.com.
;
@       IN      A       192.222.156.xx
www     IN      A       192.222.156.xx
ns1     IN      A       192.222.156.xx
ns2     IN      A       199.167.17.xx
```

5. Restart bind on both servers. First the primary, after that the secondary. Don't forget to modify the serial on the primary.

After that test from outside (the internet) and also post here that you have done the changes so we can test too.

With the modification I told you to make in the forward zone I think it briefly worked. The modification of the reverse zone is not very relevant because like Sensei already said, the IPs are not yours to control. Later about that.

Try this...

---

### Post by inadaze on 2016-09-14
I seem to be still in the same boat - although I believe my nameservers are working properly again.  I am starting to wonder if the issue stems from my second nameserver.  I am using a service called Cheapnames.com.  I do not have access to the actual bind/named config files.  they only supply me with a UI that allows me to enter a domain with an IP address and it will act as my secondary nameserver.  As I only have one server in my possession, I am only able to configure one nameserver for my domain.  Do you have any suggestions on services which would allow me create a second nameserver?  Am I suppose to have some zone configuration on my nameserver/domain server that describes the second nameserver other than what I already have?

my secondary nameserver has jadedtonemusic.com 192.222.187.xx configured

I will supply my current server configs :

db.192
```
$TTL    604800
@       IN      SOA     ns1.jadedtonemusic.com. root.jadedtonemusic.com. (
                        20160841        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.
@       IN      NS      ns2.
10      IN      PTR     ns1.jadedtonemusic.com.
```

db.jadedtonemusic.com
```
$TTL    604800
@       IN      SOA     jadedtonemusic.com. root.jadedtonemusic.com. (
                        20160913        ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.jadedtonemusic.com.
@       IN      NS      ns2.
;
@       IN      A       192.222.156.xx
www     IN      A       192.222.156.xx
ns1     IN      A       192.222.156.xx
ns2     IN      A       199.167.17.xx
```

named.conf.local
```
zone "jadedtonemusic.com" {
        type master;
        file "/etc/bind/db.jadedtonemusic.com";
        //add secondary master
        allow-transfer { 199.167.17.xx; };

};

zone "156.222.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192";
        allow-transfer { 199.167.17.xx; };
};
```

named.conf.options
```
options {
        directory "/var/cache/bind";

        forwarders {
                8.8.8.8;
                8.8.4.4;
        };

        allow-transfer {
        };

     
        dnssec-validation auto;
        recursion yes;
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { none; };
};

```

---

### Post by darkod on 2016-09-14
Hmmm, if you don't control fully the second nameserver then I think it's pointless to try setting them up in master-slave configuration. Probably the second nameserver will not be allowed to replicate the data from the first one. In such case they will both act as "main" servers and you would have to do all changes manually in both.

So, on the first server in named.conf.local try deleting the allow-transfer parameter unless you are sure the second server accepts the transfer.

If your registrar allows you to put only one nameserver for the domain, I would try that first. Set your server to be the only nameserver for the domain and check if it's working as expected. Just as simple stand-alone master, no secondary servers, nothing...

There is something wrong in the setup, right now dig from my end doesn't show any nameservers for your domain or any records for ns1.jadedtonemusic.com and ns2.jadedtonemusic.com.

---

### Post by inadaze on 2016-09-15
Unfortunately, my domain registrar requires 2 nameservers.  I will try figuring out another way to get a secondary nameserver and try from there.

Thanks Darkod.  I'll update you when I have knews (hopefully with good news).

---

