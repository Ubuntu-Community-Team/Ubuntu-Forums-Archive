---
title: "Samba PDC &amp; Exchange 2000"
date: 2011-02-04
forum: Server Platforms
---

### Post by Dave.Wynne on 2011-02-04
I presently have a 2 server system a Sambe PDC and a mail server running Bynari Insight Server and we use Bynari connector to connect our Outlook 2000 clients to the Insight Server. It works well enough. **BUT....** Bynari are stopping support for Outlook 2000.
For us the upgrade all our copies of Outlook is expensive and we have all the functionality we need.
So, we have MS Server 2000 and Exchange 2000 which we used to use, but had all sorts hacking issues etc when we used it for our Domain and Mail. I've been thinking that we could continue with our Samba PDC and use something like postfix, with amavis and spamassasin to act as a SMTP relay agent to an Exchange 2000 stand alone server which is fully isolated behind our firewall on a protected subnet and use port forwarding to enable Webmail and OpenVPN server to access the mail from outside.
Does anyone know how to connect Exchange to Samba & Openldap and also what would I have to do to set up postfix, amavis and spamassasin to act as a relay?
 
Any thoughts I'm sure someone has wanted to do this before. I'm loathed to move away from a linux mail server but costs make it attractive.

---

