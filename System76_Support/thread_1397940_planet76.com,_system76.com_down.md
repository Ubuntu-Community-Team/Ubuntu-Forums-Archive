---
title: "planet76.com, system76.com down?"
date: 2010-02-03
forum: System76 Support
---

### Post by tlroche on 2010-02-03
Just wondering if anyone else if having problems browsing to either site. I not only can't browse there (though I can browse everywhere else), I'm also getting

```
$ date ; nslookup www.planet76.com
> Wed Feb  3 21:49:02 EST 2010
> *** Request to DD-WRT timed-out
> Server:  DD-WRT
> Address:  192.168.1.1

> DNS request timed out.
>     timeout was 2 seconds.
> DNS request timed out.
>     timeout was 2 seconds.

$ date ; nslookup www.system76.com
> Wed Feb  3 21:49:24 EST 2010
> *** Request to DD-WRT timed-out
> Server:  DD-WRT
> Address:  192.168.1.1

> DNS request timed out.
>     timeout was 2 seconds.
> DNS request timed out.
>     timeout was 2 seconds.

```
but everything else works, e.g.
```
$ date ; nslookup www.google.com
> Wed Feb  3 21:49:34 EST 2010
> Non-authoritative answer:
> Server:  DD-WRT
> Address:  192.168.1.1

> Name:    www.l.google.com
> Addresses:  74.125.159.103, 74.125.159.104, 74.125.159.105, 74.125.159.106
>           74.125.159.147, 74.125.159.99
> Aliases:  www.google.com

```

---

### Post by samalex on 2010-02-03
It's working fine on my end...  

$ nslookup system76.com
Server:		208.67.222.222
Address:	208.67.222.222#53

Non-authoritative answer:
Name:	system76.com
Address: 63.135.169.119

$ nslookup [www.planet76.com](www.planet76.com)
Server:		208.67.222.222
Address:	208.67.222.222#53

Non-authoritative answer:
Name:	[www.planet76.com](www.planet76.com)
Address: 63.135.169.119


Sam

---

### Post by robtg on 2010-02-03
Working fine for me.

---

### Post by tlroche on 2010-02-03
> **samalex said:**
> It's working fine on my end...
Yep, it's good here now, too.

---

### Post by thomasaaron on 2010-02-04
Whew, you scared me there for a minute.

I dont' know if it *did* go down, but it seems to be fine now.

---

### Post by thomasaaron on 2010-02-04
OK, I take it back. Our site is very unstable at the moment. We're working with our hosting company right now to get it figured out.

Thanks for the heads up.

---

### Post by ctsdownloads on 2010-02-04
> **thomasaaron said:**
> OK, I take it back. Our site is very unstable at the moment. We're working with our hosting company right now to get it figured out.

Thanks for the heads up.

On Verizon FiOS, OpenDNS - it's down here, too.

---

### Post by nealaustin on 2010-02-04
Down here too and my starling is having the same problem. Funny thing ... My pig of a desktop computer has no problems but the starling has failed on both of the upgrades that I went through. Even though it was "made for Linux".

---

### Post by samalex on 2010-02-05
Actually now system76.com isn't loading and I'm unable to ping it...  I'm also using OpenDNS though if that matters.

Sam

---

### Post by rmeineke on 2010-02-05
That's a crying shame.  I *finally* have the cash to order my new Pangolin Performance laptop and I go to the site and it is down!

Oh, well.  I have waited long enough ... another day or two won't kill me.

I'll be back,
Robert M.

---

### Post by bvandev on 2010-02-05
Just a bump to note the System76 servers appear to remain down.  It wouldn't matter so much, but they were down when my Starling update ran.  The update requires the System76 server for the wireless driver to recompile, so I'm stuck.

---

### Post by riseringseeker on 2010-02-05
> **bvandev said:**
> Just a bump to note the System76 servers appear to remain down.  It wouldn't matter so much, but they were down when my Starling update ran.  The update requires the System76 server for the wireless driver to recompile, so I'm stuck.

Can confirm they are down as of 2 minutes ago.

```
W: Failed to fetch http://planet76.com/repositories/./Release.gpg  Could not connect to planet76.com:80 (63.135.169.119), connection timed out

W: Failed to fetch http://planet76.com/repositories/./en_US.bz2  Unable to connect to planet76.com http:

```

---

### Post by thomasaaron on 2010-02-05
Please see this sticky...

[http://ubuntuforums.org/showthread.php?t=1399130](http://ubuntuforums.org/showthread.php?t=1399130)

---

