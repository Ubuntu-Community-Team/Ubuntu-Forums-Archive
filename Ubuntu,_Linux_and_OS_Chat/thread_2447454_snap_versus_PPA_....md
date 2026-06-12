---
title: "snap versus PPA ..."
date: 2020-07-19
forum: Ubuntu, Linux and OS Chat
---

### Post by shantiq on 2020-07-19
been using snap more and more of recent times ...    not fully understanding how it all works as little is shown in terminal when installing but the versions of software installed seem often more up to date than PPA versions [I may be wrong in saying that]   so asking folks in the know: what are the main differences between PPA and snap is one the past one the future; is one better than the other? any learned info on this appreciated

---

### Post by wildmanne39 on 2020-07-19
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by CatKiller on 2020-07-19
Snaps are intended to be an upgrade over PPAs, which were themselves intended to be an upgrade over adding random repositories to your sources.list. PPAs are not very discoverable, and could adversely affect the rest of your system; snaps, being sandboxed and being listed in the default package manager, improve on those aspects. That sandboxing creates some other issues, like the slow startup time and needing to set permissions for access into and out of the sandbox, compared to traditional packages. 

There is no guarantee that the snap version of particular software will be newer than the version in the standard repositories, although the snap infrastructure makes it possible: publishing a new snap to the snap store is much quicker than going through the Stable Release Update process (which is how we get new versions of browsers and so on), but someone needs to actually do so. If the snap is provided by the original developer as a normal distribution channel that's more likely to happen than if they're just dipping a toe, or if the snap was produced by a member of the community to scratch a particular itch.

You might find [this video](https://youtu.be/_XcoWKoubjE) gives you more information.

---

### Post by shantiq on 2020-07-19
Thank u will check video too

chat on snap starts at the 13:00 mark :)

&#9679;  ahh   sometimes it is just a deb inside a snap he says

---

### Post by MartyBuntu on 2020-07-19
I like the "idea" behind Snaps and Flatpaks...and I look forward to them maturing. What I'd like to see would be a clear delineation between what is installed via Snaps, via PPA's and via Ubuntu's own software repositories....like having a green or red dot beside the app's name in the Applications list, or using a different font. But mostly I'd like to stop grinding my teeth from reading hysterical anti-Snap/ anti-container posts on the internet...

---

### Post by shantiq on 2020-07-19
> **MartyBuntu said:**
> What I'd like to see would be a clear delineation between what is installed via Snaps, via PPA's and via Ubuntu's own software repositories....like having a green or red dot beside the app's name in the Applications list

+1  excellent idea

---

### Post by grahammechanical on 2020-07-19
Quoting from

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

> Repositories make it easy to  install new software, while also providing a high level of security,  since the software is thoroughly tested and built specifically for each  version of Ubuntu. 

> Packages in PPAs do not undergo the same process of validation as  packages in the main repositories. PPAs are a low-security alternative  to the main repositories, so the user will be installing software at  their own risk. 

Snap application security

[https://snapcraft.io/blog/where-eagles-snap-snap-security-overview](https://snapcraft.io/blog/where-eagles-snap-snap-security-overview)

> In this blog post, we would like to highlight several important security  mechanisms and features in the snap ecosystem, which should help you  understand how snaps work, what isolation systems and tools are in  place, and the process of publication of applications to the Snap Store.

To my mind the main advantage of snap over PPA for the user is trusted security. The snap creation process does allow the developer to update their software without going through the Ubuntu time consuming process of getting the update in Ubuntu's repositories. The PPA was another way of avoiding that process but the user has to decide if they trust the owner of the PPA.

Regards.

---

### Post by aaronrv2008 on 2020-09-27
> **CatKiller said:**
> Snaps are intended to be an upgrade over PPAs, which were themselves intended to be an upgrade over adding random repositories to your sources.list. PPAs are not very discoverable, and could adversely affect the rest of your system; snaps, being sandboxed and being listed in the default package manager, improve on those aspects. That sandboxing creates some other issues, like the slow startup time and needing to set permissions for access into and out of the sandbox, compared to traditional packages. 

There is no guarantee that the snap version of particular software will be newer than the version in the standard repositories, although the snap infrastructure makes it possible: publishing a new snap to the snap store is much quicker than going through the Stable Release Update process (which is how we get new versions of browsers and so on), but someone needs to actually do so. If the snap is provided by the original developer as a normal distribution channel that's more likely to happen than if they're just dipping a toe, or if the snap was produced by a member of the community to scratch a particular itch.

You might find [this video]("https://youtu.be/_XcoWKoubjE") gives you more information.

Snaps were originally created for the Ubuntu Phone. As the Ubuntu Phone has been discontinued, Canonical bought snaps to Desktop and Servers.

---

