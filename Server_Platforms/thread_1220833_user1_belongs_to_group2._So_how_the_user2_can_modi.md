---
title: "user1 belongs to group2. So how the user2 can modify files of user1?"
date: 2009-07-23
forum: Server Platforms
---

### Post by PryGuy on 2009-07-23
Okay people, I'm getting rusty.
Please explain me that or I'll go crazy.

Let's say I have Samba with two users, jack and nick. I set 'create mask = 664' and 'directory mask = 775' so group members could read/modify the files/dirs made by other group members.

I add jack to the group nick, so jack could read nick's files. Now jack is fine to read/modify nick's files, but why does that mean that nick can now read/modify jack's files, 'cause I didn't add him to the jack's group?

Thank you in advance and sorry for the stupid question...

---

