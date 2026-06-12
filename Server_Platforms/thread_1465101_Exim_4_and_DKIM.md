---
title: "Exim 4 and DKIM"
date: 2010-04-29
forum: Server Platforms
---

### Post by rstackhouse on 2010-04-29
Hello,

I am trying to create an email application, but Gmail keeps kicking back my mails because they are not signed with DKIM.

I've been trying to get some help on the [exim-users list]("http://lists.exim.org/lurker/thread/20100428.135449.3a5e6036.en.html"), but no one has responded to my latest post

I've been reading the docs [here]("http://www.exim.org/exim-html-current/doc/html/spec_html/ch54.html#SECID513"), but I don't know which Exim configuration file to put the DKIM related options in or even what qualifies as "good" settings for these options.

Any help with this issue would be greatly appreciated.

Thanks,

Robert

---

### Post by rstackhouse on 2010-04-29
Just to show that I am not lazy and unworthy of assistance, I've been trying to track down a solution to this on my own.

Turns out I need version 4.70 of Exim for DKIM support and running ```
aptitude safe-upgrade
``` only gets me to version 4.69. Is there any other repository I could get this from? If that won't work, does any body have any advice on building Exim?

---

### Post by pdc124 on 2010-07-12
im just trying to upgrade Exim and sort out my LAN configuration.
I only use it on my LAN and relay to my ISP , but i cant send from my LAN clients to exim on my server because i haven't configured DKIM. 

Can i just disable DKIM (  as in an earlier version of Exim) ?

---

### Post by koenn on 2010-07-12
you probably have  a  /etc/exim.conf  ; if so, that should work. Alternatively, there may be a directory with a similar name, just create a file there (look at existing files for syntax, permissions, ownership, ...)

also, read this :  [http://newbiedoc.sourceforge.net/networking/exim.html](http://newbiedoc.sourceforge.net/networking/exim.html)

can't help you with DKIM, but afaik, there are no "defaults" for DKIM, you need to set up certs and keys so your MTA can be identified as the (legit) sender of the DKIM-tagged message

afaik you don't really need DKIM for gmail if you apply some other sender identification (fixed IP with reverse DNS, [SPF]("http://www.openspf.org/"), ...)

---

