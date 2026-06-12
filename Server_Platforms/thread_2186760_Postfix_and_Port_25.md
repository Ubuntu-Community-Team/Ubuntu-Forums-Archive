---
title: "Postfix and Port 25"
date: 2013-11-08
forum: Server Platforms
---

### Post by JKyleOKC on 2013-11-08
I've just changed my ISP from AT&T's DSL to AT&T Uverse, and found that port 25 is now irrevocably blocked for my new account; it had been grandfathered on the DSL account. As a result, my local mail server is no longer able to send traffic outside my LAN. While I don't need to do so often, since I keep an off-site non-ISP server for normal use and it allows alternate ports, I have a couple of programs that do need to send things, and I sometimes reply to messages that come into my local server.

[COLOR="#FF0000"]EDIT: Cut to the chase; solution is in message #10.[/COLOR]

The simplest solution to this problem would be to change settings of postfix to use port 587 instead of 25. However I've not been able to find anything in the documentation or the configuration files that gives me any hint of how to accomplish this change. None of the how-to pages I've read mention the subject, and a forum search turned up exactly one post that mentioned making such a change -- and it failed to say how or where it was done. Can someone please enlighten me?

If no such setting exists, is there a way to use iptables, specifically the OUTPUT chain of the nat table, to handle things?

Many thanks for all responses!

---

### Post by SeijiSensei on 2013-11-09
How about configuring the local Postfix to relay all mail through your off-site machine?  I run all my mail services at Linode, but also maintain a local mail server here in my office.  That server communicates with the remotes over an OpenVPN static-key tunnel.

---

### Post by JKyleOKC on 2013-11-10
> **SeijiSensei said:**
> How about configuring the local Postfix to relay all mail through your off-site machine?  I run all my mail services at Linode, but also maintain a local mail server here in my office.  That server communicates with the remotes over an OpenVPN static-key tunnel.That would be great, except for the fact that my off-site server's administrators reject non-SASL mail traffic from AT&T residential accounts entirely because they're on one of the many blacklists, and at the moment I'm having major difficulty getting postfix to AUTH using SASL, because I've installed dovecot as a pop3 provider locally. Seems to be a catch-22 situation, but I'm learning more than I ever wanted to know about debugging postfix servers...

Thanks for the reply; I would have been back sooner but have spent most of the day debugging with assistance from folk on the dslreports.com 'All Things Unix" forum...

---

### Post by SeijiSensei on 2013-11-10
> **JKyleOKC said:**
> That would be great, except for the fact that my off-site server's administrators reject non-SASL mail traffic from AT&T residential accounts entirely because they're on one of the many blacklists

I interpreted your earlier comment to mean you had control over the off-site machine.  Can you install software on it?  If so, I would install OpenVPN and set up a tunnel.  The remote machine would see all the traffic coming over the tunnel and not know anything about the fact that it is originating from an ATT account.

I find the $20/month I pay for a [Linode]("http://www.linode.com/") well worth the investment.  It gives me a public IP address, a machine I have total control over, big honking pipes out to the Internet, and the usual stuff like backup generators, air conditioning, and the like.  If Linode were a public company, I'd buy stock.  They are very well managed and growing world wide.

---

### Post by JKyleOKC on 2013-11-10
No, my off-site server is simply a godaddy email account that came along with my web page subscription, and I don't have any control at all over its traffic policies. It's been adequate, and at around $60/year for everything is easy to afford on retirement income. It's beginning to look as if the whole problem might be fixable by paying a one-time charge to AT&T to remove the block on my account and putting everything back to be RFC-compliant, which will probably be the easy way to fix things...

---

### Post by nebileix on 2013-11-12
To enable port 587 aka submission port, uncomment the following in /etc/postfix/master.cf
> submission inet n      -       n       -       -       smtpd

---

### Post by clearski on 2013-11-12
Hi.

To change the port from 25 to 400 (for example), edit /etc/postfix/master.cf

and change the line

```
smtpd inet n - - - - smtpd
```

to

```
400   inet   n    -     -     -     -    smtpd
```

It works just fine for me:

```
user@host:~$ sudo netstat -tanep | grep 400
tcp        0      0 127.0.0.1:400           0.0.0.0:*               LISTEN      0          13412       2826/master

```

Hope this helps.

---

### Post by JKyleOKC on 2013-11-12
That was the first thing I tried; it made EVERY attempt to send mail through the local server error out with a "points to myself" message. I undid this, and since have been attempting to use a gmail account as a relay host -- but gmail insists that authentication is required, despite my adding it in as copied from other peoples' main.cf files that work properly. I'm beginning to think there's no solution for it, in my specific configuration...

FWIW, the master.cf settings appear to deal with how postfix handles its input, not how it sends output upstream -- and it's the output problem that I'm trying to solve.

---

### Post by JKyleOKC on 2013-11-12
Thanks to all for the suggestions, but as I mentioned above the master.cf entries appear to set up what happens with incoming data, not what ports are used for output. The best solution appears to be to use a relay host, but then other problems arise.

---

### Post by JKyleOKC on 2013-11-12
Finally got it fixed; turned out to be a missing line in my main.cf file that was preventing proper authentication. While I did have a line "smtpd_sasl_auth_enable = yes" in place, it also needed "[COLOR="#FF0000"]smtp_[/COLOR]sasl_auth_enable = yes" which wasn't there. Adding it and reloading postfix did the trick. It's been an interesting week!

Thanks to TheFu, who on another thread about the same problem back in June posted a link to a thread in the Arch Linux forums that put me on the right trail. My initial search, for some reason, hadn't brought up the thread from June and thus I spent a few days trying all sorts of fixes that didn't help. However I learned much about iptables and postfix along the way so it wasn't wasted time.

Thanks again to all who replied. That's what is so great about these forums!

---

