---
title: "Why is UPG halfway implemented?"
date: 2009-12-15
forum: Security
---

### Post by Brian Vaughan on 2009-12-15
I just came across a description of user-private groups (UPGs) in *Essential System Administration* by Aeleen Frisch, p. 230. It puzzles me, because the implication is that Ubuntu halfway implements this concept, and I'm curious why Ubuntu goes halfway, instead of adhering to Unix conventions or going all the way with the UPG concept.

As explained, the traditional Unix practice is for regular users to be assigned a default group such as "users", and the default umask for regular users is 022. But on Red Hat, the UPG convention is to have each user assigned a unique default group, with the same name as the user, and the default umask is 002. This means that by default, files created by a user will have read and write access for all members of the group, but since the default group is identical with the user, this is harmless. The point is to allow for creating groups for users to share files, in directories with the set guid bit on, which would mean files created in or copied to that directory would inherit the group ID and be writable by members of the group.

The odd thing is that in Ubuntu, the default group is identical with the user, as in the UPG scheme, but the default umask is 022, not 002.

This caught my attention, because some time ago, following a suggestion, I'd created a "shared" group for members of my family to share files in a directory owned by "shared," with the set guid bit on. This hasn't proven to be particularly useful, partly because changing the permissions on each file is a nuisance, and with a umask of 022, most files are readable by everyone anyway. I'd thought of changing the default umask to 002, but I thought there might be odd side effects, and it seemed like too much hassle in any case. It still does.

So, I'm asking why Ubuntu is set up this way, out of curiousity.

---

