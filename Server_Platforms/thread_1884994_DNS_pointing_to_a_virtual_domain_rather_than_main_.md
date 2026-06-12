---
title: "DNS pointing to a virtual domain rather than main server domain?"
date: 2011-11-22
forum: Server Platforms
---

### Post by CoolBreeze47 on 2011-11-22
Let's say my server machine is "server1.example.com" and I have 3 different name-based virtual domains under server1.example.com. For instance...

server1.example.com (name of my server machine - DocumentRoot/Directory is public_html)
[www.site1.com]("http://www.site1.com") (a virtual domain - DocumentRoot/Directory is public_html\site1)
[www.site2.com]("http://www.site2.com") (another virtual domain - DocumentRoot/Directory is public_html\site2)
[www.site3.com]("http://www.site3.com") (yet another virtual domain - DocumentRoot/Directory is public_html\site3)

Do I first have to point the DNS (in my registrar) to server1.example.com before any of the virtual doamins will work or can I point the DNS to only a single virtual domain (by itself) without pointing anything to the example.com domain (my machine's name)?.

What is happening is that example.com is resolving very quickly but site1 seems to be taking forever to resolve or not resolving at all when I only point the DNS to it.

Incidentally, "example.com" (not the actual name of course) is registered with Network Solutions and "site1.com", "site2.com" and "site3.com" are registered with Godaddy.com.

Not sure if the issue is what I asked about above -or- if one registrar simply takes much longer to deal with DNS changes than the other.

Can anyone here provide some input on this?.

- Much appreciated!, CB

---

### Post by newbie-user on 2011-11-22
If you're using name-based virtual hosts, then your DNS for all your sites needs to be pointed to the public ip address of the server.  For example:

server1.example.com  12.34.56
[www.site1.com](www.site1.com)  12.34.56
[www.site2.com](www.site2.com)  12.34.56
[www.site3.com](www.site3.com)  12.34.56

DNS will take care of pointing web traffic to your physical server, then the webserver (are you using apache or something else?) will take care of the name-based virtual hosts and send traffic to the appropriate DocumentRoot

---

### Post by SeijiSensei on 2011-11-22
Alternatively you can configure an A record for the example.com site and use CNAMEs for the other sites.  I doubt this would affect performance though.

---

### Post by CoolBreeze47 on 2011-11-22
@[newbie-user]("http://ubuntuforums.org/member.php?u=464569") - Thanks for the reply. Yes, I've done that in the hosts file and in Apache.

@SeijiSensei - All of my DNS records (for all domains) are already set up on a reliable DNS server.

Was just wondering...does Godaddy usually take longer to deal with DNS changes than other registrars?.

---

### Post by newbie-user on 2011-11-22
> **CoolBreeze47 said:**
> @[newbie-user]("http://ubuntuforums.org/member.php?u=464569") - Thanks for the reply. Yes, I've done that in the hosts file and in Apache.

@SeijiSensei - All of my DNS records (for all domains) are already set up on a reliable DNS server.

Was just wondering...does Godaddy usually take longer to deal with DNS changes than other registrars?.

I didn't mean for that to go into the hosts file.  The hosts file is for name resolution for an individual machine's use only.  I meant to set up your DNS with Network Solutions and GoDaddy so that site1, site2, site3 all point to the public ip address of your server.

---

