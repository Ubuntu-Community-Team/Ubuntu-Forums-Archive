---
title: "All forums really need yours help for mail server"
date: 2016-12-25
forum: Server Platforms
---

### Post by jivko790 on 2016-12-25
All forums really need yours help for mail server  .. i have install plesk 12  ubuntu 14.04    get a lot of spam emals send end get it
never do it that send email to some one ( i am sorry my english since poor  but need your help ) cannt pay to devoloper ) 

my error look how to find resolve that ?

best regards
jivko
```

Dec 25 08:22:11 sd-100195 postfix/smtp[26554]: 7392D588C62: to=<oskar.thalhammer@unileoben.ac.at>, relay=mgate4.unileoben.ac.at[193.171.87.212]:25, delay=23170, delays=22357/813/0.52/0, dsn=4.0.0, status=deferred (host mgate4.unileoben.ac.at[193.171.87.212] refused to talk to me: 554-mgate4.unileoben.ac.at 554 Your access to this mail system has been rejected due to the sending MTA's poor reputation. If you believe that this failure is in error, please contact the intended recipient via alternate means.)
Dec 25 08:22:11 sd-100195 postfix/qmgr[20734]: 84DCA47A7B7: from=<info@......................>, size=15435, nrcpt=6 (queue active)
Dec 25 08:22:11 sd-100195 postfix/error[4585]: 84DCA47A7B7: to=<jimmy.da@verizon.net>, relay=none, delay=71838, delays=71838/0/0/0, dsn=4.0.0, status=deferred (delivery temporarily suspended: host relay.verizon.net[206.46.232.11] refused to talk to me: 571 Email from ...................... is currently blocked by Verizon Online's anti-spam system. The email sender or Email Service Provider may visit [http://www.verizon.net/whitelist](http://www.verizon.net/whitelist) and request removal of the block. 161225)
Dec 25 08:22:11 sd-100195 postfix/smtp[26487]: 7AC1856899D: to=<mpstallone@belvederepacificgroup.com>, relay=mailstore1.secureserver.net[68.178.213.243]:25, delay=55355, delays=54542/812/0.77/0, dsn=4.0.0, status=deferred (host mailstore1.secureserver.net[68.178.213.243] refused to talk to me: 554 p3plibsmtp02-03.prod.phx3.secureserver.net bizsmtp IB103. Connection refused. ...................... has a poor reputation on Cloudmark Sender Intelligence (CSI). Please visit [http://csi.cloudmark.com/reset-request/?ip=](http://csi.cloudmark.com/reset-request/?ip=)...................... to request a delisting.)
Dec 25 08:22:11 sd-100195 postfix/qmgr[20734]: 8F3C94C9E2F: from=<info@......................>, size=14011, nrcpt=6 (queue active)
Dec 25 08:22:11 sd-100195 postfix/error[4331]: 8F3C94C9E2F: to=<johndenais@hotmail.com>, relay=none, delay=83278, delays=83278/0/0/0, dsn=4.4.2, status=deferred (delivery temporarily suspended: lost connection with mx2.hotmail.com[65.55.92.184] while sending RCPT TO)
Dec 25 08:22:11 sd-100195 postfix/error[4331]: 8F3C94C9E2F: to=<vikes931@hotmail.com>, relay=none, delay=83278, delays=83278/0/0/0.01, dsn=4.4.2, status=deferred (delivery temporarily suspended: lost connection with mx2.hotmail.com[65.55.92.184] while sending RCPT TO)^C
Dec 25 08:22:11 sd-100195 postfix/qmgr[20734]: 8AF38479D00: from=<info@......................>, size=12854, nrcpt=3 (queue active)
Dec 25 08:22:11 sd-100195 postfix/error[4420]: 8AF38479D00: to=<eldo1171@hotmail.co.uk>, relay=none, delay=65527, delays=65527/0/0/0, dsn=4.4.2, status=deferred (delivery temporarily suspended: lost connection with mx2.hotmail.com[207.46.8.199] while sending RCPT TO)
Dec 25 08:22:11 sd-100195 postfix/smtp[31310]: 77253568CA2: host mx-biz.mail.am0.yaho

```

---

### Post by lisati on 2016-12-25
It looks like your server's IP address has a poor reputation. Make sure that your server isn't configured as an open relay and that it hasn't been compromised by malware. 

You might have noticed that the rejection messages include links to websites where you can find out why your email is being rejected.

You can also check which blacklists your server's IP address is listed on at [http://multirbl.valli.org/](http://multirbl.valli.org/) and [http://whatismyipaddress.com/blacklist-check](http://whatismyipaddress.com/blacklist-check) (you don't necessarily need to us both) and follow the removal instructions at the websites belonging to the blacklist owners.

---

### Post by lisati on 2016-12-25
If the log entries you have posted are from your own server, your problem is not with spam that you are receiving. The errors relate to spam that other people think that someone has sent from your IP address. Please use the links I provided to research why people might think you are a spammer.

---

### Post by SeijiSensei on 2016-12-26
First, if you're trying to send mail from a server on a residential connection, you'll often have a bad reputation because the major blacklists treat all such connections as suspect.  For many years, malware-infected Windows computers in homes were converted into spambots.  If your server is on a business-class connection or at a virtual hosting provider like Linode, then you probably have been running an "open relay" and got a bad reputation as a result.

I use [mxtoolbox.com]("http://mxtoolbox.com/SuperTool.aspx") to check my server's reputation.  You can also run simple diagnostic tests from that site to check to see if you are an open relay.

If you look though /var/log/mail.log and see mail coming in from random senders and resent to random recipients, you're an open relay.  You should only accept inbound mail for the domains for which you are a valid MX host.

Running a mail server in the modern world is a challenging task requiring careful configuration and constant monitoring.  It's much harder than running a web server.

If you have a bad reputation, it will take some time to fix it.  The easiest solution is to obtain a new IP address from your provider.  Before you do that, make sure your server is fully locked-down.

---

