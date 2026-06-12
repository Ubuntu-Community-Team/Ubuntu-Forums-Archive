---
title: "tor and logs"
date: 2014-12-16
forum: Security
---

### Post by deb2014 on 2014-12-16
Hello,

does tor  write logs while working ?

I saw that something was created under /var/log 

but I wonder if it writes logs about the connexions it makes or is it just some log debugging at startup ?

---

### Post by open2reason on 2014-12-16
deb2014, would it be possible to post examples of this behaviour?

---

### Post by bashiergui on 2014-12-16
If you're using the tor browser bundle then yes. It creates application-level logs. 
[https://www.torproject.org/docs/faq.html.en#Logs](https://www.torproject.org/docs/faq.html.en#Logs)

if you're using something other than the browser bundle then you'll have to give more details.

---

### Post by open2reason on 2014-12-17
deb2014,
in addition to the excellent link provided by bashiergui you might wish to consider these to be found on the Torproject site;
Tor weekly blog [https://blog.torproject.org/blog/tor-weekly-news-%E2%80%94-december-17th-2014](https://blog.torproject.org/blog/tor-weekly-news-%E2%80%94-december-17th-2014) general news with links to other topics.
News of the next release [https://blog.torproject.org/blog/tor-browser-45-alpha-2-released](https://blog.torproject.org/blog/tor-browser-45-alpha-2-released)
Robust discussion of some technical questions and answers of Tor nature [https://lists.torproject.org/pipermail/tor-talk/](https://lists.torproject.org/pipermail/tor-talk/)

If logging of Tor actions is of concern then perhaps running Tails OS [https://tails.boum.org/](https://tails.boum.org/)    which runs as a liveCD and contacts the net via Tor might be of use.

---

### Post by deb2014 on 2014-12-18
Hello

Thanks for your answeers and useful links.

Tor seems to create a directory /var/log/tor in which it writes something.

I wanted to know if what was written could be used to discover the user is doing with tor, as an example can someone see what pages are visited with a web browser (using tor) by reading the tor logs,

I quite doubt about it, it would be contrary to the tor goal, btu I wanted to be sure.

Thanks for your answeers

Best regards

---

### Post by bashiergui on 2014-12-18
Foolproof way to find out is read the log it creates. ```
cat /var/log/tor
```

---

