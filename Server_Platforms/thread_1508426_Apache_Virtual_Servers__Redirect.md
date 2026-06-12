---
title: "Apache Virtual Servers / Redirect"
date: 2010-06-12
forum: Server Platforms
---

### Post by Ocxic on 2010-06-12
I have a dyndns account directed at my computer. and everything with that is working fine. I can access my web server without issue.

However I do have several virtual servers(3 in fact) xirxi.mine.nu, bnet.mine.nu, kweb.mine.nu.

xirix.mine.nu is accessible from the net and is my primary website.
bnet.mine.nu and kweb.mine.nu are not accessible.

What I would like to do is be able to type in xirix.mine.nu/bnet and get the page at bnet.mine.nu 

Is this possible?

UPDATE: I got the above working. :),, now when i go to xirix.mine.nu/kweb i get the web page at keb.mine.nu

However, when clinking a link on that page I get "The requested URL /ConZost/ was not found on this server" and it's looking for "xirix.mine.nu/ConZost/"
any ideas on what is happening here?

Never mind, I give up,, marking as solved.

---

### Post by Ryan Dwyer on 2010-06-13
The 404 happens because the link you clicked is linking to /ConZost/ which is an absolute URL. The slash at the start means it will request it from the topmost level (ie. xirix.mine.nu/ConZost/) and not relative to the current directory.

You can correct the link by linking to ConZost/ instead (no starting slash), but if there are a lot of links this will obviously take a while.

So you can either:
a) Change all the links to relative links,
b) Register bnet.mine.nu and kweb.mine.nu, or
c) Add bnet.mine.nu and kweb.mine.nu to your hosts file on all client machines that need to access it from outside the network.

---

