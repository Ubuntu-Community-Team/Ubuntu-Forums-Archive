---
title: "[Server] postfix   _Connection_Rejected_   (with error text)"
date: 2020-06-30
forum: Server Platforms
---

### Post by mikecolley on 2020-06-30
Hi All:  

What works:[INDENT]1) incoming e-mail using ubuntu server postfix works.
2) outgoing e-mail using ubuntu server postfix when sent to yahoo.com
[/INDENT]

What is broken:[INDENT]1) outgoing e-mail from my personal use ubuntu server postfix here at home when sent to twc.com and other places that use Spamhaus.
[/INDENT]
 
Postfix fails sending e-mail to twc.com (Time Warner Cable) and some other places.

Problem sending e-mail to various domains such as my seldom used e-mail address at twc.com(and other places too), here is the problem report text in the e-mail sent to me from my local postfix:

```
<[my-email-id]@twc.com>: delivery temporarily suspended: host
    pkvw-mx.msg.pkvw.co.charter.net[47.43.26.7] refused to talk to me: 554
    p-impin020.msg.pkvw.co.charter.net cmsmtp Connection Rejected - see
    [http://www.spamhaus.org/query/ip/74.13x.xx.xxx]("http://www.spamhaus.org/query/ip/74.135.xx.xxx") (I obscured it because it was my home IP number) AUP#In-1240
```

Apparently Spamhaus does't like the IP here at home that postfix is sending from and twc.com refuses the e-mail because of that.  I am guessing that is what the message means.

Interesting is that e-mail to yahoo.com is received at Yahoo, I read it and it works ok!!!  but not to twc.com???  and because it sends to yahoo.com I guess postfix is set up correctly for sending e-mail.

Does anybody have any suggestions how I can fix this issue on this my personal server here at home?  This internet comes in over cable TV coax (Spectrum home use which was Time Warner in the recent past now owned by Charter)

Thanks All - Mike

Stuff: 
ubuntu server 20.04 
on an old HP 8730w core2duo 
on a flash thumb-drive (Sandisk)
through an ON NETWORKS N300 router (using DMZ on server 192...IP)
to an old ancient Motorola Surfboard modem
to Spectrum via home cable tv coax (was Time Warner)
to ...the cloud

---

### Post by SeijiSensei on 2020-06-30
Since you can send to yahoo but not to twc means that your provider does allow outbound SMTP traffic. Most providers don't support SMTP from machines on consumer networks.

However your address is likely to always get black marks at places like Spamhaus because you're connecting from a residential address.  One good place to check is here:  [https://mxtoolbox.com/blacklists.aspx](https://mxtoolbox.com/blacklists.aspx).  Enter your external IP address and see what comes back.

---

### Post by mikecolley on 2020-07-03
Thank You SeijiSensei.

That was excellent information.  I tracked down the error message to the exact error about my IP being listed on PBL (Policy Block List) and the message includes a paragraph about removal procedure and it says:
Removal of IP addresses within this range from the PBL is not allowed by the netblock owner's policy.
The suggested URL they gave pointed at a general help info page at spectrum that didn't help.

Just an idea, I wonder if postfix could send email through an IMAP server at spectrum?

Found a couple $olutions at   [https://www.clearos.com/clearfoundation/social/community/using-an-external-smtp-provider](https://www.clearos.com/clearfoundation/social/community/using-an-external-smtp-provider)   and I have to read it a couple of more times to understand it.  Google search "postfix spectrum".[URL="https://www.clearos.com/clearfoundation/social/community/using-an-external-smtp-provider"]
[/URL]
I don't have it working yet but that link does give solutions so I am marking this "solved" even though I haven't implemented it yet.

Does anybody know how-to SMTP into Spectrum from postfix?  Maybe they won't change the From: email address?????

Thanks All - Mike

---

### Post by SeijiSensei on 2020-07-04
If you want to use a Spectrum host as a mail relay, you need to modify the relayhost parameter in Postfix.

[http://www.postfix.org/postconf.5.html#relayhost](http://www.postfix.org/postconf.5.html#relayhost)

That said, Spectrum would need to have set up a relay host. Have you asked them?

---

### Post by TheFu on 2020-07-05
Residential subnets will always be very difficult for directly sending email due to the spam problem. Really the only solutions are either to setup a VPS, _use the ISP outbound SMTP-proxy_ or by external service providers. Sending and receiving email from a subnet marked as residential will never work - I would expect all SMTP traffic that directly attempts to send email without going through the ISP's email gateway to be blocked. I'd be surprised if port 25 was allowed to connect externally at all.

Spam is a world-wide problem.  On my email servers, I block all DHCP and residential subnets.  If you want an email server, spend $5/month and use a VPS. A minimal VPS can easily handle proxying email in and out for most small businesses that don't spam customer lists.  The bad part of the VPS is that someone else acting as a spammer on the same subnet may get your IP automatically blocked on a RBL.  I tend to block huge subnets, not single IPs from those providers.

OR find a service provider that will proxy inbound and outbount emails, usually those are about $40/yr if the residential ISP doesn't do that.

Or get a commercial ISP connection in your home.  For just a few servers, this isn't cost effective because commercial connections at a home address are usually $120-$500/month with much less "best effort" bandwidth than the residential agreement.

My /28 got blocked by 1 regional ISP for about 5 yrs. I knew the email people at the ISP, but due to some policies, couldn't get my system off the block list for a few years. By that point, I'd given up.  The way my subnet was added was by resending a virus email sent by one of their customers to me back to him - yes it was actually sent by his computer.  A few years later, I had some free time and they had updated their methods for auto-removal from the black list for email. It worked and I've been able to send/receive emails from that ISP (over 40M customers) since.  Of course, that ISP has outsourced all their email to an external provider - I think they use yahoo now.  Perhaps Spectrum/TWC/Charter have done the same, so they allow the yahoo mail to work?

IMAP is for viewing email on a server, not sending or receiving it.  Only SMTP does that.

---

### Post by mikecolley on 2020-07-24
[Solution #2?]  Seems to work
[https://scottlinux.com/2016/02/14/how-to-relay-mail-from-twc-home-connections/](https://scottlinux.com/2016/02/14/how-to-relay-mail-from-twc-home-connections/) was easy to do and outgoing email seems to be working just fine now. - Mike

---

