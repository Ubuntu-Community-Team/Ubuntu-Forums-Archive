---
title: "Chrome HSTS Error"
date: 2017-03-27
forum: Security
---

### Post by reegz on 2017-03-27
Howdy all,

I've having some trouble with Chrome when behind the company firewall. Basically, Chrome refuses to access any site that uses SSL. It gives me the HSTS error as below (not mine - but it's the same error).

[IMG]https://community.sophos.com/cfs-file/__key/telligent-evolution-components-attachments/00-55-00-00-00-04-65-82/chrome_5F00_hsts_5F00_error.jpg[/IMG]

Previously, I had added the company's root certificate to Ubuntu by dropping it in */usr/local/share/ca-certificates* and running *update-ca-certificates*. I also imported it into Chrome's certificate store.

I can't seem to pinpoint any event that's brought this error about but it is annoying. I'm certain that it is a Chrome issue as I'm able to browse SSL-secured sites using Firefox (spit) from behind the firewall without issue.

Anyone have any pointers for me on how to resolve this issue?

Thanks

---

### Post by #&amp;thj^% on 2017-03-27
Just heard about this in January 2017, and I don't use Chrome, but see if this is of any help/use.

[https://www.wordfence.com/blog/2017/01/chrome-56-ssl-https-wordpress/](https://www.wordfence.com/blog/2017/01/chrome-56-ssl-https-wordpress/)

Possible work around:
[https://developers.google.com/web/fundamentals/security/encrypt-in-transit/enable-https?hl=en](https://developers.google.com/web/fundamentals/security/encrypt-in-transit/enable-https?hl=en)

---

### Post by reegz on 2017-03-28
Thanks for that. Not quite what I was looking for helpful nonetheless. In fact, after reading that I upgraded my personal site to https :-)

---

