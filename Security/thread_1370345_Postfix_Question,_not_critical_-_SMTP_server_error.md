---
title: "Postfix Question, not critical - SMTP server: errors from unknown[ip address]"
date: 2010-01-02
forum: Security
---

### Post by sepius on 2010-01-02
This is a transcript I get emailed at least once every day, usually about 3 to 10 a day recently.

[FONT="Courier New"]Transcript of session follows.
SMTP server: errors from unknown[*ip address*]
*<boring stuff snipped>*
In:  RCPT TO: <server@*my domain*>
Out: 550 5.1.1 <server@*my domain*>: Recipient address rejected: User unknown
     in local recipient table

Session aborted, reason: lost connection[/FONT]

Now I cannot seem to find anything via Google, as when I put "server@" anywhere in the string, I just get web hosting or other kroomst.

The emails usually come from legit places, usually hotels.  Does this mean they are sending bad emails, i.e. they have a Trojan/worm, or is this a live hack attempt?.  I believe the later, as I might get upto 3 domains from the one ip address, which is always, NOT associated with the listed domain.

Not causing me any issues, except I have been getting a lot recently.  Any one familiar with this? Should I contact the domain owners to let them know about this?

Thanks.

---

### Post by noway2 on 2010-01-03
It looks like an attempt to use your server as a relay.  Apparently, you (correctly) have the restrictions in place to require authenticated users and your server sends back a 500 level error (meaning fatal-stop trying).

---

### Post by sepius on 2010-01-04
I never thought it might be a relay attempt.  Thanks for that, I am going to do some searches on that and see what comes up.

Could this be a Windows exploit? Does any one else have this in there Postfix logs?

---

### Post by noway2 on 2010-01-04
I don't think it is a "Windows" exploit, but more likely an attempt to try and find a server that can be hijacked into being a spam engine.

The log information you posted looks like a transcript from an SMTP transaction.  If your system is properly setup, your SMTP server should accept authenticated users (hopefully via SSL or TLS) and reject others.

---

### Post by sepius on 2010-01-05
yeah, sounds like it .... but who has a email address called server?  The number of attempts I get makes me feel it must be very common.

Yeah, I have SSL enabled and it secures well, I am just curious about the address (its only server@) and why I cannot find any documentation on it as an exploit/relay/hack attempt, virus transport or what ever, that is the weirdest bit about this.  I found some others with malicious botnets, but the email addresses are many, not one specific one.

---

