---
title: "How to connect firefox to tor?"
date: 2011-04-11
forum: Security
---

### Post by l07 on 2011-04-11
On ubuntu 10.10, firefox 3.6.16.
I followed [instructions]("https://help.ubuntu.com/community/Tor")  for installing vidalia and polipo and everything seems to be working  ok, but I cannot connect to tor from firefox using torbutton. I didn't  edit configurations other than downloaded those for polipo, as described  in the link above.
I read that somebody got it working with foxyproxy  better than torbutton, but torbutton is customised specifically to  enhance tor, so I'd prefer to use it unless there is something better.

torbutton test fails with: > Tor proxy test: Local HTTP Proxy is unreachable. Is Polipo running properly?Message log from tor:
```
Apr 11 00:39:51.187 [Notice] Tor v0.2.1.30. This is experimental  software. Do not rely on it for strong anonymity. (Running on Linux  i686)
Apr 11 00:39:51.187 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Apr 11 00:39:51.187 [Notice] Opening Socks listener on 127.0.0.1:9050
Apr 11 00:39:51.188 [Notice] Opening Control listener on 127.0.0.1:9051
Apr 11 00:39:51.219 [Notice] Parsing GEOIP file.
Apr 11 00:40:37.414 [Notice] Have tried resolving or connecting to address '[scrubbed]' at 3 different places. Giving up.
```I also tried this ([http://forum.nginx.org/read.php?31,87131):]("http://forum.nginx.org/read.php?31,87131%29:")
> After upgrade to Ubuntu 10.04 Firefox get upgraded to v. 3.6 and all at a
sudden I get the same error message as you describe.

In my case the problem was resolved by a number of random setting
manipulations within Tor Button Properties:

- open Tor Button Properties window;
- run Test Settings (it will fail);
- check "Use custom proxy settings" radio button instead of the default
"Use the recommended settings..."
- run Test Settings (in my case it failed again)
- check "Use the recommended settings..." back and run Test Settings
again. At this point all at sudden I get a positive test result and since
than everything works just fine.

I know all of it does not make much sense but in my case I get it fixed.but that didn't fix it.

Please suggest how to solve this.

---

### Post by Enigmapond on 2011-04-11
I installed it successfully by following the instructions give right at TOR...
[https://www.torproject.org/docs/tor-doc-unix.html.en#polipo](https://www.torproject.org/docs/tor-doc-unix.html.en#polipo)

Did you use the template polipo config given? Mine didn't work until I changed it.

[https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf](https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf)

---

### Post by l07 on 2011-04-11
Thanks, I checked my polipo config again and it was different from the one advised. Now everything's working.

---

### Post by Enigmapond on 2011-04-11
Awesome! No problem! :D

---

### Post by Enigmapond on 2011-04-11
You might also think about installing vidalia. TOR, by default, is always running. Vidalia give you a GUI to start/stop and a few other features. Prior to installing do a alt + F2 and killall tor.

Cheers!

---

### Post by GenePayne on 2011-06-11
Thanks Enigmapond! Changing my polipo config file according to the changes you made fixed TorButton for me.

---

