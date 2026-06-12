---
title: "Web-based SSH Clients"
date: 2015-11-19
forum: Security
---

### Post by branau on 2015-11-19
My phone runs Firefox OS, which doesn't have a whole lot to offer when it comes to native apps but it does integrate webapps quite nicely, considering the OS is built using web technologies. One particular app I'm missing from my android days is an SSH client. There are currently no native SSH options but I've seen some sites that offer SSH clients from the browser. This seems to me like a security issue, and I'm confused as to how they would even work, considering web traffic uses ports 80 and 443, while SSH is on port 22. I don't think I'd ever be able to trust a web site as an SSH client replacement, but if I were to write my own SSH webapp client, would it be a bad idea altogether or would it be fine? And what should I take into consideration when writing it?

---

### Post by papibe on 2015-11-19
Hi branau.

You may want to take a look at shellinabox. It is not exactly a client in your phone, but more of a service that provide shell access via http or https.

Here's a the basics [shellinabox]("https://help.ubuntu.com/community/shellinabox"), and here's another tutorial: [Shell In A Box &#8211; A Web-Based SSH Terminal to Access Remote Linux Servers]("http://www.tecmint.com/shell-in-a-box-a-web-based-ssh-terminal-to-access-remote-linux-servers/").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by branau on 2015-11-19
Thanks papibe, I'll have to look into that

---

### Post by HermanAB on 2015-11-26
You can install webmin on your web server and access it with a browser.

---

