---
title: "Postfix setup problem"
date: 2008-05-24
forum: Server Platforms
---

### Post by melat0nin on 2008-05-24
Hi all

I have a Hardy x86 server and I'm trying to install Postfix using the tutorial located here:

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p5](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p5)

Everything seems fine until the step where I input the command

```
telnet localhost 25
```

There is no error message, and the cursor just moves to the next line down and nothing else happens.  I can't Ctrl-C out or anything, and just have to end the SSH session by quitting the terminal.

Obviously without that step I can't be sure that I've done things correctly, so I don't want to continue until I know what the situation is.

ANy help would be much appreciated :)

---

### Post by nexxus07 on 2008-05-24
I followed the same tutorial a couple of days ago on a virtual machine and it worked fine for me. Are you sure that the smtp server is listening on port 25? Try a 

```
netstat -tap
```

and see whether it shows up.

---

### Post by HermanAB on 2008-05-24
Hmm, I used Postfix for many years, and Sendmail before that, but I believe it is now time to move on.  You may find that Citadel is better for your needs.  It is very easy to install and zero maintenance.  Postfix is really just a waste of time compared to Citadel.

See this [http://citadel.org](http://citadel.org) and run the Easy Install script.  About 20 minutes later, you'll have a full working system and you'll never look back.

Cheers,

Herman

---

### Post by melat0nin on 2008-05-24
> **HermanAB said:**
> Hmm, I used Postfix for many years, and Sendmail before that, but I believe it is now time to move on.  You may find that Citadel is better for your needs.  It is very easy to install and zero maintenance.  Postfix is really just a waste of time compared to Citadel.

See this [http://citadel.org](http://citadel.org) and run the Easy Install script.  About 20 minutes later, you'll have a full working system and you'll never look back.

Cheers,

Herman

Is it safe to install this on Hardy? I notice their repo doesn't yet have a hardy area.

---

### Post by dannyboy1121 on 2008-05-24
> **HermanAB said:**
> Hmm, I used Postfix for many years, and Sendmail before that, but I believe it is now time to move on.  

Why?

---

### Post by windependence on 2008-05-24
> **dannyboy1121 said:**
> Why?

Probably the same reason I switched to Zimbra. Because you can have a full mail server up an running in minutes instead of days or even weeks if you are a noob. Postfix is great, but you still have to build everything from scratch and add spamassassin, anti-virus and some other stuff which takes time and effort. With Zimbra, I just install and everything is there and running. I don't have time to hack around anymore.

-Tim

---

### Post by hyper_ch on 2008-05-25
if you follow the perfect howto from falko you ahve it up in minutes also.

---

### Post by windependence on 2008-05-25
> **hyper_ch said:**
> if you follow the perfect howto from falko you ahve it up in minutes also.

I have to confess hyper_ch, I haven't looked at that one. Maybe it's worth a retake. It's just that Zimbra has many features that I would have to add to the basic mail server install. I ran across it while servicing a client of mine and I was impressed.

-Tim

---

