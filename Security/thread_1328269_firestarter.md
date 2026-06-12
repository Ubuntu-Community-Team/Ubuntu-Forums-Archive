---
title: "firestarter?"
date: 2009-11-16
forum: Security
---

### Post by pvplahing138 on 2009-11-16
is firestarter good linux firewall to use?

---

### Post by Soul-Sing on 2009-11-16
> **pvplahing138 said:**
> is firestarter good linux firewall to use?

Yep. But i recommend using ufw/gufw, because is very much "alive" and in development. Firestarter isn't maintained since 2007....

---

### Post by pvplahing138 on 2009-11-16
> **leoquant said:**
> Yep. But i recommend using ufw/gufw, because is very much "alive" and in development. Firestarter isn't maintained since 2007....
ok i use firestarter cause its easier to me:P
but thanks for anwsering:)

---

### Post by Saghaulor on 2009-11-16
GUFW is very easy to use. I recommend looking into it.

---

### Post by pvplahing138 on 2009-11-16
> **Saghaulor said:**
> GUFW is very easy to use. I recommend looking into it.
i give it a try.

---

### Post by BelzeBob on 2009-11-17
I removed firestarter and kept the "GUFW". Because... firestarter wasn't really doing anything. Then I configured "GUFW" (who comes up with these names?) to be always on. Though....I can't remember how I did that... :) But that's important - otherwise you think you have a firewall...but it ain't running.

Yesterday I installed a free Avast! anti-virus too. For scanning windows/torrent files:
[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html) (Deb).

---

### Post by QLee on 2009-11-17
> **BelzeBob said:**
> I removed firestarter and kept the "GUFW". Because... firestarter wasn't really doing anything. Then I configured "GUFW" (who comes up with these names?) to be always on. Though....I can't remember how I did that... :) But that's important - otherwise you think you have a firewall...but it ain't running.

Yesterday I installed a free Avast! anti-virus too. For scanning windows/torrent files:
[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html) (Deb).

Both Firestarter and GUFW are GUI interfaces to iptables which is the "firewall" .

I think you misinterpreted what was going on with your system, When Firestarter is installed it sets up iptables and the GUI Firestarter does not have to be running eating resources for your system to be protected.

Firestarter is still maintained by the Debian maintainer even if it hasn't had any new features added in a few years, it's just a front-end to iptables.

GUFW is the GUI for uncomplicated firewall which is the recommended front-end here.

Have a look at this page by our forum admin:
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

