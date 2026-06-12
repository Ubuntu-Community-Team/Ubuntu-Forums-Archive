---
title: "&quot;gvfsd-http&quot; - What is this?"
date: 2013-07-12
forum: Security
---

### Post by JonasDeMoor on 2013-07-12
Hi,

Today I ran the following command in the terminal:

```
sudo watch netstat -tonp
```

and it displayed some results.


There were a lot of entries for chrome, which is normal because Google Chrome was running at that moment. But I don't know what "gvfsd-http" does: there are a lot of entries for that one. When I copied the foreign IP-address assigned to it and pasted it into my browser, an empty page came up, only displaying this message: "It worked!"


Does anyone know if this process is safe? If so, what does it do and what's the use of "gvfsd-http"?

Thank you in advance.

---

### Post by JonasDeMoor on 2013-07-12
Hello,

I fpund out what it does: it's part of the Gnome Virtual File System (or something like that) and I tracked the IP-address by using several websites; here's a report:


[quote="ipTRACKERonline.com"]_**IP Address Quick Report**_
**IP Address:** 91.189.89.31
**Organization:** Canonical Ltd
 **City:** n/a
**Country of Origin:** United Kingdom
* For a complete report on this IP address goto [ipTRACKERonline](http://www.iptrackeronline.com?ip_address=91.189.89.31)[/quote]The process is a process from Canonical; I guess I'm just too paranoid :p

---

### Post by Lfekey2 on 2013-07-13
i found it connect to vary websites, not just canonical. cd /usr/lib/gvfs sudo chmod -x gvfsd-http

---

### Post by F27 on 2013-07-14
As far as I know, gvfsd-http connections are established when you use Software Center and Dash web-based functions (right click previews on applications, apps for download, shopping-music-video lens searches, etc..)   For some reason, these connections are not closed until reboot.

---

