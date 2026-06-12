---
title: "DNS issues"
date: 2008-06-13
forum: Server Platforms
---

### Post by Frobe82 on 2008-06-13
I cant receive or send mail.

I bought a domain with admintools for DNS.
I pointed the DNS A records to my router at home.
I set up the router to forward all needed ports to the servers IP.

I cant send emails because my ISP does not allow outgoing traffic on port 25, fine Ill solve that later, but I should receive mail.

I think Ive done wrong when setting up the DNS A or MX records.
Internal Emails work without problems. The webbserver, ftp server, vmware server, ssh and so on works from the outside using the domain name.

I beg of you to help me, Ive been going over this for weeks and im so tired. (6-weeks old son could explain me missing a few steps here or there.)

Im using ISPConfig, and installed the server following this tutorial:
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)


Kind Regards
Fredrik

---

### Post by MJN on 2008-06-13
> **Frobe82 said:**
> I think Ive done wrong when setting up the DNS A or MX records.
 
You need to tell us the domain name if we are to be able to go anywhere from this.
 
Mathew

---

### Post by Frobe82 on 2008-06-13
sn50.com

Just ask for anything and I will deliever.

---

### Post by MJN on 2008-06-13
The DNS is fine (assuming you are server1.sn50.com) however it looks like either incoming port 25 is being blocked or your port forwarding is incorrect.
 
Whilst not a long-term solution you could work out which problem you've got by moving your mail server to another port, updating the port forwarding, and attempting to connect from the outside (using telnet) to that port.
 
Mathew

---

### Post by Frobe82 on 2008-06-13
Yes that is my server, does all the dns settings look correct?

If I telnet port 25 I get no response. If I change the public port on the router to 2525 but keep the "private" port and also the smtp server settings on port 25. I have no problems 
connecting.

How can I change the smtp port on my server?
I tried this before running CentOS. But it did not work.


Thankyou for helping.

---

### Post by hyper_ch on 2008-06-13
you did setup ispconfig on there, right? When I access sn50.com by a browser I get the default ispconfig page.

You're using Postfix as server (if you setup according to the perfect howto). If so, edit /etc/postfix/master.cf

You see service "smtp" on port 25. Copy that and rename it to smtp2 and save it.

Then edit /etc/services and copy the smtp server to smtp2 and change the port accordingly.

Then restart postfix (or whole machine)

---

### Post by Frobe82 on 2008-06-13
[B]This is my master.cf
I cant find any relations between smtp and port 25 here, no port given at all for smtp.[/B]


root@server1:/home/administrator# vi /etc/postfix/master.cf
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


But how would changing the incoming port solve anything, wont the external mailservers still try to contact me on port 25 and get denied because of my ISP?

---

### Post by MJN on 2008-06-13
> **Frobe82 said:**
> Yes that is my server, does all the dns settings look correct?
 
If I telnet port 25 I get no response. If I change the public port on the router to 2525 but keep the "private" port and also the smtp server settings on port 25. I have no problems 
connecting.
 
How can I change the smtp port on my server?
I tried this before running CentOS. But it did not work.
 
 
Thankyou for helping.
 
You've done enough - proven that your ISP is blocking incoming port 25.
 
I'm afraid that's it as all other mail servers will only connect to you on that port and so unless you get a 3rd party to relay your incoming mail to you then there's no other solution.
 
Mathew

---

