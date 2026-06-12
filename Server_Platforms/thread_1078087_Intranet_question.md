---
title: "Intranet question"
date: 2009-02-23
forum: Server Platforms
---

### Post by whaase on 2009-02-23
I have a full LAMP server set up with my site on it open to the public.

I'd like to set up TorrentFlux as a Intranet site for home. How can I do this do people can not accidentally/or purposely get access to it from the internet?

I'd like to have it set up so on our lan we would just have to type something like [http://torrent](http://torrent) and have it take us to the Torrentflux page.

I'm a bit lost on how to do this.. anyone able to help or point me to a howto on this?

Thanks :D

---

### Post by Thirtysixway on 2009-02-23
As far as restricting directories, you can use this tutorial

[http://www.cyberciti.biz/faq/apache-restrict-access-based-on-ip-address-to-selected-directories/](http://www.cyberciti.biz/faq/apache-restrict-access-based-on-ip-address-to-selected-directories/)

having [http://torrent](http://torrent) gets a bit more complicated.
On an Ubuntu machine, it would involve editing the /etc/hosts file
[http://ubuntuforums.org/showpost.php?p=11996&postcount=2](http://ubuntuforums.org/showpost.php?p=11996&postcount=2)

Not quite sure how to do it on windows.  You could try naming your server "torrent" and see if that works.

---

### Post by linux_tech on 2009-02-23
Check for more info here-
howto /etc/hosts.deny 
[http://ubuntuforums.org/showthread.php?t=248342](http://ubuntuforums.org/showthread.php?t=248342)

---

