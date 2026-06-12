---
title: "fqdn gone awry"
date: 2008-09-15
forum: Server Platforms
---

### Post by MartinHansell on 2008-09-15
Hi,

In the process of trying to solve the warning from apache2 when restarting that there was no fqdn, I somehow managed to mess up my installation a wee bit.

I have a few sites all supported by the DynDNS service, and my main link-site (the 1st <virtualhost> in "sites-available") is [http://controlcentre.homelinux.net](http://controlcentre.homelinux.net).  Underneath this site are a few more virtual hosts with various names.

After looking at various forum tips, I was led to changing the kernel.domainname in the sysctl file, which is now set to localhost (don't ask me why... I couldn't possibly explain my logic - which of course is a contradiction)

I am not sure if that is the cause of my current problem, but I think so, coz accessing my main site became a problem directly after that.  If you try to access the site you just get a listing of the directories in the site directory tree, but trying to access index.php page gives a 404.

Here's a bit more info that may help you to help me... I do hope so, and  many thanks in advance...

hostname returns Mangostine
hostname --fqdn returns hostname: Unknown host
dnsdomainname returns : Unknown host
sysctl kernel.domainname returns controlcentre.homelinux.net

I resolved the fqdn problem by adding the ServerName [Mangostine] directive directly into my apache2.conf file... is this correct?

---

