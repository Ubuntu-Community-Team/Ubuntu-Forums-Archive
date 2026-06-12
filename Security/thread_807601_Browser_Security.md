---
title: "Browser Security"
date: 2008-05-25
forum: Security
---

### Post by MaindotC on 2008-05-25
[IMG]http://www.danasoft.com/customsig.php[/IMG]

How does danasoft get this information?  One time on the [Security Now podcast]("http://www.twit.tv") I heard Steve Gibson say this information comes from the browser.  Is that true and if so, how do you keep Firefox from sending that information?

---

### Post by MaindotC on 2008-05-26
<a href="http://www.danasoft.com"><img src="http://www.danasoft.com/vipersig.jpg" border="0"></a><p><div style="font-family:Arial,sans-serif;font-size:11px;">Sign by Danasoft - <a href="http://www.danasoft.com">Myspace Layouts and Signs</a></p></div>

---

### Post by RAOF on 2008-05-26
Why would you want to?  The server will have to know your IP address (barring some anonymising proxy*), because you want the server to be able to send data back to you :).

The browser agent string (Linux/mozilla thingy) seems totally harmless.  You can get firefox to send a different browser agent string, but I don't know why you'd bother.

* An anonymising proxy type thing, such as Tor, will basically put one or more hosts between you and the server, so the hop closest to you has your IP address, but the server sees the final machine in the chain.

---

### Post by 289Shelby on 2008-05-26
The OP may be referring to the bit of code that some people put in their sigs. While it does not do any harm it can be disconcerting for some. In my case I just used Adblock to block images from danasoft.

If this is not what you meant just ignore me;-)

---

### Post by MaindotC on 2008-05-29
Well that's not what I want but it describes what I'm talking about :)  For example, that stuff that is displayed by danisoft signature links.  Is there some way to stop that information from being detected?  The more I think about it the more it seems impossible.  A web server definitely needs your ip address as RAOF stated, and I guess it needs to know your o/s too so it knows not to serve content only viewable in IE.

I'll just check GRC - maybe listen to the podcast again.

---

### Post by damatta on 2008-05-29
To spoof the browser type, go to about:config and set the general.useragent.override to whatever you want. This will break some websites as they will assume you are on IE and will send IE-only pages.
Also, disabling some other features of your browser + using adblock and noscript might help. I guess some of those information are acquired through Java, therefore TOR won't help if you dont disable that.

If that was what you wanted to know, you might be interested in reading this:
[http://www.owasp.org/images/2/25/Chuck-willis-owasp-live-o-dc-2007.pdf](http://www.owasp.org/images/2/25/Chuck-willis-owasp-live-o-dc-2007.pdf)

---

### Post by MythosLegend on 2008-05-29
You can download the firefox addon "user agent switcher". I'm using it on my firefox2 and it's pretty cool.

---

### Post by MaindotC on 2008-05-29
None of you really answered my question by thank you for the replys.  Unsubscribing from the thread.

---

### Post by derailed1 on 2008-05-30
Have you tried refcontrol plugin for firefox?  It prevents referring so the new website doesn't know where you came from.

---

