---
title: "Syslogd listening for remote logs"
date: 2005-12-31
forum: Server Platforms
---

### Post by mattski on 2005-12-31
I'm trying to use my kubuntu host as a logger for remote log messages, but syslogd doesn't seem to be listening. I can see in Ethereal that the remote host is generating the messages, and sending them to my server on port 514/UDP. However, they're not getting logged. Also, netstat doesn't show my server listening on 514/UDP. Any way to force syslogd to listen remotely? Or am I missing something else?

---

### Post by 23meg on 2005-12-31
I think you need to run syslogd with the -h switch. Refer to the manpage.

---

### Post by mattski on 2005-12-31
Thanks for that incredibly fast response... I went to the manpage and the correct switch is "-r", which worked.

It turns out the default listening behaviour has been reversed - you used to need a switch to disable it. I had been looking at obsolete man pages on the net...

---

