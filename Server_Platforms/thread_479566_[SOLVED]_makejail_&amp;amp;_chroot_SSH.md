---
title: "[SOLVED] makejail &amp;amp; chroot SSH"
date: 2007-06-20
forum: Server Platforms
---

### Post by altonbr on 2007-06-20
I've tried to wrap my head around this Debian document ([http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html)) of chrooting the SSH daemon, but I've been having some trouble.

It seems as though no one on this forum talks about makejail or chroot. Are these defunct methods to a now much more prevalent method?

I have employees that need to edit and update websites on my server, but one pointed out that he could see the entire server. I know that the permissions levels should be enough to keep everyone at bay, but if people can search through my binaries, that's got to be some sort of security risk.

I figured that chrooting SSH was safer then making them FTP... is it?

And can anyone help explain what I should do?

---

### Post by gaten on 2007-06-21
> It seems as though no one on this forum talks about makejail or chroot. Are these defunct methods to a now much more prevalent method?

No, these methods are one of the best things you can do to secure your box; however they can be a pain to setup properly. 

> 
I have employees that need to edit and update websites on my server

I would create a group for the (**web** or something like that)  and only give them access to what they need. Being able to look through /bin and /usr/bin and so on is no big deal, infact they will need access to those directories in order to do anything useful. However, if there are areas you are worried about, make the permissions as restrictive as possible (700). 

>  I figured that chrooting SSH was safer then making them FTP... is it?

Oh god yes. FTP is cleartext all the way, easy for someone to sniff you users' passwords and whatnot. SSH is encrypted, so it is by **far** the better choice. 

I've never chrooted SSH, but if you point out where you are stuck maybe I can help you. At the *least*, you should either force your users to use strict passwords or make them use public key authentication. Also, creating a specific group for them and enforcing 700 type permissions can help.

---

### Post by altonbr on 2007-06-22
Sorry for the useless post, but I just want to say **thanks** for the reply and answering my uncertainties. I'll give it a whirl in the next couple days and provide you with a link of the tutorial!

---

