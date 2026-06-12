---
title: "Linux Intrusion Detection System"
date: 2005-06-12
forum: The Cafe
---

### Post by vega44 on 2005-06-12
[http://security.linux.com/security/05/03/11/2313226.shtml](http://security.linux.com/security/05/03/11/2313226.shtml)

---

### Post by ubuntu_demon on 2005-06-12
from the article :
> 
The Linux Intrusion Detection System (LIDS) is a kernel patch for both 2.4 and 2.6 kernels that adds Mandatory Access Control (MAC) and other security enhancements to the Linux kernel. The main feature of LIDS is its ability to limit the power of the root account. LIDS uses Access Control Lists (ACLs) to control access to files, processes, and network resources. Once these permissions are set, they cannot be overridden, even if a user or process has root privileges.


I don't like patching my kernel. Let's hope SElinux gets integrated into ubuntu soon.

LIDS is not very interesting for the average ubuntu user I think because :

- let's not encourage average linux users to patch their kernel unless absolutely necessary
- ubuntu has sudo

What is your opinion lowlux ?

---

### Post by az on 2005-06-12
Isn't this one of the many different ways to secure a linux or unix system?

apt-cache search intrusion
aide - Advanced Intrusion Detection Environment
libapache2-mod-security - Tighten the Web application security for Apache 2.x
mod-security-common - Tighten the Web application security - common files
acidlab - Analysis Console for Intrusion Databases
acidlab-doc - Analysis Console for Intrusion Databases (documentation)
acidlab-mysql - Analysis Console for Intrusion Databases for MySQL
acidlab-pgsql - Analysis Console for Intrusion Databases for Postgres
bsign - Corruption & intrusion detection using embedded hashes
elfsh - The ELF shell
fcheck - IDS filesystem baseline integrity checker
fragroute - Test a NIDS by attempting to evade using fragmented packets
fragrouter - Test a NIDS by attempting to evade using fragmented packets
harden-environment - Hardened system environment
harden-nids - Harden a system by using a network intrusion detection system
hunt - Advanced packet sniffer and connection intrusion
idsa - A reference monitor, logger and intrusion detection system
idsa-apache - Apache module for IDS/A
idsa-guile - Guile module for IDS/A
idsaguardgtk - Interactive access control with GTK GUI for IDS/A
idswakeup - A tool for testing network intrusion detection systems.
karpski - ethernet analyzer and sniffer
lg-issue106 - Issue 106 of the Linux Gazette.
libelfsh0 - The ELF shell library
libelfsh0-dev - The ELF shell library
libnids-dev - IP defragmentation TCP segment reassembly library (development)
libnids1 - IP defragmentation TCP segment reassembly library
libprelude-dev - Hybrid Intrusion Detection System [ Development files ]
libprelude0 - Hybrid Intrusion Detection System [ Base library ]
lidstools-2.4 - LIDS Admintool
packit - Network Injection and Capture
piwi - P(erl|relude) IDS Web Interface - A frontend to your Prelude database
prelude-lml - Hybrid Intrusion Detection System [ Log Monitoring Lackey ]
prelude-manager - Hybrid Intrusion Detection System [ Report Manager ]
prelude-nids - Hybrid Intrusion Detection System [ Network sensor ]
prospect - Non-intrusive, system-wide performance analysis tool
raccess - Security Tool to audit remote systems
samhain - Data integrity and host intrusion alert system
snort - Flexible Network Intrusion Detection System
snort-common - Flexible Network Intrusion Detection System [common files]
snort-doc - Documentation for the Snort IDS [documentation]
snort-mysql - Flexible Network Intrusion Detection System [MySQL]
snort-pgsql - Flexible Network Intrusion Detection System [PostgreSQL]
snort-rules-default - Flexible Network Intrusion Detection System ruleset
webmin-snort - snort control module for webmin

---

### Post by vega44 on 2005-06-12
what about windows? i got sygate firewall and spyware tools.

---

### Post by desdinova on 2005-06-12
I find a good set of tools to go with your firewall as part of an IDS are hostsentry and portsentry.....

---

### Post by ubuntu_demon on 2005-06-12
[QUOTE=lowlux]what about windows? i got sygate firewall and spyware tools.[/QUOTE]
 a default ubuntu installation is a lot more secure than a default windows installation

for ubuntu you don't need anything (except doing your updates) to keep it secure. But there's no spyware or virusses for linux and you don't need to run a firewall (unless you are paranoid)
Ofcourse if you are a nerd or if you are really paranoid there are a lot of thing you could do. 

for windows you have to do a lot of things to (only) approach ubuntu's security
like :
- don't use internet explorer
- don't use outlook express
- use a virusscanner (like avg)
- use a spywarescanner (like hitman pro)
- always keep your windows AND all your programs up to date (a lot of work)

---

### Post by nocturn on 2005-06-13
LIDS is cool, but it can also potentially break things.  
And again, all these security features only work when properly configured and used (in contratiction to Pax etc, they work without intervention/training).

---

### Post by mike998 on 2005-06-13
[QUOTE=demon666_nl]a default ubuntu installation is a lot more secure than a default windows installation

for ubuntu you don't need anything (except doing your updates) to keep it secure. But there's no spyware or virusses for linux and you don't need to run a firewall (unless you are paranoid)
Ofcourse if you are a nerd or if you are really paranoid there are a lot of thing you could do. 

for windows you have to do a lot of things to (only) approach ubuntu's security
like :
- don't use internet explorer
- don't use outlook express
- use a virusscanner (like avg)
- use a spywarescanner (like hitman pro)
- always keep your windows AND all your programs up to date (a lot of work)[/QUOTE]

Without wanting to sound eliteist, I really hope that Linux remains on the edge of Operating Systems, so that we don't have to deal with the above...  Which will happen if Linux goes mainstream...

---

### Post by desdinova on 2005-06-13
I dont think its elitist to want Linux to retain its strengths without compromise .... I'm glad some one else feels the same!

---

### Post by ubuntu_demon on 2005-06-13
[QUOTE=mike998]Without wanting to sound eliteist, I really hope that Linux remains on the edge of Operating Systems, so that we don't have to deal with the above...  Which will happen if Linux goes mainstream...[/QUOTE]
 Yeah I like ubuntu to incorporate new "on the edge" stuff as long as it's stable .. for example breezy will feature beagle

But I'm sure it's entirely possible to have a popular operating system without getting it's security as crappy as windows security.

It would be great if in a couple of years linux will be so big that hardware manufacturers have to work on open source drivers!

---

### Post by az on 2005-06-13
[QUOTE=mike998]Without wanting to sound eliteist, I really hope that Linux remains on the edge of Operating Systems, so that we don't have to deal with the above...  Which will happen if Linux goes mainstream...[/QUOTE]


I do not think that linux is as prone to the kinds of security issues that windows has.  It is build a lot differently.  There is nothing there for the microorganisms to eat so that they grow.

Sure there are security threats, but the fact that it is built on a stucture (unix) that has security engrained makes a mainstream linux a lot less vulnerable than mainstream Windows.

---

### Post by desdinova on 2005-06-13
Never underestimate the idiots who write malware - every platform can be compromised ;-)

I believe a healthy degree of paranoia is worthwhile ;-)

---

### Post by ubuntu_demon on 2005-06-14
[QUOTE=desdinova]Never underestimate the idiots who write malware - every platform can be compromised ;-)

I believe a healthy degree of paranoia is worthwhile ;-)[/QUOTE]
 yeah paranoia is worthwhile

I think there are a couple of reasons why almost all mallware is targeted towards windows :

-it's easier to create mallware for windows that gets root acces than for linux / unixes
-linux / unixes are more secure
-windows is more widespread and in general linux users are better educated (I don't mean to offend anyone here!)
-there are a lot of "tastes" of unixes .... there are a lot of different kernels , applications and services that are used

But this doesn't mean that I don't want Ubuntu to get big.

---

### Post by ubuntu_demon on 2005-06-14
[QUOTE=azz]I do not think that linux is as prone to the kinds of security issues that windows has.  It is build a lot differently.  There is nothing there for the microorganisms to eat so that they grow.

Sure there are security threats, but the fact that it is built on a stucture (unix) that has security engrained makes a mainstream linux a lot less vulnerable than mainstream Windows.[/QUOTE]
 true

---

### Post by mike998 on 2005-06-14
[QUOTE=azz]I do not think that linux is as prone to the kinds of security issues that windows has.  It is build a lot differently.  There is nothing there for the microorganisms to eat so that they grow.

Sure there are security threats, but the fact that it is built on a stucture (unix) that has security engrained makes a mainstream linux a lot less vulnerable than mainstream Windows.[/QUOTE]

I completely agree.  However, take a look at some distros that run as root by default.  (Lycoris I believe) This is the kind of thing that will do damage to the Linux product.

By the way, azz, that avatar of yours is kinda scary...

---

### Post by Gtaylor on 2005-06-14
One of the advantages we have over Windows is that fixes are generally noted and reported by a userbase that is involved in the development of their operating environment. Important vunerabilities are usually handled very quickly by one of many maintainers.

---

