---
title: "Bind9 on a closed network"
date: 2011-09-27
forum: Server Platforms
---

### Post by jonobr on 2011-09-27
Hello there

I am working with a product that when it boots resolves an address that's hard-coded (1.pool.ntp.org)
When it resolves, it syncs its time via external ntp and boots properly.

I dont like that as I cant set this up on a closed network or if I am fire-walled.

I was thinking of having bind9 point to an NTP server I create - both of which will be on the one closed 'demo' network which has no external access.
I have been playing with bind 9 for some time now (which I haven't used a lot before) but Im getting no-where.

So is it possible to do this? Im guessing yes, but what is the best approach? 
Would it be to setup a zone called ntp.org and then have 
1.pool.ntp.org defined?

IS there an easier way to do this? I am hoping to make it as simple as possible, 

Ill post my current config below (gotten from [This link and others like it]("http://ubuntuforums.org/showthread.php?t=236093"),

Links welcome but if you want to look at the config I have at the moment its below (likely to change in the next few mins:-)

Cheers

jonobr

PS Apologies for the n00b bind9 question

test ntp= 192.168.1.222
test dns/dhcp/bind server=192.168.1.1 (hostname jabba)

named.local.conf

```
/etc/bind$ cat named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

#This is the zone definition inserted by me. replace example.com with your domain name

zone "ntp.org" {
type master;
file "/etc/bind/zones/ntp.org.db";
};

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0

zone "rev.1.168.192.in-addr.arpa." {
type master;
file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

```


Forward file

```
 
cat zones/ntp.org.db

$TTL    3d

ntp.org. IN SOA jabba.pool.ntp.org. admin.ntp.org. (
2007031001
28800
3600
604800
38400
)

ntp.org. IN NS jabba.pool.ntp.org.
ntp.org. IN MX 10 mail.ntp.org.

1       IN      A       192.168.1.222
2       IN      A       192.168.1.222

```


Reverse

```
cat zones/rev.1.168.192.in-addr.arpa
@ IN SOA jabba.pool.ntp.org. admin.ntp.pool.org. (
2007031001;
28800;
604800;
604800;
86400
)

IN NS jabba.pool.ntp.org.
1 IN PTR ntp.org
2 IN PTR ntp.org

```


resolv.conf

```
lumpy@jabba:/etc/bind$ cat /etc/resolv.conf
nameserver 192.168.1.1
search jabba.pool

```

---

### Post by SeijiSensei on 2011-09-27
That's way more work than required.

Just edit /etc/ntp.conf and add your local server's address above the ones already there.  

```

[...]
server 192.168.1.222
server 0.pool.ntp.org
server 1.pool.ntp.org
[etc.]

```

---

### Post by jonobr on 2011-09-27
Thanks for the response, 
the problem is the box thats issuing the dns request for ntp (1.pool.ntp.org) is hardcoded, I cant modify that piece,
The ubuntu server i placed on the same network has got bind9 and dns on it and is the only piece I can play around with

---

### Post by hawkmage on 2011-09-27
You should either change
```
zone "ntp.org"
```
to 
```
zone "pool.ntp.org"
```

or change the entries in the forward zone file to :
```
1.pool       IN      A       192.168.1.222 2.pool       IN      A       192.168.1.222
``` 

and the reverse zone to:
```
222 IN PTR 1.pool.ntp.org
```

---

### Post by brettg on 2011-09-28
Surely the simplest option is to put entries for whatever.ntp.org into the hosts file on the system in question?

---

### Post by SeijiSensei on 2011-09-28
> **brettg said:**
> Surely the simplest option is to put entries for whatever.ntp.org into the hosts file on the system in question?

That was my first reaction, but the OP says "the problem is the box that's issuing the dns request for ntp (1.pool.ntp.org) is hardcoded, I can't modify that piece."

Pretty silly design, if you ask me.

---

### Post by jonobr on 2011-09-28
hawkmage thanks for the tip, ill give that a whirl today

SeijiSensei/brettg thanks for replying,
I didn't really give enough info on the thing issuing the ntp request so Ill go into the detail here.

We make a box that integrates a piece of hardware from another company, 
This hardware is a product that has its own gui and provisioning system that allows you to configure it.

If it were a regular linux or windows based OS, adding entries to hosts files etc would be the best solution, and would be the one I would want, however, its not configurable in that way.
All the non needed ports are locked down (checked using nmap) so there doesnt seem to be a way of 'getting into' the box without going through the gui or the provisioning system.
The initial NTP setting is hard coded (which is silly) so I cant change it.


When the solution is put into a regular deployment, it will work fine with simple resolution against dns and sync its time as normal,(excluding any fire-walling,

Thats ok, but the problem  I see is that you cant demo to a entity or customer if you dont have internet access- or do field testing in the middle of nowhere as the hardware wont boot until it gets its ntp. 
There are ways around it eg by using a data stick to provide internet access. This assumes your going to have access to a carrier data network where you go which isnt always the case.

The solution I see it is two fold,
1- Short term, perform resolution myself and sync the thing off a local NTP server 
2- long term- ask the vendor company to allow NTP resolution to take place further down the road as timing is not critical for this solution. Thats going to take a while, and in the meantime I have to come up with the short term solution above.

I believe having this kind of resolution take place without the ability to change where it gets its ntp from is kind of goofy to me, but I still need to figure a solution,

Thanks all

---

### Post by jonobr on 2011-10-02
Ok

so I got to the bottom of it with a lot of work and a huge bit of "A FOR GOODNESS SAKE, WHY DIDNT I SPOT THAT!!!!"

:rolleyes:

After playing around for sometime and doing removes and reinstalls, config checks etc,
I discovered that somehow my /etc/bind/named.conf was empty.
It should have an include statement that points to the likes of named.conf.local

as soon as I added that, BANG.... ping nslookup dig and so on all worked a charm.

Thanks all for pitching in.

Jonobr

---

