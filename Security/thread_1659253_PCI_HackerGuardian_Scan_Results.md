---
title: "PCI HackerGuardian Scan Results"
date: 2011-01-03
forum: Security
---

### Post by xathras1982 on 2011-01-03
Hi,
I've ran a PCI HackerGuardian Scan and got the results below, I've had a look at them and I think a lot of them are false positives. Particularly the versioning / patch warnings (whilst I might have a lower version - I have patched them). 
 
Does anyone else get the same kind of results on 10.10?
 
xx Double Slash Authentication Bypass http (80/tcp) High 7.5Fail
xx Xerver Double Slash Authentication Bypass https (443/tcp) High 7.5 Fail
xxApache 2.2 < 2.2.14 Multiple Vulnerabilities http (80/tcp) CVE-2009-2699, CVE-2009-3094, CVE-2009-3095 High 7.5Fail
xxApache 2.2 < 2.2.14 Multiple Vulnerabilities https (443/tcp) CVE-2009-2699, CVE-2009-3094, CVE-2009-3095 High 7.5Fail
xxApache 2.x < 2.2.12 Multiple Vulnerabilities http (80/tcp)  CVE-2009-0023, CVE-2009-1191, CVE-2009-1195, CVE-2009-1890, CVE-2009-1891, CVE-2009-1955, CVE-2009-1956 Medium 6.4Fail
xxApache 2.x < 2.2.12 Multiple Vulnerabilities https (443/tcp) CVE-2009-0023, CVE-2009-1191, CVE-2009-1195, CVE-2009-1890, CVE-2009-1891, CVE-2009-1955, CVE-2009-1956 Medium 6.4Fail
xxCERN HTTPD access control bypass http (80/tcp) Medium 5.0Fail
xxWeb Server Uses Plain Text Authentication Forms http (80/tcp) Medium 5.0Fail
xxApache < 2.2.9 Multiple Vulnerabilities http (80/tcp) CVE-2007-6420, CVE-2008-2364 Medium 5.0 Pass Denial of service vulnerability
xxApache < 2.2.9 Multiple Vulnerabilities https (443/tcp)  CVE-2007-6420, CVE-2008-2364 Medium 5.0PassDenial of service vulnerabilityxx
Apache 2.2 < 2.2.17 Multiple Vulnerabilities https (443/tcp) CVE-2009-3560, CVE-2009-3720, CVE-2010-1623 Medium 5.0Pass Denial of service vulnerability
xxApache 2.2 < 2.2.17 Multiple Vulnerabilities http (80/tcp)  CVE-2009-3560, CVE-2009-3720, CVE-2010-1623 Medium 5.0PassDenial of service vulnerability
xxApache mod_proxy_ftp Globbing Cross-Site Scripting Vulnerability http (80/tcp) CVE-2008-2939 Medium 4.3Fail
xxApache 2.2 < 2.2.16 Multiple Vulnerabilities http (80/tcp) CVE-2010-1452, CVE-2010-2068 Medium 4.3Fail
xxApache 2.2 < 2.2.16 Multiple Vulnerabilities https (443/tcp) CVE-2010-1452, CVE-2010-2068 Medium 4.3Fail
xxApache mod_proxy_ftp Globbing Cross-Site Scripting Vulnerability https (443/tcp) CVE-2008-2939 Medium 4.3Fail
xxApache < 2.2.8 Multiple Vulnerabilities https (443/tcp) CVE-2007-5000, CVE-2007-6203, CVE-2007-6388, CVE-2007-6421, CVE-2007-6422, CVE-2008-0005 Low 2.6Pass
xxApache < 2.2.8 Multiple Vulnerabilities http (80/tcp) CVE-2007-5000, CVE-2007-6203, CVE-2007-6388, CVE-2007-6421, CVE-2007-6422, CVE-2008-0005 Low 2.6Pass
xxWeb Server Uses Basic Authentication http (80/tcp) Low 2.6Pass
xxExternal URLs http (80/tcp) LowPass
xxExternal URLs https (443/tcp) LowPass
xxHTTP methods per directory http (80/tcp) LowPass
xxHyperText Transfer Protocol Information http (80/tcp) LowPass
xxHyperText Transfer Protocol Information https (443/tcp) LowPass
xxHTTP methods per directory https (443/tcp) LowPass
xxWeb Application Firewall Detection http (80/tcp) LowPass
xxWeb Application Firewall Detection https (443/tcp) LowPass
xxWeb mirroring http (80/tcp) LowPass
xxWeb mirroring https (443/tcp) LowPass
xxWeb Server Allows Password Auto-Completion http (80/tcp) LowPass
xxWeb Server Allows Password Auto-Completion https (443/tcp) LowPass
xxHTTP Cookies http (80/tcp) LowPass
xxHTTP Cookies https (443/tcp) LowPass
xxProtected web pages http (80/tcp) LowPass
xxSMTP Service STARTTLS Command Support smtp (25/tcp) LowPass
xxsmtpscan smtp (25/tcp) LowPass
xxFirewall Enabled general/tcp LowPass
xxTCP timestamps general/tcp LowPass
xxSSL ciphers https (443/tcp) LowPass
xxSMTP Server type and version smtp (25/tcp) LowPass
xxIMAP Banner imap (143/tcp) LowPass
xxSupported SSL Ciphers Suites https (443/tcp) LowPass
xxSupported SSL Ciphers Suites smtp (25/tcp) LowPass
xxSupported SSL Ciphers Suites imap (143/tcp) LowPass
xxHTTP Server type and version http (80/tcp) LowPass
xxHTTP Server type and version https (443/tcp) LowPass
xxLinux Distribution Detection general/tcp LowPass
xxCOMODO Invalid SSL Certificate https (443/tcp) LowPass
xxHost FQDN general/tcp LowPass
xxOS Identification general/tcp LowPass
xxCommon Platform Enumeration (CPE) general/tcp LowPass
xxOpenSSL Detection https (443/tcp) LowPass
xxServices https (443/tcp) LowPass
xxServices http (80/tcp) LowPass
xxServices imap (143/tcp) LowPass
xxServices smtp (25/tcp) LowPass
xxTry very hard to identify what runs on common ports general/tcp LowPass
xxphpMyAdmin Detection https (443/tcp) LowPass
xxIMAP Service STARTTLS Command Support imap (143/tcp) LowPass
xxDirectory Scanner http (80/tcp) LowPass
xxDirectory Scanner https (443/tcp) LowPass
 
Consolidated Solution/Correction Plan for above IP address:Contact the web server vendor for an update or tighten its filtering rules to reject patterns such as :
//* *//* /./* */./*There is no known solution at this time.Make sure that every sensitive form transmits content over HTTPS.Either ensure that the affected modules are not in use or upgrade to Apache version 2.2.9 or later.Either ensure the affected modules are not in use or upgrade to Apache version 2.2.14 or later.Either disable the affected module or upgrade to Apache version 2.2.10 or later.Either ensure that the affected modules / directives are not in use or upgrade to Apache version 2.2.12 or later.Upgrade to Apache version 2.2.16 or later.Either ensure that the affected modules are not in use or upgrade to Apache version 2.2.17 or later.To get a more comprehensive set of scan results, either whitelist the Nessus server's IP address or scan from an unprotected location.Either ensure that the affected modules are not in use or upgrade to Apache version 2.2.8 or later.Add the attribute 'autocomplete=off' to these fields to prevent browsers from caching credentials.Make sure that HTTP authentication is transmitted over HTTPS.Disable this service if you do not use it, or filter incoming traffic to this port.If you do not wish to display this information, edit httpd.conf and set the directive 'ServerTokens Prod' and restart Apache.Ensure you have a SSL certificate issued by a legitimate CAInstall a valid SSL certificateMake sure the use of this program is in accordance with your corporate security policy.Part 3b. Special notes by IP Address

---

