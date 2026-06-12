---
title: "squid3 slow"
date: 2012-12-08
forum: Server Platforms
---

### Post by kanjah on 2012-12-08
Hi comrades, ave just installed squid3 on ubuntu12 server lts, running on transparent mode, my server specs are  core 2 duo, 3.18, 4gb ram and 1tb hardisk. The server is too slow, i have 13 nodes connected, is there  a way out of the low sever speed....?

---

### Post by newbie-user on 2012-12-10
What exactly do you mean by too slow? You might want to check your cache size, or check how much memory squid is using for in-transit objects.

---

### Post by SeijiSensei on 2012-12-10
I have a squid cache in front of 200+ users.  Not only is it running squid, but squidclamav as well.  There's essentially no observable performance effects.  It's a heftier machine than yours, but it's also doing a lot of other things like inbound mail and spam/virus scanning.

How about DNS resolution?  Check that you can resolve names from the squid server itself.  What do the logs say?

---

