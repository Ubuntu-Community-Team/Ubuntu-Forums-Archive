---
title: "redirecting to http://g.asdafdgfgf.com problem"
date: 2008-01-19
forum: Server Platforms
---

### Post by eternalsunshine on 2008-01-19
I think this is the right place to ask this.

I have this problem in my newly installed Ubuntu 7.10 x64:

Whenever i try to browse in the internet after hitting the site it writes "waiting for http://g.asdafdgfgf.com" and cannot open my actual site.
and when i look at the source code there is the line:

```
<script LANGUAGE="javascript1.2" SRC="http://g.asdafdgfgf.com/ads.js"></script> 
```

This problem surprisingly does not occur on my dual boot windows vista.
I installed noscript and adblock plus but no way i can browse the web.

When i googled this problem , i found that it is a trojan but isn't my linux system suppose to be immune to trojans?

What can i do to solve this problem please help?

I really need to solve this problem immediately.

---

### Post by MJN on 2008-01-19
> **eternalsunshine said:**
> Whenever i try to browse in the internet after hitting the site it writes "waiting for http://g.asdafdgfgf.com" and cannot open my actual site.

What site? *Any *site?

What happens if you run **wget http://<one of the sites you're trying to reach> **(this will download the default page into a local file)

Mathew

---

### Post by masterthor on 2008-01-24
if you do a google search for "asdafdgfgf.com" you'll notice that this is a sort of virus, a very widespread one these days also (my whole campus is infected). 

The thing with it is that it uses ARP spoofing or some other tehniques to inject that javascript into connections of other computers, so it basically doesn't matter what OS you are on. The fact that this didn't happen on Windows is merely a coincidence, as we managed to see that js load on pages requested from pretty much every os we could find in the network. 

The thing to do here is to block that page (maybe with the hosts file), and to talk about this problem with your ISP. the people that actually have the virus and are infected can be found by using a sniffer, as they do A LOT of arp traffic.

---

