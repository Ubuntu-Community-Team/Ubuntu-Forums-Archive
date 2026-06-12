---
title: "Installing JAVA under terminal?"
date: 2011-01-21
forum: Server Platforms
---

### Post by familyguy.02 on 2011-01-21
I am trying to install the Sun Microsystems Java Runtime on my Ubuntu Server 10.10, but it is telling me that it is not available. I have researched online and it tells me that it is a part of the multiverse repository. I have not had very much success in activating this either. Any help would be appreciated. Btw, I am a noob :P

---

### Post by HugoSerrano on 2011-01-21
Hi!

You need to enable partner repositories.

Go to /etc/apt/sources.list and uncomment the parter lines

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

then:
apt-get update
apt-cache search java | grep sun
and choose the packages you want.

Regards!

---

