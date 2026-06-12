---
title: "polipo does not open its web interface"
date: 2013-06-14
forum: Security
---

### Post by Farinet on 2013-06-14
I've up and running polipo together with tor. Polipo is set like this:

```

proxyAddress = "127.0.0.1"    # IPv4 only
proxyPort = 8123
allowedClients = 127.0.0.1
allowedPorts = 1-65535     
proxyName = "localhost"
socksParentProxy = "localhost:9050"
socksProxyType = socks5
localDocumentRoot = "/usr/share/polipo/www"
disableVia=true
censoredHeaders = from, accept-language,x-pad,link
censorReferer = maybe
forbiddenUrl = http://127.0.0.1:8118/empty.gif
redirector = /usr/bin/adzapper

```

To ad adblock to polipo i followed [this advice]("http://bodhizazen.net/Tutorials/TOR#Polipo") for (1). Tor is set standardwise. Vidalia i set as a startup program (with "start tor when vidalia starts" unchecked).

My main browsers are Midori and Iceweasel. They are set to point to 127.0.0.1:8123. In Iceweasel i had to set SOCKS-host 127.0.0.1:9050

As far as i can see all is fine without one point:

When i try to open the webinterface of polipo i'm getting an error. In Iceweasel:

==============================
ERROR: For security reasons this port is blocked (i'm translating from the german prompt text, sorry, if it's inexact)
==============================

In Midori:

==================================================
504 Connect to localhost:8123 failed: General SOCKS server failure

The following error occurred while trying to access [http://localhost:8123/polipo:](http://localhost:8123/polipo:)

504 Connect to localhost:8123 failed: General SOCKS server failure
==================================================

Anyone has an idea? Thanks a lot in advance!

----------
(1) In bodhizazen's excellent instructions to ad adblock to polipo, unfortunately the last step, those to get and install Empty.gif did not work (because the file does not exist - anymore? - in the indicated place).

---

### Post by unspawn on 2013-06-16
> **Farinet said:**
> When i try to open the webinterface of polipo i'm getting an error.That's because the tutorial didn't explain the options (it explictly says *"Here is my configuration file (without comments)."*) and you didn't check your configuration against the Polipo manual (*disableLocalInterface*) ;-p> **Farinet said:**
> excellent instructions to ad adblock to polipoThe problem with certain web log posts, HOWTO's and other documentation is they aren't time stamped, meaning instructions may be out of date (the referenced is 4 years old). What's worse is that you'll be loading lines that 0) may not match your browsing behaviour, interests, location or other such attributes (efficiency), you don't know  1) who vouched for, 2) how often it's updated (one aspect the tutorial neglects to mention) and 3) about 36K worth of "filters" which have to be parsed for a match (performance). I don't know how efficient Polipo does that (let us know?) but I can't imagine that would be without penalty.

---

### Post by Farinet on 2013-06-16
> **unspawn said:**
> . . . and you didn't check your configuration against the Polipo manual (*disableLocalInterface*) ;-p . . . 

I'm ingenuous, so i go forward asking step by step ;)  What dou you mean with what i quoted above? I checked the config file and the manual but i don't get how

```
*disableLocalInterface*
```

should be set. I set it to false (false or true seems to be the correct values) but nothing changed.

[SIZE=1]PS. I suspect it might be something different, since i remember some time ago i got trough to the webinterface without doing anything.[/SIZE]

---

### Post by unspawn on 2013-06-16
> **Farinet said:**
> nothing changed.Restart the daemon to make change stick?

---

### Post by Farinet on 2013-06-17
Sure.

```
sudo service polipo restart
```

---

