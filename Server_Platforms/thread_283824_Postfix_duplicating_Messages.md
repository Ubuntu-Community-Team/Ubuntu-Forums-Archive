---
title: "Postfix duplicating Messages"
date: 2006-10-24
forum: Server Platforms
---

### Post by sclough on 2006-10-24
I have had a problem that just started with getting duplicate messages.  At first I thought DSPAM may be at fault, but now I'm suspecting Postfix since this message appears in the log:

```
relay=none, delay=4, status=deferred (delivery temporarily suspended: conversation with 127.0.0.1[127.0.0.1] timed out while sending end of data -- message may be sent more than once)
```

I'm using a DSPAM setup where postfix gets the mail and then uses LMTP to pass the mail over a socket to DSPAM which will re-inject the mail into Postfix if it's to be delivered.  I'm assuming these messages are coming from DSPAM re-injecting the message since the conversation is all localhost?

Any clue what the problem could be here?  I do have iptables running and it blocks ICMP packets (yes I was being paranoid) although I didn't think they'd be blocked on the loopback interface, but I disabled iptables temporarily but I'm not sure that has solved the problem.  It's difficult to explain to users why they are getting duplicate emails all of a sudden.  The message id's in the messages are the same which lead me to believe that postfix is handing the message off once to dspam and it's somehow injecting it twice.  Perhaps the hand off is timing out here and that's why it's injecting it twice?  Any ideas?

---

