---
title: "Securing RDP"
date: 2010-10-08
forum: Security
---

### Post by crackconfig on 2010-10-08
There is a great security risk. plz tell me How to secure a Terminal Server. so that it can't be hacked by bruteforce/divtionary tools !

Thnx!:confused:

---

### Post by Rubi1200 on 2010-10-08
If you need our help, you need to be more verbose:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

Ubuntu Security:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by CharlesA on 2010-10-08
Terminal server as in LTSP or Windows Termaminal Services?

---

### Post by HermanAB on 2010-10-08
Howdy,

Windows RDP is secure. It has a man-in-the-middle vulnerability, but that is hard to pull off outside a laboratory. So I won't worry about RDP.

The only decent protection against brute force password attacks is to use a proper password to begin with, but you could also add an iptables rate limit filter to make brute forcing infeasible on your Linux machines.

---

### Post by pricetech on 2010-10-08
> **HermanAB said:**
> Howdy,

Windows RDP is secure.

Whhaatt ???????

---

### Post by HermanAB on 2010-10-08
Windows RDP uses RC4, which is secure.

---

### Post by CharlesA on 2010-10-08
> **HermanAB said:**
> The only decent protection against brute force password attacks is to use a proper password to begin with, but you could also add an iptables rate limit filter to make brute forcing infeasible on your Linux machines.

+1 to that. If it was a Windows environment, you could set it to lock the user account after 3 failed login attempts.

> **HermanAB said:**
> Windows RDP uses RC4, which is secure.

+2 to that. RDP is encrypted by default.

---

### Post by movieman on 2010-10-08
> **HermanAB said:**
> Windows RDP uses RC4, which is secure.

It's quite some time since I've seen anyone use the words 'RC4' and 'secure' in the same sentence...

While it's not as insecure as ROT13, it has enough well-known problems that no-one in their right mind should be using it anymore.

---

