---
title: "Mail Server Functionality"
date: 2009-03-24
forum: Server Platforms
---

### Post by Hotei on 2009-03-24
Have a problem and looking for some guidance...

The setup:
Say you have a company recieving email on domain domain.tld.  They also have domains someotherdomain.tld and theotherdomain.tld.  Now the only vaild emails on someotherdomain.tld and theotherdomain.tld are [email]info@someotherdomain.tld[/email] and [email]info@theotherdomain.tld[/email].  You would of course forward these on to someone like [email]nancy@domain.tld[/email] to handle them and respond and this is where the fun comes in.

Is there an application that can remove all the headers and rewrite the from address to [email]info@someotherdomain.tld[/email] or [email]info@theotherdomain.tld[/email] depending on who Nancy is responding to?

We currently have a C application that is working but we need to move this process to a new server and the individual who wrote it is no longer with the company.  We need a new way of doing this that we can manage and support ourselves going forward.

Thanks in advance.

---

### Post by HermanAB on 2009-03-24
Install a decent mail server.  It would likely be quicker to install Citadel and configure it to do that than to write or maintain special programs.

Citadel even has a VM that you can download and run if you are super lazy and don't want to spend time figuring things out.

Cheers,

Herman

---

