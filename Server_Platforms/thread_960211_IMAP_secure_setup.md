---
title: "IMAP secure setup"
date: 2008-10-27
forum: Server Platforms
---

### Post by stbe on 2008-10-27
Until now I use UW-IMAP/EXIM in some intranet solution (local network). I want to allow IMAP+SMTP access from internet (WAN) by opening those ports. To make this secure, I want to

- disable plain text password access (at least for WAN)
- allow only specific users to use IMAP/SMTP via WAN
- allow all users access to IMAP/SMTP via localnet
- automatically block hosts (= public IP addresses) that try to hack into some account (like denyhosts does for SSH)

Can I use another password for SSL-IMAP-users (from outside) or have I to create another user?

Can anybody give me some hints what's possible with Ubuntu(hardy) and where to look for solutions?

---

### Post by cdenley on 2008-10-27
I'm not sure how to configure exim, but fail2ban can be configured to audit any log, and block hosts based on any type of event in the log.

---

### Post by hyper_ch on 2008-10-27
I think the main problem you'll encounter is to only let a few of all users to select from outside. Right now nothing comes to my mind to simply achieve that. Either all local users can access from outside or none --> that's trivial.

---

### Post by stbe on 2008-11-20
Any more ideas?

- It seems I can fine-tune user authentication with PAM.
- hosts.allow and hosts.deny is a fine way of controlling access to services for specific hosts.

I need to control combination of user+service (ideally together with interface/hostaddress pattern):

most users can use ssh locally (private ip range or interface)
xyz can use ssh from public ip (public interface)
abc can use secure IMAP from specific ip range (might be public)
anyone can use secure(993) IMAP locally (private ip range or interface)
xyz can use unsecure(143) IMAP locally (private ip range or interface)

Is there no solution for this? (I want to setup this for uw-imap at first.)

---

