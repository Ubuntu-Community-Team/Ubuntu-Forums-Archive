---
title: "Sources.list updater"
date: 2006-10-16
forum: The Cafe
---

### Post by davedean on 2006-10-16
Hi,

I've put together what may or may not be a waste of time .. It's a sources.list tracker. I'm just looking for feedback on whether to continue working on it, or whether it's just me that is interested :)

[http://cub1cle.com/projects/ubuntusources/](http://cub1cle.com/projects/ubuntusources/)

Currently it's all read-only, but I'll be adding user accounts and the rest at some point. The idea is that:

'sources' are known repositories, and are given a unique identifier. 'Users' then combine these 'sources' into 'metasources'. A sources.list is generated from the metasources that a user is tracking.

This way, if the repository for an application moves, and someone out there updates their sources.list, rather than everyone hunting around for the new list, you just run your sources updater.

(you can also see other people's sources.list, and could track their sources.list file, rather than making your own. Let's say you know someone who is running a similar setup, well just track their sources and benefit from their work. ).

Currently the only user on there is myself, and the only sources available are the ones I use - which might be boring, but it's a Proof of Concept for the moment.

If it sounds useful/foolish, let me know so I know whether to sink any more time.

(The auto-updater script requires sudo and only writes to the current directory - this is intentional, as I dont want people burning their systems out whilst testing)

Good idea, or wretched waste of time?

---

