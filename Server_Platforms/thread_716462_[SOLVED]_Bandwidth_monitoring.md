---
title: "[SOLVED] Bandwidth monitoring?"
date: 2008-03-05
forum: Server Platforms
---

### Post by girasquid on 2008-03-05
Hello, all.

I have recently built myself a Ubuntu server, and moved it into a co-location closet which my employer has offered to let me keep it in, provided I pay them back for each GB of bandwidth I use. I am hosting multiple virtualhosts off of my server.

Does anyone know of a tool I can set up to monitor the bandwidth of each individual virtualhost? I need to monitor both incoming and outgoing bandwidth for each virtualhost, so that I can generate a monthly report of each virtualhost's bandwidth usage.

Thanks,
Girasquid

---

### Post by Alekc on 2008-03-06
I suppose you mean apache virtual hosts. In that casse you can use awstats, with that you can see bandwidth used by each virtual host by daiily/monthly/yearly basics

---

### Post by girasquid on 2008-03-06
> **Alekc said:**
> I suppose you mean apache virtual hosts. In that casse you can use awstats, with that you can see bandwidth used by each virtual host by daiily/monthly/yearly basics

Sorry, I must have forgotten to specify that these are Apache virtualhosts.

Does awstats also display the bandwidth used by things like FTP, ssh, etc.? I know that it displays the HTTP bandwidth, but I also need things like the bandwidth used by FTP - which I don't think awstats provides, due to the fact that it reads Apache access logs. If you know more, or how to setup awstats to also display all bandwidth used, I'd love to learn how.

---

### Post by Alekc on 2008-03-06
Actualy it can.
> It can analyze log files from all major server tools like Apache log files (NCSA combined/XLF/ELF log format or common/CLF log format), WebStar, IIS (W3C log format) and a lot of other web, proxy, wap, streaming servers, mail servers and some ftp servers.

Demo: [http://awstats.sourceforge.net/awstats.ftp.html](http://awstats.sourceforge.net/awstats.ftp.html)

Docs:[http://awstats.sourceforge.net/docs/awstats_faq.html#FTP](http://awstats.sourceforge.net/docs/awstats_faq.html#FTP)

---

### Post by girasquid on 2008-03-06
Yeah, that's very cool - I just happened accross that.

Is there a way to have it monitor both the FTP and the HTTP logs for a single virtualhost at a time, within a single awstats page? I'd like to visit one page and be able to see the FTP bandwidth and HTTP bandwidth for any particular virtualhost.

---

### Post by Alekc on 2008-03-06
Hmm i suppose not, since http and ftp monitoring are 2 different config files :/

You'll need to use calculator for sum i suppose :(

---

### Post by girasquid on 2008-03-06
Oh well, at least I'll have both available to sum up with.

Thanks for all the help.

---

