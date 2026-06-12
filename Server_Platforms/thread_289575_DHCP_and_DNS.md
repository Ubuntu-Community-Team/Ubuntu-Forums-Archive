---
title: "DHCP and DNS"
date: 2006-10-31
forum: Server Platforms
---

### Post by Frunktz on 2006-10-31
Hi!

I have a linux client that work with DHCP (dhcp server on another linux machine). That linux client have a fixed hostname(example: Newuntu).

There is a way to update the DNS on the server, so I can always do:
```
ping newuntu
``` and get the ip address assigned by DHCP and of cource reach that client machine?
Thanks a lot

Ps:- Of course sorry for my bad English. Have patience :D

---

### Post by jimm on 2006-10-31
Hi there!

What you want is Dynamic DNS... Luckily your standard Linux DNS server (BIND) will support it as long as it is v9 or greater.

I have not done this on Linux before, but I do know it is possible... A quick google search and I came up with this:  

[http://dag.wieers.com/howto/bits/bind-ddns.php]("http://dag.wieers.com/howto/bits/bind-ddns.php")

It looks like its a bit redhat oriented but it explains it quite well.

Have a read and a play and let me know how you get on!

Thanks,
James

---

### Post by Frunktz on 2006-11-01
Thanks! Now I try something :D

---

