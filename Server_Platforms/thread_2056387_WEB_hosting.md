---
title: "WEB hosting"
date: 2012-09-11
forum: Server Platforms
---

### Post by Jorel on 2012-09-11
Hi guys,, 

Sorry i just dont know who and where to ask so i'll start in this community,, im done setting up my Ubuntu 12.04 server (Samba, Print and Web) but my next problem is we have a Domain name but our site is being hosted by other support who's now not supporting us, so we decided to get the domain name for the website, but the thing is, i dont know how to mask it with my IP address so that the world can see the website that i did.. can you help me guys or just point me to something.

Thanks

---

### Post by d3v1150m471c on 2012-09-11
you should talk to your domain provider about publishing an A record

---

### Post by Jorel on 2012-09-11
> **d3v1150m471c said:**
> you should talk to your domain provider about publishing an A record

so its just not the domain name that im after at? its also the A record? is there anything else that i need to keep in mind or ask to my domain provider?

---

### Post by dragonfly41 on 2012-09-11
You might find that creating an account with zoneedit.com or dyndns.com as an intermediary will give you some more flexibility in mapping your domain name to hosted services.   You can instruct your registrar to use zoneedit name servers.

Also [http://dns.squish.net/](http://dns.squish.net/) allows you to monitor the propagation of domain records after changes.

---

### Post by d3v1150m471c on 2012-09-11
any reasonable registrar should be able to correct this for you if you complain to them.

---

### Post by SeijiSensei on 2012-09-11
The DNS servers for your domain include an A record which points the hostname [www.yourdomain.com](www.yourdomain.com) to the IP address where the web site resides.  If you can change that record to point to a publicly-visible IP address that connects to your server, that's all you really need to change.  If your DNS records are hosted by your domain registrar, then that's the place to start.  If you are not sure what sort of arrangements govern your domain, try these steps:

First, let's see who the registrar is and who are listed as the domain's administrators.  Install the program whois using the command "sudo apt-get install whois".  Then use the command "whois domain.name" to find out about your domain.  Here's an example of what you would see using "whois ubuntu.com":

```

[lots of cruft removed]
Registrant:
        James Troup
        Canonical, Ltd.
        One Circular Road
         Douglas Isle of Man IM1 1AF
        GB
        hostmaster@canonical.com +44.1624643643 Fax: -

    Domain Name: ubuntu.com

        Registrar Name: Markmonitor.com
        Registrar Whois: whois.markmonitor.com
        Registrar Homepage: http://www.markmonitor.com

    Administrative Contact:
        James Troup
        Canonical, Ltd.
        One Circular Road
         Douglas Isle of Man IM1 1AF
        GB
        hostmaster@canonical.com +44.1624643643 Fax: -
    Technical Contact, Zone Contact:
        James Troup
        Canonical, Ltd.
        One Circular Road
         Douglas Isle of Man IM1 1AF
        GB
        hostmaster@canonical.com +44.1624643643 Fax: -

    Created on..............: 2004-05-29.
    Expires on..............: 2014-05-29.
    Record last updated on..: 2012-02-12.

    Domain servers in listed order:

    ns1.canonical.com
    ns3.canonical.com
    ns2.canonical.com

```

Notice that the nameservers for ubuntu.com are ns1-ns3.canonical.com.  If you were ubuntu.com, you would need to contact canonical.com to change the DNS records.

In Canonical's case their domains are registered with MarkMonitor, a company that monitors domain abuse and potential trademark infringement.  However MarkMonitor does not itself maintain the servers for ubuntu.com; those are managed by Canonical.

---

### Post by Jorel on 2012-09-12
Hi SeijiSensei,

i entered whois domain.name and i got these...

> 
Disclaimer: VeriSign, Inc. makes every effort to maintain the
completeness and accuracy of the Whois data, but cannot guarantee
that the results are error-free. Therefore, any data provided
through the Whois service are on an as is basis without any
warranties.
BY USING THE WHOIS SERVICE AND THE DATA CONTAINED
HEREIN OR IN ANY REPORT GENERATED WITH RESPECT THERETO, IT IS
ACCEPTED THAT VERISIGN, INC. IS NOT LIABLE FOR
ANY DAMAGES OF ANY KIND ARISING OUT OF, OR IN CONNECTION WITH, THE
REPORT OR THE INFORMATION PROVIDED BY THE WHOIS SERVICE, NOR
OMISSIONS OR MISSING INFORMATION. THE RESULTS OF ANY WHOIS REPORT OR
INFORMATION PROVIDED BY THE WHOIS SERVICE CANNOT BE RELIED UPON IN
CONTEMPLATION OF LEGAL PROCEEDINGS WITHOUT FURTHER VERIFICATION, NOR
DO SUCH RESULTS CONSTITUTE A LEGAL OPINION. Acceptance of the
results of the Whois constitutes acceptance of these terms,
conditions and limitations. Whois data may be requested only for
lawful purposes, in particular, to protect legal rights and
obligations.  Illegitimate uses of Whois data include, but are not
limited to, unsolicited email, data mining, direct marketing or any
other improper purpose.  Any request made for Whois data will be
documented by VeriSign, Inc. but will not be used for any commercial purpose whatsoever.
 ****
Not available for second level registration.
Third level registrations may be available on this name.


i dont know if its the server having a problem or i just dont know what im doing here...

but when i got to the web and hit whois, i got these...

```

   Registration Service Provider:
      Hostopia.com Inc, d/b/a Aplus.net
      +1.8772758763
      [email]dns@cs.aplus.net[/email]


   Registrant:
      Why Plus
      Why Plus
      Hammra 
      Hammra,  961
      LB
      Phone: +1.70300161
      Email: [email]domain@whyplus.net[/email]


   Domain Name: bardawilqatar.com

   Administrative Contact:
      Why Plus
      Why Plus
      Hammra 
      Hammra,  961
      LB
      Phone: +1.3878811
      Email: [email]domain@whyplus.net[/email]


   Technical  Contact:
      Why Plus
      Why Plus
      Hammra 
      Hammra,  961
      LB
      Phone: +1.3878811
      Email: [email]domain@whyplus.net[/email]


   Registrar of Record: 
      Hostopia.com Inc. d/b/a Aplus.net, [www.aplus.net](www.aplus.net)
      Record last updated on 2012-01-30
      Record expires on 2012-11-19
      Record created on 2007-11-19
 
   Domain servers in listed order:
      ns1.911-host.com
      ns2.911-host.com

```

so in my case, i need to contact 911-host.com?

---

### Post by Bucky Ball on 2012-09-12
*Moved to **Server Platforms***

---

### Post by dragonfly41 on 2012-09-12
If you are the owner of the domain name (registrar aplus.net)

bardawilqatar.com

you go here ..

[http://www.aplus.net/contacts](http://www.aplus.net/contacts)

Choose department .. domain services

**Or** login to your aplus.net control panel.

You then ask to transfer your name servers to some other host of your choice.

Your current name servers are ..

     ns1.911-host.com
     ns2.911-host.com

Your new name servers will be provided by your chosen hosted service.

You can *optionally* use squish.net to monitor the transfer progress which might take 24 hours + to propagate.

---

### Post by Jorel on 2012-09-12
thats the problem,, i dont know who aplus.net is... and all i know for now is that i need to get the our name (so i can mask my IP or whatever i needed to do with it to my server) coz most of our customers and partners are still contacting us with that website address,, all im contacting is the one at the bottom of the webpage named "Media Network" (coz its indicated there that they powered the website)

---

### Post by sandyd on 2012-09-12
You registered your domain name when you went with 911-host right?

Then, you need to talk to 911-host to release/transfer your domain name. They are the ones who registered your domain name, and they are the ones with control over it.

---

### Post by SeijiSensei on 2012-09-12
As I said before, you do not need to transfer the domain.  Right now you just need to get the A record for your site to point to the new server.  You may want to transfer the domain eventually, but in the short term focus on fixing the A record.

---

