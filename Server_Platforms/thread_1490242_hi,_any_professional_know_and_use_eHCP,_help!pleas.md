---
title: "hi, any professional know and use eHCP, help!please"
date: 2010-05-22
forum: Server Platforms
---

### Post by AresArtemis1 on 2010-05-22
hi, professional, I just installed the ehcp latest version on my Ubuntu  10 lts server, everything is running well, but the ehcp subdomain account  creation function doesn't work.

here is the issue:
hi, professionals,first, I set up the first domain in web based eHCP control panel, then followed your instruction that I went to my FQDN domain(hotwebhosting.mobi) register company to do the following work:

"Now you need to redirect your domain from registrar to your server.. go to registrar (like godaddy, networksolutions.com) that you registered (bought) your domain. login to your domain control panel, then redirect your domain to "ns1.mydomainx.com" and "ns2.mydomainx.com" with same ip of your server... "

but I received error message on the register web site DNS setting page:

" 
    

Nameservers
Error(s) encountered: Nameserver [ns1.hotwebhosting.mobi] doesn't exist at the registry "

then I checked Cname setting on the register page:

" C name (alias)                       Points to A record (host)
ns1.hotwebhosting.mobi.                  hotwebhosting.mobi.
ns2.hotwebhosting.mobi.                   hotwebhosting.mobi.      
 "

see, I did put the two dns server on the register website dns setting page.

I also emailed help to my register, but I haven't receive reply yet.

In my house, I have two different internet provider, one is ADSL cable, another is televsion company cable. I connect my laptop wiht the televsion company cable. I connect my Ubuntu 10lts Server with the ADSL cable. After I setting up a subdomain account under my domain(hotwebhosting.mobi), it is girl.hotwebhosting.mobi, but firefox says:

Firefox can't find the server at girl.hotwebhosting.mobi


* Check the address for typing errors such as
ww.example.com instead of
[www.example.com](www.example.com)

* If you are unable to load any pages, check your computer's network
connection.

* If your computer or network is protected by a firewall or proxy, make sure
that Firefox is permitted to access the Web.

finally, I did checked the ehcp ,which was running, and I opened email account, ftp account for the subdomain girl.hotwebhosting.mobi, all of those were working, just people could not access the website "girl.hotwebhosting.mobi".


I have  created the first domain account after ehcp initial installation. It is a  FQDN(hotwebhosting.mobi), which I bought from a register company, then,  I uploaded my website file into webserver, then, I can access my  website in WAN(my Ubuntu hosting server is connected with a cable  internet provider at my home), I can access my website in school.

However,  after I created a subdomain account under my hosting server domain  name(hotwebhosting.mobi), it is girl.hotwebhosting.mobi, then I put  this subdomain name address into firefox, firefox say:


         
Firefox can't find the server at girl.hotwebhosting.mobi


     *   Check the address for typing errors such as
           ww.example.com instead of
          [www.example.com]("http://www.example.com")

    *   If  you are unable to load any pages, check your computer's network
           connection.

    *   If your computer or network is protected by a  firewall or proxy, make sure
          that Firefox is permitted to  access the Web.



help, please

I promise that I will donate webspace to Ubuntu develop team or Ubuntu other service needs web host space, please help me solve this problem, now just one step to set up my hosting server ready, everything is running well, just the subdomain issue, so please help!


best regards and appreciate,

Artemis,

Canada

:guitar::guitar::guitar::guitar::guitar:

---

### Post by HermanAB on 2010-05-22
```
$ nslookup sexgirl.hotwebhosting.mobi
Server:         213.42.20.20
Address:        213.42.20.20#53

** server can't find sexgirl.hotwebhosting.mobi: NXDOMAIN

$ nslookup hotwebhosting.mobi
Server:         213.42.20.20
Address:        213.42.20.20#53

Non-authoritative answer:
Name:   hotwebhosting.mobi
Address: 96.55.172.149

```

You got to configure your DNS to resolve subdomains, either with an explicit entry for the host or with a wild card.

---

### Post by AresArtemis1 on 2010-05-22
So you mean that I must do and can not skip the following step:

" * Now you need to redirect your domain from registrar to your server..  go to registrar (like godaddy, networksolutions.com) that you registered  (bought) your domain. login to your domain control panel, then redirect  your domain to "ns1.mydomainx.com" and "ns2.mydomainx.com" with same ip  of your server... 
on some registrar, you may need to register your new dns first, in  domain control panel, there may be a link like "register new dns" ...  after registering that dns, every people on world can reach you, if  everything is ok.. "


 I find this service at [http://www.dyndns.com/services/dns/secdns/](http://www.dyndns.com/services/dns/secdns/),  Secondary DNS provides redundant name service for a domain that you own,  whose DNS you manage on your own nameserver(s). The servers providing  Secondary DNS are located on separated networks to prevent any downtime. With Secondary DNS even if yours goes down, we will continue to resolve  your queries

is it correct service to solve the subdomain issue? I think that I  should change registrar company because I haven't receive my registrar  reply and I didn't find any service of register my own dns server  service there,

is  it any other way to work on my Unbuntu server to solve problem, can I  skip the step of redirecting at the registrar company?:guitar:

---

### Post by HermanAB on 2010-05-22
Howdy,

Whoever you registered your domain name with, should also provide a DNS service.  If not, then they are not really worth using, since you would have to run your own DNS, which can be painful.

The funniest thing is that the registrars that don't provide DNS, are more expensive than the ones that do.

---

### Post by AresArtemis1 on 2010-05-22
hi, professional, my registrar helped me to register my own dns in their server, see,

     [IMG]https://members.easydns.com/gifs/t-whois_record.gif[/IMG]
**current record for: hotwebhosting.mobi**
 


**nameservers for: hotwebhosting.mobi**

  [IMG]https://members.easydns.com/gifs/cap-ul.gif[/IMG]
nameservers
[IMG]https://members.easydns.com/gifs/cap-ur.gif[/IMG]
  [IMG]https://members.easydns.com/gifs/cap-ll.gif[/IMG]
    ns1.hotwebhosting.mobi96.55.172.149 ns2.hotwebhosting.mobi96.55.172.149     [IMG]https://members.easydns.com/gifs/spacer.gif[/IMG]
    


 

**current registrar lock state for: hotwebhosting.mobi**


but now I suddenly can not access my Ubuntu hosting server domain website, I think that it is happened because I change the nameserver, but I access eHCP main page on my server with IP address:

[http://96.55.172.149/](http://96.55.172.149/)

so my Ubuntu hosting server is working and the eHCP is working, professionals , could please help to figure out the problem and how to solve it, help please.............
:guitar:

---

