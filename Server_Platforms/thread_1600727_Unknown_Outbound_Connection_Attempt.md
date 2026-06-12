---
title: "Unknown Outbound Connection Attempt ???"
date: 2010-10-19
forum: Server Platforms
---

### Post by mistypotato on 2010-10-19
I use ipblock and found a rare and unknown outgoing connection attempt in my ipblock log this morning

it is the ONLY outgoing connection attempt in 1000's of entries and I cannot find any trace of it's source in any of the system logs or apache logs.

my server attempted to connect to a US University computer source port 40663 (my server) to port 80 on the remote computer.

It was blocked, but I cannot figure out what caused this outgoing connection attempt.

During this same time period (24 hours), I'm seeing a significant increase in hits from Russia, Latvia, China and so forth)

Any suggestions?

thx

---

### Post by James78 on 2010-10-19
Don't you mean inbound connection attempt? Outbound would be departing from your server.

Anyways, it's nothing more than bunches of zombified computers. Nothing to worry about... If your server is properly secure, otherwise it's everything to worry about, and your server could get hacked, and used as part of the botnet, just like the ones attacking you.

Anyways, just bulk up on security. Here's a few things and ideas to get you started:

Apache::
Mod_evasive (DoS attacks protection)
Mod_security2 ([Atomic Security rules]("http://www.atomicorp.com/wiki/index.php/Atomic_ModSecurity_Rules#ModSecurity_Rules_download"), [Core rules]("http://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project") - Use the ones from SVN)
Http guardian (protects against DoS attacks) and modsec-clamscan (this scans file upload - both part of Mod_security2)

Postfix::
[Scan incoming and outgoing emails for viruses]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto")
My postfix security configuration::
```
# Security related config
smtpd_helo_required = yes
disable_vrfy_command = yes
smtpd_helo_restrictions =
    permit_mynetworks,
    reject_non_fqdn_hostname,
    reject_invalid_hostname
smtpd_recipient_restrictions =
    permit_mynetworks,
    permit_sasl_authenticated,
    reject_unauth_destination,
    reject_invalid_hostname,
    reject_unauth_pipelining,
    reject_non_fqdn_hostname,
    reject_non_fqdn_sender,
    reject_unknown_sender_domain,
    reject_non_fqdn_recipient,
    reject_unknown_recipient_domain,
    reject_rbl_client bl.spamcop.net,
    reject_rbl_client zen.spamhaus.org,
    reject_rbl_client combined.njabl.org,
    reject_rbl_client bhnc.njabl.org,
    reject_rhsbl_client rhsbl.sorbs.net,
    reject_rbl_client dul.dnsbl.sorbs.net,
    reject_rbl_client web.dnsbl.sorbs.net,
    reject_rbl_client zombie.dnsbl.sorbs.net,
    reject_rbl_client dnsbl.ahbl.org,
    reject_rhsbl_client rhsbl.ahbl.org,
    permit
```

General::
fail2ban (latest version includes an action called complain, which sends an abuse email to the ISP of the attacker)
[DoS attacks in general]("http://www.mydigitallife.info/2007/12/13/prevent-and-stop-dos-or-ddos-attacks-on-web-server-ddos-deflate/")
[Security help]("http://www.linuxsecurity.com/content/view/121960/49/")

SSH::
Disable passworded logins.
Disable root login.
Only use SSH with keys. Makes SSH attacks completely pointless to bots.

BIND::
Enable DNSSEC, and apply it to zones (helps protect your zones against things like DNS poisoning)

Router/Firewall::
Block all ports not needing to access outside world.

---

### Post by dtfinch on 2010-10-19
Could it be updating that "message of the day" that displays whenever you log on?

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/522452](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/522452)

---

### Post by mistypotato on 2010-10-19
> **James78 said:**
> Don't you mean inbound connection attempt? Outbound would be departing from your server

Well,

Almost all the connections to my server will be inbound connections.

What I dont want is my server connecting to another computer via an outbound connection.

Outbounds are the dangerous ones since a Trojan or Bot would try to connect to somewhere via outbound  :)

thx for all the info btw :KS

---

### Post by James78 on 2010-10-19
> **mistypotato said:**
> What I dont want is my server connecting to another computer via an outbound connection.
Of course, that would be bad, and could signify some type of infection (probably not in this case, but in general it could).

> **mistypotato said:**
> Outbounds are the dangerous ones since a Trojan or Bot would try to connect to somewhere via outbound  :)
Certainly. My server detects those ones (incoming to the server anyways), and sends them 400 (Bad request), and 403 forbidden requests, which is pretty sweet. Of course, mod_security is far more extensive than that. I've had my server block comment spammers even. :)

> **mistypotato said:**
> thx for all the info btw :KS
No problem. My server is really beefy on security now, and I'm loving it. :KS Might as well share my configuration so it's one more safe and secure server on the internet.

---

### Post by mistypotato on 2010-10-19
Mod_security sounds good.

I just read the Install procedures.

Did you have to do anything special to get it up and running?


I can tell you this...I've been watching iplist today and as I plug holes so their bots can't reach forums on my server, they step up the efforts.  Annoying.  They've been hitting my server non-stop since about noon.  They haven't been able to get in at all since about noon and they hits are now non stop.   Not quite a DoS attack...but it's ramping up.

---

### Post by mistypotato on 2010-10-19
What Hardware security aappliance do you use?

I use a Watchguard Firebox Enterprise model.

---

### Post by SeijiSensei on 2010-10-19
Are you blocking with iptables rules?  If you have a list of attackers, just block all traffic from their addresses in iptables:

```
sudo iptables -I INPUT -s ip.of.evil.spammer -j REJECT --reject-with-icmp-port-unreachable
```

If they seem clustered in a subnet you can block a bunch of them quickly by replacing "ip.of.evil.spammer" with "evil.spammer.net.work/mask".  Use the -I switch to put all the blocks above any existing rules in the INPUT chain.

There's certainly no reason for these packets to ever reach Apache once you've identified them.

---

### Post by James78 on 2010-10-19
> **mistypotato said:**
> Did you have to do anything special to get it up and running?
Many special things in fact. I'll quickly recap them.

[LIST]
[*]Use Atomic Security configuration (along with the main configuration, link to the configuration is in the security ruels link I gave)
[*]Use main default configuration
[*]Move some data files from base_rules to optional_rules (seems they're supposed to be in optional rules, as your server keeps getting startup errors due to the data files, just keep moving them one at a time)
[*]Moved optional_rules/modsecurity_crs_43_csrf_protection.conf to optional_rules/disabled/modsecurity_crs_43_csrf_protection.conf (it caused cookie IP collection problems)
[/LIST]

I'll give you my configuration, just to help you out. :)

Apache2.conf
```
...
# Include generic snippets of statements
#Include conf.d/
Include conf.d/phpmyadmin.conf
Include conf.d/security
...
```

httpd.conf
```
# Include mod_security2 configuration
<IfModule security2_module>
    Include mod_security.d/modsecurity_*.conf
    Include mod_security.d/base_rules/*.conf
    Include mod_security.d/optional_rules/*.conf
    Include mod_security.d/asl/*asl*.conf
    # Load post rules last
    Include mod_security.d/post_rules.conf
</IfModule>

# mod_doevasive configuration
<IfModule evasive20_module>
    Include conf.d/mod_evasive.conf
</IfModule>

```

conf.d/mod_evasive.conf
```
DOSHashTableSize 3097
DOSPageCount 3
DOSSiteCount 60
DOSPageInterval 1
DOSSiteInterval 1
DOSBlockingPeriod 10
DOSEmailNotify root

```

conf.d/security (well, who needs a full Apache version signature anyways!!)
```
...
#
ServerTokens Minimal
#ServerTokens OS
#ServerTokens Full
...
```

modsecurity.d/mod_security_crs_10_asl_config.conf
```
SecRuleEngine On
SecRequestBodyAccess On
SecResponseBodyAccess On
SecResponseBodyMimeType (null) text/html text/plain text/xml
SecResponseBodyLimit 2621440
SecServerSignature Apache
SecComponentSignature 200911012341
SecUploadKeepFiles Off
SecAuditEngine RelevantOnly
SecAuditLogRelevantStatus "^(?:5|4(?!04))"
SecAuditLogType Concurrent
SecAuditLogParts ABIFHZ
SecArgumentSeparator "&"
SecCookieFormat 0
SecRequestBodyInMemoryLimit 131072
SecResponseBodyLimitAction ProcessPartial

# file paths
SecUploadDir /var/modsec/data/upload
SecAuditLog /var/modsec/data/audit/log/audit.log
SecDataDir /var/modsec/data
SecTmpDir /tmp
SecAuditLogStorageDir /var/modsec/data/audit

# set PCRE match limits
SecPcreMatchLimit 100000
SecPcreMatchLimitRecursion 100000 

# help protect apache from DoS attacks
SecGuardianLog |/etc/apache2/mod_security.d/base_rules/httpd-guardian.pl

```

mod_security.d/mod_security_crs_10_config.conf
* You can just find this in the default package. E.g. Download mod_security2 from source, and it'll come with this config

mod_security.d/modsecurity_crs_15_customrules.conf
```
# scan all uploaded files for viruses
SecRule FILES_TMPNAMES "@inspectFile /etc/apache2/mod_security.d/base_rules/modsec-clamscan.pl" "phase:2,t:none,log,deny,msg:'Malicous File Attachment Identified.'"
```

modsecurity.d/post_rules.conf
All I have in here are SecRuleRemoveByID, because they conflict with the site

modsec-clamscan.pl
Disable default clamscan (add # in front of it), and enable the one that says clamdscan
In the $cmd part, change it to this (--disable-summary is deprecated, but the new one is not)
```
$cmd = "$CLAMSCAN --stdout --no-summary $FILE";
```

Extra notes: You can get the perl files modsec-clamscan.pl and httpd-guardian.pl from downloading the mod_security2 source. Make sure the perl files have the executable bit (chmod o+x), or they'll fail to execute. Of course I just recommend installing mod_security from the repos, as they have the latest version for maverick, and you won't have to build it.

> **mistypotato said:**
> What Hardware security aappliance do you use?

I use a Watchguard Firebox Enterprise model.
I'm pretty poor right now, so I had to just take a regular computer and put it into a server box. It obviously will work fine for now though. Niiicee server setup you got though.

---

### Post by mistypotato on 2010-10-20
Thanks for the info :KS

The first thing I did with mod_security was look over the dependency list to make sure I had all the pre-requisites installed.

Right off the bat....line 2 **[COLOR="Red"]mod_unique_id[/COLOR]** threw me.
Couldn't find where it was installed and couldn't find where to get it :confused:

So, I'm on hold right now with mod_security until I can get that resolved.

The Firebox is my first line of defense.  It catches all kinds of stuff...spoofed IP address, port scans, attempts to connect via ports other than http and https and a lot of other things.
But it's not Linux specific so mod_security would be another good "layer".   Not many people I know are rolling in the cash at present...myself included.

ModSecurity installation requirements:

   1.

      ModSecurity 2.x works only with Apache 2.0.x or higher. Version 2.2.x is highly recommended.
   2.

      Make sure you have mod_unique_id installed.

      mod_unique_id is packaged with Apache httpd.
   3.

      libapr and libapr-util

      [http://apr.apache.org/](http://apr.apache.org/)
   4.

      libpcre

      [http://www.pcre.org/](http://www.pcre.org/)
   5.

      libxml2

      [http://xmlsoft.org/downloads.html](http://xmlsoft.org/downloads.html)
   6.

      liblua v5.1.x

      This library is optional and only needed if you will be using the new Lua engine.

      [http://www.lua.org/download.html](http://www.lua.org/download.html)

      Note that ModSecurity requires the dynamic libraries. These are not built by default in the source distribution, so the binary distribution is recommended.
   7.

      libcurl v7.15.1 or higher

      If you will be using the ModSecurity Log Collector (mlogc) to send audit logs to a central repository, then you will also need the curl library.

      [http://curl.haxx.se/libcurl/](http://curl.haxx.se/libcurl/)

---

### Post by James78 on 2010-10-20
There are a quite a few modules that are in the repositories, and these 2 happen to be part of them. :)
```
sudo apt-get install libapache-mod-security
sudo apt-get install libapache2-mod-evasive
```

---

