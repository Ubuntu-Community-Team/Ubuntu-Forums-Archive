---
title: "Really confused re gmail sending through my server"
date: 2011-05-31
forum: Server Platforms
---

### Post by puremetal on 2011-05-31
Hi all,

I run a 6.06.2 Dapper server for a not-for-profit, and have had a very simple email set-up working for a couple of years. Users have their email address set up on the server, and use a gmail account as webmail access/storage. Emails are downloaded via POP to users gmail accounts, and are sent out from gmail via SMTP to the server. Like I said, this has worked fine for ages, but in the last couple of days its all gone wrong.

The SMTP log I get for an email I tried to send from gmail is as follows:

> 
May 31 12:08:47	postfix/qmgr[26708]	1C03D3301D: removed
May 31 12:08:46	postfix/smtp[27167]	Server certificate could not be verified
May 31 12:08:46	postfix/smtp[27167]	certificate peer name verification failed for gmail-smtp-in.l.google.com: CommonName mis-match: mx.google.com
May 31 12:08:46	postfix/smtp[27167]	certificate verification failed for gmail-smtp-in.l.google.com: num=27:certificate not trusted
May 31 12:08:46	postfix/smtp[27167]	certificate verification failed for gmail-smtp-in.l.google.com: num=20:unable to get local issuer certificate
May 31 12:08:46	postfix/qmgr[26708]	1C03D3301D: from=<***@mail.***.org.uk>, size=21600, nrcpt=1 (queue active)


Does this make sense to anyone? I haven't changed any settings for email in months, just occasional maintenance (eg flushing deferred queue). Please help! :confused:
Thanks!


edit: and the mail I get returned from the server is:

> Delivery to the following recipient failed permanently:

    *****@*****.com

Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 535 535 Error: authentication failed (SMTP AUTH failed with the remote server) (state 8 ).

---

### Post by spynappels on 2011-05-31
I'm afraid I can't help you with your specific problem, but I would suggest a distribution upgrade as that version is now end-of-life.

---

### Post by puremetal on 2011-05-31
Fixed, I think... I added the following to my postfix main.cf

> # Alternatively, you can specify the mynetworks list by hand, in
# which case Postfix ignores the mynetworks_style setting.
#
# Specify an explicit list of network/netmask patterns, where the
# mask specifies the number of bits in the network part of a host
# address.
#
# You can also specify the absolute pathname of a pattern file instead
# of listing the patterns here. Specify type:table for table-based lookups
# (the value on the table right-hand side is not used).
#
#mynetworks = 168.100.189.0/28, 127.0.0.0/8
#mynetworks = $config_directory/mynetworks
#mynetworks = hash:/etc/postfix/network_table
[B]mynetworks = 192.168.0.1
mynetworks = *my server's IP 1*
mynetworks = *my server's IP 2*
mynetworks = gmail-smtp-in.l.google.com
mynetworks = mx.google.com[/B]


Still none the wiser as to why it happened, but this appears to be a good enough workaround.

And, yeah I know I need to dist upgrade. Just a little scared of doing so in case it mucks up my settings. There isn't a way to test an upgrade (for problems) before actually going through with it, is there?

---

### Post by brettg on 2011-06-01
If you can afford some downtime, you could always boot the machine to a liveCD and image the HDD using dd to an external drive.

Something like;

dd if=/dev/sda of=/path/to/imagefile.img

If things go pear shaped after the upgrade, you could roll back by reversing the parameters;

 dd if=/path/to/imagefile.img of=/dev/sda 

Even better, convert the server to a virtual server image and run it virtualised. Taking a snapshot of a virtual server before upgrading it makes dist-upgrades far less nerve wracking.

---

