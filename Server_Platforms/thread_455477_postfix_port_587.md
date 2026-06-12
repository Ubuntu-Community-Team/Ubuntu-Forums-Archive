---
title: "postfix port 587"
date: 2007-05-26
forum: Server Platforms
---

### Post by vimrss on 2007-05-26
I have postfix setup to use tls and port 587.  Testing with telnet on port 587 works.  An ehlo reveals that tls is working as well.  

Interstingly, when I try to send a message, with either thunderbird or mutt, I get an error about the message timing out on port 25.  I can't even telnet port 25, only 587.  

I know this is zero detail, but I thought it would be good to get a nudge before posting tons of data lines.

---

### Post by MJN on 2007-05-26
Presumably you modified /etc/postfix/master.cf to get Postfix to listen on port 587? If so, you need to add back the line that you changed i.e. **smtp      inet  n       -       -       -       -       smtpd**

Bear in mind that if you want to receive mail from the outside world you'll need to be listening on port 25 as 3rd parties won't be able to authenticate (on port 587 or any another).

Mathew

---

### Post by vimrss on 2007-05-26
Yes I did make that change to master.cf it brought the desired effect.  I may have been a little unclear, sorry about that, I do intend to use port 587 and tls on this box with postfix (not the isp relay).  I have everything working, certs authentication, et al.  It is when sending the message that it is then somehow timing out on port 25 (mail.log), which is odd since everything is setup, and seems to be working on port 587.

---

### Post by MJN on 2007-05-26
That's why you need an instance of Postfix listening on port 25 - at the moment you don't. Or do you mean you've added the line I suggested back in, but still no joy?

Mathew

---

### Post by vimrss on 2007-05-26
Ah, ok, I added back the line.  The file currently looks like this:  (Incidentally, for now outgoing is key, incoming mail isn't a big deal)

```
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       -       -       -       smtpd
587       inet  n       -       n       -       -       smtpd
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       n       300     1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp

relay     unix  -       -       -       -       -       smtp
        -o fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
```

---

### Post by MJN on 2007-05-26
Does it work?

---

### Post by vimrss on 2007-05-26
Unfortunately, not yet.  Here is what mail.log says when trying to send mail to a gmail user.
```

May 26 14:52:38 headless postfix/smtp[14008]: connect to alt1.gmail-smtp-in.l.google.com[64.233.183.114]: Connection timed out (port 25)
```

---

### Post by MJN on 2007-05-26
That timeout is with the gmail server - a problem either at their end, en route, or possibly your ISP blocking outgoing port 25.

Can you telnet to the gmail server on 25? (I can do so fine from here)

Mathew

---

### Post by vimrss on 2007-05-26
I was thinking using port 587 would get around the port 25 problems.  I suppose the thing that confuses me is if postfix is configured to use port 587 with tls, why would there then be a timeout error on port 25?  This is something that is happening at the receiving end?

---

### Post by MJN on 2007-05-26
When we're talking of ports and Postfix we're talking about what port Postfix runs on i.e. what port it *listens* on for *incoming *connections. Hence, your client is connecting to Postfix on port 587, it is accepting the message and then attempting to relay it on to the destination. It does this on port 25 - it has to given that is the port that other mail servers (including GMail's) is listening on.

I take it you can't telnet to the gmail server either? Do you know if your ISP blocks port 25? If they do then it's likely you'll have to relay outgoing mail via their server (using the relayhost directive).

Mathew

---

### Post by vimrss on 2007-05-26
Yep, they definitely block outgoing 25.  I was thinking I could get around my isp's block of 25 and run my own postfix relay off of 587.  What I think you are saying is that if my isp blocks outgoing 25 then I have no work-around option, and am forced to use the relayhost directive, and not my local box as the relay.  If this is so, then I guess there's nothing left to try.

I have tested the relayhost directive and it works fine but I was dead set on using this local box as the relay with tls.  Oh wells.  Thanks for the help though, big time!

---

### Post by MJN on 2007-05-26
Unfortunately no other workaround. Well, I say 'unfortunately' but if there was then the spammers would just do it!

Mathew

---

