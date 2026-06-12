---
title: "Could this be a bad sign ?"
date: 2012-03-13
forum: Security
---

### Post by starz677 on 2012-03-13
My Ubuntu 10.04LTS Server has a nearly continuous stream of outgoing attempts to contact IP Addresses belonging to Proxy servers.  For example...

HideSmart.com
ByPass.ohbah.com
ProxyWorld.com
ProxyStealth.com
MyPrivatgeProxy.com
ShieldProxy.com
CheapPrivateProxy.com
and many, many others

The port is 123 (NTP).

I have the NTP service disabled.  (Actually, it's not installed) so should it still be generating outgoing NTP traffic at all ?

My guess is that a database or web pages(s) have been compromised and something is generating this traffic.  But at this point that's just a guess.

Is there something Ubuntu does (such as checks for updates that this could be related to or is this behavior suspicious?

Finally, if this is not normal, how would I best go about tracking down the offending code or database ?

thx

---

### Post by Ms. Daisy on 2012-03-13
I don't know if that's normal. But you can start checking by looking at the logs. I have found the "Did I Just Get Owned" wiki to be helpful,

[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

---

### Post by starz677 on 2012-03-14
Thank you Ms. Daisy

I need to figure out how to watch to see what process or web page ig generating those outbounds

---

### Post by youngunix on 2012-03-14
> **starz677 said:**
> Thank you Ms. Daisy

I need to figure out how to watch to see what process or web page ig generating those outbounds

If you have physical access or SSH to your machine, and keep the below command running in a separate terminal window. ```
tail -f /var/log/auth.log
```

You can also investigate all the logs in  ```
/var/log
```

---

