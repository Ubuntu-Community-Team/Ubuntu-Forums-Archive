---
title: "Questions about proftpd"
date: 2005-06-29
forum: Server Platforms
---

### Post by frodon on 2005-06-29
Hi

I run my FTP server with proftpd and all work well but I have some questions I can't answer.

I install proftpd using synaptic and when I use the ftptop command or run gproftpd I can't see the download speed and generally the state of the downloaded file. My first idea is that synaptic don't compile proftpd with this feature. Can someone bring insight on this point ?

I run my FTP server as standalone server, and every time I reboot my computer proftpd is running when I start gnome. I would prefer to start it myself in order to not let my FTP opened when I don't want it. Does someone have knowledge about that ?

Thanks for any kind of answer and don't hesitate to post questions in this thread if you think it would interest someone.

---

### Post by marsian on 2005-06-29
[QUOTE=frodon]
I run my FTP server as standalone server, and every time I reboot my computer proftpd is running when I start gnome. I would prefer to start it myself in order to not let my FTP opened when I don't want it. Does someone have knowledge about that ?[/QUOTE]

I don't use proftpd, but maybe this can help:
[http://ubuntuguide.org/#permanentlydisableenableboot-upservices](http://ubuntuguide.org/#permanentlydisableenableboot-upservices)
where service_name should be something that sounds like proftpd...

---

