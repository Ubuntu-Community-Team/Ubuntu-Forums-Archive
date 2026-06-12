---
title: "Why is the Firefox in Ubuntu repository always &quot;delayed&quot; (old version) ?"
date: 2009-07-24
forum: The Cafe
---

### Post by Andre-D on 2009-07-24
Why is the Firefox in Ubuntu repository always "delayed" (old version) ?
..even when Mozilla does provide a newer version for Linux ?

I bet there's a reason .. but is it good ? - and what is it ?

---

### Post by RJ12 on 2009-07-24
Maybe stability

---

### Post by kerry_s on 2009-07-24
> **Andre-D said:**
> Why is the Firefox in Ubuntu repository always "delayed" (old version) ?
..even when Mozilla does provide a newer version for Linux ?

I bet there's a reason .. but is it good ? - and what is it ?

cause ubuntu is not a rolling release distro, once the ubuntu version is released it's locked in. to get newer versions of software you update the distro to the next release.
you of course always have the option of upgrading manually.

---

### Post by QIII on 2009-07-24
Many things in Ubuntu are "delayed" while the developers work to make sure that the vendors' latest releases work well in Ubuntu.

If you are interested, you can keep up with the latest FF builds (I think I am using "Minefield" right now.  May be updated again today when I get home...)

You can find out how here:

**[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)**

---

### Post by Andre-D on 2009-07-24
ok, so if I want the latest browser, for security reasons, I need to download/install from Mozilla myself.
-Is there any good reason NOT to do it ?
-can I add a source to the "third party software" , and make it update automagically ?

---

### Post by aysiu on 2009-07-24
> **Andre-D said:**
> ok, so if I want the latest browser, for security reasons, I need to download/install from Mozilla myself.
-Is there any good reason NOT to do it ?
-can I add a source to the "third party software" , and make it update automagically ? A few things:

1. Even if Ubuntu keeps the old version of Firefox, it'll keep issuing security updates to the old version even if Mozilla doesn't.

2. Yes, you can easily install the Mozilla build of Firefox. It's as simple as copying and pasting one command. More details here:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

3. You can add a third-party software source, but it'll be branded as Shiroteko, and it'll have other problems (user agent identification to work around on some websites, an ugly blue icon, non-default-browser setting to change).

---

### Post by Andre-D on 2009-07-24
ok, great - thanks.

---

