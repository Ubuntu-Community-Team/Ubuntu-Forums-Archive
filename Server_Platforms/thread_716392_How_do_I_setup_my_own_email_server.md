---
title: "How do I setup my own email server?"
date: 2008-03-05
forum: Server Platforms
---

### Post by sk545 on 2008-03-05
So, the problem is privacy.  Is there a way to not depend on your ISP's servers and web based services such as hotmail/gmail?  If I have a internet connection, can I make my own email server for sending and receiving mail?  Basically something completely independent of the ISP.

Thanks.

---

### Post by rapiscan on 2008-03-05
You would have to be willing to meet the following prerequisites:

* Your server would have to be on at all times.
* You would have to have a static IP address (it is possible to use a dynamic IP address, but you would have to use a service that automatically updates your DNS when your IP changes.)
* Assuming you have a router and other computers connected to the internet, you would need to make sure that your email traffic is forwarded to your mail server.
* You would have to have your own domain registered along with DNS setup so that the mail exchange record points to your IP address.

If you can meet the above requirements, then you can set up your own mail server.

---

### Post by HermanAB on 2008-03-06
The best:
[http://citadel.org](http://citadel.org)

---

### Post by sk545 on 2008-03-06
> **rapiscan said:**
> You would have to be willing to meet the following prerequisites:

* Your server would have to be on at all times.
* You would have to have a static IP address (it is possible to use a dynamic IP address, but you would have to use a service that automatically updates your DNS when your IP changes.)
* Assuming you have a router and other computers connected to the internet, you would need to make sure that your email traffic is forwarded to your mail server.
* You would have to have your own domain registered along with DNS setup so that the mail exchange record points to your IP address.

If you can meet the above requirements, then you can set up your own mail server.

I understand most of what you wrote, but I think I would have to go ahead and try to install it to see if its something I can do.  Do email servers require a powerful computer?

---

### Post by smileypaul on 2008-03-06
Generally they don't require a powerful computer at all..just a reliable one.

but it depends, are you pushing 5,000,000 emails a day? or just a handful?

---

### Post by FakeOutdoorsman on 2008-03-06
> **sk545 said:**
> Do email servers require a powerful computer?

Generally no, unless you have a huge amount of traffic like what smileypaul mentions.  In fact, I'd recommend using an older computer for this as they often use less power.  I have a small Pentium II dev box that works just fine and uses about 35 watts on average, as measured by my Kill-a-Watt, where my P4 box uses 96 watts idle.

> **HermanAB said:**
> The best:
[http://citadel.org](http://citadel.org)

Citadel may not be what you want since it is an all-encompassing software suite and isn't in the repos.  From the Citadel site:

[LIST]
[*]email
[*]calendaring/scheduling
[*]address books
[*]bulletin boards
[*]mailing list server
[*]instant messaging
[*]multiple domain support
[*]modern AJAX-style web interface
[/LIST]

I hear it is a nice set if you're looking for something like that, but keep in mind that it is quite a bit of extra bulk if you only want a mailserver (MTA) such as Postifx.

Ubuntu Wiki on [Postfix]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=postfix&titlesearch=Titles") is a good place to start, and many people like the tutorials on [Howtoforge]("http://howtoforge.com/howtos/email/postfix").

---

### Post by miju on 2008-03-06
> **rapiscan said:**
> You would have to be willing to meet the following prerequisites:

* Your server would have to be on at all times.
* You would have to have a static IP address (it is possible to use a dynamic IP address, but you would have to use a service that automatically updates your DNS when your IP changes.)
* Assuming you have a router and other computers connected to the internet, you would need to make sure that your email traffic is forwarded to your mail server.
* You would have to have your own domain registered along with DNS setup so that the mail exchange record points to your IP address.

If you can meet the above requirements, then you can set up your own mail server.

hi,

I'm trying to configure a mixmaster server using mixmaster/post fix packages - I used the tutorials here -

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
[http://www.webservertalk.com/message1857875.html](http://www.webservertalk.com/message1857875.html)

but it doesn't seem to be working.

I wonder if you can instruct me how to register my own domain with dns setup so I can allow mixmaster to work

I am beind a router too so I have no idea which ports to forward.

I do have a static connection from my isp.

please help! ](*,)

---

### Post by Radio91 on 2008-03-06
is it not just a matter of registering a domain name at godday or similar and just point the dns of the domain name to your dns server. Thats how it works with online shared hosting. It can all be done in godday's domian interface very simply.

---

### Post by rapiscan on 2008-03-06
Miju, 

It sounds like there are several independent tasks that you would like to complete.   First, I want to say that I'm not personally familiar with mixmaster, but I will try to help if you're stuck on a specific step.  I think the best way to proceed is to go through the tutorial and let us know where you get stuck (and simply post it here or in a new thread).  Try to be as specific as possible as to where you are stuck or what isn't working.  (Be sure to read the tutorial carefully to make sure no mistakes were made.)

Regarding the router port forwarding, it would be best to refer to your router-specific documentation.  For example, if you have a linksys router you can go to their support area and download the user guide, which will have step by step instructions on how to do port forwarding.  Any port on your server that you want to have access to the internet will need to be forwarded from your router.  In your case, it sounds like you'll want the standard SMTP Port 25 to be forwarded to your server.   You may also want the POP/IMAP ports forwarded if you want to be able to check your email remotely.

Regarding DNS setup, see my response below to Radio91.

---

### Post by rapiscan on 2008-03-06
Radio91,

Although it is very simple when you have a shared hosting as noted in your comment, it's not that simple when you're setting up a home server.

After registering a domain, you need to set the authoritative name servers for your domain.  These nameservers are responsible for identifying what IP address the domain should point to.   When you get a shared hosting account, the provider for your account gives you permission to use their name servers.  They automatically set the appropriate DNS records for you, and all you have to do point your domain to their name servers.  Sometimes your registrar will have DNS management, so that you can use their name servers, but I don't think that's as common.

At any rate, sorry for the complicated explanation, the point is that it's not a simple task of logging in and pointing something to your server.  In every case, there has to be an authoritative nameserver for your domain, and someone has to maintain that.  

Miju, if your domain registrar has DNS management services, this means they will allow you to use their nameserver and you can manage your own DNS records.  This would be the easiest option.  You can simply ask the registrar if they have DNS management services if it's not immediately obvious on their website.

---

### Post by miju on 2008-03-06
> **rapiscan said:**
> Miju, 

It sounds like there are several independent tasks that you would like to complete.   First, I want to say that I'm not personally familiar with mixmaster, but I will try to help if you're stuck on a specific step.  I think the best way to proceed is to go through the tutorial and let us know where you get stuck (and simply post it here or in a new thread).  Try to be as specific as possible as to where you are stuck or what isn't working.  (Be sure to read the tutorial carefully to make sure no mistakes were made.)

Regarding the router port forwarding, it would be best to refer to your router-specific documentation.  For example, if you have a linksys router you can go to their support area and download the user guide, which will have step by step instructions on how to do port forwarding.  Any port on your server that you want to have access to the internet will need to be forwarded from your router.  In your case, it sounds like you'll want the standard SMTP Port 25 to be forwarded to your server.   You may also want the POP/IMAP ports forwarded if you want to be able to check your email remotely.

Regarding DNS setup, see my response below to Radio91.

thanks for your help!

I am thinking about using OpenDNS, but I am operating a Tor and Freenet server already - I am satisfied with my isp to manage those services - is there a way to configure mixmaster/postfix to use a DNS service ONLY for the mixmaster/postfix mail server?

---

### Post by HermanAB on 2008-03-06
Here is the Citadel groupware server running on my little Eee PC:
[http://aeronetworks.ca/eeepc-mdv-howto.html](http://aeronetworks.ca/eeepc-mdv-howto.html)
(scroll down to the end for snapshots)

...proving that you *really* don't need much power to run a mail and web server!

---

### Post by miju on 2008-03-07
at this point, what I need is to register a domain ( a free one) right? and then point them to my isp's static address? is that correct?:confused:

---

### Post by HermanAB on 2008-03-07
You got to register a domain and point it to the IP address given you by your ISP and assigned to your mail server.  Godaddy is a good one to use, since they include DNS in their service and they are so cheap they are practically free.  You need A, PTR and MX records for a mail server to work.

---

### Post by miju on 2008-03-07
> **HermanAB said:**
> You got to register a domain and point it to the IP address given you by your ISP and assigned to your mail server.  Godaddy is a good one to use, since they include DNS in their service and they are so cheap they are practically free.  You need A, PTR and MX records for a mail server to work.

Is there a actually Free organization that offers these services? I am 'practically' poor. :popcorn:

---

### Post by rickyjones on 2008-03-07
> **miju said:**
> Is there a actually Free organization that offers these services? I am 'practically' poor. :popcorn:

There is no DNS service that is completely free for you to register a domain name and DNS services. There are several dynamic DNS services that are pretty much free (I use dyndns.org) but they have limitations and are not nearly as customizable as having your own DNS registrar and control.

I do recommend Godaddy for domain name registering and management. I've been with them for several years now and the interface is simple and the price is just right.

-Richard

---

### Post by HermanAB on 2008-03-07
I don't know of any free DNS services that provide MX records.  So you are SOL.

---

### Post by miju on 2008-03-07
> **rickyjones said:**
> There is no DNS service that is completely free for you to register a domain name and DNS services. There are several dynamic DNS services that are pretty much free (I use dyndns.org) but they have limitations and are not nearly as customizable as having your own DNS registrar and control.

I do recommend Godaddy for domain name registering and management. I've been with them for several years now and the interface is simple and the price is just right.

-Richard

does it matter what suffix I choose? for example, is there any real difference between .com or .net or .info or whatever? I want only to be able to point to my mixmaster postfix server (while not disabling my tor and freenet servers)

---

### Post by HermanAB on 2008-03-07
No, the TLDs are not managed anymore.  Use whatever you like.

---

### Post by chris.zeman on 2008-03-08
I use the free DNS services offered by DNS Park [http://dnspark.com]("http://dnspark.com") and have no complaints. They'll allow you to use your domain(s) (registered through GoDaddy for example) at home. You have full control over the records, including MX records. The free service limits you to 2 domains.

The only drawback to hosting your own mail server on a home account is that many domains will block e-mail from your domain if it's on a dynamic I.P. address. I ran into that with my own mail server.

Chris

---

### Post by miju on 2008-03-09
> **chris.zeman said:**
> I use the free DNS services offered by DNS Park [http://dnspark.com]("http://dnspark.com") and have no complaints. They'll allow you to use your domain(s) (registered through GoDaddy for example) at home. You have full control over the records, including MX records. The free service limits you to 2 domains.

The only drawback to hosting your own mail server on a home account is that many domains will block e-mail from your domain if it's on a dynamic I.P. address. I ran into that with my own mail server.

Chris

Well, I registered with them and created a domain name but they say it is dormant and I don't really understand their explanation of what I must do to make it active. Here is their explantion -

Frequently Asked Questions
FAQ Database : DNS Hosting
 
Title: 	Why is my domain dormant?
Views: 	5875
Submitted By: 	Steve Helms
Last Updated: 	2008-03-09 10:37:10
 
Problem: 	My domain is dormant. How do I make it active?
Solution: 	If you have received a message at the top of a zone stating that the zone is dormant, it simply means that the nameservers that the domain recognizes as authoritative are not DNS Park nameservers. Domains will only be dormant for the free services. All paid services are immediately activated.

The DNS Park systems check this status hourly by querying the root nameservers. The WHOIS information provided by the registrar is not a reliable source for nameserver information. It is important to understand that the WHOIS information may display the DNS Park nameservers, but the central records and root nameservers have not been updated. Once the global root nameservers recognize the change, DNS Park will begin to advertise your domain. This entire process generally takes 24 to 48 hours to complete and is dependant on the efficiency of your registrar.

When a domain is dormant the DNS Park nameservers do not advertise that domain.

What must I do to make it active and working? :confused: thanks for any and all help.

---

### Post by Mr. C. on 2008-03-09
> **miju said:**
> Well, I registered with them ... and I don't really understand their explanation of what I must do to make it active. 

...
Title: 	Why is my domain dormant?
... Domains will only be dormant for the free services. All paid services are immediately activated.

What must I do to make it active and working? :confused: thanks for any and all help.

Sounds like you need to pay.

---

### Post by miju on 2008-03-09
> **Mr. C. said:**
> Sounds like you need to pay.

the poster that gave me the link said that he was using it for free, altho it was a limited service.

---

### Post by chris.zeman on 2008-03-10
> If you have received a message at the top of a zone stating that the zone is dormant, it simply means that the nameservers that the domain recognizes as authoritative are not DNS Park nameservers.

You'll need to login to GoDaddy (or whoever you registered your domain with) and set the nameservers to whatever DNS Park tells you they're supposed to be at. In my case, they are:
```
NS1.DNSPARK.NET
NS5.DNSPARK.NET
NS3.DNSPARK.NET
```

Let me know if you need anything else! :)

Chris

---

### Post by miju on 2008-03-10
> **chris.zeman said:**
> You'll need to login to GoDaddy (or whoever you registered your domain with) and set the nameservers to whatever DNS Park tells you they're supposed to be at. In my case, they are:
```
NS1.DNSPARK.NET
NS5.DNSPARK.NET
NS3.DNSPARK.NET
```

Let me know if you need anything else! :)

Chris

thanks :P I guess the only other question I have is do you know if there are any free registrars? I read that godaddy is among the cheapest but I read also that they have a reputation for bad service and pulling the plug on free speech groups. My intent is to operate a free anonymous remailer service - I operate a tor and freenet server already. thank you

---

### Post by chris.zeman on 2008-03-10
Really? :confused: I have had nothing but excellent service with GoDaddy. They even call me from time to time to ask if everything is alright and if I have any questions. I'm certainly not one of their biggest customers either. I have about 13 domains through them, and I was getting great service when I only had a few.

I don't think you're going to find any free registrars out there. Domain registrations don't come without a price AFAIK. 

Now, what do you mean by a free anonymous remailer service? It sounds like something SPAMMERS could exploit, but I'm sure you have your bases covered.

Chris

---

### Post by miju on 2008-03-10
> **chris.zeman said:**
> Really? :confused: I have had nothing but excellent service with GoDaddy. They even call me from time to time to ask if everything is alright and if I have any questions. I'm certainly not one of their biggest customers either. I have about 13 domains through them, and I was getting great service when I only had a few.

I don't think you're going to find any free registrars out there. Domain registrations don't come without a price AFAIK. 

Now, what do you mean by a free anonymous remailer service? It sounds like something SPAMMERS could exploit, but I'm sure you have your bases covered.

Chris

hi, 

thanks for the quick response. my intent is to configure a mixmaster postfix anonymous remailer service. possibly also a mixminion service too

At this point mixmaster and postfix are configured to allow only encrypted email transmission ( altho I think I might change that to allow unencrypted postings to usenet if I can determine how)

I believe I configured the programs correctly to thwart spamming. For example, I limit the bandwidth to 100k/sec and I limit the number of addresses to 16.

it this the best and most thorough policy? :confused:  also I downloaded and installed spamassasin. I read on slashdot about godaddy's bad reviews. are they a fair source?

---

### Post by miju on 2008-03-12
this is what I meant about godaddy free speech issues.

[http://yro.slashdot.org/yro/08/03/12/1739228.shtml](http://yro.slashdot.org/yro/08/03/12/1739228.shtml)

---

### Post by jflaker on 2008-03-12
> **chris.zeman said:**
> I use the free DNS services offered by DNS Park [http://dnspark.com]("http://dnspark.com") and have no complaints. They'll allow you to use your domain(s) (registered through GoDaddy for example) at home. You have full control over the records, including MX records. The free service limits you to 2 domains.

The only drawback to hosting your own mail server on a home account is that many domains will block e-mail from your domain if it's on a dynamic I.P. address. I ran into that with my own mail server.

Chris

I will almost guarantee that you will have trouble getting your outbound mail delivered to its destination from a broadband provider's IP range.  Most blacklists include dynamic IP ranges from most ISPs to eliminate spam/spambot mail

Anyone who is referencing blacklists to identify spam will not receive your emails---

---

### Post by jflaker on 2008-03-12
> **miju said:**
> this is what I meant about godaddy free speech issues.

[http://yro.slashdot.org/yro/08/03/12/1739228.shtml](http://yro.slashdot.org/yro/08/03/12/1739228.shtml)

The site is back, significantly SLOWED, but is still up.

---

### Post by HermanAB on 2008-03-12
FWIIW, Godaddy is fine.  I have never had any issues with them.

---

### Post by vpsville on 2008-03-12
You will definately want a static IP address and SPF defined on your DNS server.  

Otherwise most of what you send out will get flagged as spam and your intended recipient might never see it.

surgemail is a great package that you can run in Ubuntu.

---

### Post by miju on 2008-03-12
> **vpsville said:**
> You will definately want a static IP address and SPF defined on your DNS server.  

Otherwise most of what you send out will get flagged as spam and your intended recipient might never see it.

surgemail is a great package that you can run in Ubuntu.

what is SPF?

---

### Post by Railsbuntu on 2008-03-14
> **HermanAB said:**
> You got to register a domain and point it to the IP address given you by your ISP and assigned to your mail server.  Godaddy is a good one to use, since they include DNS in their service and they are so cheap they are practically free.  **You need A, PTR and MX records for a mail server to work.**
My questions are:

1) What is a PTR?
2) How do I know if I have a PTR and/or an MX record?
3) Where do I have to set them to make it work?

Thanks for your support :KS

---

### Post by Mr. C. on 2008-03-14
[http://en.wikipedia.org/wiki/PTR_record#Types_of_DNS_records](http://en.wikipedia.org/wiki/PTR_record#Types_of_DNS_records)

Search PTR and MX.

---

### Post by vpsville on 2008-03-14
> **Railsbuntu said:**
> My questions are:

1) What is a PTR?
2) How do I know if I have a PTR and/or an MX record?
3) Where do I have to set them to make it work?

Thanks for your support :KS

A PTR Record is reverse-dns.  That means the owner of the IP address has listed your domain as being authorized to use it.  SPF is a more modern way of doing it, and the big mail servers will check both.

Only the network provider can set the rDNS record, as they pay for the IP address.

---

### Post by Railsbuntu on 2008-03-14
EDIT: okay I have found what is my problem: my ISP is blocking access to port 25 since last year.

---

