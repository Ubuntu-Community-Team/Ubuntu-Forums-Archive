---
title: "How to validate Ubuntu web page"
date: 2010-05-07
forum: Security
---

### Post by yeehi on 2010-05-07
How can one ensure that one is looking at the real web page? This is important if you are going to download an iso image or validate md5 sums.

For example, the Ubuntu web page here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Has information about certificates available in the URL bar. (If you look at the left of the URL, one can click on the certificate information.)

Surprisingly, there is no such certificate information available at this other Ubuntu web page:

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

The page above is not https. Why is that, by the way?

Thank you for your help!

---

### Post by bodhi.zazen on 2010-05-07
You "validate" a web page by looking at the url in your browser and ensuring it is spelled properly.

If you need to go further, you can install a firefox extension which will validate the ip address of the server you are connected to. Look up the ipadress ...

The next step would be to install wireshark and watch the traffic.

Why do you need ssl to download an iso ?

---

### Post by CharlesA on 2010-05-07
Judging by the OP's other threads, it seems they are very concened about security.

As bodhi.zazen already said: why bother downloading an iso using SSL? As long as you get it from a reputible source (ubuntu.com) and verify the MD5SUM, you are fine.

Why would someone hijack yer browser and take you to a site that looks exactly like ubuntu.com? You don't log in to download the ISO and I don't see why it would be done in the first place, if they aren't able to get personal info.

I can understand phising using a look-a-like of a bank's site, but looking at the address bar would let you know if it was the true site or not.

---

### Post by Jive Turkey on 2010-05-07
From what I have seen the types of attacks one would encounter are not to do with substituting malicious payloads via DNS redirection, but to redirect clients to fake shopping sites offering what they were looking for only after they enter their credit card number.  I cleaned up a friend's computer that probably had a combined total of 10GB of malware installed.  If you searched google with it it would only turn up results offering to sell you anything that you searched for.  

"Nobody ever went broke underestimating the intelligence of the American public." P.T. Barnum

---

