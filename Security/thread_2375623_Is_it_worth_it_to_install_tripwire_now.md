---
title: "Is it worth it to install tripwire now?"
date: 2017-10-26
forum: Security
---

### Post by calby on 2017-10-26
Hi,
I have three servers running, I have harden the security, used fail2ban, ufw and done some other configs.
But now I'm wondering if I should install Tripwire, but.... the servers has been running for 1 week - I don't think that I have been hacked but I don't know either so is it worth it to install Tripwire or is it to late to do that now as the servers are in production already?

---

### Post by TheFu on 2017-10-26
yes, but it depends on the risks for a the server.  If it is internally facing, the risks are probably low.  If it runs php webapps on the internet, with cheap themes, that's a completely different story.

I'd restore a backup of the systems into local VMs, then compare all the files to similarly configured, freshly installed, VMs versions.  Do the signatures match?  Are any differences explainable?

---

