---
title: "SSH freeze when UFW is enabled"
date: 2011-06-22
forum: Server Platforms
---

### Post by cristian.vrabie on 2011-06-22
Hey guys,
I have a small Ubuntu 10.10 server and i recently noticed a weird behavior (not sure if it was happening before). If I have ufw enabled (with default deny all in, allow all out, allow all http, allow all on a random port i use for ssh) when i perform some actions in a ssh sesion, the ssh console completely freezes. The server continues to work and if i close the console i can start another ssh session. This happens no matter from where I log in (tried from another ubuntu and a mac). The actions are fairly reproducible, for example vim some config files (though vim-ing other files works), cat some other file, etc. The freeze never happens if ufw is disabled. Any idea what's going on?
Thanks!
Cristian

Addition: if you're wondering, yes, I have TcpKeepAlive on yes and I doubt is related (it would happen with ufw disabled too)

---

