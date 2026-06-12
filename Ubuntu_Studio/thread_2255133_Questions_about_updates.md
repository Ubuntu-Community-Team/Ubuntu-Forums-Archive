---
title: "Questions about updates"
date: 2014-12-02
forum: Ubuntu Studio
---

### Post by Mike_Bourgeault on 2014-12-02
So I've been using Ubuntu studio for a little while now, and am getting comfortable in it (it my first real foray into lunux).

My question is when it updates, does it also update the applications that are packaged with it?

My main area of interest is Ardour. If the automatic updating doesnt update it, what is the best way to manually do it?

---

### Post by ian-weisser on 2014-12-02
> **Mike_Bourgeault said:**
>  when it updates, does it also update the applications that are packaged with it?

Ardour is in Ubuntu's 'universe' repository.
Universe contains software that is "[c]ommunity maintained software, i.e. not officially supported software." ([source]("https://help.ubuntu.com/community/Repositories/Ubuntu"))

There are two types of updates:
1) Security patches and critical bugfixes. These updates occur after a release of Ubuntu. Most of your updates are these. Ubuntu provides updates for packages in the Main and Restricted repositories (not Universe). 

2) New upstream releases. These occur *before* a new release of Ubuntu, not after. The current version of Ardour in Ubuntu 14.04 and 14.10 is 2.8.16. If Ardour releases a new version 3.0 today, Ubuntu will add it to the next release (15.04). Ubuntu won't backport the new release to 12.04, 14.04, or 14.10. Community members can (and do) create these backports, but they are not automatic. Generally, if you want the latest release, use a new version of Ubuntu.
 
So the short answer to your question is:
Yes, many applications will be updates along with the rest of your system automatically...
but no, Ardour is not one of those applications.


Best way to update Ardour depends on many factors.
If there is an active user community, the group can maintain an up-to-date PPA. You system can update Ardour from that.
If Ardour maintains it's own upstream repository, your system can update Ardour from that.
(Warning: Non-Ubuntu PPAs and Repositories may be risky. Some people have broken their systems, others have been just fine.)
Lacking any other useful option, you can always install without using packages from Ardour.org...though that is not recommended for beginners.
(Warning: Installing without using a package manager has a learning curve,and may be risky. Might damage your system, might not.)

---

