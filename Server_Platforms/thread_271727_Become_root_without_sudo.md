---
title: "Become root without sudo"
date: 2006-10-05
forum: Server Platforms
---

### Post by eirirlar on 2006-10-05
Hi all,

I've done the following:

sudo -i
moduser -G p4users username1
moduser -G p4users username2
cat /etc/group

To my surprise username1 and username2 had it's username deleted from all other groups. End of day, so frantic search after a decent /etc/group file to copy the contents of. Didn't find any, went home from work, came back today. ssh session interrupted by router because of no keepalive.

ssh username1@hostname
sudo -i
  "username1 is not in the sudoers file.  This incident will be reported."
ehh.... su -
  "su: Authentication failure"

[Pause for spiteful laugh]

I should have this fixed today, so I'm looking for solutions to become root or fix the group file so I can sudo, all via ssh.

Of course, when I get physical access to the box I can boot with a Knoppix cd and edit the group file, but again, should have it fixed now if possible.

Ideas? Thanks :)

Eirik

---

### Post by eirirlar on 2006-10-05
Yeah, I forgot to say this: because I ran the moduser twice, the /etc/group- is of no value :(

---

