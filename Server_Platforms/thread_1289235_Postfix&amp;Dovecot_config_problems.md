---
title: "Postfix&amp;Dovecot config problems"
date: 2009-10-12
forum: Server Platforms
---

### Post by Musicalgibbon on 2009-10-12
Hi all, 

I've installed the server 9.04 build recently, with a view to setting up a mail server. I've followed the instructions [here]("https://help.ubuntu.com/9.04/serverguide/C/email-services.html") (also did the firewall steps). 

It seems to be working okay for the most part (can telnet in from localhost, and from other machines; can connect through Outlook and pass all the tests; can send a test email to an external address), however it seems to be having trouble if I send a test message to anyone within the domain I've set up. Whenever this is attempted the lines:

Oct 12 13:46:21 [Domain] deliver(root): chdir(/root) failed: Permission denied
Oct 12 13:46:21 [Domain] deliver(root): stat(/root/.dovecot.sieve) failed: Permission denied
Oct 12 13:46:21 [Domain] deliver(root): stat(/root/Maildir/tmp) failed: Permission denied (euid=65534(nobody) egid=65534(nogroup) missing +x perm: /root)

are produced in /var/mail.err (I've replaced my domain with [Domain], if you're wondering). From my very limited knowledge, it seems a little strange that it's trying to setup the folders within the root directory, but this may be normal.

Any ideas?

Note - Eventually I'm looking to add virtual users, through mySQL and incorporate squirrelmail, but I thought I'd get this all sorted first.

*[Solved] It turned out that the issue was simply one of access permissions. Once I had changed the user whose details I was connecting to the mail server with, to an administrator, then everything seems to have worked.*

---

