---
title: "how can I install the ipt_limit module?  (9.04 Server)"
date: 2010-01-15
forum: Server Platforms
---

### Post by guvnr on 2010-01-15
Troubleshooting this for a reader of my VPS blog who says ..



I had a slight problem with the iptables on my xensmart.co.uk vps. The following line caused an error:
 -A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
 It seems that the ipt_limit module isn't installed as part of Ubuntu 9.04 on xensmart.co.uk VPSes. For now, I've commented out that line. Is that a bad idea? If so, how can I install the ipt_limit module?


..


so I guess ipt_limit isn't kernelled.  Any ideas on how to rectify this safely please?

---

