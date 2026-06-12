---
title: "Apache logs - succesful POSTs?"
date: 2010-02-12
forum: Security
---

### Post by The Cog on 2010-02-12
I installed an apache web server recently, and in looking through the logs I see some POSTS which returned 200 success codes. Since it is only service static files, I don't see how a post can succeed. What's more, the POST seems to be using my server as a proxy. Is this normal? Do I have some kind of weakness here? ```
85.190.0.3 - - [11/Feb/2010:22:19:18 +0000] "CONNECT 213.92.8.7:31204 HTTP/1.0" 405 313 "-" "-"
85.190.0.3 - - [11/Feb/2010:22:19:18 +0000] "POST http://213.92.8.7:31204/ HTTP/1.0" 200 1315 "-" "-"
63.245.212.23 - - [11/Feb/2010:23:26:38 +0000] "CONNECT 63.245.212.23:6667 HTTP/1.0" 405 315 "-" "-"
63.245.212.23 - - [11/Feb/2010:23:26:38 +0000] "POST http://63.245.212.23:6667/ HTTP/1.0" 200 1315 "-" "-"

```

---

### Post by Satoru-san on 2010-02-12
port 6667 is an IRC server port, I dont know why its in apache, but it appears that perhaps a bot is trying to find an IRC network to spam

As for the other 31204 it is *IANA reserved *port range, and is nothing to worry about.

EDIT: Here is my log, just so you can see that that is really no big deal!

Its so big I cant even attach it D:

[http://pastebin.com/m169ead29](http://pastebin.com/m169ead29)

_____________________________

edit 2: 85.190.0.3 <-- I searched with a program I found that I use on my forum to check spam lists, this one doesnt show. Not a spammer.
63.245.212.23 <-- also clean..

I scanned a few of mine, I get some returns for project honeypot of suspicious behavior etc.

---

### Post by The Cog on 2010-02-13
I'm learning something. I manually connected to 213.92.8.7:31204 with nc to see what would cme back, and it said "Proxy Check" before disconnecting. So they are looking for open proxies. The fact that my server returned a 200 code suggests that it is indeed runnng as an open proxy. 

I've corrected my firewall to prevent outgoing connects from the webserver - it was only open to allow apt-get upgrade and I forgot to close it again afterwards. And I've left a sniffer running so I can see if the server actually tries to make the outgoing connection next time it happens. The firewall will block it now, but I should capture the outgoing SYN entering the firewall.

UPDATE:
I got it with the sniffer. The POST succeeds (code 200), but apache is ignoring the host specification of the URL and returning its own root document. So I'm not an open proxy after all.

---

