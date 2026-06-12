---
title: "DNS server working but sometimes not for local intranet"
date: 2013-05-10
forum: Server Platforms
---

### Post by Toriku on 2013-05-10
I set up a DNS server on the local network to provide pages for an intranet, the network router was set to use the DNS server as its primary and only DNS server, to ensure that all the local pages would be accessible  and they were; all computers on the network could access all the pages without problem, including mobile phones and tablets connected to the wireless extenders. However, today the pages cannot be reliably found, occasionally page could not be found errors appear for local pages but the DNS server is still forwarding external pages correctly... The pages are all stored on the same machine that runs the DNS server, and the server can be accessed by a browser directly by IP address (in fact doing this seems to correct the problem for some reason).

 When the local pages cannot be found, they are unavailable to all computers for a short while, but the DNS server seems to still connect to external pages just fine, google, bbc, amazon etc...

 Can anyone explain why this could be happening?

  [sorry about the quick description, this is the THIRD time I've typed in my problem, having described at length my issue twice now the forum keep spouted silly error messages related to timing out and wouldn't submit, then when I click back my messages were gone]

---

### Post by d4m1r on 2013-05-13
Is the DNS machine running bind or? Have you tried restarted the server or flushing the DNS of the clients?

---

### Post by Toriku on 2013-05-14
yes, the machine is running bind9, I've restarted the server, but I've not flushed anything;
it seems that accessing it directly on its IP address through a browser on one computer makes it available to the network again for some reason, I can't understand why that should be...

[IMG]http://cdn.memegenerator.net/instances/400x/27270314.jpg[/IMG]

---

