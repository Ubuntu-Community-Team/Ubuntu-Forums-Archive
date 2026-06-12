---
title: "Set up a proxy for DAAP shares in rhythmbox?"
date: 2006-05-27
forum: Server Platforms
---

### Post by dude2425 on 2006-05-27
Here's the idea I want to try.

I want to make my computer into a proxy server. Somebody else from somewhere else on the internet would connect to my proxy server, and using iTunes, be able to browse my selection of music in Rhythmbox, as if they were on the local network with me.

My question to you, is how would this be done, if it were possible? Is there an easier way than setting up a proxy server?

---

### Post by d.code on 2006-05-30
I'm not that familiar with the DAAP protocol specifically, but the shares appear through use of mDNS (i.e. Bonjour).  You would have to be able to send this mDNS traffic to your desired remote subnet.  You can do this, I believe, with Avahi.  This particular setup would be more useful if say, you live in the dorms and your friend is on a different subnet or your friend has an apartment across town or state and you want to share your music.  Once you get the mDNS part of it right, it would just take port forwarding on your firewall/gateway, or if you are directly connected and have a public IP, ensure your firewall allows access.

I know it's not your answer, but it should get you moving in the right direction. ;)

---

