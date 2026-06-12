---
title: "Hosting Providers"
date: 2021-01-13
forum: The Cafe
---

### Post by yellowhousejake on 2021-01-13
Good day,

I have had two small, tiny, websites hosted on Godaddy for over a decade and they have been good to us so far. In the last month they have moved our email onto Office 365 and it is proving to be a disaster. Godaddy has told us there is no road back to the previous mail system.

I am looking for a solid hosting provider and I am interesting in others experiences. I would like something that is Linux/Unix based and not MS based. I have very light traffic on the web servers but good email services are my primary concern. I will be moving web, email, and DNS if possible.

Any advice would be very appreciated.

DAve

---

### Post by mastablasta on 2021-01-13
location of servers? USA?

---

### Post by yellowhousejake on 2021-01-13
USA location would be preferred.

I am a sysadmin and well versed in CL, Postfix, Qmail, Apache, AMP, LAMP, etc. I do enough IT work at my day job so, a reasonable web based set of controls would be nice. I just want to make changes now and then and have a UI my wife can use if I have to talk her through something over the phone.

Thanks for the response.

DAve

---

### Post by SeijiSensei on 2021-01-13
You can lease an entire virtual server from [Linode]("https://www.linode.com/pricing/") for $5/month. You'd have to set up your own email system, of course, but it sounds like you would know how to do that. There are a few [web-based mail clients]("https://opensource.com/alternatives/gmail") out there as well. I once used Horde back in the day. Roundcube also gets pretty good press.

These days I just use Mozilla Thunderbird with a server running IMAP.

---

### Post by zebra2 on 2021-01-13
123ehost.com has everything you need.  Been using them since back in the 90's. Been paying the same $50 for 25 years.

---

### Post by yellowhousejake on 2021-01-14
That may be the route I take, though if changes are needed my wife, while very computer literate, would struggle with the CL.

I have been using Sylfeed the past few years and love it.

DAve

---

### Post by yellowhousejake on 2021-01-14
> **zebra2 said:**
> 123ehost.com has everything you need.  Been using them since back in the 90's. Been paying the same $50 for 25 years.

Thank you, that is one I did not know about. I will look into them.

DAve

---

### Post by mastablasta on 2021-01-14
i dont' kno wwhich ones are good in US. 

but cPanel or similar software is usually on hosts. 

but it depends what kind of things she actually does on the server itself. 

if you go your own way, then for example Ajenti is a nice web gui for server and it is easy to use. of course installing and uninstalling wordpress is not as easy to do as it is in cpanel. there are also Zentyal, Nethserver or Openmediavault (but all these are more for home server or business server). 

or you could go with one of the cpanel like interfaces Blueonyx or aaPanel. maybe Plesk or Virtualmin could also work. 

another option is to use something like digital ocean or similar and then maybe add what you would need.


i have to say that once we setup wordpress and email we rarely visit cpanel that the host provides. only on occasion.

---

### Post by TheFu on 2021-01-14
+1 for Linode.  They are well known and reputable.

If you really know what you are doing, DO or Vultr are options - both provide only SSD storage for their VMs. Be certain you have excellent, local (not on the provider's hardware) backups. $5/month or less VMs available.

GoDaddy has this all-in-one thing they've been successful at selling for a long time.  I used them as a resistrar only for a few decades, but they finally drove me away with an $18/yr domain renewal earlier this year.  I'd been paying much less in 10 yr chunks previously. 6 weeks after that expensive renewal, found a $7/yr deal somewhere else reputable and moved.  

Email for small companies can be handled by a raspberry pi most of the time.  It is the extra stuff we put on those systems that bogs them down. If you split the email into a gateway and a end-user server, then you can have a tiny gateway or 2 or 3 with different VM providers and have your end-users access your real email server in-house through a VPN.  If setup correctly, the gateway will block 90% of the emails anyway, so even a home ISP can handle running email for a 50 person company, while having a store-n-forward gateway so the service is always up to the rest of the world.  Just a though.

As for web hosting, there are plenty of great solutions, but it depends on the sorts of websites you have and the traffic it needs to handle. If you have 50 static pages with CSS making it appear dynamic, then for $0.25/month, you can have a dynamically scaled static website at NearlyFreeSpeech.net.  They charge by bandwidth used, so if your website isn't too popular, it will be very cheap.  OTOH, if all of slashdot visits, it might be $8-$10 for that month, but it drops back the next month. They expect expert clients, so you'll get an ssh/sftp login to place your files and set the permissions.

---

### Post by makitso on 2021-01-17
Tigertech.net.  Very technology oriented and great customer support.

---

### Post by CharlesA on 2021-01-17
I tried to roll my own mail server once upon a time, but it was more hassle then it was worth.

I ended up going with mxroute for my email. I'm on their "small" plan since I'm only hosting email from my domains and they get very little mail.

For a web host, Linode works fine, but you need to set it up yourself, which is unlike GoDaddy's hosting.

For DNS, I've got my zones set up in Cloudflare, but that might not be for everyone.

---

### Post by remy-wehrung on 2021-01-24
you have OVH, whose domain names are not expensive

---

### Post by tendouser on 2021-04-17
anybody expirenced with 1&1 Ionos?

i'm looking into move some wordpress websites to ionos!

---

