---
title: "reverse dns record one ip"
date: 2011-01-27
forum: Server Platforms
---

### Post by koszta on 2011-01-27
Hi,

how do I create a reverse dns record for one ip??

I have called it (my public ip being 213.22.14.143)

rev.143.14.22.213.in-addr.arpa

and it looks like:

@ IN SOA leonardo.seeit.com. hostmaster.seeit.com. (
    200709132 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; define the authoritative name server
        IN NS leonardo.seeit.com.
        IN MX 1 leonardo.seeit.com.
; our hosts
0       IN PTR seeit.com.
0        IN PTR zenon.seeit.com.


I know the zeros are probably wrong but how do I make it work since I have only one IP? I need to set my PTR records right so that I can recieve mail properly .... please :) It is a work under pressure :)

---

### Post by SeijiSensei on 2011-01-27
Short answer is that it's out of your control.  Your ISP controls the reverse mappings for its addresses.  If you have a business-class Internet account with a static IP address, your ISP may offer this service, typically for free.  If you're on a consumer-grade connection, or have a dynamic IP, you're probably stuck with the reverse entry your ISP maintains.

---

### Post by koszta on 2011-01-27
> **SeijiSensei said:**
> Short answer is that it's out of your control.  Your ISP controls the reverse mappings for its addresses.  If you have a business-class Internet account with a static IP address, your ISP may offer this service, typically for free.  If you're on a consumer-grade connection, or have a dynamic IP, you're probably stuck with the reverse entry your ISP maintains.

I got this ip to work the way that it forwards all the 53 requests to my ip 213.29.153.106 - I just need to know how to set up my own bind server for this single ip reverse mapping.. Is my reverse dns ok?

---

### Post by SeijiSensei on 2011-01-27
> **koszta said:**
> I got this ip to work the way that it forwards all the 53 requests to my ip 213.29.153.106 - I just need to know how to set up my own bind server for this single ip reverse mapping.. Is my reverse dns ok?

Your ISP owns the 153.29.213.in-addr.arpa domain.  You need to talk to them.  This really isn't something you can do on your own.

---

### Post by koszta on 2011-01-27
ok, I will but how is it possible that I got my normal DNS records working for my external ip (i got subhosts like mail or leonardo all directed to my external ip... how is it possible? And which domain name do I need to tell my ISP to stand for my external ip? the mail server ?
so 
if I have this:
...
seeit.com. IN NS leonardo.seeit.com.
seeit.com. IN MX 10 leonardo.seeit.com.
...
in my normal-domain I need to tell them to set external ip to leonardo.seeit.com???

---

### Post by SeijiSensei on 2011-01-27
It should match the A record for the IP.

---

### Post by koszta on 2011-01-27
is it possible that it is a reason why I dont recieve some of the emails? 
Or is the reverse lookup used only when I send messeges to others

---

### Post by SeijiSensei on 2011-01-27
Some mail servers will check reverse DNS to help identify spams.  Especially paranoid systems will refuse to accept mail from machines where the forward and reverse resolution don't match.  Inbound mail shouldn't be affected at all.

You might also look into adding an [SPF record]("http://www.openspf.org/") to your zone file to identify the legitimate SMTP sending server for the domain.  Not all servers will pay attention to SPF records, but those that do will be happier if your server is listed there.

---

### Post by koszta on 2011-01-27
thank you so much man... you really helped... I am so happy to be a part of linux community... I am glad to help anybody with cisco or perl tho I really had no really big experience with DNS up to now (just the basic stuff) 

thanks again :)

---

