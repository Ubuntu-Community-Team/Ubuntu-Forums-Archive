---
title: "Old gateway to new gateway"
date: 2009-01-27
forum: Server Platforms
---

### Post by JeppeM on 2009-01-27
Hey guys,

I know that this isn't directly ubuntu related, but this is by far the best linux-forum i know...

Now, the issue is that we have an old fedora gateway which the guy who came before me has set up... Basically it's rather unstable, and i'd like to get it up and working correctly... The server has the following things to take care of:

- DHCP of 3 different subnets
- IPtables which redirects incoming requests on some different ports to different servers inside the different subnets
- OpenVPN server to give some of the staff access to the subnets and their servers from home
- DNS service (we get the gateway server as the primary DNS server when asking for the DHCP information) - Not exactly sure how this works, but am i wrong if i say that it's the named service?

I think thats it.. Now, my question is, if it would be worth the trouble to try and move this to a pfsense platform, which i heard is really great for firewall/gateway stuff? And how long would you think it would take? 

I think that I'll do it by installing a new harddisk in the server, and setting it up on there. That way, i still have the old disk in case it messes up and we need to get up again asap - Is this is good way of doing it?

We did think about using ubuntu for the gateway, but from what i've heard, pfsense is better since it's build specially for that kind of task, and i guess that it's not that hard to set pfsense up, we are used to dealing with ubuntu servers on just the commandline...

---

