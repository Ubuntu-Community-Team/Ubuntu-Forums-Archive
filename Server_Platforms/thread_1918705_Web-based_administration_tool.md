---
title: "Web-based administration tool"
date: 2012-02-01
forum: Server Platforms
---

### Post by createdcreature on 2012-02-01
I am just wondering, as I have seen professional web hosts use Cpanel and the like, is there a free, open source web based administration tool to manage apache and my system. I am sick of having to ssh/telnet into servers to change basic settings on them, not least because of the fact that telnet is not encrypted. Any help would be welcome.

---

### Post by Dry Lips on 2012-02-01
Check out: [http://webmin.com/](http://webmin.com/)

---

### Post by sandyd on 2012-02-01
> **Robert Moyse said:**
> I am just wondering, as I have seen professional web hosts use Cpanel and the like, is there a free, open source web based administration tool to manage apache and my system. I am sick of having to ssh/telnet into servers to change basic settings on them, not least because of the fact that telnet is not encrypted. Any help would be welcome.
webmin.
Mind you, don't run this over the internet - webmin is known to be insecure.
Bind it ONLY to localhost, then access it thorough a SSH Tunnel or something.

---

### Post by createdcreature on 2012-02-02
So what is wrong with webmin over the internet? It is https (although not a totally valid certificate)!

---

### Post by Habitual on 2012-02-02
> **Robert Moyse said:**
> ....although not a totally valid certificate...

Pish-posh:
Self-signed Certs are Perfectly Valid.

---

### Post by sandyd on 2012-02-04
> **Robert Moyse said:**
> So what is wrong with webmin over the internet? It is https (although not a totally valid certificate)!
its vurneable to a whole plethora of stuff.
cross-site scripting, directory permissions .etc .etc.

---

### Post by createdcreature on 2012-04-04
Done! Webmin is great!

---

