---
title: "small office network setup"
date: 2008-07-14
forum: Server Platforms
---

### Post by sparkles on 2008-07-14
we currently have a fairly messy network setup in the office and i'm looking for peoples opinion on how i can tidy it up.

at the moment there are are 8 computers, 6 running xp (i think 3 are home and 3 are pro), 1 running 98 and a file server running xp pro and ubuntu under vmware. the 7 workstations are networked in that they all belong to the same workgroup but they aren't members of a domain (i won't tell you that all passwords to log into windows are all really easy and the same of every workstation, that would just be way too embaressing :)). our mail is hosted on our web server and everyone downloads their mail via pop3 which is stored locally on each workstation. backup of mail is done via sharing the folders mail is stored in. for internet access we use our adsl router as the gateway. we have port forwarding setup for a few things that we want to access from outside the office on the weekends.

there are some things that are prompting this tidy up, 1 is we have no shared address book and the other is that we're probably going to purchase a jira license. what i'm really hoping to do is abrogate the need for people to only have a local copy of their email, a shared address book of all our customers, sso or at least ldap authentication so people have 1 username and password for all applications, and real security (rather than just through obscurity).

what i think i need to setup is:
- samba (as a pdc)
- bind
- zimbra or something similar
- a firewall (maybe?)
- vpn server

the mail server needs to be setup as a secondary server so it handles mail for local users but forwards mail for any other domain to our external mail server. i'm also guessing that it would probably download mail using fetchmail rather than having the mail delivered directly to it.

is there a good guide for doing all of this stuff? i think the basics are easy enough to do but things like the hostname of the server being *server*.**domain.com** and what implications that has for the rest of the network, and how it ties in with dns are the things my mind boggles over.

any help/advice is much appreciated.
tia

---

### Post by windependence on 2008-07-15
Well you got a few things to think about. XP home does not have some networking capabilities.

You probably don't need to set up a full domain, and if you do, you will have to upgrade the XP home machines and maybe the 98 machine as well. Using SAMBA can be done with a workgroup.

I don't think you need to set up a DNS server unless you really want to so you may not need bind.

Zimbra is a great choice for collaboration, and you could set it up as an IMAP server so mail would stay on the server. Zimbra does like to have it's own box though. You may be able to run it in a VM.

Just maybe a firewall? Yes, you need a firewall but I would recommend a hardware firewall. A simple SOHO unit should be fine here.

For VPN you can use OpenVPN.

Here are some tutorials:

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

[http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend)

[http://www.thebakershome.net/openvpn_tutorial](http://www.thebakershome.net/openvpn_tutorial)

Hope this helps!

-Tim

---

### Post by sparkles on 2008-07-15
> **windependence said:**
> I don't think you need to set up a DNS server unless you really want to so you may not need bind.

the reason i thought i'd need a dns server is that in all the howtos i've read (ldap, mail, dns etc) they all assume the hostname of the machine is *something*.domain.com, not just *something*, and the zimbra instructions for making it play nice with apache assumes the use of a subdomain, which would mean i would have to be running a dns server, right?

hypothetically if i were to make the hostname something.domain.com does that mean that the hostnames of the other computers on the network would be theirname.domain.com? and considering dns for our web/mail server is currently hosted else does that mean i'd have to work some magic to make it all work properly?

thanks again

---

### Post by windependence on 2008-07-15
DNS is something many people don't quite understand. External DNS (for your web site) and internal DNS are not (usually) related. You can call your internal machines and network anything you want. Your hostname is set to the server name whatever. Your domain is specified and then you have your FQDN whatever.yourdomain.tld. It could be sparkles.messynetwork.nix if you want it to be on the internal network. each machine on the domain would then be machine1.messynetwork.nix, etc.

With Zimbra, you just make sure you have an FQDN listed in your hists file eg. zimbra.messynetwork.nix. If you are going to serve mail, it would be nice if your internal domain was the same as your mail domain, but it does not have to be that way.

One thing that bugs me is that here it seems like every N00b wants to set up a DNS server using BIND. It's not really necessary unless you have tons of computers where it would be a pain to put all those aliases in the hosts file.

-Tim

---

### Post by dbenamy on 2010-08-09
I'm working on this type of guide at [http://www.benamy.info/guides/setting-up-a-small-linux-network](http://www.benamy.info/guides/setting-up-a-small-linux-network)

Edit: Now that I read the request more carefully, I see that what I'm working on isn't an exact match. But some of it may still be useful.

---

### Post by HermanAB on 2010-08-09
Howdy,

Eight PCs do not justify the hassle of a DNS and domain authentication.  Wait till you have 20.

You should be able to do fine with Samba simple user/password authentication and IP addresses defined in the hosts files.

---

