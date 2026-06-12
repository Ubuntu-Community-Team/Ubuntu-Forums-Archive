---
title: "How to transer domain/SSL Question"
date: 2011-10-01
forum: Server Platforms
---

### Post by CwTechies on 2011-10-01
I plan on setting up and running my own website; using ubuntu server 11.04. I know how to set up everything but two things. 
 
1) How do you transer a domain from a major hosting company to your own ubuntu server? I don't want to have to use something like dyndns.org.
 
2) How do you setup a signed SSL certificates from a CA such as VeriSign on a ubuntu server? Do they send you the files and you just place them in the right directory?
 
 
Thanks.

---

### Post by Ryan Dwyer on 2011-10-01
Hosting companies tend to host more than just your website. They might host your DNS as well and might be the registrar for your domain. They might also host your email. You need to know exactly what services they provide and what services you want to migrate.

You need a static IP if you don't want to use DynDNS. Your ISP would also need to allow you to "run servers" (ie. allow incoming port 80 traffic) on your internet plan.

If you already have SSL with your current provider then you may be able to get them to send you your website's private key. You can then use the private key along with your website's certificate (which is publicly available).

If that isn't possible, you'd need to generate your own private/public keypair and a certificate signing request (CSR). This gets sent to a CA, they sign it (after you pay them...) and they send you the signed certificate back. You store it on your server and configure Apache to use the certificate.

---

### Post by Jonathan L on 2011-10-01
> **CwTechies said:**
> I plan on setting up and running my own website; using ubuntu server 11.04. I know how to set up everything but two things. 
 
1) How do you transer a domain from a major hosting company to your own ubuntu server? I don't want to have to use something like dyndns.org.
 
2) How do you setup a signed SSL certificates from a CA such as VeriSign on a ubuntu server? Do they send you the files and you just place them in the right directory?
 
 
Thanks.

Hi CW

Just a note about addressing: If your IP address isn't static, you might find yourself using dyndns just to get your current IP address working, and have a CNAME record in your real domain, which you'd set up on your DNS control panel from your hosting companyC

```
www.example.com. CNAME  cwtechiehouse.dyndns.org.
```Per Ryan's comments though, you have to be quite sure which services you want to move to your own server.

Hope that's of some use.

Kind regards,
Jonathan.

---

### Post by Ryan Dwyer on 2011-10-01
> **Jonathan L said:**
> www.example.com. PTR cwtechiehouse.dyndns.org.

You mean CNAME, not PTR.

---

### Post by sampatho2 on 2011-10-01
sorry to post here.
But can anyone tell me where to get j ee and how to install?

---

### Post by ubudog on 2011-10-01
> **sampatho2 said:**
> sorry to post here.
But can anyone tell me where to get j ee and how to install?

Please start a new thread.  You will get much more help that way.  :)

---

### Post by CwTechies on 2011-10-01
Don't want to read? skip to the red part, it's the short version.
Thank you for all the replys, I have a static IP, and I've got a self-signed SSL working remotely before. I have got SSH, HTTP, and HTTPS working remotely so I know it will work.
 
I've done some research and thanks to one of you I understand how to get a signed SSL, you pay the CA, you send the request, they send it signed you replace it and setup apache for it.
 
As far as hosting my own domain I have no clue, like I said I rather not use dyndns or something like it. It says you can only get like 600,000 people a month...I don't like having limits (even though all my sites together only get about 500 people a month -atm).
 
[COLOR=red]So all I need to know is how to host my own domain. I got a static IP and every works, I just need to transer the domain from a major host. (1&1 to be extact)[/COLOR]

---

### Post by Jonathan L on 2011-10-01
> **CwTechies said:**
> Don't want to read? skip to the red part, it's the short version.
Thank you for all the replys, I have a static IP, and I've got a self-signed SSL working remotely before. I have got SSH, HTTP, and HTTPS working remotely so I know it will work.
 
I've done some research and thanks to one of you I understand how to get a signed SSL, you pay the CA, you send the request, they send it signed you replace it and setup apache for it.
 
As far as hosting my own domain I have no clue, like I said I rather not use dyndns or something like it. It says you can only get like 600,000 people a month...I don't like having limits (even though all my sites together only get about 500 people a month -atm).
 
[COLOR=red]So all I need to know is how to host my own domain. I got a static IP and every works, I just need to transer the domain from a major host. (1&1 to be extact)[/COLOR]

Hi again Gareth

By "host your own domain" I understand you to mean run your web server (and other services) on your own computer(s) on your static IP addresses.  There is in pricinple complete separation between running web and mail servers and the DNS for them.

In the end, you just put address records into your zonefiles, normally by using the web interface at 1&1 to add things like:

```
www.yourdomain1.com. A 1.2.3.4
www.yourdomain2.com. A 1.2.3.4

```And then have your web servers set up to deal with name-based virtual hosts or however you want to do it.

If you want to do your own mail server, 
```
yourdomain1.com. MX 10 mail.yourdomain1.com.
yourdomain2.com. MX 10 mail.yourdomain1.com.
```Sending mail can be more tricky, as most recipients won't accept mail from you unless your reverse lookups match, and you usually need to get your reverse addresses sorted out at your ISP which controls your IP address 1.2.3.4, and you get them to put
```
4.3.2.1.in-addr.arpa. PTR mail.yourdomain1.com.
```If you want to run your own DNS too, then install bind or whichever nameserver you prefer, and set up the zone files as above.  You change the nameserver addresses in the control panel at 1&1 to something like
```
yourdomain1.com. NS ns1.yourdomain1.com.
and then you give them the glue record
ns1.yourdomain1.com. A 1.2.3.4
```But be warned: hosting your own DNS can be fiddly especially for multiple domains because of the requirement for:

[LIST]
[*]Glue records for nameservers inside their own domains
[*]Multiple nameservers for a domain, ideally in different domains
[*]The complexities of managing secondaries
[/LIST]
I took a look at 1&1's web site and they say you can 
> **[SIZE=1]1&1 DNS management provides you with complete flexibility to:[/SIZE]**


[LIST]
[*]Point your domain names to any static IP address or hostname.
[*]Point your domain to 1&1 name servers.
[*]Assume up to four name servers of your own choice.
[*]Only one name server at your disposal? Use a 1&1 name server as a backup.
[*]Use 1&1 name servers and set your own mx records.
[/LIST]
Hope that's addressed your target a bit better.

Kind regads
Jonathan

---

