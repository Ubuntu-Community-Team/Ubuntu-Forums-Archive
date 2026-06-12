---
title: "Proxy: limit by rquested address"
date: 2006-02-24
forum: Server Platforms
---

### Post by kharyett on 2006-02-24
We are looking at putting in a proxy server at our office. I have been looking closely at squid. It seems to meet our needs, but I can't seem to find out if we can set iy up to allow access only to addresses we define.

For example, we want to limit web browsing, ftp, ssh, and other traffic to a few domains:
domain1.com
domain2.com
xyz.domain3.com

Is this possible with squid? or is there another proxy that will allow us to do this? Is there a Howto on doing this, I have searched almost all threads here on Proxy or Squid and not found anything relevant. I have looked at the squid-cache site as well without seeing anything that states I can do this.

---

### Post by Glut on 2006-02-26
Dan's Guardian: [http://dansguardian.org](http://dansguardian.org) can work in whitelist mode. It can work in conjunction with squid.

---

