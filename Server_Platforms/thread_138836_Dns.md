---
title: "Dns"
date: 2006-03-02
forum: Server Platforms
---

### Post by Coolio10 on 2006-03-02
I want to know howto setup a domain with these instructions [http://howtoforge.com/perfect_setup_ubuntu_5.10]("http://howtoforge.com/perfect_setup_ubuntu_5.10")

I know that you type on a domain during setup but if i have a uni.cc domain with dns where do i point the ns to use it for the home webserver?

Do you know anyone internet providers that offer internet and allow webserver in Canada.

---

### Post by suRoot on 2006-03-02
You register the domain with a registrar.  As part of the domain registration, you point your domain at name servers.  They can be your own, your web host, the registrar, whomever.

The DNS server you point the record at needs a zone file for the domain.  If you setup the domain with your registrar to point to your personal server, you need to configure bind & create a zone file for the domain.  Configure your firewall, if necessary to allow connections to port 53.  That's about it.

The domain name you setup during Ubuntu installation really has squat to do with true DNS, at least insofar as you're concerned.  You could name your machine foo.jimbob.local & so far as bind & dns go it really wouldn't matter.

Any more specific questions, we'll try to help.

---

### Post by Coolio10 on 2006-03-02
So what is this zone file i need and how do i point the domain to computer that doesnt exist with a domain already?

---

### Post by Coolio10 on 2006-03-02
I used a bind zone file generator to make one for me so now i want to know what to do with it.

```
; BIND db file for site4free.uni.cc

$TTL 86400

@       IN      SOA     ns1.site4free.uni.cc.      admin.site4free.uni.cc. (
                        2006030301      ; serial number YYMMDDNN
                        28800           ; Refresh
                        7200            ; Retry
                        864000          ; Expire
                        86400           ; Min TTL
                        )

                NS      ns1.site4free.uni.cc. 
                NS      ns2.site4free.uni.cc. 

                MX      10 mail.site4free.uni.cc.
                MX      20 mail-spool.site4free.uni.cc.


$ORIGIN site4free.uni.cc.
```

What do i call the file and where does it go?

---

