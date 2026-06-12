---
title: "DNS zone needed or not?"
date: 2011-06-13
forum: Server Platforms
---

### Post by Dutchbeer on 2011-06-13
I build a webserver following the HOWTO: [http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3]("http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3").
I have my own domain name registered at register.com and it is tied into my static public IP. My intention is to host some more websites for others.

Should I still use the DNS server and create the DNS records for my domain using ISPConfig, or is that not needed?
If I don't do this can I then still create domains names for others using my server?

Please advice.

---

### Post by SeijiSensei on 2011-06-15
You'd still need to register those domains with a registrar, so why not use the servers the registrar provides?  If you want to host your own domains, you [must]("http://www.zoneedit.com/doc/rfc/rfc1034.txt") have **two** servers available, one primary and one backup.  So I'd recommend registering any other names you wish to host at your current registrar, and set up the A record for the www host to point to your server.

You can have as many domains as you wish point to a common web server.  If you're running Apache, you just need to define virtual hosts.  Any decent introduction to hosting on Apache will explain how to do that.

---

### Post by falko on 2011-06-15
> **Dutchbeer said:**
> 
Should I still use the DNS server and create the DNS records for my domain using ISPConfig, or is that not needed?
If I don't do this can I then still create domains names for others using my server?

If you define DNS records in your registrar's web panel, then you don't need to configure BIND and use the DNS part of ISPConfig.

---

### Post by Dutchbeer on 2011-06-15
Thanks guys for your help. :p

---

