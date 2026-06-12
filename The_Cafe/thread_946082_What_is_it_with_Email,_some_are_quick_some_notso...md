---
title: "What is it with Email, some are quick some notso..?"
date: 2008-10-13
forum: The Cafe
---

### Post by Plumtreed on 2008-10-13
When I email, my message usually leaves my computer and most often, almost always, gets to it's destination. I don't know how fast it gets there but there are seldom indications that it takes a long time.

When i run a test email, as you do when you set up a new 'email client' the email test can be quick or very slow. On occasion, I have set about fixing things only to find that the email test has arrived.

I recently sent a long message to myself on another PC in order to get the file on to the other computer. It took ages to get through! ( I know there are other ways of transfering files but it seemed like a good idea at the time)

How long does it take for an email to get from point A to B ???

---

### Post by lisati on 2008-10-13
It's not just a simple case of "send out an email and it arrives the same instant at its destination"
An email doesn't necessarily go straight from A to B, it has to make its way past C, and possibly D and other places on its way. (edit) And any one of the computers involved in the journey could be busy.

EDIT: The next time you send yourself an email, you might want to look at all the message headers and other "behind the scenes" information that is recorded with your email but not normally displayed. How you do this depends on how you're viewing your mail - with Thunderbird (both Windows and Linux versions) you can select a message and then from the Thunderbird menu choose View->Message source. The thing to look for is the lines that begin "Received from", which represent one computer involved in the journey from source to destination. They are usually listed in reverse order, with the most recently involved computer first in the list.

---

### Post by cariboo on 2008-10-13
Email really depends on your network. It seems to take longer for email within my ISP's network then  it does to other networks. Several years ago myself and two cousins organized a family reunion. The guy that was doing most of the footwork worked in Amsterdam, myself and the other cousin live on the west coast of Canada. there were many emails sent back and forth in less than 5 minutes between myself here in Williams lake and my cousin in Amsterdam. It was almost faster than real time chat :)

Jim

---

### Post by shuttleworthwannabe on 2008-10-13
because of ISP (local ones) issues, I decided to 'trust' the big G (not God) but Google's email service; since then (2004 I think), i have not had issues with delays. people I communicate with (an companies I work with) are seriosuly thinking of moving to G. Downtimes are alomost unheard off and delays between g-to-g account not even a milli-second.

---

### Post by Plumtreed on 2008-10-13
It doesn't seem to add up. I feel that some emails just get 'held' until a quieter time by my provider.I have found that a 'test' email didn't show till the following morning.

To be honest I can't understand why they would do that or, in fact, if they would even be interested.

I better try GMail!

---

### Post by lisati on 2008-10-13
> **Plumtreed said:**
> It doesn't seem to add up. I feel that some emails just get 'held' until a quieter time by my provider.I have found that a 'test' email didn't show till the following morning.

To be honest I can't understand why they would do that or, in fact, if they would even be interested.

I better try GMail!

Mine sometimes seem to get held up too, and I'm not even using the same ISP. I recently had some show up from a mailing list that I'd submitted a couple of months ago.

---

### Post by ssam on 2008-10-13
[http://en.wikipedia.org/wiki/Greylisting](http://en.wikipedia.org/wiki/Greylisting) and other spam prevention techniques can slow down emails.

---

### Post by shuttleworthwannabe on 2008-10-13
my isp, batches emails and sends when the systems are quiter (traffic is not congested)...man what gives in this day and age!
try G and see what it can do for you,
S

---

### Post by beercz on 2008-10-13
It's all to do with [packet switching]("http://en.wikipedia.org/wiki/Packet_switching").

Emails (and all internet traffic) are broken down into small packets, and transmitted across the internet and the email is reassembled at the destination (in the correct order), once all the packets have reached their destination.

Packets can take several different routes to reach their destination, and if one (or more) get delayed or have to be re-routed then the entire email cannot be reassembled until all the packets have arrived.  Hence the delay.

---

### Post by Plumtreed on 2008-10-14
It seems to be a pretty clear pattern. My emails go well until about 8AM then they go into the 'do later' box. They seem to be 'delivered' after midnight.I can send and receive prior to this 8AM deadline.

I realised all this when I had an urgent item to deliver and I thought an email would get there the same day, at least! When it didn't arrive at the destination I sent it again.:confused:

Gmail is good but it becomes ineffective while my ISP is skimming Emails and holding things back.

From what I read here it seems to standard practise.

---

### Post by Dr Small on 2008-10-14
I run my own mailserver, and it is snappy.

---

### Post by Plumtreed on 2008-10-15
C'mon tell us a bit more! Is it practical and doable?

I make money writing and it is beneficial I can get my storey to it's destination on time!:KS

---

### Post by beercz on 2008-10-15
Does this help? 

[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

---

### Post by Plumtreed on 2008-10-15
Thanks everybody, I'll give that a try, it looks complex but, if I get it working, it will be worthwhile!

---

