---
title: "Email server (Zimbra) is reporting a massive increase in amount of emails treated"
date: 2015-04-23
forum: Security
---

### Post by bmunger on 2015-04-23
I have a server that is essentially used for email purposes, a little for other stuff, but 90% of the activity is email for my small community.

I have seen, recently, a very lage increase in number of message in the stats of ths server and I have difficulty identifying the nature of the messages and the source.

In the past two month, the increase is exponential.


The server has been running for years without any glitch.

the server is not listed in the blacklists ( I checked with mxtoolbox), but I cannot identify the nature of the emails nor the source, I need help.

Ideally, if a Ubuntu guru that knows Zimbra would like to step in and offer his services, I'd be willing to pay for the help... but how tio identify who's an expert and who's pretending?

Any known experts in the crowd that everybody agrees to call an expert?

Thanks!
Bernard

---

### Post by HermanAB on 2015-04-24
Hmm, it sounds like you are running an open relay and is now wondering why it is getting abused?

---

### Post by Habitual on 2015-04-24
Zimbra *version*?

---

### Post by SeijiSensei on 2015-04-24
> **HermanAB said:**
> Hmm, it sounds like you are running an open relay and is now wondering why it is getting abused?
I had the same thought as Herman.  Did you run the test for an open relay at mxtoolbox.com, bmunger?  If not, you should do that right away.

What do you see in /var/log/mail.log?  Senders?  Recipients?  Mail only for your legitimate domains or others?  If all the recipients are legitimate, then what percentage of the messages are marked as spam? 

If Zimbra is using Postfix, what do you have in the "mydestination" field in /etc/postfix/main.cf?

Read this document carefully: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

---

### Post by Habitual on 2015-04-24
and examine /var/tmp closely.
I found 'rogue' zimlets on my zimbra server that were being used against us, and they 'called' files from remote hosts and stuck them in /var/tmp

---

### Post by bmunger on 2015-04-25
Hello,

Thanks for all the replies. I'm not sure what to do next, how to analyze and identify the source of the increase.

I have Zimbra 8.5 on Ubuntu, uname -a reports:
Linux zimbra 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
I have upgraded all the packages I could on it.

Here is an image of the version of zimbra:
[ATTACH=CONFIG]261524[/ATTACH]

Here is what worries me

[ATTACH=CONFIG]261525[/ATTACH]
[ATTACH=CONFIG]261526[/ATTACH]

The increase is not really easy to explain, other than someone is using my email, or able to send emails using one of the accounts (there are not that many, me and my extended family...). I have attached a picture of the mxtoolbox SMTP test, I'm not an open relay.

I'm not extremely familiar with the stats I can get out of my server, I guess that would be a great start. How can I pin point what is going through, with which account(s) and what is the general content being sent.

Can you help start me off?

If one of you is willing to login and check, contact me at bmunger at ingenieur.org

Thanks!
Bernard

---

### Post by bmunger on 2015-04-25
I forgot, the antivirus / Antispam is running also on increased volume. But that might simply by a collateral damage...

[ATTACH=CONFIG]261529[/ATTACH]

---

### Post by bashiergui on 2015-04-25
> **SeijiSensei said:**
> I had the same thought as Herman.  Did you run the test for an open relay at mxtoolbox.com, bmunger?  If not, you should do that right away.

What do you see in /var/log/mail.log?  Senders?  Recipients?  Mail only for your legitimate domains or others?  If all the recipients are legitimate, then what percentage of the messages are marked as spam? 

If Zimbra is using Postfix, what do you have in the "mydestination" field in /etc/postfix/main.cf?

Read this document carefully: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)
Did you do everything seijisensei suggested? **Please** do that before you allow random strangers from the internet to log in.

---

### Post by bmunger on 2015-04-26
Hello,

I have maybe identified a reason: I get thousands of messages from the same domain: 

> Apr 26 06:43:39 zimbra postfix/smtpd[31272]: NOQUEUE: filter: RCPT from unknown[115.159.87.233]: <Janna@1g77.com>: Sender address triggers FILTER smtp-amavis:[127.0.0.1]:10024; from=<Janna@1g77.com> to=<**removed**> proto=ESMTP helo=<Janna.1g77.com>

I guess it's an email attack....

Anyone can suggest how block a domain? I forget how to blacklist with postfix..

Thanks!

---

### Post by SeijiSensei on 2015-04-27
Are all the recipients the same?  Are the recipients valid addressees in your domain? 

I usually block spammers at the IP level with iptables.  Add this line to /etc/rc.local and reboot:
```
/sbin/iptables -I INPUT -s 115.159.87.233 -j REJECT
```
That way your Postfix server never has to deal with the traffic.

---

### Post by bmunger on 2015-04-28
Hello,

Thanks for the replies, I'm moving forward.

I *finally* got a stats package to work on my system... Ah man, it's been a long time since I've linuxed (yes, it's a new verb, I know).

Here is what I could find. I've got a lot of rejected messages:
[INDENT][INDENT]Grand Totals
------------
messages

     93   received
    190   delivered
      0   forwarded
      0   deferred
      8   bounced
   3744   rejected (95%)
      0   reject warnings
      0   held
      0   discarded (0%)[/INDENT][/INDENT]

And I've look at the reasons:

[INDENT][INDENT]message reject detail
---------------------
  RCPT
    **blocked using b.barracudacentral.org (total: 29)**
           8   verizon.net
           6   dyndsl-178-142-096-179.ewe-ip-backbone.de
           3   charter.com
           2   rr.com
           1   smtp8.ltzxyahoo.cc
           1   kumssg.com
           1   ono.com
           1   dynamic.qsc.de
           1   alkar.net
           1   sbcglobal.net
           1   vtr.net
           1   windstream.net
           1   85-192-188-210.dsl.esoo.ru
           1   82-208-83-188.dynamic.mts-nn.ru
   ** blocked using zen.spamhaus.org (total: 7)**
           3   hinet.net
           3   bl22-217-159.dsl.telepac.pt
           1   mta18.pvmg74vs.eu
    **cannot find your hostname (total: 3691)**
        2194   115.159.87.233
         769   115.159.82.46
         367   115.159.40.125
          21   103.40.8.18
[/INDENT][/INDENT]



So the majority of the rejected email com from the reason **cannot find your hostname (total: 3691)**



And I've done a summary of the top 5 for the past weeks :


[INDENT][INDENT]Summary of rejected emails with reason "cannot find your hostname"
**This week**
** * *2194   115.159.87.233
** * * 769   115.159.82.46
** * * 367   115.159.40.125
** * * *21   103.40.8.18
** * * *18   5.133.176.82


**Last week:**
** * * *1202 * 115.159.87.233
** * * * 534 * 115.159.40.125
** * * * 450 * 115.159.82.46
** * * * 404 * 96.31.174.169
** * * * 100 * 203.195.194.160


**3 weeks ago:**
** * * *1742 * 115.159.5.165
** * * * 394 * 115.159.22.72
** * * * 346 * 115.159.82.214
** * * * 174 * 96.31.174.169
** * * * *67 * 5.133.176.85

**4 weeks ago:**
** * * * 681 * 96.31.174.169
** * * * 142 * 70.32.114.178
** * * * 121 * 72.55.171.213
** * * * *84 * 115.159.22.72
** * * * *77 * 103.40.8.18

**5 weeks ago:**
** * * * 469 * 96.31.174.169
** * * * 243 * 115.159.107.185
** * * * 134 * 74.120.222.246
** * * * *97 * 72.55.171.213
** * * * *72 * 70.32.114.178
[/INDENT][/INDENT]


And now I'm wondering if this is a targeted attack on my mail server.

What do you think?


Anyone can help figure this out and avoid further problems?

The idea of blocking with an IP table is appealing, since it could be done for the most common IP addresses with a mask...  But will I have to do that every week?

I'm not doing it for now, my system responds fin for now, the amount of processed data is still acceptable.

But I need to do something about it. I know this is not usual but I can't figure out why someone would be interested in crashing my email system...

Thanks for the help!

---

### Post by SeijiSensei on 2015-04-28
Unless you have a burning desire to receive random spams from machines in China, I'd use iptables to block 115.159.0.0/16.  They are cloud servers in the Tencent network:
```

$ whois 115.159.0.0@whois.apnic.net
[Querying whois.apnic.net]
[whois.apnic.net]
% [whois.apnic.net]
% Whois data copyright terms    http://www.apnic.net/db/dbcopyright.html

% Information related to '115.159.0.0 - 115.159.255.255'

inetnum:        115.159.0.0 - 115.159.255.255
netname:        TencentCloud
descr:          Tencent cloud computing (Beijing) Co., Ltd.
descr:          Floor 6, Yinke Building,38 Haidian St,
descr:          Haidian District Beijing
country:        CN

```

If you want to be precise you can block connections just to port 25:
```
/sbin/iptables -A INPUT -p tcp -s 115.159.0.0/16 --dport 25 -j REJECT
```

All this mail looks like spam to me.  You still haven't told us about recipients.  Find a message in /var/log/mail.log from one of those Chinese servers. To whom is it sent?  Seems likely someone in your domain(s) got added to a spamming list.  Did you advertise any email addresses on web sites in the past few months?

---

### Post by bmunger on 2015-04-28
Thanks for the quick response, Sensei.

I do not have stats about whom the message are to, but it seems all the two same recipients, from a quick look visually. My wife and I...

I'll add the iptable rules, thanks for the specification on port, but I think I want to reject all traffic.

I guess I'll have to monitor this on a frequent basis, now, and put the mail statistics into my to-read list for each week...



I'll let you know by posting here how things evolve...

Thanks!

---

### Post by bmunger on 2015-04-28
5 minutes on the job, and the rules are already working:

> root@zimbra:/var/log# iptables -v -L
Chain INPUT (policy ACCEPT 4929 packets, 2522K bytes)
 pkts bytes target     prot opt in     out     source               destination
    8   480 REJECT     tcp  --  any    any     115.159.0.0/16       anywhere             reject-with icmp-port-unreachable
    0     0 REJECT     tcp  --  any    any     0.0.31.96.unassigned.premieronline.net/16  anywhere             reject-with icmp-port-unreachable
    0     0 REJECT     tcp  --  any    any     70.32.64.0/18        anywhere             reject-with icmp-port-unreachable

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 3729 packets, 2116K bytes)
 pkts bytes target     prot opt in     out     source               destination




Thanks for the help, it's greatly appreciated.


):P

Bernard

---

### Post by SeijiSensei on 2015-04-28
If you and your wife have the only valid accounts in the domain, one or both of them got added to a spamming list recently.  Over time the volume will grow. 

As you say, managing spammers via iptables requires a lot of attention.  If it starts to get out of hand, you could install [SpamAssassin]("https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-spamassassin-on-ubuntu-12-04") on the server.

You can also make a change to your Postfix configuration that helps cut down on really stupid spamming machines.  Look in /etc/postfix/main.cf and find the "smtpd_client_restrictions" entry.  It's probably set to "reject_unknown_client_hostname" since the statistics you reported indicated that was the most common issue.  Add this to the entry:
```

smtpd_client_restrictions = reject_unknown_client_hostname, sleep 3, reject_unauth_pipelining

```
The "sleep 3" entry tells Postfix to wait three seconds after the connection is made before sending its "banner" to the client.  A lot of spamming software doesn't wait for the banner but starts spewing as soon as the connection is made.  The "reject_unauth_pipelining" entry tells Postfix to disconnect from any sender that doesn't wait.

---

### Post by bmunger on 2015-04-28
Thanks for the info, I'll check that out.

I also realized that those ip filtering rules must be in my rc.local script to be reactivated at each reboot.

The sleep 3 is really interesting, I hope I had known this before.

Thanks again, great help.

---

### Post by HermanAB on 2015-04-29
Ayup.  The problem with a mail server is that the faster the server, the more spam you receive.  Long ago, when I ran a mail server for a bunch of small businesses, the machine received millions of spams a day.  Slowing the server down with a sleep command (in those days I had to modify the code and recompile Postfix), dropped the spam load to tens of thousands per day, which was then processed by Spam Assassin with relative ease.  

Spammers don't like it when you waste their time. They want to waste yours and turning the table on them is good retribution, but you then have to increase the number of Postfix threads, to ensure that legit mail can get through, when several threads are blocked on spammers.

---

