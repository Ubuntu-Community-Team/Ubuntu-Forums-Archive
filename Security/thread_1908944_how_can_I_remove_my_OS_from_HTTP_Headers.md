---
title: "how can I remove my OS from HTTP Headers"
date: 2012-01-14
forum: Security
---

### Post by Fertech on 2012-01-14
I notice that in whatsmyip.org I click on http headers and my operating system will show.
how can I remove my operating system from the http headers.

---

### Post by SeijiSensei on 2012-01-14
I don't know that you can, though you can spoof your OS headers in Firefox with the [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") add-on.  Perhaps you can create a User Agent string with an empty OS field; never tried myself.

---

### Post by coldraven on 2012-01-14
Yes you can edit the User Agent

---

### Post by Doug S on 2012-01-15
Does this help?: [http://httpd.apache.org/docs/current/mod/mod_headers.html](http://httpd.apache.org/docs/current/mod/mod_headers.html)

---

### Post by hackertarget on 2012-01-15
HTTP Headers come from a Web Server. These can be changed by web server configuration; varies depending on the server.

What you are refering to is the User Agent, a string that your browser sends to the web server.

The User Agent can be changed as mentioned however, some pages perform checks against the User Agent, to attempt to do clean formatting for browsers that are not standards compliant; (IE 6 & 7) are particularily bad for this.

---

### Post by Dangertux on 2012-01-15
Tamper data is also a cool firefox extension. Web Scarab can also do this though both on a more in depth level. Including modifying http GET and POST requests in flight.

---

### Post by gsgleason on 2012-01-17
> **hackertarget said:**
> HTTP Headers come from a Web Server. These can be changed by web server configuration; varies depending on the server.

What you are refering to is the User Agent, a string that your browser sends to the web server.

Not exactly.

Headers exist both in the REQUEST (from the client) and the RESPOSE (from the server).

The User-Agent is in fact an HTTP header.

OP, the solution depends on the browser you're using.

---

### Post by emiller12345 on 2012-01-17
> **SeijiSensei said:**
> I don't know that you can, though you can spoof your OS headers in Firefox with the [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") add-on.  Perhaps you can create a User Agent string with an empty OS field; never tried myself.

I made a substantial database for this particular firefox addon, which can be found here
[http://digitalmagican.comze.com/useragentswitcher-201101151440.xml](http://digitalmagican.comze.com/useragentswitcher-201101151440.xml)

---

