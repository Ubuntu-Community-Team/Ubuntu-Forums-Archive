---
title: "Telnet Issues for Postfix through port 25"
date: 2016-04-21
forum: Security
---

### Post by Clockmender on 2016-04-21
Hello,

First of all I hope this is the right forum to post in, if not can a kind Mod move it and let me know here it has gone.

I need to stop anybody from using **telnet** to post emails from one of my internal mailboxes to another or the same one, so for example I can telnet to my server through port 25, issue a "helo" command, then a "mail from:" command, followed by a "rcpt to:" then the "data" command, etc. and the mail gets delivered - and i am never asked for a password, not good if anyone finds this loophole. I need them to login first, but I still need to allow **incoming** mail. I am using Postfix, Dovecot and Roundcube. I have been trying to configure Postfix to do this for a long time now and need some help!

If I set:

smtp_client_restrictions = permit_mynetworks, reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl

Then anyone can telnet in and send a message, relaying is not permitted - this only works from one internal mail address to another, but if I do this:

smtp_client_restrictions = permit_mynetworks, reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject

nobody can telnet in, but I cannot receive any external mail either! This defeats the object of the mail server.

Can someone please let me know what I am doing wrong?

Thanks in Advance, Clock.

---

### Post by TheFu on 2016-04-21
2 ways that I know to deal with this.

1) Only allow encrypted connections.  I do that, since only spammers won't support TLS encryption for email.  Professionally run email servers will support TLS connections, period.

2) Place an email gateway server for the MX stuff to handle anonymous SMTP connections, but not end-user, authenticated, connections.  Then you can reject any connections from servers that don't match reverse-DNS lookups, FROMs that aren't for other domains, don't match reverse lookups, come from DHCP IPs, and a multitude of other options.  I use Scrollout for this stuff (got lazy doing it manually), though the most recent version is sorta bloated compared to the old version which ran for years on a 256MB VM. New version is using almost 800MB of RAM! The main.cf on that box is kinda ugly since it is created/managed by a web-GUI (about 20 lines of smtpd_helo_restrictions and 40 for smtpd_sender_restrictions).  For connections from outside my normal client countries, it slows things down and forces retries before any email is accepted, until the remote server proves to be non-bad.  

The real email server for end-users is in a different VM and not directly on the internet. It is running bloated Zimbra - which is amazing for an Enterprise, but needs a ton of RAM to be happy.  It isn't the 256MB postfix days anymore.

---

### Post by Clockmender on 2016-04-22
> **TheFu said:**
> 2 ways that I know to deal with this.

1) Only allow encrypted connections.  I do that, since only spammers won't support TLS encryption for email.  Professionally run email servers will support TLS connections, period.

2) Place an email gateway server for the MX stuff to handle anonymous SMTP connections, but not end-user, authenticated, connections.  Then you can reject any connections from servers that don't match reverse-DNS lookups, FROMs that aren't for other domains, don't match reverse lookups, come from DHCP IPs, and a multitude of other options.  I use Scrollout for this stuff (got lazy doing it manually), though the most recent version is sorta bloated compared to the old version which ran for years on a 256MB VM. New version is using almost 800MB of RAM! The main.cf on that box is kinda ugly since it is created/managed by a web-GUI (about 20 lines of smtpd_helo_restrictions and 40 for smtpd_sender_restrictions).  For connections from outside my normal client countries, it slows things down and forces retries before any email is accepted, until the remote server proves to be non-bad.  

The real email server for end-users is in a different VM and not directly on the internet. It is running bloated Zimbra - which is amazing for an Enterprise, but needs a ton of RAM to be happy.  It isn't the 256MB postfix days anymore.
Thank you for your response.

We tried forcing encrypted connections, and lost all incoming mail. I sent a test message from my iCloud account and it was rejected! See below:

[COLOR="#0000FF"] Reason: Server rejected MAIL FROM address.
 Diagnostic code: smtp;530 5.7.0 Must issue a STARTTLS command first[/COLOR]

Also the Postfix documentation explicitly says not to force encryption for public accessible mail server, but to use security level "may".

And no mail came in during this period when we had forced TLS, after we set it back to "may", mail came in again, but the Telnet problem returned. So I do not know how to overcome this.

On your second point, the server is for a small flying club, we don't have the resources for multiple servers, that is really overkill for us, it was hard enough getting the members to use a simple Webmail service, although they took to the OwnCloud setup nicely.

---

### Post by TheFu on 2016-04-22
[https://www.howtoforge.com/postfix-smtp-authentication-on-the-secure-port-only](https://www.howtoforge.com/postfix-smtp-authentication-on-the-secure-port-only)  might help getting the TLS working.

There are examples for restricting inbound email on the postfix website. Did you try the other 20 options?  I tend to get specific instructions FROM THE PROJECT SITE, not from random blogs. Though a few sites have proven to be reasonably trustworthy.

Would firewall blocking the source subnet work in the short term?

Found this which shows how to configure a delay: [http://ubuntuforums.org/showthread.php?t=1698196](http://ubuntuforums.org/showthread.php?t=1698196)

[https://wiki.centos.org/HowTos/postfix_restrictions](https://wiki.centos.org/HowTos/postfix_restrictions) explains the HELO restrictions. Postfix is postfix, IME.

---

### Post by Clockmender on 2016-04-22
OK I have already tried the tutorial and implemented everything it says - no luck yet! The reason for this is that we have a credit card machine here and the PCI compliance company (Trustwave - I note a number of pending lawsuits against them.....) said we cannot allow unencrypted traffic through port 25. If I force encryption, the mail system breaks. I do not know what else to do, other than take a new Internet link on a second IP address for the card machine, so they don't see the server.

This problem just seems to go around in circles - we have SSL certs from Letsencrypt and a clean bill of health from WSSA scanning - I don't know how anyone could get to our card machine, which uses only encrypted traffic or even read what's coming from it, by using telnet to send an internal email. If I could just stop people using telnet, i.e. require them to login first, would that solve the issue or would that stop incoming mail?

Cheers, Clock.

---

### Post by TheFu on 2016-04-22
#1 - Keep all payment processing stuff off the internet if it is on a shared network with non-highly-secured systems .... er ... like email. Just because you don't see how, doesn't mean it isn't possible.  I'd use dialup for card processing to start - or pay a high-price internet card processor for the favor - like Square. Sure, there are networking methods to separate this stuff, but you don't seem to have **any** money to spend solve the issue and I'm positive the entire situation is more complex that we know.

PCI compliance doesn't make anyone secure. It is a minimal level.  I know some retail stores (hundreds of locations, 3 counties) that were forced to reduce their security to become PCI compliant.  PCI auditors don't always have any hands-on experience.  OTOH, what do I know?  I've never been involved with any of this stuff, just have discussions with friends at banks, retail store IT, and card processors who share their stories. Consider it hearsay.

Scanning only shows things that are already known. We all have to do it, but it definitely isn't enough and cannot scan for the new/unknown method.

Perhaps if we step back and you post the postconf -n output, then maybe someone can help?  Need a few facts and data. Please use code tags.  Feel free to globally search and replace any public IPs or domainnames. - example.com can work.

---

### Post by Clockmender on 2016-04-23
Hello TheFu,

Here is the output from postconf -n, IP's and domains redacted:

```

root@server1:/etc/postfix# postconf -n
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
disable_vrfy_command = yes
dovecot_destination_recipient_limit = 1
enable_original_recipient = no
header_checks = regexp:/etc/postfix/header_checks
inet_interfaces = all
inet_protocols = all
local_transport = error:Local Mail Delivery is Disabled
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination = localhost
myhostname = server1.EXAMPLE.COM
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
myorigin = /etc/hostname
readme_directory = no
recipient_delimiter = +
smtp_helo_timeout = 60s
smtp_sasl_security_options = noplaintext, noanonymous
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_use_tls = yes
smtpd_banner = EXAMPLE-ESMTP (Real domain name not here, just three letters)
smtpd_client_restrictions = permit_mynetworks, reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject, reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_rbl_client zen.spamhaus.org, reject_rbl_client bl.spamcop.net, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, check_policy_service unix:private/policy
smtpd_relay_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/letsencrypt/live/EXAMPLE.COM/cert.pem
smtpd_tls_dh1024_param_file = ${config_directory}/dh1024.pem
smtpd_tls_dh512_param_file = ${config_directory}/dh512.pem
smtpd_tls_exclude_ciphers = aNULL, eNULL, EXPORT, DES, RC4, MD5, PSK, aECDH, EDH-DSS-DES-CBC3-SHA, EDH-RSA-DES-CDC3-SHA, KRB5-DE5, CBC3-SHA
smtpd_tls_key_file = /etc/letsencrypt/EXAMPLE.COM/privkey.pem
smtpd_tls_loglevel = 1
smtpd_tls_mandatory_protocols = !TLSv1,!SSLv2,!SSLv3
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf, mysql:/etc/postfix/mysql_virtual_alias_domainaliases_maps.cf
virtual_mailbox_base = /var/vmail
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf, mysql:/etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf
virtual_transport = dovecot

```

We have a board meeting today and I am going to propose that we take a second Internet connection on a new static IP - I will then put the card machine on one connection, and nothing else, then put all the other club internet resources - like the server, which handles our mail, cloud and SMS gateway, along with the clubhouse Wifi, etc on the other connection, so a scan of the card machine IP will not show the server. Do you agree with this? Another person sent me this advice:

[COLOR="#0000FF"]"We definitely will not be able to encrypt traffic on port 25 before STARTTLS is being issued &#8211; so we will not be able to solve the PCI audit issue in this matter.
 
In regards to the issue with sending emails with no need to authenticate, I think all we are able to do is to disconnect unwanted senders at the time they send HELO command (via more restricted policies).
I would suggest to review `smtp_helo_restrictions = permit_mynetworks, reject` or similar and `smtpd_client_restrictions = permit_mynetworks, reject` and see how you can send and receive emails with such configuration."[/COLOR]

I haven't tried this yet.

So if you agree with this as well, the only option is to separate the two on different IP addresses. Oh yes, we cannot use dial-up for the card machine as the only telephone cable to the airfield was laid in 1940 when the airfield was built by the USAAF and no longer works! We use a local radio link to a fibre optic network - the transmitter is only 1/2 mile away and we get 30Mb/sec both upload and download. Our telephones in the clubhouse use VOIP.

Thanks for you help, Clock.

---

### Post by TheFu on 2016-04-23
Seems you do have some budget and could solve this a few different ways that would be less expensive than paying for another internet connection.

Options:
a) move the email server to a VPS in "the cloud"; keep the CC processing local, but don't allow **any** mixed use traffic; no web browsing by anyone. A $5/month VPS should suffice for simple postfix needs, but it depends on what other things the system does and how many users it has to support and how active they are with email.

b) Get a mifi cell connection for CC stuff. Since that is very low bandwidth, a cheap plan should be fine.

c) Keep the current static IP; Setup a 2 or 3 router config to put the CC processing part onto a completely different internal subnet behind another router. This will use double-NAT.  The WAN port on the new internal router would treat everything out there like it was the internet (hostile). The email server would be there. If allowing end-users to browse the internet over this link is required, then it is important from a security standpoint to have 3 separate networks - that just means more subnets and more firewalls.
1) CC secured network (wired)
2) Server network (wired)
3) end-user network + all local wifi

There are lots of other options, but those are the main ones.

Any router that can run pfsense or a current dd-wrt would be fine for the 2nd config, assuming this is a small biz setup. I would avoid most home-router products since keeping them patched is next to impossible. Also, seems that about 80% of them have intentional back doors in the firmware for some reason.  

If you are slightly network savvy, the low-end Ubiquiti routers for $60 are an excellent value, but you'll need to learn that OS.  Heard that brocade has free training online for it.

I just spent about $150 for some new hardware to upgrade an Alix system  (limited to about 50Mbps VPN connections) running pfSense to a newer, faster, solution.

I don't have time to compare the postconf output in detail with a formerly working config here now (would need to dig through some old backups). At first glance, there are some settings that don't make sense to me (my expectations), like no local delivery and no local subnet?  Maybe there's a good reason for this based on the network design.  It is impossible to separate server security from network security, IMHO. The design for both is important for overall application security.

Sorry to bring all this other stuff up.  This is all for a club?  Knew a guy who lived with a small runway in his neighborhood - all the houses were part owner in the field - fly-in-fly-out, but uncontrolled.  Don't think they had a store, but that was many years ago.

Saturday morning is system patch time here, plus I need to migrate 2 email servers to a fresh Zimbra install this weekend.

---

### Post by bashiergui on 2016-04-23
> We have a board meeting today and I am going to propose that we take a second Internet connection on a new static IP - I will then put the card machine on one connection, and nothing else, then put all the other club internet resources - like the server, which handles our mail, cloud and SMS gateway, along with the clubhouse Wifi, etc on the other connection, so a scan of the card machine IP will not show the server. Do you agree with this?Very much yes. Isolating the sensitive data is an exceptionally good idea. Having the free wifi on the same subnet as your credit card machines is a phenomenally bad idea- I'm surprised it is PCI compliant.

If you don't trust Trustwave, there are dozens of consultants that can help you not only be PCI compliant but also be actually secure. I STRONGLY suggest you consider hiring a firm to help- some provide data breach protection which could save you thousands in the event of a breach. Here's one:
[https://www.controlscan.com/compliance/pci-compliance-overview/pci-1-2-3-self-assessment/](https://www.controlscan.com/compliance/pci-compliance-overview/pci-1-2-3-self-assessment/)

---

### Post by Clockmender on 2016-04-23
Thanks for all the advice, Someone told me to stop the local transport so people couldn't use telnet to send from one internal email to another - this appears to be bull**t so I will put it back to how it was. The only ones that can be guessed at are postmaster@xxx and webmaster@xxx, these are virtaul mailboxes that cannot send mail out.

The Board of the club resolved today to have a second internet connection, we will use the ISP's basic package and put the CC machine on that and nothing else. We will leave the server on the high speed connection, that way the PCI compliance scan won't even see it as it will have a separate static IP. This is a cheaper option than using a hosting service for the mail. Trustwave are happy with our Cloud and SMS gateway services, these are all over a fully certified SSL encrypted channel. We use OwnCloud for the data and PlaySMS for the text gateway. Their only issue was with unencrypted connections to port 25, before the STARTTLS command was sent. So this solutions will cure the problem. I cannot change PCI the compliance company as it is dictated by the Bank/Credit Card company. Incidentally, Trustwave also failed us on TLSv1.0/SSLv2/SSLv3 although these are specifically excluded in both the Postfix and Apache config files. Trustwave said in an email that they get false positives at times, but they still fail you rather than ask to see your configs or do the testing properly! I have told Trustwave what we are doing and am waiting for a reply, I cannot see how they could fault this setup.

I know you have said that a radio link might cause more problems, but our downtime since we changed to this has been a total of 2hrs 28mins in 2 years. The change was forced when the old landline finally gave up and the telecom company wanted around £100,000 to replace it.

All the club's data is backed up to a second disk in the server and to my server at a remote location, and from there to an external disc kept in my safe - overkill I know, but that keeps the other directors happy. Our server is constantly monitored by Beyond Security, who give us a clean bill of health with a 100% A+ rating. They note the port 25 issue, but say it is very low risk and with the other measures we have in place to prevent abuse of the mail system, they are happy to keep our security status.

Thanks again for the help - I will continue to monitor the systems for security breaches, there have been none to date.

Cheers, Clock.

---

### Post by Clockmender on 2016-04-23
Thanks for all the advice, Someone told me to stop the local transport so people couldn't use telnet to send from one internal email to another - this appears to be bull**t so i will put it back to how it was. The only ones that can be guessed at are postmaster@xxx and webmaster@xxx, these are virtaul mailboxes that cannot send mail out.

The Board of the club resolved today to have a second internet connection, we will use the ISP's basic package and put the CC machine on that and nothing else. We will leave the server on the high speed connection, that way the PCI compliance scan won't even see it as it will have a separate static IP. This is a cheaper option than using a hosting service for the mail. Trustwave are happy with our Cloud and SMS gateway services, these are all over a fully certified SSL encrypted channel. We use OwnCloud for the data and PlaySMS for the text gateway. Their only issue was with unencrypted connections to port 25, before the STARTTLS command was sent. So this solutions will cure the problem. I cannot change PCI the compliance company as it is dictated by the Bank/Credit Card company. Incidentally, Trustwave also failed us on TLSv1.0/SSLv2/SSLv3 although these are specifically excluded in both the Postfix and Apache config files. Trustwave said in an email that they get false positives at times, but they still fail you rather than ask to see your configs or do the testing properly! I have told Trustwave what we are doing and am waiting for a reply, I cannot see how they could fault this setup.

I know you have said that a radio link might cause more problems, but our downtime since we changed to this has been a total of 2hrs 28mins in 2 years. The change was forced when the old landline finally gave up and the telecom company wanted around £100,000 to replace it.

All the club's data is backed up to a second disk in the server and to my server at a remote location, and from there to an external disc kept in my safe - overkill I know, but that keeps the other directors happy. Our server is constantly monitored by Beyond Security, who give us a clean bill of health with a 100% A+ rating. They note the port 25 issue, but say it is very low risk and with the other measures we have in place to prevent abuse of the mail system, they are happy to keep our security status.

Thanks again for the help - I will continue to monitor the systems for security breaches, there have been none to date.

Cheers, Clock.

---

