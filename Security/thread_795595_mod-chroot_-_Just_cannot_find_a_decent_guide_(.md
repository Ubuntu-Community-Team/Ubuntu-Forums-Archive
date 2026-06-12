---
title: "mod-chroot - Just cannot find a decent guide :("
date: 2008-05-15
forum: Security
---

### Post by Georgecooldude on 2008-05-15
I've been trying to chroot apache2 on ubuntu 6.02 in test.

I was following the guide over on howtoforge for a debian system ([http://howtoforge.com/chrooting-apache2-mod-chroot-debian-etch](http://howtoforge.com/chrooting-apache2-mod-chroot-debian-etch)) but no matter how I try it I always get errors the moment I restart apache. 

Can anyone recommend any step by step guides for installing, setting up and verifing apache 2 chrooting?

Thanks in advance :D

---

### Post by HermanAB on 2008-05-16
Well, first you got to ask yourself why?  What is the security concern that warrants going to all that trouble and will chroot really help against the perceived threat?

Once you have read up about it, you will likely conclude that it is not worth the trouble, since it doesn't provide any real security enhancement, while it increases the required maintenance effort tremendously.

Basically, your chroot guides don't work, because they are not maintained and they are not maintained because nobody use them anymore...

If you are really concerned about Apache security, rather look into SELinux.  Redhat/Centos provide a working Apache with SELinux setup.

Cheers,

Herman

---

