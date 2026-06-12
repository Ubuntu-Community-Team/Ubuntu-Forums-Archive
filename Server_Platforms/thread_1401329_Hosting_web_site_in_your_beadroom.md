---
title: "Hosting web site in your beadroom"
date: 2010-02-07
forum: Server Platforms
---

### Post by bereta on 2010-02-07
Hello All

I am looking for a straight forward answer about name servers that I haven't been able for find after reading posts and FAQs. 

I have a web server set up (LAMP, ubuntu) and I am hosting a website. I am on a dynamic IP address from my ISP. I have setup a dynDNS account. I have registered for the first time a domain with GoDaddy.com. What I need is to point my domain to my home server. I am doing that by having setup forwarding in my godaddy account and it works. Why would I need to setup a name server? Why would I need something like zoneedit.com? And what exactly does the name server do? Wouldn't my registrar (godaddy) be making DNS entries and stuff? 

I want to make sure that I am setting things up right.

Thanks

---

### Post by stlsaint on 2010-02-08
If im understanding you correctly...
You dont need anything to do with dyndns if you are going thru godaddy. I have a godaddy domain and i use it without dyndns. I also point my account to my server at home using public ip and port forwarding to private ip for vps. Godaddy handles the dns side for me.

---

### Post by bereta on 2010-02-08
Thanks for the reply

The reason I use dynDNS is because my public IP address changes. I could do the same and forward directly to my IP but when the IP will change than going to [www.mydomain.com](www.mydomain.com) will point to no where. Anyways what I am wondering is, is domain forwarding the right thing to do? Because in the help sections they keep on talking about name servers and forwarding parked domains.... I'm getting confused. I did not enter any name servers, does this mean that there are no entries on DNS servers that will result to my location? Will search engines find me? That is what I don't understand.:confused::confused::confused:

---

### Post by dragos2 on 2010-02-08
I think you should set up a small dns server on your server too. 

I don't know how much it will help since dns propagation will take some time in
case your ip changes. Either ways a local dns server will help.

---

### Post by tlsarles on 2010-02-08
Ok, here is the deal. You can point your domain to your IP with godaddy, but it won't be dynamic. Your going to need to transfer the domain to the DDNS provider, so they can manage it properly.

Setting up your own DNS server doesn't make sense to me, unless I'm missing something... I'm not claiming to be Macgyver.

But yeah. Godaddy != DDNS, is your short answer

---

### Post by BobVila on 2010-02-08
> **tlsarles said:**
> Ok, here is the deal. You can point your domain to your IP with godaddy, but it won't be dynamic. Your going to need to transfer the domain to the DDNS provider, so they can manage it properly.

Setting up your own DNS server doesn't make sense to me, unless I'm missing something... I'm not claiming to be Macgyver.

But yeah. Godaddy != DDNS, is your short answer

Seconded, sort of. Zonedit/ddns will make sure that yourdomain.com actually resolves to your home server in the case that your modem resets/reconnects and comes up with a new IP address. It doesn't happen as often as the words "dynamic IP address" would have you beleive, but it DOES happen and is easy to get around.

If you create an account at zoneedit, you can leave the registration at Godaddy.com, and point the nameservers to the ones zoneedit provides to you. A dynamic client will then tell zone edit when your IP changes. Zone edit's name servers will make sure the internet at large gets to the right IP.

---

### Post by bereta on 2010-02-09
Thanks for the replys. So a name server is another term for DNS server?  

And also tlsarles when you say I can point my domain to my IP, that would mean there needs to be an entry on some DNS server with my domain to my IP. If I do domain forwarding like I am at the moment, the domain resolves to godaddys IP and they forward to me... Have I got this right?

---

### Post by tlsarles on 2010-02-09
Ok, so its like this... You buy a domain at a registrar. Most registrars; godaddy included, provide DNS servers with this.

The registrar really only has one job, and that is to guide people to your DNS servers. You DNS server is a simple database that looks like

[www.example.com](www.example.com) = <Server's IP>
mail.example.com = <MailServer's IP>
and so forth.

With godaddy's DNS server this would be a static assignment, but Bob is saying that if you tell your registrar (godaddy) to use zone edit's DNS servers, they hook you up with free DDNS, which is what you want.... so do that... instead of doing your DDNS thru dyndns... if your prefer

---

### Post by maddog2050 on 2010-02-10
Here is the solution that I used for doing the same thing.

My public IP address was not static so I have used dyndns.com to get myself a free dynamic DNS address e.g. xyz.gotdns.org and use ddclient running as a service to keep it updated. Then I created a CNAME DNS record on my domain (you should also be able to do this) and pointed it at the xyz.gotdns.org

[www.xyz.com](www.xyz.com) -> xyz.gotdns.org -> your dynamic public IP

This I'm sure is just one of many ways to achieve the same thing. But it will do what you want.

Adam

---

