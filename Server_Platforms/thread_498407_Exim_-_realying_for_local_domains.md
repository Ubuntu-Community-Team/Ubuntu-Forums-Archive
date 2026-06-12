---
title: "Exim - realying for local domains"
date: 2007-07-11
forum: Server Platforms
---

### Post by Rich99 on 2007-07-11
Just a quick qestion to make sure I haven't made a mistake.  Under my old debian server, if exim was set to 'internet' in update-exim4.conf.conf, then exim relayed for local machines - i.e. machines on the same subnet as the server.

I've just set up dapper drake & am using exim again.  update-exim4.conf.conf is set as 'internet', but otherwise is blank.  The only changes I've made to exim4.conf.template are to enable TLS and uncomment the login & plain auth server sections.

Exim works fine if I login with TLS to send email, but wil not relay for even local machines otherwise.  This is actually the bahaviour I want, but I was a little surprised since I presumed that it would relay for local machines by default.

Have I done anything wrong?

---

### Post by Rich99 on 2007-07-11
Ignore me, just realised my memory's failing me.  There is no problem :)  How do you delete posts?

---

