---
title: "BIND9 to resolve FQDN on Apache2"
date: 2007-05-24
forum: Server Platforms
---

### Post by a.d.gardiner on 2007-05-24
Hey all,

I'm quite new to Ubuntu (running feisty) and just getting going building my own Apache2 to serve a couple of my own sites.

After grappling with 'virtual host's' for a couple of days I think I have that nailed now, but I still have a few outstanding bits to do.

Question is, how exactly do I get my registered domain names to replace my IP address when loading a page?just

At present when I load [www.chevinstaffportal.co.uk](www.chevinstaffportal.co.uk) from the internet I get my IP address '81.149.22.40' in the address bar instead of the URL.

I'm sure I sound a little bit vague on this... I take it from reading around I need to install BIND9 or NSD or similar to peform the function of a 'Authoritative-only Nameserver', but I'm stuck for where to take this now.

Does anybody have a very simple setup guide? Or am I taking this along the wrong path?

---

### Post by kidders on 2007-05-25
Hi there,

I've done some poking around, to try to fill in the blanks. Hopefully, we can pin down what you'd like to achieve in a little more detail. I pasted some of the diagnostic information I used onto the end of this post fyi.

Basically, it looks as though you're using a European nameserver provided by Lycos to point your domain name to a shared web service in Sweeden. It's configured to forward visitors to a domestic BT DSL connection in the UK, with a HTTP redirect.

People usually do that because it's a simple (and free) way to make it easier for vistors to access a home web server. The down-side is that the redirection is protocol-dependent (ie there is no publicly accessible DNS record connecting chevinstaffportal.co.uk to 81.149.22.40). This means that you won't be able to use name-based virtual hosting on your end, and can't run any non-HTTP services off your domain name.

> **a.d.gardiner said:**
> How exactly do I get my registered domain names to replace my IP address when loading a page?

One option would be to use a dynamic DNS service.

> **a.d.gardiner said:**
> I take it from reading around I need to install BIND9

That's one possible way of getting yourself started. A local DNS service would allow you to force [www.chevinstaffportal.co.uk](www.chevinstaffportal.co.uk) to resolve to something like 192.168.1.17 on *your* side of the firewall, while the rest of the world would see it as 81.149.22.40 (assuming you joined up with a dynamic DNS SP). 

Is that any help?



```
$ telnet www.chevinstaffportal.co.uk 80
Trying 212.78.206.150...
Connected to www.chevinstaffportal.co.uk.
Escape character is '^]'.
GET / HTTP/1.0
Host: www.chevinstaffportal.co.uk            

HTTP/1.1 302 Found
Date: Fri, 25 May 2007 17:20:20 GMT
Server: Apache
Location: http://81.149.22.40
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<HTML><HEAD>
<TITLE>302 Found</TITLE>
</HEAD><BODY>
<H1>Found</H1>
The document has moved <A HREF="http://81.149.22.40">here</A>.<P>
</BODY></HTML>
Connection closed by foreign host.
```

```
$ whois chevinstaffportal.co.uk

    Domain name:
        chevinstaffportal.co.uk

    Registrant:
        Chevin Cycles Ltd

    Registrant type:
        UK Entity

    Registrant's address:
        The Showrooms Leeds Road
        Otley
        LS21 1BR
        United Kingdom

    Registrant's agent:
        united-domains AG [Tag = UNITEDDOMAINS-DE]
        URL: http://www.united-domains.de

    Relevant dates:
        Registered on: 04-Jan-2007
        Renewal date:  04-Jan-2009
        Last updated:  04-Jan-2007

    Registration status:
        Registered until renewal date.

    Name servers:
        nshost1.st2.lyceu.net
        nshost2.st2.lyceu.net
        nshost3.st2.lyceu.net

    WHOIS lookup made at 18:24:29 25-May-2007

-- 
This WHOIS information is provided for free by Nominet UK the central registry
for .uk domain names. This information and the .uk WHOIS are:

    Copyright Nominet UK 1996 - 2007.

You may not access the .uk WHOIS or use any data from it except as permitted
by the terms of use available in full at http://www.nominet.org.uk/whois, which
includes restrictions on: (A) use of the data for advertising, or its
repackaging, recompilation, redistribution or reuse (B) obscuring, removing
or hiding any or all of this notice and (C) exceeding query rate or volume
limits. The data is provided on an 'as-is' basis and may lag behind the
register. Access may be withdrawn or restricted at any time.
```

---

### Post by a.d.gardiner on 2007-05-27
Thanks for the reply :) Very much appreciated!

I think I'm following everything so far.

Looking over my details at Lycos I have webpointing activated to '81.149.22.40'. Lycos also provide options to specify 'DNS settings'. I'm not sure if that is the same as dynamic DNS? ;)

If so, I figure the next step is installing BIND9 at my end and then change 'DNS settings' area at Lycos to redirect to my machine here? 

(As a side point I'm running this Apache2 at work as a fun forum for staff.. not being paid to do so, just a project to keep me busy.. if only I knew a little bit more about this stuff)

---

### Post by kidders on 2007-05-27
Hmm... I'm not a Lycos user, so I've no idea what services they provide, I'm afraid.

What to do first is a question of priorities, I suppose. If external accessibility is top of the agenda, and you _do_ need name-based virtual hosting, then you'll need to arrange a dynamic DNS service.

A local DNS service (eg Bind) can be a nice convenience, but isn't essential. By the way, it sounds as though you might be running your server from within your workplace's LAN ... if so (since it presumably already provides local DNS services), having your own Bind installation would be completely pointless, since there would be no way to instruct any networked machines to use it. If you *do* install a local DNS service, the most important thing to remember is to make absolutely certain it doesn't bind to an externally accessible interface.

---

### Post by a.d.gardiner on 2007-05-28
Sounds like I'm probably barking up the wrong tree with BIND then.

I'm taking a look into 'DYNDNS'.

And your absolutely right, my Apache2 box is sat inside our LAN on the office network.

Being from a very none tech background it looks like this is starting to sink in! :)

---

### Post by kidders on 2007-05-28
If you're not very familiar with HTTP, DNS, and so on, I would suggest consulting with your office's IT people. Small things you might not think of can make big differences. For instance, if the IP of the machine running your web server isn't public, dynamic DNS solutions won't work.

There are lots of other factors worth considering. For example, using DynDNS & similar tends to attract a lot of malicious interest in the target network. You will need to make sure your office's network isn't running anything that wouldn't be able to cope.

---

### Post by a.d.gardiner on 2007-05-29
I managed to get this thing going by plugging my domain at Lycos to the a free DNS service at [Afriad FreeDNS]("http://freedns.afraid.org/menu/")

Visiting [www.chevinstaffportal.co.uk](www.chevinstaffportal.co.uk) seems to work.

I'd love to ask the IT people here (but we don't really have anybody, we're a very small outfit.. only really have static IP on our DSL so the till network guys can do maintenance). Setting up this old box as a web server is more of a side project I'm doing in my lunch hour. Will be hosting a couple of my colleagues personal sites on the box too. Really like the sense of achievement you get when something starts to work out :)

But sounds like I need to get some serious reading done on security!

Our network isn't very big, everything sits behind our router/firewall and I keep Feisty up to date. I've installed Suhosin for PHP to try secure PHPBB a little.

Many thanks for all your advice as well!

---

### Post by kidders on 2007-05-29
Looks like you have everything up and running. :-)

---

### Post by a.d.gardiner on 2007-05-29
haha.. just when I thought I was out of the woods! (perhaps I spoke too soon)

Looks like I now have a mistake somewhere in my configuration of Apache's  'Virtual Host' settings.

I've just setup 'www.soundsessions.co.uk' as before with 'Afraid FreeDNS', but it seems to point at the same site as 'www.chevinstaffportal.co.uk'?

My files in sites-enabled files look like this:

'001-chevinstaffportal.co.uk'
```
<VirtualHost *>
DocumentRoot /var/www/phpBB2/
ServerName www.chevinstaffportal.co.uk
ServerAlias chevinstaffportal.co.uk
ErrorLog /var/log/apache2/chevin-error.log
TransferLog /var/log/apache2/chevin-access.log
</VirtualHost>
```

and...

'002-soundsessions.co.uk'
```
<VirtualHost *>
DocumentRoot /home/soundsessions/
ServerName [www.soundsessions.co.uk](www.soundsessions.co.uk)
ServerAlias soundsessions.co.uk
ErrorLog /var/log/apache2/soundsessions-error.log
TransferLog /var/log/apache2/soundsessions-access.log
</VirtualHost>
```

I then  used the  'sudo a2ensite' command to enable both sites configuration files files. I disabled the site 'default', which was the original file in 'sites-available' from installing Apache2, and restarted the server 'sudo /etc/init.d/apache2 restart'

I'm still wrong somewhere?

Incidentally when I type the local address (static) of the server from any machine on the LAN (192.168.1.113) I get the site hosted for 'www.chevinstaffportal.co.uk' :(

When I get this thing nailed I might write an 'idiots guide to setting up your own apache2 by an idiot' (or at least document just exactly what I did to get my box up and running)

---

### Post by kidders on 2007-05-29
> **a.d.gardiner said:**
> haha.. just when I thought I was out of the woods!Hehe... I'd say you've made only a minor error. Tracking it down might not be easy though! Let's see...

With name-based virtual hosting, Apache essentially tries to match the "Host" request header with a virtual server (or alias). If it can't find a match, it always resorts to the default host, which (I *think*) is the first one it encounters as it trawls through its configuration file.

The trouble with Ubuntu (and similar distros) is that the standard Apache configuration is spread out among multiple files that are all included in eachother, so it can be quite difficult to isolate a problem, when something goes funny. Nothing crazy leaps out at me from what you posted, but something basic to check before doing anything else is...```
find /etc/apache2 -type f -exec grep 'NameVirtualHost' {} \;
```

> **a.d.gardiner said:**
> Incidentally when I type the local address (static) of the server from any machine on the LAN (192.168.1.113) I get the site hosted for 'www.chevinstaffportal.co.uk'Hopefully you can now follow why that is. When you type http://12.34.56.78/ into a browser's address bar, it will send something along these lines to your server...```
GET / HTTP/1.0
Host: 12.34.56.78
...
...
```Since that "Host" header won't match any sensible virtual hostname, you wind up on the fallback, default site. The technically correct way to manage this is with a local DNS service (eg Bind), which would resolve all virtual hostnames to the correct internal IP address. (Good lord... we're going around in circles hehe!)

Assuming your Ubuntu box is properly configured, typing ...```
grep -i "nameserver" /etc/resolv.conf
```... will give you the address of the server that needs to be tweaked. Once it stops shrugging its shoulders at name resolutions for your virtual hosts, they'll work as expected, both inside and outside your LAN.

---

### Post by a.d.gardiner on 2007-05-30
ohh err. lol.

The command 'grep -i "nameserver" /etc/resolv.conf' is chucking up 'nameserver 192.168.1.1'... looks like I need to start over! :(

---

### Post by kidders on 2007-05-30
> **a.d.gardiner said:**
> The command 'grep -i "nameserver" /etc/resolv.conf' is chucking up 'nameserver 192.168.1.1'... looks like I need to start over! :(What's your correct DNS server address?

Since you seem to know it's not 192.168.1.1 (which suggests you know what it really is), you can still reconfigure it to resolve your virtual hostnames appropriately for the rest of your LAN ... even if your own box won't work properly for the time being.

Did the search for "NameVirtualHost" directives throw anything up?

---

### Post by John_W on 2007-05-30
I know that kidders is VERY knowledgeable as he has helped me!

Not to Hi-Jack your post but I just want to include this Redhat LINUX link for others trying to setup a home web server. It provides some basic information to get you started.
See the link here:
[http://www.redhat.com/magazine/022aug06/features/webserver/](http://www.redhat.com/magazine/022aug06/features/webserver/)

---

### Post by a.d.gardiner on 2007-05-30
The search for 'NameVirtualHost' is throwing out:

```
NameVirtualHost *
NameVirtualHost* 
```

The readout refers to each of my virtual host files in sites-available I'm guessing.

The only reason I'm assuming that 192.168.1.1 isn't relevant here is because thats the IP of my router.

Heck' I wish I had a better idea what I was doing here ](*,)

---

### Post by kidders on 2007-05-30
Hi John_W! :-)

> **John_W said:**
> I know that kidders is VERY knowledgeableHaha... not really!

> **John_W said:**
> I just want to include this Redhat LINUX link for others trying to setup a home web server.That's a nice link. Redhat-based systems are a little different than Debian-based ones, but I have to say I often find their documentation quite helpful too.

> **a.d.gardiner said:**
> The search for 'NameVirtualHost' is throwing out:
```
NameVirtualHost *
NameVirtualHost* 
```The readout refers to each of my virtual host files in sites-available I'm guessing.Hmm... I can't help wondering if "NameVirtualHost*" (ie without the space between 't' and '*') is legal. In any case, an Apache configuration should normally only have one "NameVirtualHost" directive in it. Are you able to find where the duplicate is coming from?

 > **a.d.gardiner said:**
> The only reason I'm assuming that 192.168.1.1 isn't relevant here is because thats the IP of my router.Oh. Well that's both good *and* bad. It probably means your DNS information _is_ correct, but (assuming "router" means a tiny little box sitting in a corner somewhere) you might have trouble getting it to do what you want.

> **a.d.gardiner said:**
> Heck' I wish I had a better idea what I was doing here ](*,)Let's see if I can help...

_**DNS**_
DNS works a bit like this...[LIST=1]
[*]You try to check your Gmail in Thunderbird, or maybe perform a Google search in Firefox.
[*]The application issues a request for an IP address for pop.gmail.com (or maybe [www.google.ie](www.google.ie)), which is forwarded by your OS to your network's DNS server (192.168.1.1).
[*]Your DNS server checks its database, and realises it doesn't know anything about addresses that end in ".gmail.com" or ".google.ie", so it forwards the request to another DNS server.
[*]This action sparks a chain of requests, until somebody somewhere finds a server that knows the answer.
[*]Your local DNS service gives you Google's IP, and then stores it, so future requests for the same address won't be so time-consuming.[/LIST]_**Running services behind your firewall**_
It's good practice to look at the internet as two distinct worlds ... the stuff behind your firewall, and the rest of the planet. Superficially, you will want to blur the distinction between them though, so nobody can tell the difference in practice.

The safest and most extensible way of doing this in DNS terms is to create the following:[LIST]
[*]Requests for [www.chevinstaffportal.co.uk](www.chevinstaffportal.co.uk) originating from your LAN should resolve to 192.168.1.113, and follow that computer around, as it's (presumably DHCP-assigned) internal IP address changes. They should only involve your LAN's local DNS service.
[*]Requests originating from the outside world should resolve to 81.149.22.40, and follow *that* around, as/if your ISP changes your network's public IP. These would be forwarded to the correct internal IP by your router (although the person making the request wouldn't know that). These resolutions would involve a chain of DNS queries, ending at your dynamic DNS service providers nameservers.[/LIST]Anyhow, I'm assuming external requests are working correctly, and that remote visitors' browsers are provided with enough information to send a request to 81.149.22.40 that still has "Host: www.chevinstaffportal.co.uk" in its header.

I had also assumed that your office LAN had a software-based (Linux, or perhaps Microsoft) DNS service on it, which would make doing the same for *internal* requests trivial. I'm getting the impression that's not the case though. :-( Your alternatives in that case are...
[LIST=1]
[*]See if your router's built-in configurator is flexible enough to allow you to amend it's DNS database, or provides some mechanism for updating it (perhaps based on DHCP leases).
[*]Disable your router's network management functionality & transfer it to an actual computer on your network (ie the setup I was expecting).[/LIST]Does any of that help clear things up for you (or have I just made everything worse!!) ?

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by a.d.gardiner on 2007-05-30
:) that gives me something to be working on.

gonna grab me a coffee and sit in on this thing till i get it sorted.

---

### Post by a.d.gardiner on 2007-06-07
Okay nearly a week later, it seems that I've managed to fix things up. Both sites are now successfully being hosted by my Apache2! :p

In the end I installed 'Webmin' to help me configure my virtual hosts. I also still need to fix up BIND to sort out local requests for each site, but I think I'm understanding things better now.

In the end I ditched creating separate files to describe each of my virtual hosts in sites-available/sites-enabled and rolled everything together into one file. I did this after poking around the Apache2 documentation for so long it started to make sense and also looking over how Webmin was trying to configure the system.

Still got a few things to fix. I seem to have hosed my 'phpmyadmin' installation, but I think I'm on top of it.

Cheers for all the help :KS

---

### Post by kidders on 2007-06-07
> **a.d.gardiner said:**
> Okay nearly a week later, it seems that I've managed to fix things up. Both sites are now successfully being hosted by my Apache2! :pYay! You seem to be having a tough time of it, in that you're having to learn how things work *and* how Linux does them all at the same time.  Don't forget to post back if you get stuck on something, or (if you're sick of my opinion!), start a new thread. :-)

> **a.d.gardiner said:**
> In the end I installed 'Webmin' to help me configure my virtual hosts. I also still need to fix up BIND to sort out local requests for each site, but I think I'm understanding things better now.Nice work. Over time, I've learned not to trust Webmin very much, but it does do *certain* things quickly & cleanly. There really is no substitute for getting down & dirty with a text editor, but Webmin is still nice. :-)

> **a.d.gardiner said:**
> In the end I ditched creating separate files to describe each of my virtual hosts in sites-available/sites-enabled and rolled everything together into one file.Tut tut! That's not the Ubuntu way hehe! Seriously though, whatever way you'd like to work your config files is perfectly fine, as long as you're aware of where you've deviated from the norm.

> **a.d.gardiner said:**
> I seem to have hosed my 'phpmyadmin' installationEeek. It can be a little annoying to set up first time. For some reason, it never quite seems to work out for me either, and I wind up having to tinker with its configuration file myself. Btw, I would strongly recommend creating an unprivileged MySQL user for use with PHPMyAdmin (eg a user that can't delete databases or drop tables). I've seen a few threads that start "Help! I was logged into PHPMyAdmin as a privileged user & accidentally clicked the wrong thing..."

Anyhow, let me know if you need a hand with anything!

---

### Post by a.d.gardiner on 2007-06-14
> Nice work. Over time, I've learned not to trust Webmin very much, but it does do certain things quickly & cleanly. There really is no substitute for getting down & dirty with a text editor, but Webmin is still nice. 

I think this is something I'm becoming familiar with already.

Mainly I mention this because despite a lot of fiddling with webmin, no matter how much I tried to setup my virtual hosts configuration with it, it would just 'shrug its shoulders' (to quote your wise words).

It wasn't until I tried with my slightly unconventional method of lumping everything together in one file that things appear to work? lol ](*,)

What I'm on with now is getting BIND going to do the job of resolving internal requests for the sites /zones that my server is authoritative on. I'm going to try and get it to keep a DNS cache for all machines on the network to speed things up a little ;)

I'm wrestling with the first bit right now, still looking for a comprehensive guide.

---

### Post by kidders on 2007-06-14
Hi again,

> **a.d.gardiner said:**
> no matter how much I tried to setup my virtual hosts configuration with it, it would just 'shrug its shoulders' (to quote your wise words).Lol! (I'm trying to decide whether I'm offended!) :tongue:

> **a.d.gardiner said:**
> I'm wrestling with the first bit right now, still looking for a comprehensive guide.I find Red Hat's documentation reasonably good in this area. It does some stuff slightly differently (eg the precise locations of configuration files, and so on), but the concepts are all the same, from one distro to the next.

With DNS, it's important to really understand what's going on though ... tiny, bearly noticeable details can make enormous differences! One important piece of advice is to set TTLs very short until you're sure you've got the basics down. If your DNS clients cache  erroneous or botched up stuff that doesn't expire reasonably quickly, it's easy to start getting confused. I often find it useful to open a terminal and watch the output of **tail -f /var/log/syslog** change as I do stuff.

If you run into problems, I'd be happy to let you poke around my DNS server for a while. It's not perfect, but it's alive. :-)

---

### Post by a.d.gardiner on 2007-06-14
No seriously 'just shrug its shoulders' was totally helpful. It helped me to make sense of everything a whole lot better! :p

---

