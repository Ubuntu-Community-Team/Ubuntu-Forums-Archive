---
title: "help please"
date: 2007-07-18
forum: Testimonials &amp; Experiences
---

### Post by denkz on 2007-07-18
how can i block web site as router with iptables???

---

### Post by HermanAB on 2007-07-18
I'm not sure what you mean, but the easiest and quite efficient way to block a web site is by using your /etc/hosts file.  An entry like this will block Yahoo:
127.0.0.1 [www.yahoo.com](www.yahoo.com)

The best way to clean up the web and block millions of junk sites is with a combination of Squid Proxy and SquidGuard or Dan's Guardian.  However, setting it up is non-trivial.  If you have to ask how, then you likely won't be able to do it.  However, there is a VMware appliance on the VMware site for this, which would be super easy to get to work with the free VMware Server.

'Hope that helps.

Herman

---

### Post by Sarisar on 2007-07-19
I made some notes on how to set up squid when I set it up.  I have it blocking cookies and various websites that are listed in files.

[My notes are here]("http://www.leggate.org/pmwiki/pmwiki.php?n=Linux.Squid").

Hope that helps, if not let me know and I'll see if I can help you understand my notes :P

---

### Post by wolfen69 on 2007-07-19
you will get more responses by posting in the correct(help) forum.

---

### Post by bigie on 2007-07-23
did you mean block some web site from your router???that router are pc router???
I think you can use squid on your pc router ....:)

---

