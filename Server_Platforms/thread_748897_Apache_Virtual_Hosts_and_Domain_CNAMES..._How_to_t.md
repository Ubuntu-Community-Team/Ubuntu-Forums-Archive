---
title: "Apache Virtual Hosts and Domain CNAMES... How to test?"
date: 2008-04-07
forum: Server Platforms
---

### Post by luvit on 2008-04-07
i host my server: DynDNS Custom DNS (mydomain.com)

then i bought 2 domain names from GoDaddy.com (site1 & site2)
these domains seem to work just fine without Apache Virtual Hosts
godaddy site1 forwarding w/ masking to mydomain.com/site1
godaddy site1 CNAME [www.site1.com](www.site1.com) points to @ (site1.com)
godaddy site2 forwarding w/ masking to mydomain.com/site2
godaddy site2 CNAME [www.site1.com](www.site1.com) points to @ (site2.com)

results
site1 shows it's own index.html from mydomain.com/site1/index.html
[www.site1](www.site1) shows it's own index.html from mydomain.com/site1/index.html
set2 shows it's own index.html from mydomain.com/site2/index.html
[www.site2](www.site2) shows it's own index.html from mydomain.com/site2/index.html

[LIST]
[*]all this very basic testing works before setting up Apache Virtual Hosts
[*]so what is the purpose of Apache Virtual Hosts?
[*]i now believe i have Apache Virtual Hosts installed
[*]how do i effectively test the Virtual Hosts since I had success before Virtual Hosts were configured??
[/LIST]
I have not installed SMF, yet until I know I have the foundation right.

i followed the directions of this thread to setup virtual hosts: [http://ubuntuforums.org/showthread.php?t=608626&highlight=apache+virtual+hosts](http://ubuntuforums.org/showthread.php?t=608626&highlight=apache+virtual+hosts)

---

### Post by MJN on 2008-04-08
Post your domain names and Apache config. Your post is too confusing without it!

Mathew

---

