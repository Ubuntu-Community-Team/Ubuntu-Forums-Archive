---
title: "Dual email servers, is it possible?"
date: 2006-10-01
forum: Server Platforms
---

### Post by Zyzzyx on 2006-10-01
I've had an Exchange 2003 server going for a few years now, its treating me fine. I'd like to fiddle about with an email server on a linux system. But, I don't want to lose what I have set up with Exchange.

I really doubt this, but would it be possible to run two email servers for the same domain at the same time? Perhaps at the router forward port 25 to both systems? I'm kinda thinking that would seriously screw with any communications back to the sending system though.

Perhaps another way would be to set up one server as the main, and then have it forward (somehow?) a copy of everything on to the other system.

---

### Post by sgirard on 2006-10-02
I don't think you can do exactly what you want to do, but if you just want to test the new system you might be able to edit the hosts file on your workstation and point it to the test server.

I too am planning on replacing an old mail server and was thinking about the best way to do something similar.

Hopefully someone can provide a little more guidance.

-sean

---

