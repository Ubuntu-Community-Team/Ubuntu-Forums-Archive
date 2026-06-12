---
title: "How to enhance security in Xubuntu?"
date: 2014-08-30
forum: Security
---

### Post by Murong_Yao on 2014-08-30
I already have a few measures in hand:
1)  Firefox with Ghostery, Adblock Plus, Procon Latte (OK, naughty websites are often security compromised), WOT, Webutation.
2)  Only install software from repos.  
3)  Boot with an external hard drive instead of the internal one, and avoid Windows as much as possible.  &#65288;Since the advent of external hard drives, I don´t mess with internal hard drives anymore.)

---

### Post by ThatBum on 2014-08-30
Turn on the firewall, [FONT=courier new]sudo ufw enable

[/FONT]Be sure to add a rule if you have a peer-to-peer program or what have you, gufw is a GUI for ufw that may help with that.

Also of note is that external hard disk are usually much slower than internal ones due to the interface they use, and the drives in the enclosures are often 5400 rpm drives. It might do to install Xubuntu to the internal drive and use the external drive for storage. If Windows is on the internal drive and you want to keep it, you could resize the partition, but doing that for NTFS is complicated. Installing Windows to an external drive is even more complicated...

---

### Post by ajgreeny on 2014-08-31
Just remember that the most insecure part of any computer OS is the person pushing the buttons, and only you can make any difference to how that is done.

Just take care not to do anything stupid and you are very likely to be uncompromised.

---

### Post by whitesmith on 2014-08-31
Tails enhances security by enhancing privacy. Tor does the same, but not as safely.

---

### Post by nomenkultur on 2014-09-01
tor/tails is not a security tool, on the contrary, they work to provide anonymity to your internet traffic by having it go through 6 +/- nodes before reaching your final destination. Your data is much more prone to be intercepted the more nodes there are since each node can capture it.

Obviously it's must more secure for you to have a direct connection to the service you are using, e.g. never do online banking with tails or tor.

 Find a thread 'is it difficult to harden ubuntu?' that one explains in simple steps how to activate apparmor's ffox profile, how to setup iptables and how to monitor active connections

---

### Post by HermanAB on 2014-09-02
Hmm, just relax and enjoy your system!

---

### Post by bashiergui on 2014-09-03
> **nomenkultur said:**
> it goes through 6 +/- nodes before reaching your final destination. Nope. It goes through 3. If it goes through more or less, you're not using Tor. [https://www.torproject.org/about/overview.html.en#thesolution](https://www.torproject.org/about/overview.html.en#thesolution) > Your data is much more prone to be intercepted the more nodes there are since each node can capture it.Hmm. Are you thinking of this? [https://tails.boum.org/doc/about/warning/index.en.html#index1h1](https://tails.boum.org/doc/about/warning/index.en.html#index1h1) Your traffic can be sniffed by an evil exit node unless you encrypt it end to end.

---

