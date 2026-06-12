---
title: "Setting up a web/ftp/svn server"
date: 2007-03-22
forum: Server Platforms
---

### Post by clievers on 2007-03-22
Hi there,

I recently installed the LAMPP server from the Ubuntu install. I finally got Apache working with multiple hosts (currently 1 host and 3 sub-domains, but may have additional ones in the future). I found that setting up the user accounts and apache stuff with Webmin was fairly straight forward.

What I would like to do next is set up an ftp server on it. There would be some requirements for this. I would like it to be able to differentiate between the hosts. So if the user account USER1 is the user for HOST1 (home directory, etc), I would like to have that user account be the login for HOST1 FTP, where the ftp directory is his home directory. Optionally, I would also like to have a public ftp for HOST1. Then, the same would go for USER2/HOST2, etc. What, please, would be your recommendations on the best (free) ftp server to use, and can it be configured through Webmin?

Finally, the step after this would be the same as ftp, only for subversion/svn. Each host could potentially have a private/public subersion repository(ies) to access. Is this also easy to set up?

Thank you in advance,

-- a n00b linux user, cheers!

---

### Post by jboss1995 on 2007-03-26
[http://www.howtoforge.org/ubuntu6.10_firewall_gateway](http://www.howtoforge.org/ubuntu6.10_firewall_gateway)

This is a good place to find out how to do what you are asking for. I would not install all that he does but just what you need.

Justin

---

### Post by clievers on 2007-03-26
Thanks for the reply, however this particular article doesn't answer any of my questions. I have bookmarked it for future reference though.

> Includes: Shorewall, NAT, Caching NameServer, DHCP Server, VPN Server, Webmin, Munin, Apache (SSL enabled), Squirrelmail, Postfix setup with virtual domains, courier imap imaps pop3 pop3s, sasl authentication for road warriors, MailScanner as a wrapper for SpamAssassin, Razor, ClamAV, etc. Samba installed, not configured.

Out of the topics it covers, Apache and Webmin only apply to me; however, I already have this going. I need to know about different FTP server possibilities and how to configure it, then SVN. I'm not interested in webmail at all.

Thanks.

---

### Post by elst on 2007-03-26
vsftpd is easy to configure, and works very well. I don't know whether there is a Webmin module for it. You can host Web sites inside account home directories, so what you describe should be easy to set up.

For Subversion:

[http://svnbook.red-bean.com/](http://svnbook.red-bean.com/)

If you set up SSH access (for Subversion, or just to provide secure remote access) then FTP is probably redundant.

---

