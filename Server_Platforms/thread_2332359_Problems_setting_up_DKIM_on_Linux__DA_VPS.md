---
title: "Problems setting up DKIM on Linux / DA VPS"
date: 2016-07-30
forum: Server Platforms
---

### Post by dutchlearner on 2016-07-30
I'm having a problem with sending e-mails directly from the mailserver to Microsoft mail accounts (Live, Outlook, Hotmail, etc). These e-mails are being send from [EMAIL="admin@mail.example.com"]admin@mail.example.com[/EMAIL] (this is an example, but the 'mail'-subdomain is included in the full address). When the mail arrives, it says that the SPF record has been passed, but DKIM doesn't show up. See here:


```
CMM-Authentication-Results: hotmail.com; spf=pass (sender IP is redacted)
smtp.mailfrom=admin@mail.example.com; dkim=none
header.d=xampledomain.net; x-hmca=none
header.id=contact@exampledomain.net
```


I followed this tutorial to set up the DKIM:


[https://help.directadmin.com/item.php?id=569](https://help.directadmin.com/item.php?id=569)


I verified that it has been enabled:


```
[root@VPS /]# cat /usr/local/directadmin/conf/directadmin.conf | grep dkim
dkim=1
```


I then went to the admin panel, User Level, and coppied the whole record to the DNS-configuration at my provider. Note that I'm using a VPS myself. When I dig it through the command line, I see that it resolves:


```
[root@VPS /]# dig txt x._domainkey.mail.example.com


; <<>> DiG 9.8.2rc1-RedHat-9.8.2-0.47.rc1.el6 <<>> txt x._domainkey.mail.example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15635
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;x._domainkey.mail.example.com. IN  TXT


;; ANSWER SECTION:
x._domainkey.mail.example.com. 617 IN TXT   "v=DKIM1\; k=rsa\; p=MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAru6kqwqnkt1krh/eKle/cP1+wK/lbA4aD1enQUm24BOHjiEQI3/7WB5O1UAZi4f4DZ0sQP3PVJreEZBqtL5dl+d eoU/Qj9oL+qCAe7IHdNgFW3/Fzg3ke8aOvWsPC8o0M5VvYAfibgcFpLCvu5BUqYwqvME3oU7WNK7OSjtPinf1wbFKEGUIh9ZzUcib0JO3" "gRzIxf6qXXu8htmFiNnInPDKHsn4oIioI5gWHiyKXs/EB GupIxrFJOlFmX213iYv/O9W3zpIz/+lOredactedforpurposesrTZgzDIyAb2HXZeSAmT0Rcp/mFMF5dPZw1KA6m/dkmqvwIDAQAB"
```


What am I missing here, why does Microsoft keep telling me that DKIM is not enabled?

---

### Post by dutchlearner on 2016-07-31
Anybody?

---

### Post by howefield on 2016-07-31
Moved to the "*Server Platforms*" forum.

---

### Post by Graham_Willis on 2016-07-31
When did you perform these actions? If you make changes in DNS zone of a domain, then they need some time to propagate - let's say up to 48 hours. So the first thing that you can do is to perform this test again. If it doesn't work as you expected - send e-mails to other domains and check if DKIM is seen. Check what's the response of other nameservers that the ones you have configured in your settings (your dig was querying the nameserver which is default for you, you can query any nameserver opened to external traffic by a command like **dig ****@nameserver domain.com txt**), preferrably Microsoft servers. If it doesn't work for any domain, then you must have something wrong with your configuration. If it just doesn't work for Microsoft domains - the best thing that you can do is to contact them why they behave this way.

One more thing: updating zone serial may prove useful.

---

