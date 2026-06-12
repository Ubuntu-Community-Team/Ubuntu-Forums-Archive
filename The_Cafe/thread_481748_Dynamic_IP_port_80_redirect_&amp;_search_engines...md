---
title: "Dynamic IP port 80 redirect &amp; search engines..."
date: 2007-06-22
forum: The Cafe
---

### Post by Cheese Sandwich on 2007-06-22
For those of you not familiar, when you host your own website, and you have a dynamic IP address, and your ISP blocks port 80, you can hire a service to redirect a domain name URL to your current IP & open port (other than 80).

It can do this in one of two ways: It can offer up its own page, which consists of one big frame where it inserts your page, where you the browser see your entire page & your domain-name URL in the address bar, or it can redirect you to to your current IP + port, so that your browser opens up purely your page (no frame container), and you see the current IP address plus port in the address bar.

Now, I use the first option (using the frame container). However, when I googled my domain name, the desired result came up for the front page (it listed my front page, and listed the domain-name URL as its address), but for sub-pages linked to from the front page, google returned an old, no-longer-valid IP address for those!

This is no good for me, as the significant content is in the sub-pages, so users won't be able to get there from web searches. Note that the way I linked from the front page to the sub page is via local, relative paths (for example, instead of linking to "http://www.domain.com/next/nextpage.html" from "http://www.domain.com/index.html", I'd link to "./next/nextpage.html").

So: Any tips on how to rig it so that search results will always consistently work, despite inevitable IP addresss changes? Should I change from the frame container scheme to the full redirect scheme (& sacrifice the meaningful address in the address bar)? Would switching from relative local linking to absolute linking affect it?

---

### Post by tcpip4lyfe on 2007-06-22
Why not pay the extra 5 buck a month and get a static IP?

---

### Post by Cheese Sandwich on 2007-06-23
> **tcpip4lyfe said:**
> Why not pay the extra 5 buck a month and get a static IP?

I could look into that - it doesn't give a price on that on my ISP's website (I have RCN) but I could call them.

---

### Post by Cheese Sandwich on 2007-06-25
Here's something interesting:

[http://www.searchtools.com/robots/index.html](http://www.searchtools.com/robots/index.html)

---

