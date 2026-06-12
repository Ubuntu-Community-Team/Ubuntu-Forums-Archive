---
title: "Troubleshooting Secondary DNS (bind) Fallback"
date: 2013-03-27
forum: Server Platforms
---

### Post by jlacroix on 2013-03-27
Hello everyone. I have a server in my home network running Ubuntu Server 12.04, and beyond the fact that it is my file server, it is also the DNS server for my network (bind). I know it's overkill for someone to have a bind server in their home network, but I do it because I'm learning this stuff.

Anyway, I notice lately that DNS resolving in the network is inconsistent. I'll notice that sometimes DNS won't resolve at all (I get a 404 while trying to browse a site, for example) and other times I can be watching a Youtube video that starts to load fast, but quickly dies and stops buffering completely. Basically, most of the time it will work, but other times it won't. I'm not sure what exactly changed, since this issue didn't start happening during any configuration changes or anything. The problem is much worse when my server is backing up to Crashplan (which happens between 12:30am to 6:30am).

My DNS server has DHCP as well. DHCP is configured to give all clients its address as the primary DNS, and the secondary DNS is my D-Link router. I'm curious not only why bind sometimes doesn't work, but I'm also curious why my clients don't fail over to my D-Link router if my main server is busy. I wouldn't think there would be a reason for a secondary DNS entry in a client if the client never has any intention of actually using it. (My clients mostly run Kubuntu).

I have been somewhat entertaining the idea that the problem could by my 24-port switch (unmanaged) but I see nothing concrete that would narrow it down to the switch and not bind on my server. But, my server doesn't ever have much traffic except for when Crashplan backs up at 12:30am.

Attached are my config files for bind from my server. Just looking for some opinions on what may cause an unreliable bind server, as well as the failure of a client to not fail over to secondary DNS despite setting a secondary DNS address.

---

