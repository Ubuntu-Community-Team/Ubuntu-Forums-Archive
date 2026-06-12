---
title: "apache2 problem - I think"
date: 2009-11-14
forum: Server Platforms
---

### Post by ab8yy on 2009-11-14
I am using no-ip to point a domain name to my server which is on a dynamic IP.  Here is the situation - I have configured the DSL Modem/Router to use DMZ on the server so that all internet traffic will reach it - at least for testing anyway.  I have the ability to ping the server without issues.

In fact, if I use hamnet.no-ip.org/index.html, I can get to the server without issue as well.  But without the index.html, it doesn't show the proper page.

I think I have everything in apache2 setup right, html as well as htm and php are listed for default extentions.  I added ServerName hamnet.no-ip.org to the configuration file as well.

Still won't work right.  If I go directly to the IP address, it works just fine, if I use localhost on the server it also works fine.

What am I missing here????  Anyone got a clue on this one?

Thanks
Steve

PS Sorry if this has been answered already, please repost or give me a link to the older post on this issue.

---

### Post by shred_eng on 2009-11-15
do you mean if you type hamnet.no-ip.org that it doesnt go to - it works page?

because i just typed that and it does, guess you fixed it:)

---

