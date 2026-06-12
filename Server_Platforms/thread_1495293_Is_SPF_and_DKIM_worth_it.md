---
title: "Is SPF and DKIM worth it?"
date: 2010-05-27
forum: Server Platforms
---

### Post by MechaMechanism on 2010-05-27
I'm thinking about setting up an SPF record at the Godaddy DNS for my domain.  I use Exim4 and might try DKIM.  What do you all think?  How is your experience?

---

### Post by windependence on 2010-05-28
If you're gonna run a REAL mail server you should have an SPF record set up as well as full reverse DNS for your mail IP. Otherwise, some servers won't talk to you at all.

-Tim

---

### Post by Vishal Agarwal on 2010-05-28
what "windependence" is saying is absolutely true. the reverse DNS is very important for a mail server to get a proper hand shake with other servers.

---

### Post by MechaMechanism on 2010-05-28
I have setup SPF for my domain.  My DNS has full reverse lookup enabled.  Been testing SPF a lot since last night, I like it, so I'm gonna stick with SPF now.  I'm gonna put DKIM on hold for now.  Thanks for the replies.

---

### Post by paulisdead on 2010-05-28
DKIM only seemed to help me on days when I had to send several thousands of messages to yahoo in a fairly short amount of time.

RDNS and SPF are the most important.

---

