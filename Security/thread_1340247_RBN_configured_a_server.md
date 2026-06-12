---
title: "RBN configured a server?"
date: 2009-11-28
forum: Security
---

### Post by abm2485 on 2009-11-28
I went to some medical website and it connected to an ip address. Instead of loading the actual webpage...it loaded a different (blank) webpage saying "Congratulations, your server has been correctly configured..." I traced the ip address back to the Russian Business Network...my question, is ...what does that mean and do I have anything I need to be worried about, (i.e. malware, trojans, identity theft, stolen ip...etc.) And if so, what should I do?

---

### Post by cariboo on 2009-11-28
It sounds like you connected to a web site that wasn't set up correctly.

You more than likely have nothing to worry about, as Windows trojans and other Windows malware don't work on Linux.

Unless you entered personal information I doubt you have to worry about idnetity theft.

I'm not sure what you mean about stolen ip, do you mean intellectual property, or ip address?

I would suggest you read the stickies at the top of this page, if you are worried about security.

---

### Post by abm2485 on 2009-11-28
"stolen ip address" as in a trojan, but from what I can understand, that's not really an issue in Ubuntu 9.10 either...

Thank you for your response.

---

### Post by OpSecShellshock on 2009-11-28
If you followed a link directly from a search engine results page, then what most likely happened is that it led to an illicit pharmaceuticals site. It may have been taken down by the hosting provider in response to abuse complaints, or it may have been set up to look at operating system information in the headers and to display content/run scripts only for browsers on a Windows system. It's hard to be sure. That kind of message would be what you'd expect to find on the hosting provider's configuration/administration portal rather than the public-facing web page.

Searches for medical information are used quite a bit by web-based criminals who exploit the functionality of search engine optimization to push links to malicious websites into high ranks on Google and other search services.

---

