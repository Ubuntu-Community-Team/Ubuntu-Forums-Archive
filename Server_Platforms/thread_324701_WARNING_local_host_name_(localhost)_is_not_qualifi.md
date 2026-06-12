---
title: "WARNING: local host name (localhost) is not qualified; see cf/README: WHO AM I?"
date: 2006-12-24
forum: Server Platforms
---

### Post by HAL98 SE on 2006-12-24
I'm an Ubuntu noob. Trying to setup and configure sendmail, every time i run the command:-

```
./sendmail -d0.1 -bt < /dev/shell
```

To get stats on sendmail, i get the following output:-
```
Version 8.13.5.20060308
 Compiled with: DNSMAP LDAPMAP LDAP_REFERRALS LOG MAP_REGEX MATCHGECOS
                MILTER MIME7TO8 MIME8TO7 NAMED_BIND NETINET NETINET6 NETUNIX
                NEWDB NIS NISPLUS PIPELINING SASLv2 SCANF SOCKETMAP STARTTLS
                USERDB USE_LDAP_INIT XDEBUG

============ SYSTEM IDENTITY (after readcf) ============
      (short domain name) $w = localhost
  (canonical domain name) $j = localhost
         (subdomain name) $m = <null>
              (node name) $k = steve-desktop
========================================================

[COLOR="Red"]WARNING: local host name (localhost) is not qualified; see cf/README: WHO AM I?[/COLOR]
ADDRESS TEST MODE (ruleset 3 NOT automatically invoked)
Enter <ruleset> <address>

```

Can anybody tell me what this means?

I've looked in *usr/share/sendmail/cf/cf/README* for an explanation, but can find none.

---

### Post by Littleweseth on 2006-12-24
It means that 'localhost' is not a fully qualified domain name - that is, you can't go to any random computer, type 'localhost' and get your computer. The effect of this with relation to a mail server is that the 'sending from this server' field will be nonsensical (I don't know the exact reasons why this is bad, but it's totally unacceptable.)

An example of a FQDN is [www.google.com](www.google.com). You can get a free FQDN by signing up at [www.dyndns.com](www.dyndns.com), or you can register your own domain name.

---

### Post by HAL98 SE on 2006-12-26
Ah ha, now i see! thanks for your help. 

There is one other small thing thats bothering me though, if anybody happens to know the answer:-

As i was initially going through the procedures and tutorials for setting up sendmail (still am) i thought that the distro was broken as it appeared to hang whenever i execute a sendmail command, i.e:- 
```
sendmail -d0.1 -bp
```
On further inspection this wasn't the case at all, there is in fact a delay of exactly 1 minute between submitting any command like the above, and sendmail then processing it.

Is this default sendmail behaviour? if so, how can i modify it? 

I'm running 6.06LTS with sendmail Version 8.13.5.20060308 (synaptic)

---

### Post by HAL98 SE on 2006-12-28
Nobody have any ideas on that?

---

