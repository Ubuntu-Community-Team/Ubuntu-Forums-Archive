---
title: "&quot;HD Activity Log&quot;"
date: 2008-08-02
forum: Security
---

### Post by tricota on 2008-08-02
HI All, I'm setting up an Ubuntu File Server for 7 Windows Workstations.

They Have 400Gigabytes Company Information. 

My boss ask me for a Hard Disk Activity Log, in order to detect "data stealing".

Is that possible? where should I start Reading or How can I do it.

Any orentation will be fine!!

Thanks!!

---

### Post by Biochem on 2008-08-04
I don't know exactly what could be done, but since it's a file server my uneducated guess would be to look at the logs produced by samba, and maybe auth.log. The samba documention will also give you a lot of pointer to secure the server before the data get stolen whereas a log will only informe you that you lost something.

If the "bad guys" has direct access to the machine than any log directly provided by the FS could be bypassed easily (or delete or tempered with). So physically securing the server would be essential.

I think for better answer you should provide us with more information such who's potentially going to steal the information. If you are scared of a hacker on the internet, firewall will be better suited than logging the HDD activity. If it's from an unhappy employee that is another matter and encryption might be more appropriated.

---

### Post by exssnrg on 2008-08-04
You might want to check out these links or do some google searching on your own:

[http://www.linuxjournal.com/article/7251](http://www.linuxjournal.com/article/7251)
[http://www.debuntu.org/how-to-remote-syslog-logging-debian-and-ubuntu](http://www.debuntu.org/how-to-remote-syslog-logging-debian-and-ubuntu)

I can't help much with your question with direct experience about how to generate logs from samba, but I did want to comment about the bad guys deleting or altering logs.  This is not possible if you don't maintain logs on the system itself and ship them off to a syslog server.

Not to take anything away from what Biochem offered with the suggestion that you make sure the file system is as secure as it can be to start with.  Good Security is done with layers of defense and logging is one of those.

---

