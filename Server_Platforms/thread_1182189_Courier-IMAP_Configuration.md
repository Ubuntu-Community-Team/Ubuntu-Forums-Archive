---
title: "Courier-IMAP Configuration"
date: 2009-06-08
forum: Server Platforms
---

### Post by Lord_Dicranius on 2009-06-08
I'm working on moving my users to another server.  So I've changed all the MX record to point to the new server, but setup forwarding of email from the new server to the old server until I can get all the email moved over tot he new server (moving users in phases).  I'm having issues with the users who are sending email from the old server though.  When they try to send an email to another interdomain user, it just sends it to the old servers mailbox.  It seems it's not checking the MX records at all because it's simply finding the mailbox by the username already on that server.

Is there a way to reconfigure Courier-IMAP to check the MX records first and route email that way first before delivering locally?

---

