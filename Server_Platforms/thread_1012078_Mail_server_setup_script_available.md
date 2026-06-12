---
title: "Mail server setup script available?"
date: 2008-12-15
forum: Server Platforms
---

### Post by papabach on 2008-12-15
Hi, I'm trying to set up a mail server with virtual mailboxes using postfix, postfixadmin and courier.  I've already had one go at it, but found that while there are lots of "how to" guides on the web (e.g. [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)), there's still an unbelievable amount of typing to be done in lots of disparate places.  :mad:

Having spent two days working on it, I managed to get POP3 email working for an account on my Ubuntu machine, so I know that my DNS MX records are OK. However, it all fell apart when I went to virtual mailboxes with MySQL.

I'm now going to start with a fresh 8.10 install.  My question is:  Is there a (trusted) install script that I'm missing in the repository that can set all this up without me altering a thousand things by hand?

Thanks in advance.

---

### Post by Titan8990 on 2008-12-15
> I'm now going to start with a fresh 8.10 install. My question is: Is there a (trusted) install script that I'm missing in the repository that can set all this up without me altering a thousand things by hand?


This would take away from the highly configurable environment that Linux provides. Things seem difficult to configure now, but with practice, you will find it easier, faster, and more powerful than any GUI could ever provide.

---

### Post by papabach on 2008-12-15
> **Titan8990 said:**
> This would take away from the highly configurable environment that Linux provides. Things seem difficult to configure now, but with practice, you will find it easier, faster, and more powerful than any GUI could ever provide.

Thanks Titan, however I'm hoping not to need to get too practised at this! ;)  It seems that the ideals of Ubuntu to reduce the complexity of Linux setup and management are really needed in this area...

I can see many common themes in the "how to" guides, but they all differ slightly. Just count the number of times the phrase "cut & paste" appears in the following guide: [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto]("https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto"). This is just crying out to be automated...

---

### Post by cdenley on 2008-12-15
If you want a simple drop-in mail server/collaboration suite, use zimbra.
[http://www.zimbra.com/community/](http://www.zimbra.com/community/)
It is not supported for 8.10, but you should be using 8.04 LTS for a server, anyway.

---

### Post by HermanAB on 2008-12-15
Here you go, the Easy Install script takes about 20 minutes:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

You can also get a pre-configured Citadel VMware image from the VMware appliance web site.

Cheers,

Herman

---

