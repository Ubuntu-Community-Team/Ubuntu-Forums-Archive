---
title: "HTTPS on Ubuntu Apache2"
date: 2019-10-22
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2019-10-22
I run a couple in internal Apache2 servers. I'm finally getting around to setting up https. 

I was thinking of using Let's Encrypt. 
Is there any reason I should do something different? 

Is there any reason I shouldn't use certbot?

I notice that all of the "cookbooks" I've found use ppas or downloads from other sites.

I'd prefer to use something Ubuntu maintains and updates.
Are there any similar clients in the Ubuntu repositories?

Finally my server is also a router that does 1 to 1 NAT to [rovide it a public IP ADDRESS 

and communicates to the ISP through the ISPs Gateway. 
Is that a problem?

---

### Post by SeijiSensei on 2019-10-23
I've converted all my sites to HTTPS with Let's Encrypt. certbot is really simple to use.  I wouldn't worry that its not in the Ubuntu repositories. Just use the version offered at the [certbot site]("https://certbot.eff.org/").  I managed one site where we had a traditional certificate to support GiveWP contributions. Now we're running LetsEncrypt instead.

If the server and your connection provides the support you need for sites on port 80, I don't think there's any reason to believe certbot won't work with your current setup. All my servers are directly on the Internet, though, so I don't have actual experience with your type of connection.

If you still have concerns, switch over one site and see how well it works.

---

### Post by slickymaster on 2019-10-23
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2019-10-23
I wouldn't mix a router/firewall with any other purpose for security reasons.  It is a beachhead so if it is lost over any misconfiguration of something unrelated to performing just the router/firewall tasks, it would be bad. Yes?  

IMHO, certain, specific, tasks should be on dedicated hardware. Routers and WAN firewalls are critical.

I switched to Let's Encrypt when a 5 yr commercial cert expired a few years ago.  Started out using Certbot, but found it couldn't handle re-newals for many of my domains due to some added complexities in my setup.  After fighting with it for 9 months, I found **acme.sh**, which is a bash script that I found easier to use. Easier to upgrade and it provides a standalone web server which I've been able to use with all my more complex domains.  New and renewals are working perfectly, but I do have to take down all websites on a single IP when doing the renewals.

My "complex" domains are a mix of 
* static websites
* reverse proxy'd dynamic webapp servers running on a shared back-end system
* load balanced websites with a multiple dynamic webapp servers running on different backend systems
The static, local, websites just worked. Never had any issues with either.
The other 2 sorts were always an issue.

My issues with certbot don't mean it isn't great, just that I was unable to figure it out for my needs.

As for wanting to use a solution from the ubuntu repos, in general I would agree, but Let's Encrypt has changed their API a few times, so the only way to have a currently working tool is to have a solution that is updated constantly.  In theory, the API should be stable by now.

```
$ ./acme.sh --upgrade
[Wed Oct 23 12:38:45 EDT 2019] Installing from online archive.
[Wed Oct 23 12:38:45 EDT 2019] Downloading https://github.com/Neilpang/acme.sh/archive/master.tar.gz
[Wed Oct 23 12:39:03 EDT 2019] Extracting master.tar.gz
[Wed Oct 23 12:39:03 EDT 2019] Installing to ...

``` does a self-upgrade, in-place.

The downside to using Let's Encrypt is that certs are for 90 days, no longer. That means that updating certs isn't annual or bi-annual, but every 60-89 days.  Due to my setup, I don't allow automatic renewals, so I have a calendar reminder to renew every 77 days. Why 77?  I want to do renewals during a weekend maintenance period since it requires about 20 min of website downtime to update all the certs.  Why not 84 days?  Because I might be on travel when the reminder comes up or there could be issues that take a few days to resolve.  
Could probably find a way to reduce the downtime to just a few seconds total by preventing apache/nginx from listening on port 80 completely during the renewal process.  Hummmm.

---

### Post by rsteinmetz70112 on 2019-10-23
Thanks, A lot of useful information here.

Seems like the path of least resistance is to use certbot so I'll probably try that first. Then I can see if I have any issues. My setup is for four simple company use only websites on 3 different servers so it's not a complex issue. I even have one server with Apache installed and no active websites to play with.

I do have a couple of  questions I hadn't thought of. 
[LIST]
[*]Does certbot automatically update itself as well as the certificate(s)? 
[*]Is it necessary to take down a site to upgrade either certbot or renew the certificate?
[*]Are there any Ubuntu ppas you would trust to keep things updated?
[/LIST]

I also have one site that runs proprietary application on a Windows Server. That should be fun.
```

I wouldn't mix a router/firewall with any other purpose for security reasons. It is a beachhead so if it is lost over any misconfiguration of something unrelated to performing just the router/firewall tasks, it would be bad. Yes? 
```

Just to be clear, I have a firewall that is Internet Facing, it has a Cascaded Router behind it that points to the private IP of one of my servers which is running iptables as a 1 to 1 NAT (and some other rules), that routes traffic from the Internet to my ISP assigned Public IPs. All traffic is subject to the firewall rules. It is probably not as tight as it should be but my main problem has been login attempts from the Internet which fail2ban running on the servers handles pretty well.

---

### Post by SeijiSensei on 2019-10-23
My LetsEncrypt sites have mostly run for longer than the default renewal period.  The automatic renewal process has worked flawlessly for me without any manual intervention of any kind.

---

### Post by TheFu on 2019-10-23
If the WAN-facing router doesn't block all inbound connections except those that should be allowed by IP:port, then it isn't a firewall at all.
Privates --> Pants --> Trousers --> Belt --> Suspenders
We want each of those things doing their jobs when we are on the internet, so if any one of them fails for any reason. The "privates" aren't shown to the world.

---

### Post by rsteinmetz70112 on 2019-10-24
Thanks to everyone who responded. I've now got a previously unconfirmed server running https. I think I've kind og gotten the han of it.

---

### Post by LHammonds on 2019-10-26
> **TheFu said:**
> Privates --> Pants --> Trousers --> Belt --> Suspenders
We want each of those things doing their jobs when we are on the internet, so if any one of them fails for any reason. The "privates" aren't shown to the world.
ROFL...if my company allowed quotes in signatures...this would be it.  Thanks for the lol

---

### Post by kevdog on 2019-10-28
I've used certbot and acme for management of LE (Let's Encrypt) Certs.   Both work fine.  One of the limitations of LE is that you can only have 5 renew completions per week.  What this means, is that if you have 5 or less computers needing access to the certs, each could theoretically call LE and renew their certificates.  With more than this method, however, you're going to have to come up with a method of copying of distributing the renewed LE certs among the computers needing the certificates.  I'm currently using an Ansible script to do this which it works fairly well.  LE also requires some type of domain authentication mechanism when issuing new certs or with renewals.  I'd personally recommend you use a dns authentication method rather than a stand-a-lone or web root mechanism.  I used web-root for a long time however I found dns to be much easier to use through scripting.  LE certs can be renewed automatically, however this is usually from a cron job which then fires a script along with the method for authentication.  I converted over to Cloudflare as my DNS provider just for this reason -- meaning lets encrypt has a cloudflare plugin that can be used to automate the authentication portion of the renewal process.  If you need more details please post.  Btw -- you don't need to totally shut down apache2 to install the new certificates.  apachectl -k graceful is the command to soft reload the new configuration files without taking down the server.

---

### Post by LHammonds on 2019-10-30
I've documented on particular method of [using Let's Encrypt](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=261#p709) if your web server is accessible from the Internet and how to schedule renewals.  This is for Ubuntu Server 18.04 and uses the systemd renewal timer Certbot provides which checks twice a day.

LHammonds

---

