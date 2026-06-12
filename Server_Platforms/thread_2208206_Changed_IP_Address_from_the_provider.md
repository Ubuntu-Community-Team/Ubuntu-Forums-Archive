---
title: "Changed IP Address from the provider"
date: 2014-02-27
forum: Server Platforms
---

### Post by Duane_Diaz on 2014-02-27
Hi and good day.

I currently move to another office and my Internet Provider just notify my that we cannot use the old IP Address anymore. We change the IP Address but I don't know what effect on that on my Server.

I was using:

SquirrelMail
Postfix
VNC
SSH

On the localhost I can still do everything, but on my Mail Server is there any changes? Do I need to update something? I really really don't have ANY IDEA please help me out.

---

### Post by papibe on 2014-02-27
Hi Duane_Diaz.

Is this a proper server edition, or a desktop serving as a server?

Do you receive a modem or router from your ISP?

How is your server connected to the router or the Internet?

Could you post the results of these commands on your server?
```
cat /etc/network/interfaces 
nm-tool 

```
Regards.

---

### Post by Duane_Diaz on 2014-02-27
Hallo sir papibe

Yes its Linux Ubuntu Server, when we were using our old IP address there are no problems. Now the problem is we cannot receive e-mails. But we can send emails.

Yes we have a router from the ISP I can set it up on 192.168.1.1

It wired sir, it was set up by the provider. They did the wiring.

for nm-tool:

 Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            bnx2
  State:             unmanaged
  Default:           no
  HW Address:        D4:AE:52:97:78:6B


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on

for /etc/network/interfaces



# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1


I already set the "resolv.conf" and can send emails. The problem is we cannot recieve emails and I don't know what effects it did(the change of IP address) to our Web Server.

Thank you so much! Its unbelievable how fast the response is

---

### Post by Duane_Diaz on 2014-02-27
Also It seems that the others cannot access our web site from out side the network. What do I do?

---

### Post by papibe on 2014-02-27
> **Duane_Diaz said:**
> Also It seems that the others cannot access our web site from out side the network. What do I do?
That was expected.

You can either distribute the new IP address, or (what I'd do) subscribe to a Dynamic DNS service, so you can send them a name instead of an IP (for instance myserver.np-ip.org).

Regards.

---

### Post by papibe on 2014-02-27
It looks that the server is connected to a router, so you may not need to do anything on the server.

If you got a new router, you may need to check if the LAN is set to work with 192.168.1.*, and also that the server address (192.168.1.103) is outside the range of the DHCP range.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Duane_Diaz on 2014-02-27
Sir how do I look if 192.168.1.193 is outside the range of DHCP? Also the router's LAN is set up on 192.168.1.1 already, is there chance that this is connected to port forwarding issues because the router was restarted and the port forwarding has been deleted.

---

### Post by papibe on 2014-02-27
> **Duane_Diaz said:**
> Sir how do I look if 192.168.1.193 is outside the range of DHCP?
You need to get into the router admin page. Usually you use the router url in your browser (192.168.1.1). There, you should be able to navigate though the admin pages. Find the one that manage DHCP.
> **Duane_Diaz said:**
> is there chance that this is connected to port forwarding issues because the router was restarted and the port forwarding has been deleted.
Very unlikely. Routers don't delete port forwarding rules when restarted.

On the other hand, If the router is new, or was reseted to restore factory settings, you need to create all the rules again.

Regards.

---

### Post by Duane_Diaz on 2014-02-27
Thank you sir. but sir do we need to set those up so that the others can view our web page? to make our web portal online?

---

### Post by Duane_Diaz on 2014-02-27
I already check the DHCP sir, it said its DHCP Server, Sir, what about the domain name? Should I put the domain name of the server?

---

### Post by lisati on 2014-02-27
How did others acces your website before? 

If you had a domain name, you will need to update its registration to point to your new IP address.

---

### Post by Duane_Diaz on 2014-02-27
Yes I have a domain name its [www.premier-fm.com](www.premier-fm.com). how do i Register it? They access by typing the address in the browser sir

---

### Post by Duane_Diaz on 2014-02-27
another update: It seems that they can access ung the IP address of the router, but when the domain name, they cannot access it

---

### Post by lisati on 2014-02-27
> **Duane_Diaz said:**
> Yes I have a domain name its [www.premier-fm.com](www.premier-fm.com). how do i Register it? They access by typing the address in the browser sir

You will need to log in to your domain register's control panel and set your new IP address there.

---

### Post by Duane_Diaz on 2014-02-27
Sir, where do you usually find the Domain registers control panel? is it on the router?

---

### Post by lisati on 2014-02-27
> **Duane_Diaz said:**
> Sir, where do you usually find the Domain registers control panel? is it on the router?

It's not in the router. You will need to talk to the people who provided you with the domain name, and they should be able to guide you to the correct web page to update your web site's details.

---

### Post by Duane_Diaz on 2014-02-27
I really don't get it Sir, by the way thank you. Here is what I got, I got a Host Name, I named it on our past host name which is [www.premier-fm.com](www.premier-fm.com) but still cannot reach it. Do you think the domain name is the real problem? Because I don't remember paying anything to get our domain name. Also when you type the IP address of the router I can access it. The only problem is the when type with the address I can't accress it.

---

### Post by SeijiSensei on 2014-02-27
Somebody paid to register the domain name.  Here's who they are/were:
```

Seiji@GhostWorld:~$ whois premier-fm.com

Domain Name: PREMIER-FM.COM
Registry Domain ID: 923736809_DOMAIN_COM-VRSN
Registrar WHOIS Server: whois.tucows.com
Registrar URL: http://tucowsdomains.com
Updated Date: 2013-03-06 22:44:07
Creation Date: 2007-04-13 09:23:10
Registrar Registration Expiration Date: 2014-04-13 09:23:10
Registrar: TUCOWS, INC.
Registrar IANA ID: 69
Registrar Abuse Contact Email: domainabuse@tucows.com
Registrar Abuse Contact Phone: +1.4165350123
Reseller: DOMAIN2020, LLC
Reseller: domreg@domain2020.com
Reseller: 03-77250112
Domain Status: ok
Registry Registrant ID: 
Registrant Name: NUR YASMIN BT YAHAYA
Registrant Organization: PREMIER SOLUTIONS SDN BHD
Registrant Street: NO 5, 7, JALAN BA/11, KAWASAN PERUSAHAAN BUKIT ANGUAT,
Registrant City: KAJANG
Registrant State/Province: SEL
Registrant Postal Code: 43000
Registrant Country: MY
Registrant Phone: 603-87395331
Registrant Phone Ext: 
Registrant Fax: 603-87394331
Registrant Fax Ext: 
Registrant Email: evone@premier-fm.com
Registry Admin ID: 
Admin Name: NUR YASMIN BT YAHAYA
Admin Organization: PREMIER SOLUTIONS SDN BHD
Admin Street: NO 5, 7, JALAN BA/11, KAWASAN PERUSAHAAN BUKIT ANGUAT,
Admin City: KAJANG
Admin State/Province: SEL
Admin Postal Code: 43000
Admin Country: MY
Admin Phone: 603-87395331
Admin Phone Ext: 
Admin Fax: 603-87394331
Admin Fax Ext: 
Admin Email: evone@premier-fm.com
Registry Tech ID: 
Tech Name: Nickolas Wright
Tech Organization: DOMAIN2020, LLC
Tech Street: 104, 6th Street Unit B
Tech City: Lyden
Tech State/Province: WA
Tech Postal Code: 98264
Tech Country: US
Tech Phone: 800 964 0258
Tech Phone Ext: 
Tech Fax: 800 964 0258
Tech Fax Ext: 
Tech Email: jasper@klhost.com
Name Server: NS2.WPDNS.COM
Name Server: NS1.WPDNS.COM
DNSSEC: Unsigned

Registration Service Provider:
    DOMAIN2020, LLC, domreg@domain2020.com
    03-77250112
    03-77250112 (fax)
    This company may be contacted for domain login/passwords,
    DNS/Nameserver changes, and general domain support questions.

```

Your domain name records are kept here:
```

Seiji@GhostWorld:~$ host -t ns premier-fm.com
premier-fm.com name server ns1.wpdns.com.
premier-fm.com name server ns2.wpdns.com.

```

You need to contact the registrar and repoint the "A" record for [www.premier-fm.com](www.premier-fm.com) to your new IP address.

Didn't your ISP discuss these matters with you when your IP address changed?  If not, they're not doing well by you as a customer, especially as a business customer.

---

### Post by papibe on 2014-02-27
It seems like you are inheriting someone else's job, or that the person in charge in not available.

Here's how usually works:

If you need an domain name, you go to a [registrar company]("http://en.wikipedia.org/wiki/Domain_name_registrar"), create an account, buy a domain name, and configure it to point to your IP address.

Examples of domain registrars: GoDaddy, DreamHost, etc.

When you change your static IP (as you just did), you need to:
[LIST]
[*]find out what company you registered "www.premier-fm.com" with.
[*]get the proper account name and password to get access to their admin/control panel.
[*]there, make the changes described by  SeijiSensei.
[/LIST]
That's it, it would take some time for the changes to propagate (usually up to 24hrs).

As I see it now, you need to get hold of either the person who was in charge of this, or at least the documentation left behind by the same person.

Hope that helps. Let us know how it goes.
Regards.

---

### Post by Duane_Diaz on 2014-02-27
HOLY COW! This site is FULL OF AWSOME PEOPLE! Thank you sir papibe, thank you sir lisati and thank you sir Seiji Sensei. The thing is, when I got this job I don't have any information or documentation about anything YES ABOUT ANYTHING. Now I got the site online again thanks to the secretary of the company(bare with me we are only 3 in this large company for gods sake) Thank you again. This topic has been SOLVED! We fix it after we request to point the domain name on the new IP Address. Thank you so much. Ill go visit here and read some topics from now on!!

---

