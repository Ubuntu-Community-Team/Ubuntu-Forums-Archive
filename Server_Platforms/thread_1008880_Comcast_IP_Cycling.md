---
title: "Comcast IP Cycling"
date: 2008-12-12
forum: Server Platforms
---

### Post by R.Bucky on 2008-12-12
Comcast has done it again. I live in Olympia, WA and utilize Comcast as my ISP. Aparently, they have cycled their IP's. I found that  today, 11 Dec '08, my IP no longer points to my domain. The solution is to visit your domain name provider and change your IP to whatever it was altered to. I used whatsmyip.com. 

I utilized my previous IP for around a year before it was changed. Any ides or suggestions on fixing this little annoyance? Or, would it be best to pay for something like noip.com?

~Mark

---

### Post by CrucifiedEgo on 2008-12-12
No need to pay -- dyndns.org offers this as a free service.  You can use ddclient in ubuntu, or many routers support dyndns as well.  I worked for the company that owned zoneedit, and, uh, use dyndns personally :)

---

### Post by R.Bucky on 2008-12-12
I am a bit confused. Registration with DynDNS is shown in the screenshot. But, how do I configure my domain name with NetworkSolutions to reflect an IP that is not static? By the way, my IP changed AGAIN this morning. 

Also, I installed ddclient to reflect my DynDNS registration using the custom hostname that I created. I am missing a link here. I host my own at home, so no 3rd party host is in play here. Pictures here: [http://picasaweb.google.com/lh/photo/eLBhT5nQT-eCT5kFNKTtjg]("http://picasaweb.google.com/lh/photo/eLBhT5nQT-eCT5kFNKTtjg")
[http://picasaweb.google.com/lh/photo/9b_cPpXEA2BrdLDhKEgUyg]("http://picasaweb.google.com/lh/photo/9b_cPpXEA2BrdLDhKEgUyg")

What next?

---

### Post by gpsmikey on 2008-12-12
Seems to me there was something in the Comcast AUP about not using any of those domain resolution services.  It definitely states you can not have any kind of server on a home type internet account.  There were some other "gotchyas" in there too last time I actually read the silly thing and from what I have heard, they do monitor for servers etc on home accounts.  Comcast is very good at jacking the rates up, deleting services (newsgroups etc) and you can't get a straight answer from them.  They are also very intollerant sometimes when they find people violating "their rights" as they have stated them.  I have Comcast just a ways north of you -- up near Seattle and am seriously considering changing to Verizon FIOS since they have just put it in. They do tell you they are using dynamic addressing unless you pay extra for a fixed IP etc.  The address does not usually change very often, but it does change (and they have stated it can/will in the AUP).

mikey

---

### Post by CrucifiedEgo on 2008-12-12
gpsmikey:  i used this for a good 5 years with comcast and they didn't seem to care.  

What you'll want to do with your domain at netsol is instead of setting it to an A record, use a CNAME for the root domain and www. (or *.) pointing to the dyndns hostname.  so, something like example.com CNAME demo.dyndns.com.

---

### Post by R.Bucky on 2008-12-12
> **gpsmikey said:**
> I have Comcast just a ways north of you -- up near Seattle and am seriously considering changing to Verizon FIOS since they have just put it in.

I called Verizon today. They do not offer FiOS in Olympia. I spoke with Comcast this morning about designating a static IP. They want a service agreement, $15/mo extra, and a technician to come by and install another modem. Pissing me off. 

Altering my CNAME record has not changed my lack of ability to visit my domain. I feel a bit humbled by this problem, as it is not one that I have encountered. Still troubled...

---

### Post by CrucifiedEgo on 2008-12-12
DNS changes can take a few hours to show up. I don't see the CNAME in there though.  Might want to give netsol a call and see how long their updates take:

```
james@phoenix ~: host buckyspalace.net
buckyspalace.net has address 71.231.166.48
buckyspalace.net mail is handled by 10 aspmx.l.google.com.
buckyspalace.net mail is handled by 20 alt1.aspmx.l.google.com.
buckyspalace.net mail is handled by 30 alt2.aspmx.l.google.com.
buckyspalace.net mail is handled by 40 aspmx2.googlemail.com.
buckyspalace.net mail is handled by 50 aspmx3.googlemail.com.
james@phoenix ~: host -t CNAME buckyspalace.net
buckyspalace.net has no CNAME record

```

---

### Post by R.Bucky on 2008-12-12
I believe that this is the correct method of entering the CNAME record.
[http://picasaweb.google.com/lh/photo/irvDJoDzwdkK4fb1yRQb_g]("http://picasaweb.google.com/lh/photo/irvDJoDzwdkK4fb1yRQb_g")

Yes, still waiting.........

---

### Post by CrucifiedEgo on 2008-12-12
ah-ha! Here's the deal,

DNS is a terrible system.  It's a hack.  You can't use a CNAME record on the root domain (you aren't).  However, I see that you do have both the CNAME and an A record active for *.  Go ahead and remove the A record -- it's mucking things up here.

It's probably worth it to set the A record for your root domain to your current IP address, and then setup a permanent redirect(think mod_rewrite) to www.

---

### Post by R.Bucky on 2008-12-12
My sub-domains are returning with the appropriate CNAME record. For instance, john.buckyspalace.net is a blog that I host for my brother. However, it is not being routed properly. I attempted to call NetworkSolutions (NetSol), however they are having some sort of a company 'picnic' today and are out until Monday.

I am unable to delete the A Name record at NetSol. As you stated before, the CNAME record only allow sub-domains. Therefore, I am not certain how to work the problem. DDClient is also installed and functioning on my Ubuntu server. My router also has a parameter for DynDNS, which is also updated. 

The A and CNAME records at NetSol require an IP to associate with the directives. Do these need to be changed as my IP changes, or is that really a moot point with DynDNS?

In short, my domain is down.

---

### Post by Robstarusa on 2008-12-12
> **R.Bucky said:**
> Comcast has done it again. I live in Olympia, WA and utilize Comcast as my ISP. Aparently, they have cycled their IP's. I found that  today, 11 Dec '08, my IP no longer points to my domain. The solution is to visit your domain name provider and change your IP to whatever it was altered to. I used whatsmyip.com. 

I utilized my previous IP for around a year before it was changed. Any ides or suggestions on fixing this little annoyance? Or, would it be best to pay for something like noip.com?

~Mark

You can get an/several static IP's from comcast.  It is not that expensive.

---

### Post by R.Bucky on 2008-12-12
Well, I travelled down to my friendly neighborhood Comcast main office to figure out the deal with my IP changing twice in 2 days. They did not state directly that they were cracking down on people hosting services, but it was dang near close. I hate it when big businesses give you little choice. 

For an additional 8.95/mo, I secured a business account with a static IP. Comcast has a monopoly in this area. FiOS is not available here either. What is a guy supposed to do? On the flipside, they gave me a month free internet...

I am part of the machine they call a consumer now - just say it!!!

---

### Post by gpsmikey on 2008-12-12
Another option would be to write a little application that periodically logs into your router, finds out what the WAN side IP address is currently and sends you email or a text message any time it changes.  See if they could figure that one out.
I have heard from a number of people in the past when they put a firewall in place with logging how surprised they were to find all those probes poking at the various ports (ftp, http etc) that all seem to be originating at the ISP's addresses.  They are checking to see what you are offering ):P

mikey

---

### Post by Thirtysixway on 2008-12-12
Comcast changes my IP address randomly.

What I did was point a no-ip.com address to my IP, and use their client to update my IP when it changes.

Then I pointed a CNAME from my domain name to my no-ip.com address.

Then I set a static LAN IP for my server so it never changes from the router's dhcp.

Works :)

---

### Post by CrucifiedEgo on 2008-12-12
> **Thirtysixway said:**
> Comcast changes my IP address randomly.

What I did was point a no-ip.com address to my IP, and use their client to update my IP when it changes.

Then I pointed a CNAME from my domain name to my no-ip.com address.

Then I set a static LAN IP for my server so it never changes from the router's dhcp.

Works :)

Unless he wants to recieve email.  having a CNAME on the root domain breaks email delivery, and violates RFCs.

---

