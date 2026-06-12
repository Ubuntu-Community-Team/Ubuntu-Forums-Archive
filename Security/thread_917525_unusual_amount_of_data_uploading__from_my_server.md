---
title: "unusual amount of data uploading  from my server"
date: 2008-09-12
forum: Security
---

### Post by Hawkowl on 2008-09-12
I have an ubuntu server, which seems to be having a lot of data uploaded from it.
I mean over 1.4GB in a 2 week period.
This is from a mere handful of websites that i host.
Is this a normal amount or is there something else going on?
Is there a way that someone could have cracked into my server and is now using it to upload stuff or am i just being paranoid?
Any comments would be greatly appreciated, thanks.

---

### Post by cariboo on 2008-09-12
Check your log files, they are located in /var/log/apache2, Another option would be to install something like **webalizer**, this will give you a web based visual representation of your log files. Webalizer is available in the repositories.

Jim

---

### Post by cdenley on 2008-09-12
> **Hawkowl said:**
> I have an ubuntu server, which seems to be having a lot of data uploaded from it.
I mean over 1.4GB in a 2 week period.
This is from a mere handful of websites that i host.
Is this a normal amount or is there something else going on?
Is there a way that someone could have cracked into my server and is now using it to upload stuff or am i just being paranoid?
Any comments would be greatly appreciated, thanks.

I would just capture some traffic, and see what's going on.
```

sudo apt-get install tcpdump
sudo tcpdump -w traffic.pcap

```
You can open the file traffic.pcap with wireshark from a desktop computer.

---

### Post by Hawkowl on 2008-09-13
Thanks for the replys.
I checked the log files first and found tonnes of error logs.
They all basically referred to the same thing, this
"Sun Sep 07 12:19:04 2008] [error] an unknown filter was not added: DEFLATE"
This appeared a number of times whenever anybody accessed a website on my server.
What that means I have no idea...
It seems though as the data upload could well be legit, as a couple of websites that sell stuff online figure predominantly in the error messages.
If anyone here knows what the error message means and is able to help me resolve I would really appreciate it, thanks

---

### Post by cariboo on 2008-09-14
Have a look here:

[http://www.divideandconquer.se/2008/02/27/an-unknown-filter-was-not-added-deflate/](http://www.divideandconquer.se/2008/02/27/an-unknown-filter-was-not-added-deflate/)

This should help with your deflate not added problem.

Jim

---

### Post by pqrs541 on 2008-09-16
The Weather:[buy wow gold](http://www.mmoinn.com)  It's so dry, the trees are bribing the dogs. It's been hitter?s a goat's butt in a pepper patch.  Wintry roads are said to be "slicker than otter snot. [wow gold](http://wowus.mmoinn.com/index.do?PageModule=OrderForm_new)[wow gold](http://woweu.mmoinn.com/index.do?PageModule=OrderForm_new) [World of warcraft Gold](http://www.mmoinn.com)[wow gold](http://www.mmoinn.com)

---

