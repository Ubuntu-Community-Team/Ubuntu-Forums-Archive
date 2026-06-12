---
title: "Poor F-Spot performance in 8.10: the problem of tying the applications to the OS"
date: 2008-12-15
forum: The Cafe
---

### Post by rmjb on 2008-12-15
When I started using Ubuntu full time on my personal PC with dapper it took me a while to realise and appreciate that my applications were "tied" to my OS version. In fact I installed many out of repo packages only to have to fight up with them when I upgraded to 6.10.

I happily use F-Spot for my photo management, but I find the version that was delivered in 8.10 is performing very slowly. Now I couldn't stay on a previous version, and I've been checking on F-Spot's website to see if they've updated past 0.5.0.3, but they haven't.

I'm thinking it might be better to just use non-repo programs that can stay when the OS and all it's apps are upgraded and I can upgrade those as needed. Because it will be very tedious to look at all the apps I use at each release to see if there were any degradations before deciding if to upgrade my OS every 6 months.

- rmjb

---

### Post by yogo on 2008-12-15
I found fspot to freeze on 8.04 and lower seems to be a well known bug, I removed fspot for this very reason.

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/292721](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/292721)

---

### Post by cardinals_fan on 2008-12-15
Poor F-Spot performance: the problem of buggy and bloated applications with little or no redeeming value ;)

---

### Post by bruce89 on 2008-12-15
How you can claim that 3rd party packages are better when so many peoples' upgrades have gone awry thanks to them is beyond me.

---

### Post by Polygon on 2008-12-15
its because how the packaging system works.....if you have a higher or equal version package installed , when the updater runs, it wont be able to install that package because it already exists, adn then all of the programs that depend on that dont get installed and it becomes a giant mess.

its better to just search for 'getdeb' and remove all package before upgrading. Then upgrade, then modify any package versions you need. or better yet, install from scratch. works every time =)

---

