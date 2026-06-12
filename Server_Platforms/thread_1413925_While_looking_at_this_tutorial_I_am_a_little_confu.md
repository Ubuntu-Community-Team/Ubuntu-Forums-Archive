---
title: "While looking at this tutorial I am a little confused and could use some expertise!"
date: 2010-02-23
forum: Server Platforms
---

### Post by waloshin on 2010-02-23
A) 
[http://www.howtoforge.com/perfect_setup_suse_10.1_p3]("http://www.howtoforge.com/perfect_setup_suse_10.1_p3")

Then go to the Hostname and Name Server settings. The hostname (server1.example.com) should already be there (remember, we specified this earlier in our setup). Fill in up to three Name Servers (e.g. 145.253.2.75, 193.174.32.18, and 194.25.0.60). Unfortunately we cannot disable Update Name Servers and Search List via DHCP - I think this is a bug in YaST. Afterwards, hit OK.

[IMG]http://images.howtoforge.com/images/perfect_setup_suse10.1/32.png[/IMG]

When choosing the three name servers do you just choose a random IP address or do you have to use a specific one for the name servers?

B) 

[IMG]http://images.howtoforge.com/images/perfect_setup_suse10.1/32.png[/IMG]

I own the domain waloshin.com so I would imput: 

server1.waloshin.com and walsohin.com

instead of server1.example.com and example.com

Thanks!

---

### Post by cariboo on 2010-02-23
This thread doesn't belong in the Cafe. Moved.

---

### Post by bab1 on 2010-02-23
> **waloshin said:**
> A) 
[http://www.howtoforge.com/perfect_setup_suse_10.1_p3]("http://www.howtoforge.com/perfect_setup_suse_10.1_p3")...
When choosing the three name servers do you just choose a random IP address or do you have to use a specific one for the name servers?


These should be the IP addresses of the DNS servers you wish to query.  You ISP maintains DNS servers or you can use either [**_[COLOR="Navy"]OpenDNS[/COLOR]_**]("http://www.opendns.com/start/") or [**_[COLOR="Navy"]Google Public DNS[/COLOR]_**]("http://code.google.com/speed/public-dns/")
.

If you have a local DNS Cache server you should put that first and add 2 more (max is 3).  The query should start with the first address and go on to the next and so on. 
> 
B) 

[IMG]http://images.howtoforge.com/images/perfect_setup_suse10.1/32.png[/IMG]

I own the domain waloshin.com so I would imput: 

server1.waloshin.com and walsohin.com

instead of server1.example.com and example.com

Thanks!

The short answer is, yes.  

You should have the hosting DNS server map your IP address to your FQDN (host and domain name).  Typically this is the registrar where you got the name.

---

### Post by waloshin on 2010-02-23
1) I have a domain with godaddy.com so would I just use the godaddy name servers they supplied me with? 

- NS19.DOMAINCONTROL.COM
- NS20.DOMAINCONTROL.COM

2) Or can I use a service like Google Public DNS?

3) Do i have to use yast to setup my own? Using a tutorial like this? SolutionBase: Configuring a DNS server with SuSE's YaST

4) And if I use number 3) do I just grab the dns servers from my router that was supplied by my isp?

---

### Post by bab1 on 2010-02-23
> **waloshin said:**
> 1) I have a domain with godaddy.com so would I just use the godaddy name servers they supplied me with? 

- NS19.DOMAINCONTROL.COM
- NS20.DOMAINCONTROL.COM

2) Or can I use a service like Google Public DNS?

3) Do i have to use yast to setup my own? Using a tutorial like this? SolutionBase: Configuring a DNS server with SuSE's YaST

4) And if I use number 3) do I just grab the dns servers from my router that was supplied by my isp?

First let me say that there are **[COLOR="Red"]2 separate functions for DNS[/COLOR]**.

That is to say we need to configure a DNS server to direct requests of others for resources at *waloshin.com* and we use a the same DNS servers to field our requests for resources of others (e.g the IP address of ubuntuforums.org)

Neither of these senarios require you to setup your own DNS server so installing or cofiguring via yast is not needed.

You would do the following for you do do lookups:

1. Use godady's DNS servers for your lookups as you asked in the original question.```

- NS19.DOMAINCONTROL.COM
- NS20.DOMAINCONTROL.COM
```

2. You could, but good net manners would be to use GoDaddy as described above in #1

3. No you do not.

You need to follow this to provide DNS services for others to find you.

4. I do not recommend you running your own DNS servers for public use.  It is a lot of work to keep it secured and GoDaddy will do this for you.  You need to contact them and provide your IP address.  Tell them what you want mapped to your IP address (A record / MX record, etc.)

So where do you need to have your own DNS server?  Only when you want to resolve hostnames on your **[COLOR="Navy"]own internal LAN[/COLOR]**.  If that would be the case I would use DNSmasq if there is not one running on your MODEM/router.

Edit: SuSE is not the same as Ubuntu/Debian.  The structure can be very different.  Are you aware of that?

---

### Post by waloshin on 2010-02-23
> **bab1 said:**
> First let me say that there are **[COLOR="Red"]2 separate functions for DNS[/COLOR]**.

That is to say we need to configure a DNS server to direct requests of others for resources at *waloshin.com* and we use a the same DNS servers to field our requests for resources of others (e.g the IP address of ubuntuforums.org)

Neither of these senarios require you to setup your own DNS server so installing or cofiguring via yast is not needed.

You would do the following for you do do lookups:

1. Use godady's DNS servers for your lookups as you asked in the original question.```

- NS19.DOMAINCONTROL.COM
- NS20.DOMAINCONTROL.COM
```

2. You could, but good net manners would be to use GoDaddy as described above in #1

3. No you do not.

You need to follow this to provide DNS services for others to find you.

4. I do not recommend you running your own DNS servers for public use.  It is a lot of work to keep it secured and GoDaddy will do this for you.  You need to contact them and provide your IP address.  Tell them what you want mapped to your IP address (A record / MX record, etc.)

So where do you need to have your own DNS server?  Only when you want to resolve hostnames on your **[COLOR="Navy"]own internal LAN[/COLOR]**.  If that would be the case I would use DNSmasq if there is not one running on your MODEM/router.

Edit: SuSE is not the same as Ubuntu/Debian.  The structure can be very different.  Are you aware of that?

Yeah I am aware that OpenSuse and Ubuntu is totally different in configuring. 

What I am trying to do is run a mail server with web access at waloshin.com so I would not need to do step 3? And I would proceed to phoning godaddy and letting them set it up with an Mx record and an A record? 

Thanks

---

### Post by bab1 on 2010-02-23
> **waloshin said:**
> ...
What I am trying to do is run a mail server with web access at waloshin.com so I would not need to do step 3? And I would proceed to phoning godaddy and letting them set it up with an Mx record and an A record? 

Thanks

Yes you are correct.  There are other records for DNS.  Ask GoDaddy what else you need.

---

### Post by waloshin on 2010-02-23
> **bab1 said:**
> Yes you are correct.  There are other records for DNS.  Ask GoDaddy what else you need.

Would I give them my ip address to the server from the router such as 192.168.2.4 or would I give them the Ip address that my isp has supplied me with?

---

### Post by bab1 on 2010-02-23
> **waloshin said:**
> Would I give them my ip address to the server from the router such as 192.168.2.4 or would I give them the Ip address that my isp has supplied me with?

You would give them the WAN side address (The one supplied by your ISP).  The LAN side addresses are not routable (i.e. 192.168.2.4).

If you are using residential DSL/Cable services then they most likely are assigning the WAN side address dynamically (via DHCP) and you will need DDNS services (Aka DynDNS / Dyanamic DNS).  This is to allow for use of the domain name with an IP address that changes.

When you have all of this sorted out.  You can then *port forward * the destination of your mail traffic to the actual server.  This is to translate the outside (WAN) address to the inside (LAN) address.

---

### Post by waloshin on 2010-02-23
Phoned godaddy.com they had me enter my ip address in the A record. They then asked me what mx records I was supposed to enter. And I have no idea. 

This is what the godaddy.com mx record setup looks like. So how would I set that up? What would I put in for host goes to:

Thanks

MX (Mail Exchange)		
	Priority	Host	Goes To	TTL	Actions
	0	@	smtp.secureserver.net	 1 Hour	
	10	@	mailstore1.secureserver.net

---

### Post by bab1 on 2010-02-23
> **waloshin said:**
> Phoned godaddy.com they had me enter my ip address in the A record. They then asked me what mx records I was supposed to enter. And I have no idea. 

This is what the godaddy.com mx record setup looks like. So how would I set that up? What would I put in for host goes to:

Thanks

MX (Mail Exchange)		
	Priority	Host	Goes To	TTL	Actions
	0	@	smtp.secureserver.net	 1 Hour	
	10	@	mailstore1.secureserver.net

I assume they want the *actual host name*.  but I do not run our mail server.  We offload that task.  I searched and found [**_[COLOR="Navy"]this[/COLOR]_**]("http://www.petri.co.il/configure_mx_records_for_incoming_smtp_email_traffic.htm").  The Google search was [**_[COLOR="Navy"]this[/COLOR]_**]("http://www.google.com/search?q=mx+records+needed&btnG=Go!").

Edit: An explanation of the MX record can be seen [**_[COLOR="Green"]here[/COLOR]_**]("http://www.zytrax.com/books/dns/ch8/mx.html")

---

### Post by waloshin on 2010-02-24
To setup postfix on Ubuntu: Does [this tutorial]("http://jonsview.com/setting-up-email-services-on-ubuntu-hardy-using-postfix-and-courier") actually work?

And if so when setting up:

Again, you’ll be asked some questions:

General type of configuration? <– Internet Site
Where should mail for root go? <– Leave blank
Mail name? <– server1.example.com
Other destinations to accept mail for? <– server1.example.com, example.com, localhost.example.com, localhost
Force synchronous updates on mail queue? <– No
Local networks? <– 127.0.0.0/8
Use procmail for local delivery? <– Yes
Mailbox size limit? <– 0
Local address extension characters? <– +
Internet protocols to use? <– all

Is this how I would set mine up? Or do I leave it as server1.example.com?


General type of configuration? <– Internet Site
Where should mail for root go? <– Leave blank
Mail name? <– mail1.waloshin.com
Other destinations to accept mail for? <– mail1.waloshin.com, waloshin.com, localhost.example.com, localhost
Force synchronous updates on mail queue? <– No
Local networks? <– 127.0.0.0/8
Use procmail for local delivery? <– Yes
Mailbox size limit? <– 0
Local address extension characters? <– +
Internet protocols to use? <– all

---

