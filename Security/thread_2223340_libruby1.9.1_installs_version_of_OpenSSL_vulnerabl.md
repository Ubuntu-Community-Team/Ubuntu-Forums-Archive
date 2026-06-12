---
title: "libruby1.9.1 installs version of OpenSSL vulnerable to the Heartbleed bug"
date: 2014-05-10
forum: Security
---

### Post by robert.miesen on 2014-05-10
Hi everyone.

I was doing some research and noticed that libruby1.9.1 installs version 1.0.1f of the OpenSSL library, which is one of the version vulnerable to the Heartbleed bug. You can verify this for yourself by running the following script from the command line:

```
ruby -ropenssl -e 'puts OpenSSL::OPENSSL_VERSION'
```

I'm not sure if this is the correct place to put such a report. If this isn't the right place, could someone tell me where I should post this information?

---

### Post by bashiergui on 2014-05-10
Are you sure? 

[http://aaronparecki.com/articles/2014/04/08/1/how-to-test-and-confirm-openssl-is-updated-for-nginx-and-ruby-on-ubuntu-12-04](http://aaronparecki.com/articles/2014/04/08/1/how-to-test-and-confirm-openssl-is-updated-for-nginx-and-ruby-on-ubuntu-12-04)

> Due to the way Ubuntu OpenSSL works, asking Ruby what OpenSSL version it's using doesn't give us any more helpful information:```
$ ruby -r openssl -e 'puts OpenSSL::OPENSSL_VERSION'
OpenSSL 1.0.1 14 Mar 2012
```Now, you won't be able to check the version number, but you can check the date that openssl was built:```
$ openssl version -a
OpenSSL 1.0.1 14 Mar 2012
built on: Mon Apr  7 20:33:29 UTC 2014
```

---

### Post by robert.miesen on 2014-05-10
I followed the link to the article and was able to determine that the ruby code I gave gives inaccurate information and, in fact, calls out to whatever version of the openssl library is installed on the system.

It's good to know that the bug identified is only one of the ruby library reporting the wrong information! Thanks for your help bashiergui!

---

