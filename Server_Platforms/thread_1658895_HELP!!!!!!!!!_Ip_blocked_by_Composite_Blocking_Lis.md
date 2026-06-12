---
title: "HELP!!!!!!!!! Ip blocked by Composite Blocking List for spamming"
date: 2011-01-03
forum: Server Platforms
---

### Post by cbarron on 2011-01-03
My IP has been blocked by Composite Blocking List for "
[FONT=Verdana, Arial, Helvetica][SIZE=2]IP Address ***.**.***.207 **is listed** in the CBL. It appears to be infected with  a spam sending trojan or proxy.[/SIZE][/FONT]
 [FONT=Verdana, Arial, Helvetica][SIZE=2]It was last detected at 2011-01-02 11:00 GMT (+/- 30 minutes), approximately 1 days, 3 hours, 29 minutes ago.[/SIZE][/FONT]
 [FONT=Verdana, Arial, Helvetica][SIZE=2]It has been relisted following a previous removal at 2010-12-30 17:15 GMT (3 days, 21 hours, 2 minutes ago)"[/SIZE][/FONT]


[FONT=Verdana, Arial, Helvetica][SIZE=2]How do I find this "trojan" and remove it???? I have a network of 6 computers right now, 5 are running Ubuntu (3 server and 2 Desktop versions) and one windows computer. I have run a virus scan in the windows computer and found nothing. How can I scan a linux computer for a virus? Any and ALL ideas welcomed.[/SIZE][/FONT]


[FONT=Verdana, Arial, Helvetica][SIZE=2]
[/SIZE][/FONT]

---

### Post by b0b138 on 2011-01-03
who exactly is blocking your ip? Your isp, dyndns site, a specific web site?

---

### Post by cbarron on 2011-01-03
It is listed on [http://cbl.abuseat.org/](http://cbl.abuseat.org/)  this was seen when I tried to send an email to someone who uses emailsrvr.com. This is the response I got when I tried to send the email:
 
[FONT=-moz-fixed]This is the mail system at host Server1.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

[EMAIL="trc@fieldsolutions.com"]<trc@***********.com>[/EMAIL]: host mx1.emailsrvr.com[**.***.185.3] said: 554 5.7.1
    ACL dns_rbl; Client host [***.**.***.207] blocked using
    pf-ip4tset.blagr.emailsrvr.com=127.24.0.2 Please visit
    [http://bounce.emailsrvr.com/?a0](http://bounce.emailsrvr.com/?a0) for more information on why this message
    could not be delivered (in reply to RCPT TO command)
[/FONT]

Hope this helps shed some light on the matter.

---

### Post by psusi on 2011-01-03
Did you install a proxy server?

---

### Post by cbarron on 2011-01-03
no i did not install a proxy server.....I do now know that my email that i host got hijacked now I just need to figure out how to prevent it in the future and how to fix it now........would a proxy server have helped?

---

### Post by wilee-nilee on 2011-01-03
From the FAQ link on removing the IP from the list.

I'm running Linux (FreeBSD, OpenBSD, UNIX...) and CANNOT be infected with a virus!

While it is perfectly true that UNIX-like operating systems are almost NEVER infectable with Windows viruses, there are a number of virus-like things that UNIX-like systems are susceptible to.
For example:

   1. Windows emulation software (eg: VMWARE or Wine) are just as susceptable to infection as native Windows. In fact, it's probably somewhat more likely that an emulator instance of Windows gets infected, because the fact that it's running under another O/S can lead to a false sense of security, and emulator instances are less likely to be protected with a full anti-virus suite.
   2. Open proxies (eg: insecure Squid configurations) leading to open proxy spamming.
   3. Acting as a NAT for a local area network - meaning that machines on the local area network could be infected, and the CBL detects the NAT address not the machine LAN that's actually responsible. It's best to secure the NAT.
   4. Web server vulnerabilities or compromises. For example, the DarkMailer/DirectMailer trojan is injected via FTP (using compromised user's userid/passwords) onto web servers, and thereupon is used to send very larger volumes of spam. Virtually all web servers are susceptible to this if they permit upload of content from the Internet.
   5. Application vulnerabilities: many applications have security vulnerabilities, particularly those associated with PHP on web servers. Eg: older versions of PHPNuke, Mamba etc.

      Some of these vulnerabilities are to the extent that a malefactor can install a full proxy/trojan spamming engine on your machine and control it remotely. Watch out for strange directories being created, particularly those starting with a "." in /tmp. Check for this by doing an "ls -la" in /tmp, and look for directory names starting with "." (other than "." and ".." themselves).
   6. Rootkits are where a malicious entity has installed software on your machine and buried it in such a way that the normal system utilities cannot find it. In some cases they replace the normal system utilities with hacked versions that won't show their tracks.

      Check that you have good remote login-capable passwords (eg: telnet, FTP, SSH), inspect your logs for large quantities of failed SSH/telnet login attempts.

      Consider running a "system modification" detector such as Tripwire.
   7. Not all viruses are windows binaries. Some viruses/worms are in application-level files using non-binary programming techniques (such as macro viruses). These can be truly infectious cross-platform.
[http://cbl.abuseat.org/faq.html](http://cbl.abuseat.org/faq.html)

---

### Post by psusi on 2011-01-03
So you have a mail server installed?  Which one and what version?  You need to make sure that it is not configured as an open relay or spammers will use it to forward mail.

---

### Post by cbarron on 2011-01-03
yeah its a postfix mail server......kinda...........my email all runs through EHCP.......what do i need to look for? any ideas?

---

### Post by psusi on 2011-01-03
You need to configure the smtp server to not accept connections from the outside, or if it does, to require authentication.

---

### Post by James78 on 2011-01-03
This guide has a section on restrictions (security configuration) *
[http://flurdy.com/docs/postfix/#config-simple-mta](http://flurdy.com/docs/postfix/#config-simple-mta)

Scanning incoming/outgoing emails for viruses using ClamAV clamscan (ClamSMTP)
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#ClamSMTP SMTP Virus Filter](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#ClamSMTP SMTP Virus Filter)

Here's my restriction section. This catches 85% of spam coming in, but there are 1 or 2 occasional ones that can get through (very rarely). Which is why you can setup something like spamassasin, which will move the spam emails to the spam folder.
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

* Please note that the rbl and rhbl they use in the example config MAY be out of date, so you will need to use different ones (see my list; none on my list are inactive).

---

### Post by cbarron on 2011-01-03
wow this is great guys......thanks for the help......please keep the info and ideas coming

---

### Post by cbarron on 2011-01-04
Well I found the issue: It seems that root was open by default so that is how they got in and started spamming email. so now I just need to clean up the "mess" and do some damage control and tighten up security.


Thanks for all the help

---

### Post by psusi on 2011-01-04
Yet another reason why you should not muck about setting a root password.

---

