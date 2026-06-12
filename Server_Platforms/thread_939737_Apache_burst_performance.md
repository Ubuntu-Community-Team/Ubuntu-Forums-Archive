---
title: "Apache burst performance"
date: 2008-10-06
forum: Server Platforms
---

### Post by asmith3006 on 2008-10-06
I have a server running apache which, because of the way the website works, needs a high burst rate but low continuous rate.

I need to be able to server out the same file to ~1000 simultaneously (it's requested by a server triggered ajax call). I'm obviously hitting the limits on maxclients in the apache config, but I'm not sure where to change it to up it?

Also, I've read that I can up the maxclients to 20,000. Is this correct? Is this recommended?

Thanks.

---

