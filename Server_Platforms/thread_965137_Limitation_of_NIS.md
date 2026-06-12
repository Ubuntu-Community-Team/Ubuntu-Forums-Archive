---
title: "Limitation of NIS"
date: 2008-10-31
forum: Server Platforms
---

### Post by chrislynch8 on 2008-10-31
Hello,

With NIS are there any limits to the number of Users and Groups it can handle to make it database file.

I created my databases today after adding new users and groups to the networks and I got the following warnings

[B]Update group.byname.....
makedbm: warning: data too long:[/B] It then lists all the groups

[B]Update group.bygid.....
makedbm: warning: data too long:[/B] It then lists all the groups

Is there a setting to just a max number of groups/users or is it a set value.

**_Updated below_**

**I looked into this a bit more and found that the issue is I have too many users in one group. I have a group for all users that I use for allowing access to general folders that contain update, manuals etc. But I have over 60 users so far and I will have a total of 230 users and I want all of them of belong of an "all" group. I read that in /etc/groups one line can only contain 1024 characters - is there any workaround?????**

Rgds
Chris

---

### Post by KennedyM on 2008-10-31
Chris

As you mentioned, it seems there's a limit to the length of a line in /etc/group. Maybe 255; maybe 1024 (I don't know).

A NIS howto at: [http://www.spack.org/wiki/UsingNis](http://www.spack.org/wiki/UsingNis) states that the "only" solution is to manually create multiple "groups" in the /etc/group file, with different names (perhaps with the same generic name, and a numeric suffix), but with the same GID. Leave significant free space in the FIRST of these, to facilitate "normal" new additions.

  - Mike

---

### Post by chrislynch8 on 2008-11-03
Thanks Michael,

That worked a treat

Rgds

---

