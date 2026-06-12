---
title: "Exim - accept mail from certain domain?"
date: 2006-07-03
forum: Server Platforms
---

### Post by catfox on 2006-07-03
Hi All,
I'm trying to configure my exim MTA to allow all mail from my personal domain to be delivered without performing any spam, malware or content scans on it. 

the config i have right now is: [http://pastebin.ca/77934](http://pastebin.ca/77934)

and I'm confused because as far as I'm aware, doing something like:
acl_check_rcpt:
  accept domains = foo.com

should stop the process there if the mail has foo.com in its from field, and send it onto a transport. but my mail's still fail the acl_content_scan and acl_mime_bodypart scans, which are further down in the config.

does anyone have any ideas how to get this working?
thanks for reading.

---

### Post by nagilum on 2006-07-05
The ACL you used only verifies the recipient, i.e. the "To" header. If you send any mail to *@foo.com the mail is automatically accepted. To check for the sender domain you can use something like "accept senders = *@foo.com" (you know these can be forged easily, don't you?).

---

