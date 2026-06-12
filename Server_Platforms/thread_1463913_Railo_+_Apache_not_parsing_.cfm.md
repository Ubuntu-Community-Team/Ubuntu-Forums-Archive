---
title: "Railo + Apache not parsing .cfm"
date: 2010-04-27
forum: Server Platforms
---

### Post by xkaliburx on 2010-04-27
Didn't compile, but rather installed apache via apt and railo (railo-3.1.2.001-railo-express-with-jre) binary and installed.  I setup the site the same way my cf8 servers are set (so yes the /admin/web,cfm works and parses fine), but on a railo and apache clean start, it (apache) doesn't seem to be sending the .cfm traffic to ralio.  I made a test.cfm page with nothing more than;
<cfdump var="#cgi#" />

and on a page load I got;
<cfdump var="#cgi#" />

So... basically it's not saying, "Oh, your a .cfm, you goto railo". I am not sure if I should start on the apache side, etc. so anyone running this environment, any help is appreciated.  This is running U9.10-server 64 bit.

Not sure what else I can / should provide, but that will be enough for me to send and clear my head a bit!

Thanks.

---

