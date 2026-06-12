---
title: "BIND9 Help [Zone Files - Basic]"
date: 2010-04-10
forum: Server Platforms
---

### Post by Skidbladnir on 2010-04-10
I am moderately experienced with BASH, and somewhat with other Ubuntu services like Apache and ProFTPd, but not at all with BIND.

I have a subdomain from [http://co.cc/](http://co.cc/) , which allows me to use zone records, name server, etc.  It REQUIRES a domain name DNS, so I'm just going to use an alias [aworldofgeeks.co.cc] that has an A record pointed to 70.112.152.206, my IP.  The domain I want to configure is skidbladnir.co.cc.

So, this is what should be in my named.conf.local, correct?
```

zone “skidbladnir.co.cc” {
type master;
file “/etc/bind/zones/skidbladnir.co.cc”;
};

zone "0.168.192.in-addr.arpa" {
type master;
file "/etc/bind/zones/0.168.192.in-addr.arpa";
};

```

So, in /etc/bind/zones/skidbladnir.co.cc I should have something similar to
```

$TTL [ Please suggest a time, I'm not sure what to use (I know what TTL is, though) ]
@ IN SOA [???]. email.skidbladnir.co.cc. [Right?] )
2010041000 ; YYYYDDMMXX
28800
3600
604800
38400)

IN NS [???].
IN MX [???].

www IN A 192.168.0.100
[???]

```

And I'm not sure about the reverse file.  This is just a learning experience for me, and it's a home server that used to be a Linux desktop; I'm a teenager, so... Please, no big words that I have to lookup on Wiktionary.

---

### Post by Bachstelze on 2010-04-10
What do you want to do with your domain? Do you want to use it inside your LAN to access different computers by a name, or to allow people to access your home server from the Internet (or both)?

---

### Post by Skidbladnir on 2010-04-10
I want people to be able to put in skidbladnir.co.cc in their internet browsers and be directed to my server where I can then use an Apache VHost.  So, the second one.
Of course my server is screwed up beyond recognition and didn't survive an SSH reboot.  I'm not at my server right now... so... =/  This isn't an uncommon thing, however.  =P

---

### Post by Skidbladnir on 2010-04-10
Help.  Please.

---

### Post by Bachstelze on 2010-04-11
Then you can't use your private IP, and you have to use your public ISP-provided IP. Your zone file shouold look a bit like this:

```
$TTL 3600        ; 1 hour default TTL
skidbladnir.co.cc.    IN      SOA      ns.skidbladnir.co.cc. admin.skidbladnir.co.cc. (
                                2006051501      ; Serial
                                10800           ; Refresh
                                3600            ; Retry
                                604800          ; Expire
                                300             ; Negative Reponse TTL
                        )

; DNS Servers
                IN      NS      ns.skidbladnir.co.cc.

; MX Records
                IN      MX 10   mail.skidbladnir.co.cc.

                IN      A       70.112.152.206

; Machine Names
mail            IN      A       70.112.152.206
ns              IN      A       70.112.152.206

; Aliases
www             IN      CNAME   skidbladnir.co.cc.
```

---

### Post by Skidbladnir on 2010-04-11
Reverse?
And, do I just leave my NS on CO.CC as aworldofgeeks.co.cc?

---

### Post by Bachstelze on 2010-04-11
You can't define the reverse PTR record of your ISP-provided IP address yourself because you don't have authority on the reverse zone. You must ask your ISP about that.

As for the NS records, you should put the same thing in your zonefile that you put on your account at your registrar.

---

### Post by Skidbladnir on 2010-04-11
Well, time to go complain to TWC support.  What should I ask them?

---

### Post by Bachstelze on 2010-04-11
> **Skidbladnir said:**
> Well, time to go complain to TWC support.  What should I ask them?

Complain? Nothing to complain about, that's how things work... What you can ask them is whether they provide some kind of control panel to customize your reverse DNS, but even then it will be on *their* DNS server, not yours. Nothing you can do about it.

---

### Post by Skidbladnir on 2010-04-11
So, what your saying is, there is no possible way for me to host my own DNS server at my home?

---

### Post by Bachstelze on 2010-04-11
> **Skidbladnir said:**
> So, what your saying is, there is no possible way for me to host my own DNS server at my home?

No. What I'm saying is that you can't define *the PTR record associated with your ISP-provided IP address* on your home nameserver.

---

### Post by Skidbladnir on 2010-04-11
I thought that that was REQUIRED.  Other wise you get an auth error... ???

---

### Post by Skidbladnir on 2010-04-11
O_O... I think my... ISP... will let me set PTR records.

"In addition to these block lists, Road Runner's mail servers will also refuse mail from IP addresses that either have no reverse DNS, or PTR, record, or that have a PTR record that is unresolvable, and from email addresses in domains that do not resolve.  Those error messages will  look like this:"

It may only apply to business class, or something like that, but I'm going to ask again.

---

### Post by Skidbladnir on 2010-04-11
Business class... So there's the end of that dream.  But, still,
"I thought that that was REQUIRED.  Other wise you get an auth error... ???"

---

### Post by Bachstelze on 2010-04-11
> **Skidbladnir said:**
> I thought that that was REQUIRED.  Other wise you get an auth error... ???

What did you think was required?

---

### Post by Skidbladnir on 2010-04-11
The PTR record?  I've read somewhere that they are required. ... =\

---

### Post by Bachstelze on 2010-04-11
> **Skidbladnir said:**
> The PTR record?  I've read somewhere that they are required. ... =\

You do have one, it is also assigned by your ISP. You can't customize it, but you don't need to.

---

