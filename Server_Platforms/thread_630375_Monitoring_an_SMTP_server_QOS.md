---
title: "Monitoring an SMTP server QOS ?"
date: 2007-12-03
forum: Server Platforms
---

### Post by jethro10 on 2007-12-03
Hi,
I'm after a way to monitor an external SMTP server's Quality of service.

It need not be too exotic as I want to run on a very low powered underclocked very old fanless server.

Something along the lines of me manually telnetting in, getting a reply to "Hello" and writing it to a log file every hour would do.

Of course I've never got too involved in mail server and I have no idea, so what i've asked may be total rubbish.

Any ideas?

Jeff

---

### Post by mellowd on 2007-12-03
You can try cacti. 

I've never actually measured QOS though. I suppose you could use wireshark to check which protocols are getting through quicker, but it wouldn't show the priority given to them. You could do a test with a voice call for example and see if that goes through while your other data stalls. I'm not really sure.

---

