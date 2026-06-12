---
title: "Ubuntu Server Release Confusion"
date: 2005-12-21
forum: Server Platforms
---

### Post by fdamstra on 2005-12-21
I read [an article]("http://arstechnica.com/news.ars/post/20051215-5777.html") (which got a lot of press) about the first release of Ubuntu Server.  The [announcement]("http://lists.ubuntu.com/archives/ubuntu-announce/2005-December/000047.html") reads like this is an official release, and I love [the specs]("https://wiki.ubuntu.com/ServerCandy").

But doing more research, it reads like the specs are more of a plan than specs of the release.  I can't find a reference to the server release on the Ubuntu main page.  The wiki docs are incomplete at best.  

My main concern is security updates.  Once I have a server doing its job well, my only concern is that it continues to do so without becoming a honeypot.  Windows does this very well.  Gentoo wants to update glibc whenever there's a new stable release.  FreeBSD wants me to rebuild the world whenever BIND releases a security release.  RedHat wants my money, and CentOS wants me to wait.  Debian seems 3 years out of date.  Ubuntu Server appears to want to make my life easy, but 18 months of security updates doesn't even come close to satisfactory.

So, here's the **first question: Is the currently downloadable Ubuntu Server release to be supported for 5 years?**  It's in the spec, but I can't find an answer to it.

So we move to docs.  Gentoo is truly fantastic at support, especially considering it is community-based.  There is documentation (or at least well-written how-to's) on everything you might want to do.  I've rarely run into a problem that wasn't solved in the Gentoo Forums through helpful, friendly advice.  But browsing through the Ubuntu forums reveals mainly unanswered questions, unresolved problems, and worse, a lot of frustration.  

Perhaps I'm just new to Ubuntu and don't know how to find the support I'm looking for, so **question #2: When problems arise, is the Ubuntu community knowledgable enough and responsive enough to assist in solving them in a server environment?**

I love that the specs call for built-in revision control in /etc.  I love that Ubuntu provides a lot of flexibility in what packages to install.  I love that Ubuntu is listed under the VMWare 5 list of linux installs.  Hell, I want everything that's listed in the specs.  But is it there?

While questions one and two (above) are most important, I'll conclude with a couple more general questions:
[LIST]
[*]Is Ubuntu suited for an enterprise environment that demands 0-2 hours downtime per month?
[*]Can "Joe Sysadmin" keep an Ubuntu server secure from hackers and worms without requiring them to know that /etc/fstab should probably not be overwritten by an update, but /etc/mime.types probably should?
[*]And lastly, what happens to the machine in 18 months when this release is no longer supported?  18 months is absurdly short, even for a desktop OS (didn't Win98 go out of support in March, 6 years after it's release?  Aren't most corporations running Windows 2000 on their servers still?  And I bet you could throw a baseball out your window and find a company that still had an NT 4.0 server).
[/LIST]

---

### Post by nick0danger on 2005-12-22
As far as using Ubuntu, for a server enviroment, i can not comment on uptime, but i do contract work for an Oil and Gas, company in alberta, and that is what they provide there user that do not need windows but are unable to choose what Distro of linux they want to use.  (The company lets people choose there linux distro)  Not a totally Windows free enviroment but it is close. (over 2000 users to)  And we have no problems with Crashs at all it is super stable.

Not sure about the joe blow admin being able to keep it secure, cause my impression of joe blow admin where im from dont change default password on routers.

And they say a Distro of Ubuntu is supported for 18 months, but they typically want you to upgrade you install though apt get to the latest version.  We use suse at work, and they have a 4 year support deal.

---

### Post by MikeN on 2005-12-24
These are exactly the points I'm wondering about too. If some Ubuntu devver could give some feedback on this that would be nice :)

---

