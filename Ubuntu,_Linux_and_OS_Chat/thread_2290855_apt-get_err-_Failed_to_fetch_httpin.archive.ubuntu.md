---
title: "apt-get err- Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty/Release"
date: 2015-08-16
forum: Ubuntu, Linux and OS Chat
---

### Post by kalyan3 on 2015-08-16
[COLOR=#141823][FONT=helvetica]I was installing Ubuntu 14.04 in my lab machines. I found apt-get update is not working properly in 14.04 (tried all LTS versions) and 15.04. Its giving following error messages for all the computers. It is working fine in 12.04 LTS. I tried everything with [http://repogen.simplylinux.ch/]("http://l.facebook.com/l.php?u=http%3A%2F%2Frepogen.simplylinux.ch%2F&h=SAQEAo5P4AQHhLqJhs5ADrjZG6CkSTghRYYQZa6bJ0-3EQA&enc=AZPS5z2UbRc_dvJRAkY9DI3SH41hLdxvrOpKUGUNdK6eMFw3BZHokbe7i58fvI6WGKazYxhOlCjRKgXrsdJesA6ZEmA8_m_TCdi7O3UaReuHH_17lZ5FaB29gaAFW2r7v-DTFYPaP496DJARP-o0-iAn9LIS6sGIGAa8UOJ32YLd9g&s=1") also, didnt help. Any idea?[/FONT][/COLOR]
[COLOR=#141823][FONT=helvetica]and it is not able to locate package, even apt-get install vlc is not working, but works via software center.[/FONT][/COLOR]
[COLOR=#141823][FONT=helvetica]W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/Release](http://in.archive.ubuntu.com/ubuntu/dists/trusty/Release)Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)[/FONT][/COLOR]
[COLOR=#141823][FONT=helvetica]E: Some index files failed to download. They have been ignored, or old ones used instead.
[/FONT][/COLOR]

---

### Post by QIII on 2015-08-16
There are a couple of very likely causes:

The mirror site is down or is being updated.

Try switching your mirror to the US or the UK.

---

### Post by kalyan3 on 2015-08-16
Tried to change other mirrors. I got the same error in software center in GUI. But, luckily working with Canadian mirror. Continuing testing with all packages. Will get back with results soon

---

### Post by kalyan3 on 2015-08-16
Qlll now everything is working fine with Canadian mirror. I think the problem is with software sources servers near by (India). Ubuntu has to  check it, Local mirrors are working fine with 12.04 only 14.04cand 15.04 having these problems.

What do you think ?

---

### Post by QIII on 2015-08-16
I think that during mirror updates there may be some unusual behavior.  Things never quite seem to work in practice as they are supposed to.  There may be a network admin pulling his/her hair out and cursing up a storm right now.

Add to that power failures, servers going down, construction workers accidentally digging up cables ...

When I encounter that sort of thing I either change mirrors or wait an hour or two.

---

### Post by flocculant on 2015-08-16
Indian mirrors are 2 days behind.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by QIII on 2015-08-16
Oh, dear!

Oregon State University is a week behind?  Slackers!

---

### Post by Irihapeti on 2015-08-16
Better than one of the New Zealand mirrors with "last update unknown"... :eek:

---

### Post by kalyan3 on 2015-08-16
This is happening after the release of LTS 14.04.3

---

### Post by QIII on 2015-08-16
I think if the mirror you are using now is up to date, it would be fine to just use that for the time being.  You might have some latency going half way around the world if you are in India, but that is just an annoyance.

You can always use the link given above to find out when your preferred mirror is up to date.

---

### Post by kalyan3 on 2015-08-16
Yeah! Thanks Qlll

---

