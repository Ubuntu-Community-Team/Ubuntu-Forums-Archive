---
title: "How To trace an Email"
date: 2008-11-06
forum: Security
---

### Post by Hoonakwa on 2008-11-06
Hello everyone,
 My niece is receiving unwanted email from a cyber stalker. I have tried to get the headers but the header field is blank. She forwarded the email to me. It came from anonymous.com. I tried going to the website but is was no help. Any advise would be appreciated.

---

### Post by amac777 on 2008-11-06
Are you sure she forwarded the whole email including the headers? She probably needs to "forward as an attachement", or something like that to make sure you also get a copy of the headers. I am not an expert, but if the email came accross the internet, there should be some headers attached to it along the way. (at least when it arrives at whatever account provides her mail service such as yahoo or gmail.)

---

### Post by damis648 on 2008-11-06
I know for a fact that it is possible to send an email without headers, I have done so. What should happen, though, is that the server he is using should attach his ip address, so like said above, see if it can be forwarded as an attachment, or see if she can look at the email's herself and copy-paste them into an email to you.

---

### Post by todb on 2008-11-06
> **damis648 said:**
> I know for a fact that it is possible to send an email without headers, I have done so.

The above is patently false, assuming one is using a network to send e-mail and not doing something complicated like writing directly to the local spool.

I agree with the prior sentiment that your daughter is failing to forward the headers. The procedure for collecting e-mail header information is different for different mail clients. Googling for procedures turns up a list of for desktop clients [here]("http://128.175.24.251/headers.htm"), and for web clients, [here]("http://www.johnru.com/active-whois/headers-yahoo-gmail-hotmail-aol.html").

Your stalker is likely using a throwaway web mail account, so the best bet is to either ignore or filter out the messages. If she's getting death threats, you can tell the local police, (who will almost certainly do nothing, but will take a report), or if you're in the U.S. and the stalker is out of state, you can tell your local FBI field office (who will also do nothing, and may or may not take a report). If it's *not* a throwaway account, a simple mail filter on the From: field should suffice to stop getting the messages, though if something physical comes of it all, the prosecutor would appreciate it if you hung on to the incriminating messages.

Finally, if your daughter is 13 or under, lives in the U.S., and the threat is credible, you have a slightly better chance of law enforcement paying attention, thanks to the [Children's Online Privacy Protection Act]("http://www.ftc.gov/ogc/coppa1.htm").

Sorry for the bleak advice. With casual internet annoyances, it's almost always best to just ignore it.

---

### Post by persistentstubborn on 2008-11-06
> **todb said:**
> [QUOTE=damis648;6116918]I know for a fact that it is possible to send an email without headers, I have done so. 

The above is patently false, assuming one is using a network to send e-mail and not doing something complicated like writing directly to the local spool.[/QUOTE]

The above is patently true, but those wanting not to believe it are entitled to it.

> **todb said:**
> ...like writing directly to the local spool.

Or like doing another "complicated" stuff, like telneting to the recipient box, eh?

@OP

The way to examine what's happening is:

a) check the logs of your niece's box, try to see what was happening

b) examine the mail server from whom you determined she received the message from (probably her ISP); comcast would be able to trace it, that's sure; in case of public mailboxes (gmail, yahoo, hotmail) they would be able to trace further too.

The questions in case of b) are:

b1) Would they be willing to do so without a legal action your niece/her parents would be required to take.

b2) The trace could face an anonymized IP address as sender, so there is no guarantee it would be successful.

Cheers.

---

### Post by Nepherte on 2008-11-06
> **damis648 said:**
> I know for a fact that it is possible to send an email without headers.
If you send your mail with smtp, you always need a header no?

---

### Post by todb on 2008-11-06
> **Nepherte said:**
> If you send your mail with smtp, you always need a header no?

If you expect anyone to get it, you absolutely need a header. 

Argument by [RFC]("http://rfc.dotsrc.org/rfc/rfc2822.html"):

> Section 3.5: "A message consists of header fields, optionally followed by a message body."

Section 3.6: "The only required header fields are the origination date field and the originator address field(s)."

At any rate, re-reading the original response:

> I know for a fact that it is possible to send an email without headers.

..I will retract my "patently false" comment. It is possible to send an email without headers. However, given the state of modern SMTP, it is impossible to receive an email without at least a (possibly incorrect) date and originator address field in the header.

nit: picked.

---

### Post by randy78 on 2008-11-07
Offer to Paypal him $100 to leave you alone ("will you leave me alone if I give you $100? I can paypal it to you tomorrow when I get paid".)

DON'T SEND ANY MONEY!

He'll have to give you a valid email address for the transaction to take place ;)


:lolflag:

---

### Post by persistentstubborn on 2008-11-07
> **todb said:**
> ..I will retract my "patently false" comment. It is possible to send an email without headers. However, given the state of modern SMTP, it is impossible to receive an email without at least a (possibly incorrect) date and originator address field in the header.

nit: picked.

This is, IMHO, a completely accurate statement. It doesn't imply that the stalker actually used SMTP and doesn't exclude the possibility of IP spoofing, IP anonymizing, or the use of open relays.

My post above was aimed at pointing to what it seemed to me as a wrong assumption. I wasn't completely wrong, but by doing it I also take a wrong assumption. :D

Cheers to all.

---

### Post by Nepherte on 2008-11-07
> **todb said:**
> 
..I will retract my "patently false" comment. It is possible to send an email without headers. However, given the state of modern SMTP, it is impossible to receive an email without at least a (possibly incorrect) date and originator address field in the header.
That's exactly what I was thinking. If you're using smtp, you shouldn't be able to send a mail without a header because the header kinda makes the protocol. Though damis648 never implied smtp.

---

### Post by daleus on 2008-11-07
chances are if its @anonymous.com it's been sent using a mail spoofer through a mail host who hasn't configured their services correctly.

5 years ago we used to get funny emails from friends posing as "billgates@microsoft.com"

So chances are they just did @anonymous.com to highlight the fact that they are infact, anonymous.

well, until you extract the headers.

---

### Post by Hoonakwa on 2008-11-09
Thanks for the advice guys. I will see her this month and set her email to block this nut. While he hasn't made any threats he does seem to know a lot about her. He got into her photo bucket account and changed the password. I would love to be able to find this guy and get even with him.

---

### Post by persistentstubborn on 2008-11-09
> **Hoonakwa said:**
> Thanks for the advice guys. I will see her this month and set her email to block this nut. While he hasn't made any threats he does seem to know a lot about her. He got into her photo bucket account and changed the password. I would love to be able to find this guy and get even with him.

There is the nearby thread [http://ubuntuforums.org/showthread.php?p=6136257](http://ubuntuforums.org/showthread.php?p=6136257) that actually might apply to your question here, featuring an example how an e-mail could be received, thought the stalker has not sent it by smtp, imap, or any other mail protocol.

---

