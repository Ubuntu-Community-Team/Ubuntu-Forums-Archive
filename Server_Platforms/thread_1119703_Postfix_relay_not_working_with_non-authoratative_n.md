---
title: "Postfix relay not working with non-authoratative name server?"
date: 2009-04-08
forum: Server Platforms
---

### Post by wkulecz on 2009-04-08
Some time Friday afternoon my postfix gmail relay stopped working with mail accumulating in the queue with an error message saying host not found, non-authoritative DNS.  This is a low Email volume setup, I'm talking 7 messages queued with three or them being test messages when I noticed something was wrong.

I commented out the main.cf line:
(you can see my main.cf in this thread: [http://ubuntuforums.org/showthread.php?t=1097249](http://ubuntuforums.org/showthread.php?t=1097249))
delay_warning_time = 4h

and the queue seemed to empty eventually and a test message immediately worked this morning while the DNS was still giving non-authoritative answers with nslookup.

Did I stumble upon a fix or is this an external DNS issue beyond my control?  My ISP is the old swbell.net which took over AT&T and switched back to the old Ma Bell name  -- a mistake IMHO because of all the ill will that remains from the Ma Bell days.

After the breakup when AT&T first went consumer, I though things summed up well when some pundit said:  "AT&T, great technology saddled by a marketing department that couldn't sell eternal life".

Google searching found some forum answers about postfix MX errors saying some ISPs disable MX lookups in a mis-guided attempt to block spam from infected machines on their networks.
I guess its possible AT&T rolled this out on my subnet Friday afternoon, but my error messages reference the A records, not the MX records

--wally.

---

### Post by HermanAB on 2009-04-08
Are you sure it worked, since you only stopped the warning.

---

### Post by wkulecz on 2009-04-08
> **HermanAB said:**
> Are you sure it worked, since you only stopped the warning.

Yes I'm sure it worked this morning as my test mail arrived and the queue was empty by the time I checked it after sending the test message.

I never did get any warnings.

--wally.

---

### Post by wkulecz on 2009-04-10
Either it was a temporary network issue beyond my control that co-incidentally resolved about the time I made the change, or disabling the warnings causes the smtpd to just send them anyways despite the non-authorative DNS results.

I was getting the warnings to my gmail account, I just didn't notice them initially because of the gmail threading, and the from feild showed "me" which  made me think they were just spam that snuck by. I get 100s of gmail spams per day.

--wally.

---

