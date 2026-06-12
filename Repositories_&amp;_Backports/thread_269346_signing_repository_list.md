---
title: "signing repository list"
date: 2006-10-01
forum: Repositories &amp; Backports
---

### Post by daroof on 2006-10-01
Hi 
I am using Jabref as my bliography reference manager (kubuntu edgy). It will be available to install if we add following line to our sources.list:

deb [http://www.toastfreeware.priv.at/debian/](http://www.toastfreeware.priv.at/debian/) unstable/

It works great, but I have problem with signing it with the PGP key. On the blog ([http://info.comodo.priv.at/blog/archives/2005/09/#e2005-09-02T15_13_14.txt](http://info.comodo.priv.at/blog/archives/2005/09/#e2005-09-02T15_13_14.txt)) they advise to do: 

lynx -dump [http://info.comodo.priv.at/0x00F3CFE4.asc](http://info.comodo.priv.at/0x00F3CFE4.asc) | apt-key add -

but is doesn't work. What did I wrong?

Thanx for all help
daroof

ps. this is what I get after trying to sign:
gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

---

