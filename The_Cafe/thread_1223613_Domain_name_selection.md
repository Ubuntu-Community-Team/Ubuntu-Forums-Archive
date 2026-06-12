---
title: "Domain name selection"
date: 2009-07-26
forum: The Cafe
---

### Post by sefs on 2009-07-26
Can some one suggest some safe utilities that I can use safely in order to check the availability of domain names.

I asked because I know network solutions has/had a policy of registering the domain with themselves if you checked it on their site, forcing you to register with them, if you did not want to wait a couple of days until they released it.

---

### Post by chris200x9 on 2009-07-26
put it in firefox and see if anything at all loads?

---

### Post by mr.propre on 2009-07-26
in the  terminal: whois <domain name>

Here a nice example:
```

stijn@Lappie-II:~$ whois ubuntuforums.com

Whois Server Version 2.0

Domain names in the .com and .net domains can now be registered
with many different competing registrars. Go to http://www.internic.net
for detailed information.

   Domain Name: UBUNTUFORUMS.COM
   Registrar: MARKMONITOR INC.
   Whois Server: whois.markmonitor.com
   Referral URL: http://www.markmonitor.com
   Name Server: NS1.CANONICAL.COM
   Name Server: NS2.CANONICAL.COM
   Name Server: NS3.CANONICAL.COM
   Status: clientDeleteProhibited
   Status: clientTransferProhibited
   Status: clientUpdateProhibited
   Updated Date: 21-jan-2009
   Creation Date: 09-oct-2004
   Expiration Date: 09-oct-2010

>>> Last update of whois database: Sun, 26 Jul 2009 16:14:39 UTC <<<

NOTICE: The expiration date displayed in this record is the date the 
registrar's sponsorship of the domain name registration in the registry is 
currently set to expire. This date does not necessarily reflect the expiration 
date of the domain name registrant's agreement with the sponsoring 
registrar.  Users may consult the sponsoring registrar's Whois database to 
view the registrar's reported date of expiration for this registration.

TERMS OF USE: You are not authorized to access or query our Whois 
database through the use of electronic processes that are high-volume and 
automated except as reasonably necessary to register domain names or 
modify existing registrations; the Data in VeriSign Global Registry 
Services' ("VeriSign") Whois database is provided by VeriSign for 
information purposes only, and to assist persons in obtaining information 
about or related to a domain name registration record. VeriSign does not 
guarantee its accuracy. By submitting a Whois query, you agree to abide 
by the following terms of use: You agree that you may use this Data only 
for lawful purposes and that under no circumstances will you use this Data 
to: (1) allow, enable, or otherwise support the transmission of mass 
unsolicited, commercial advertising or solicitations via e-mail, telephone, 
or facsimile; or (2) enable high volume, automated, electronic processes 
that apply to VeriSign (or its computer systems). The compilation, 
repackaging, dissemination or other use of this Data is expressly 
prohibited without the prior written consent of VeriSign. You agree not to 
use electronic processes that are automated and high-volume to access or 
query the Whois database except as reasonably necessary to register 
domain names or modify existing registrations. VeriSign reserves the right 
to restrict your access to the Whois database in its sole discretion to ensure 
operational stability.  VeriSign may restrict or terminate your access to the 
Whois database for failure to abide by these terms of use. VeriSign 
reserves the right to modify these terms at any time. 

The Registry database contains ONLY .COM, .NET, .EDU domains and
Registrars.
-----------------------------------------------------------------------
MarkMonitor, the Global Leader in Enterprise Brand Protection

Domain Management
Online Trademark Protection
Online Channel Protection
AntiPhishing Solutions
-----------------------------------------------------------------------
The Data in MarkMonitor.com's WHOIS database is provided by MarkMonitor.com
for information purposes, and to assist persons in obtaining information
about or related to a domain name registration record.  MarkMonitor.com
does not guarantee its accuracy.  By submitting a WHOIS query, you agree
that you will use this Data only for lawful purposes and that, under no
circumstances will you use this Data to: (1) allow, enable, or otherwise
support the transmission of mass unsolicited, commercial advertising or
solicitations via e-mail (spam); or  (2) enable high volume, automated,
electronic processes that apply to MarkMonitor.com (or its systems).
MarkMonitor.com reserves the right to modify these terms at any time.
By submitting this query, you agree to abide by this policy.

Registrant:
        James Troup
        Canonical, Ltd.
        One Circular Road
         Douglas Isle of Man IM1 1AF
        GB
        hostmaster@canonical.com +44.1624643643 Fax: -

    Domain Name: ubuntuforums.com

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

    Created on..............: 2004-10-09.
    Expires on..............: 2010-10-09.
    Record last updated on..: 2009-07-09.

    Domain servers in listed order:

    ns1.canonical.com
    ns3.canonical.com
    ns2.canonical.com
    



-----------------------------------------------------------------------
MarkMonitor, the Global Leader in Enterprise Brand Protection

Domain Management
Online Trademark Protection
Online Channel Protection
AntiPhishing Solutions
-----------------------------------------------------------------------


```

---

### Post by sefs on 2009-07-26
> **mr.propre said:**
> in the  terminal: whois <domain name>

Here a nice example:
```

stijn@Lappie-II:~$ whois ubuntuforums.com

Whois Server Version 2.0

Domain names in the .com and .net domains can now be registered
with many different competing registrars. Go to http://www.internic.net
for detailed information.

   Domain Name: UBUNTUFORUMS.COM
   Registrar: MARKMONITOR INC.
   Whois Server: whois.markmonitor.com
   Referral URL: http://www.markmonitor.com
   Name Server: NS1.CANONICAL.COM
   Name Server: NS2.CANONICAL.COM
   Name Server: NS3.CANONICAL.COM
   Status: clientDeleteProhibited
   Status: clientTransferProhibited
   Status: clientUpdateProhibited
   Updated Date: 21-jan-2009
   Creation Date: 09-oct-2004
   Expiration Date: 09-oct-2010

>>> Last update of whois database: Sun, 26 Jul 2009 16:14:39 UTC <<<

NOTICE: The expiration date displayed in this record is the date the 
registrar's sponsorship of the domain name registration in the registry is 
currently set to expire. This date does not necessarily reflect the expiration 
date of the domain name registrant's agreement with the sponsoring 
registrar.  Users may consult the sponsoring registrar's Whois database to 
view the registrar's reported date of expiration for this registration.

TERMS OF USE: You are not authorized to access or query our Whois 
database through the use of electronic processes that are high-volume and 
automated except as reasonably necessary to register domain names or 
modify existing registrations; the Data in VeriSign Global Registry 
Services' ("VeriSign") Whois database is provided by VeriSign for 
information purposes only, and to assist persons in obtaining information 
about or related to a domain name registration record. VeriSign does not 
guarantee its accuracy. By submitting a Whois query, you agree to abide 
by the following terms of use: You agree that you may use this Data only 
for lawful purposes and that under no circumstances will you use this Data 
to: (1) allow, enable, or otherwise support the transmission of mass 
unsolicited, commercial advertising or solicitations via e-mail, telephone, 
or facsimile; or (2) enable high volume, automated, electronic processes 
that apply to VeriSign (or its computer systems). The compilation, 
repackaging, dissemination or other use of this Data is expressly 
prohibited without the prior written consent of VeriSign. You agree not to 
use electronic processes that are automated and high-volume to access or 
query the Whois database except as reasonably necessary to register 
domain names or modify existing registrations. VeriSign reserves the right 
to restrict your access to the Whois database in its sole discretion to ensure 
operational stability.  VeriSign may restrict or terminate your access to the 
Whois database for failure to abide by these terms of use. VeriSign 
reserves the right to modify these terms at any time. 

The Registry database contains ONLY .COM, .NET, .EDU domains and
Registrars.
-----------------------------------------------------------------------
MarkMonitor, the Global Leader in Enterprise Brand Protection

Domain Management
Online Trademark Protection
Online Channel Protection
AntiPhishing Solutions
-----------------------------------------------------------------------
The Data in MarkMonitor.com's WHOIS database is provided by MarkMonitor.com
for information purposes, and to assist persons in obtaining information
about or related to a domain name registration record.  MarkMonitor.com
does not guarantee its accuracy.  By submitting a WHOIS query, you agree
that you will use this Data only for lawful purposes and that, under no
circumstances will you use this Data to: (1) allow, enable, or otherwise
support the transmission of mass unsolicited, commercial advertising or
solicitations via e-mail (spam); or  (2) enable high volume, automated,
electronic processes that apply to MarkMonitor.com (or its systems).
MarkMonitor.com reserves the right to modify these terms at any time.
By submitting this query, you agree to abide by this policy.

Registrant:
        James Troup
        Canonical, Ltd.
        One Circular Road
         Douglas Isle of Man IM1 1AF
        GB
        hostmaster@canonical.com +44.1624643643 Fax: -

    Domain Name: ubuntuforums.com

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

    Created on..............: 2004-10-09.
    Expires on..............: 2010-10-09.
    Record last updated on..: 2009-07-09.

    Domain servers in listed order:

    ns1.canonical.com
    ns3.canonical.com
    ns2.canonical.com
    



-----------------------------------------------------------------------
MarkMonitor, the Global Leader in Enterprise Brand Protection

Domain Management
Online Trademark Protection
Online Channel Protection
AntiPhishing Solutions
-----------------------------------------------------------------------


```

You learn something new everyday.  Whose backend does this command use??

---

### Post by Barrucadu on 2009-07-26
It checks the WHOIS server responsible for holding details about that domain. So it depends on the domain. WHOIS data should not be treated as completely accurate, however.

(if I understood your question right&#8230;)

---

### Post by sefs on 2009-07-26
I think i understand.

So if it checks network solutions whois db for instance it would query that directly and by pass their web system which would have their domain pre-registering system in place.  Is that correct?

---

### Post by Barrucadu on 2009-07-26
Yes. Unless they also have such a system in place for WHOIS queries.

---

### Post by ssam on 2009-07-26
just check a few random strings of letters first :-)

---

### Post by sefs on 2009-07-26
> **ssam said:**
> just check a few random strings of letters first :-)

lol. good one.

---

### Post by HappinessNow on 2009-07-26
> **sefs said:**
> Can some one suggest some safe utilities that I can use safely in order to check the availability of domain names.

I asked because I know network solutions has/had a policy of registering the domain with themselves if you checked it on their site, forcing you to register with them, if you did not want to wait a couple of days until they released it.

Use Google Domain Apps:

[http://www.google.com/a/cpanel/domain/new](http://www.google.com/a/cpanel/domain/new)

Once there click on:

**[I want to buy a domain name]("http://www.google.com/a/cpanel/domain/new#")**

---

### Post by michaelzap on 2009-07-26
My favorite domain name registration checking utility right now is Domainr:
[http://domai.nr/](http://domai.nr/)

Finds options that you'd never know about on your own (although many of them may be pricey).

The suggestions offered by the GoDaddy or Register.com forms can sometimes be helpful, and I've never known them to preregister a good name (personally I think that's a myth).

iWhois is a good, clean web-based whois:
[http://www.iwhois.com/](http://www.iwhois.com/)

---

