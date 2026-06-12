---
title: "WebDAV server for Ubuntu 10.04"
date: 2011-03-13
forum: Server Platforms
---

### Post by zander x on 2011-03-13
I am looking for a software package(s) that will allow me to setup a WebDAV server on my existing server. It needs to be able to store Outlook calendars so that the Outlook users don't have to store them on their own computers. The list of necessary functions may expand in the future, but for right now, just hosting the Outlook (and Thunderbird) calendars is enough.

I thought Oracle Beehive was going to do the trick, but it doesn't work under Ubuntu. Zentyal was my next though, but I think that overwrites what I presently have.

Anyone got any clues?

---

### Post by SeijiSensei on 2011-03-14
[Apache]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html") supports WebDAV.

---

### Post by zander x on 2011-03-15
> **SeijiSensei said:**
> [Apache]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html") supports WebDAV.

I need uncomplicated directions. That didn't tell me *how* to do it.

---

### Post by SeijiSensei on 2011-03-15
OK.  I spent less than five minutes after searching Google for "apache webdav ubuntu" before finding [this](http://www.linuxserver.org/linux/ubuntu/webdav-ubuntu-10-04/).

---

### Post by falko on 2011-03-15
Take a look here: [How To Set Up WebDAV With Apache2 On Ubuntu 10.04]("http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-10.04")

---

### Post by zander x on 2011-03-18
Both of those two crash on apache2 reload (right before step 5). I tried them. But before crashing, they screwed up my apache so I had to figure out how to get it back.

I also tried Zimbra, and not only will it not do 32 bit for U10.04, it crashed during install.

Scalix basically doesn't work under U10.04 or any other version for that matter.

I'm also not finding any packages that will setup the server WITHOUT touching Apache. All I want to do is share calendars -- not do email because that is still screwed up (Citadel), not change my web server, *just* share calendars and maybe contacts.

---

### Post by SeijiSensei on 2011-03-18
Maybe you should look into [Google Calendar for Business]("http://www.google.com/apps/intl/en/business/calendar.html")?

---

### Post by stmiller on 2011-03-18
[http://www.bedework.org](http://www.bedework.org)

^This is an open source calendar server that supports publishing / syncing.

Doing what you ask will take more then just enabling webdav on the server. :/ Regards,

---

### Post by CVGH on 2011-03-19
I used to use NetDrive on Windo$e to copy files to a app on my iPhone4 over my wifi
network. Is there a way to do this in 10.10?

---

### Post by garfonzo on 2011-03-20
I'll second SeijiSensei's idea for Google Calendars. We use that for our company and it is fantastic. We use the paid-for service, but a company can use the free version.

---

### Post by dmovad on 2011-09-19
Your tutorials are great by the way!  I'd like to add SSL and a different directory for each user.  I'm having a touch time finding such a tutorial.  Any idea if such a tutorial exists?

Thanks a lot!

---

### Post by ykanello on 2011-09-20
Why follow a guide?
The 'idea' behind it of how it works it aint that complicated.
I assume a fast and crude way is to create a separate config for each user in the apache conf. 

For SSL the easiest and IMHO the most robust way to set it up , is to use stunnel, in front of apache. I would put apache to listen to localhost:81 lets say, and then ssl listen from localhost:81 and bind to the normal 443 port.

My advice again is not to follow guides. Read it, understand what the author is doing and then do it yourself.

---

