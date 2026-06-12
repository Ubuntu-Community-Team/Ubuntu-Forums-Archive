---
title: "Associate internal ISS with website hosted by Apache"
date: 2011-04-18
forum: Server Platforms
---

### Post by pepsifx357 on 2011-04-18
Hey guys, we have a dual server setup: Windows server 2003 and Ubuntu 10.04 with apache installed with all the goodies.  This is all virtualized.

What I'm wanting to do, is make the new website we've created run on the Ubuntu machine, which it is, and be accessible outside the office.  However, by doing this, we forfeit being able to use remote access or web exchange on Windows server 2003.

How can I create a link from the new website on Apache point to the internal server and it work outside of the office?

---

### Post by pepsifx357 on 2011-04-18
No bites?

---

### Post by pepsifx357 on 2011-04-20
bump

---

### Post by volkswagner on 2011-04-20
You may have better luck on a Windows forum if you wan the Windows Server to be the main web server.

Have a look into reverse proxy for your specific server.

Here is a link for [IIs 7]("http://forums.iis.net/t/1156458.aspx") which may get you started.

---

### Post by pepsifx357 on 2011-04-20
> **volkswagner said:**
> You may have better luck on a Windows forum if you wan the Windows Server to be the main web server.

Have a look into reverse proxy for your specific server.

Here is a link for [IIs 7]("http://forums.iis.net/t/1156458.aspx") which may get you started.

No, I want linux, apache, mysql, php, and samba to do as much as possible.  Since I can't get around not having Active Directory or Exchange at work, I have to keep those.  However, in order to keep those functioning, the Exchange->IIS connector needs to be able to talk to the user over the internet along with the website hosted by apache, so that people can still use exchange web-mail.

In my opinion, Windows is not stable enough to run a web-server.  Ours actually turns off a few times per week, leaving us without a website.  I have to manually restart IIS to get it running again.

I would go FULL LINUX if I could.

---

### Post by usatonycuba on 2011-04-20
Why not to create your LAMP, as your primary server, install a FQDN, and then... create virtual host (IP based) pointing to your Windows machine, where it would be (are) your web-mail. ??

---

### Post by pepsifx357 on 2011-04-21
> **usatonycuba said:**
> Why not to create your LAMP, as your primary server, install a FQDN, and then... create virtual host (IP based) pointing to your Windows machine, where it would be (are) your web-mail. ??

Wouldn't I have to forward port 80 to the Windows machine or does the Virtual Host take care of that?

---

### Post by usatonycuba on 2011-04-21
> **pepsifx357 said:**
> Wouldn't I have to forward port 80 to the Windows machine or does the Virtual Host take care of that?
Example of a Simple name-based vhosting

The server machine has a primary name server.domain.tld. There are two aliases (CNAMEs) [www.domain.tld](www.domain.tld) and [www.sub.domain.tld](www.sub.domain.tld) for the address server.domain.tld.
```

    ...
    Port 80
    ServerName server.domain.tld

    NameVirtualHost *:80

    <VirtualHost *:80>
    DocumentRoot /www/domain
    ServerName www.domain.tld
    ...
    </VirtualHost>
    
    <VirtualHost *:80>
    DocumentRoot /www/subdomain
    ServerName www.sub.domain.tld
    ...
    </VirtualHost> 

```
**Or**

 The server machine has one IP address (111.22.33.44) which resolves to the name server.domain.tld. There are two aliases (CNAMEs) [www.domain.tld](www.domain.tld) and [www.sub.domain.tld](www.sub.domain.tld) for the address 111.22.33.44.
 ```

     ...
    Port 80
    ServerName server.domain.tld

    NameVirtualHost 111.22.33.44 

    <VirtualHost 111.22.33.44>
    DocumentRoot /www/domain
    ServerName www.domain.tld
    ...
    </VirtualHost>
    
    <VirtualHost 111.22.33.44>
    DocumentRoot /www/subdomain
    ServerName www.sub.domain.tld
    ...
    </VirtualHost> 
 
```
 
 Now make sure to set propper sets at your Router/Firewall (port wowarding, port redirection, internal permanent-ip based maquine set.. etc)

---

