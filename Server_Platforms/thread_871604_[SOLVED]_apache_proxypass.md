---
title: "[SOLVED] apache proxypass ?"
date: 2008-07-27
forum: Server Platforms
---

### Post by tossable001 on 2008-07-27
I followed the citadel guide for citadel with apache that said to use proxy pass to redirect to the web interface of citadel and hit a snag. I did some looking and found I needed to edit my proxy.conf, no problem. My issue is the only way I have access is with the "allow" parameter set to "all", which it states in the bottom of the config is a no-no. Can any one explain how/why this is a no-no or suggest usable setting? If you would like any more info just let my know.

Thanks

---

### Post by amenszer on 2008-07-29
Only a no-no if you have ProxyRequests turned on.

Comments from my config file:
#turning ProxyRequests on and allowing proxying from all may allow
#spammers to use your proxy to send email.

---

### Post by tossable001 on 2008-07-30
Thanks, I should have seen that, it was a late night.

---

