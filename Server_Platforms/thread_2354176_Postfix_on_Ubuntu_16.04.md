---
title: "Postfix on Ubuntu 16.04"
date: 2017-02-28
forum: Server Platforms
---

### Post by pcunix on 2017-02-28
Where can I find proper instructions for setting up mail forwarding to gmail (as described at [http://www.binarytides.com/postfix-mail-forwarding-debian/](http://www.binarytides.com/postfix-mail-forwarding-debian/) ) or better debugging help?

I can get postfix listening, but when I do the config changes suggested at that link, it won't restart, failing in mail.err with 

postfix/postfix-script[8388]: error: unknown command: ''

So I assumed at first that perhaps I'd added an accidental blank line in one of the two files edited, but no, I haven't.  

```
# postfix check
postfix: Postfix is running with backwards-compatible default settings
postfix: See [http://www.postfix.org/COMPATIBILITY_README.html](http://www.postfix.org/COMPATIBILITY_README.html) for details
postfix: To disable backwards compatibility use "postconf compatibility_level=2" and "postfix reload"
postfix/postfix-script: warning: group or other writable: /usr/lib/postfix/./libpostfix-tls.so.1
postfix/postfix-script: warning: group or other writable: /usr/lib/postfix/./libpostfix-global.so.1
postfix/postfix-script: warning: group or other writable: /usr/lib/postfix/./libpostfix-master.so.1
postfix/postfix-script: warning: group or other writable: /usr/lib/postfix/./libpostfix-util.so.1
postfix/postfix-script: warning: group or other writable: /usr/lib/postfix/./libpostfix-dns.so.1
postfix/postfix-script: warning: group or other writable: /usr/lib/postfix/./sbin/lmtp
postfix/postfix-script: warning: group or other writable: /usr/lib/postfix/sbin/./lmtp

```
That doesn't seem to help..

---

### Post by bearlake on 2017-02-28
I use Postfix for send only and this post worked very well with 16.04

[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-16-04)

---

