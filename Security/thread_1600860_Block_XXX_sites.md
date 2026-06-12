---
title: "Block XXX sites"
date: 2010-10-19
forum: Security
---

### Post by Vexiphne on 2010-10-19
I've just installed Ubuntu on my sisters son computer and I was wondering if there is a way to block all XXX sites so he can't surf to those sites.
I know I can edit hosts, but it's impossible to block all XXX sites this way.

---

### Post by iavor on 2010-10-19
> **Vexiphne said:**
> I've just installed Ubuntu on my sisters son computer and I was wondering if there is a way to block all XXX sites so he can't surf to those sites.
I know I can edit hosts, but it's impossible to block all XXX sites this way.

im no expert in linux but i think you can do this with
[http://www.opendns.com/](http://www.opendns.com/)

you can register for free.. then add those dns servers to your ubuntu and you can then customize what to be filtered.. pr0n, adult etc.. and this should work for your whole network

---

### Post by macem29 on 2010-10-19
firefox has an add on called fox filter...I've tried it in the past and it works, the menu to adjust settings and turn it on-off can be password protected...any bright teenager will get around whatever blocking efforts you try pretty quickly though...Open DNS can be proxied around in about 5 seconds

---

### Post by SeijiSensei on 2010-10-19
Take a look at [Dan's Guardian]("http://dansguardian.org/?page=whatisdg").  You'd need another computer in the house to run it as a server, though.  Anything with 512 MB of memory and a 5-10 GB hard drive is sufficient.

You can install it from the repositories ("sudo apt-get install dansguardian").  It will install the [Squid]("http://www.squid-cache.org/") caching proxy as well.

---

### Post by ratcheer on 2010-10-19
One way is to switch to OpenDNS, which allows you to turn on XXX site filtering that is maintained by them.

[http://www.opendns.com/](http://www.opendns.com/)

Tim

---

### Post by uRock on 2010-10-19
+1 more for openDNS.

---

### Post by CharlesA on 2010-10-19
OpenDNS would be the easier option if you don't want to run a machine with DansGuardian or something similar.

---

### Post by wacky_sung on 2010-10-20
Dansguardian is the best way.Opendns has a problem if you are using dynamic ip in which you require a client to synchronize with them.

---

### Post by Mustache Villain on 2010-10-20
[OpenDNS]("http://www.opendns.com/") is really great for this.

---

### Post by uRock on 2010-10-20
> **wacky_sung said:**
> Dansguardian is the best way.Opendns has a problem if you are using dynamic ip in which you require a client to synchronize with them.
Most home routers store the host mac address and give it the same IP every time.

---

### Post by Vexiphne on 2010-10-20
I decided to use OpenDNS. Easy to setup and easy to install and configure the client for dynamic dns :)

---

