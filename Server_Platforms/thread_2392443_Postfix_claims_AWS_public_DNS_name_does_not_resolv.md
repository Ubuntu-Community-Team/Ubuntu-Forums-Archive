---
title: "Postfix claims AWS public DNS name does not resolve"
date: 2018-05-21
forum: Server Platforms
---

### Post by storwalle2 on 2018-05-21
Hi!

I am running an Ubuntu 16.04 server in an AWS VPC machine. When I read my syslog I get a warning that the smtpd is not resolving the server address. I have checked my Elastic IP settings in AWS Management Console and everything is correctly given. The warning log line looks like:
[I]May 21 11:57:39 ip-kkk-ll-mm-nnn postfix/submission/smtpd[6489]: warning: hostname ec2-xx-yyy-vvv-zzz.eu-central-1.compute.amazonaws.com does not resolve to address xx.yyy.vvv.zzz
[/I]

If I do a lookup on the DNS name I get the correct Public IP given by AWS, so there is nothing wring with the resolving process of the DNS systems.

The public IP and DNS name given by AWS is not in the main.cf parameter "mydestination =". Should it? There I have $myhostname and some more details.

Any idea on why this warning is given?

Kind regards
Michael

---

### Post by SeijiSensei on 2018-05-21
What about reverse resolution from the IP to the hostname?  

Most mail administrators now require SMTP servers to have correct forward and reverse resolution.  You can control the former with the DNS records for your domain.  Only the provider can configure reverse resolution, since it is the provider with authority over the relevant in-addr.arpa domains.  I use Linode for viirtual hosting, and it provides a place in the configuration for a virtual machine to enter the host's fully-qualified domain name for reverse resolution.  

The mydestinaton parameter must include any domain for which the server provides local delivery.  Do you accept mail as account@ec2...amazonaws.com? 

What if you do a lookup outside the machine with "host ec2....amazonaws.com 8.8.8.8" to query Google's DNS server?  Is that correct?

If you are sending mail from this server using your own domain name, you should have an [SPFv1]("http://www.openspf.org/Project_Overview") TXT record in your DNS as well.

---

