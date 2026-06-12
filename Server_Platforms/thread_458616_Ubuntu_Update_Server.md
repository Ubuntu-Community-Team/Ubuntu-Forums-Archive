---
title: "Ubuntu Update Server"
date: 2007-05-29
forum: Server Platforms
---

### Post by Rossow on 2007-05-29
Hi all, First poster alert!

What i'm trying to do is setup a local Ubuntu Update Server. I've got my local repository setup and the clients have their sources.list all configured correcty. BUT what i now need is some way of managing which updates the clients get.

I'll want all security updates to be allowed obviously but I want to be able to control which other updates go out.

Is there some sort of package management tool out there that can "Authorise" an update before it gets Pushed to all the clients.??  Kind of like the Red Hat Network does for Red Hat updates??

I been looking around for a while but only found a half completed document. :(
Any help would be greatly appreciated.


cheers
Nick

---

### Post by craigp84 on 2007-05-30
Hi Nick,

There's nothing pre-baked for this kind of thing. You just have to roll your own with ubuntu for now.

See apt-proxy which gets you 25% of the way there.

There are a few gotchas with ubuntu updates on a large scale currently. Some updates require manual intervention (a debconf prompt typically). You need to arrange to update the debconf databases on the recieving boxes with the answers before they do an apt-get update. See debconf-utils package. You create a selections file then roll that out to each box first.

-c

---

