---
title: "SSH server hub"
date: 2012-07-26
forum: Server Platforms
---

### Post by Sout on 2012-07-26
Hi,

I need some help pointing me in the right direction.

I have a couple of users that needs to access a couple of ubuntu servers. The problem is not all of them need to have access to all the servers.

I was thinking of allowing them to login to a centralized hub server and from their allow or restrict access for users to ssh to other servers. I would like to have centralized management of user access.

What do I need to look at to make this possible?

---

### Post by Lars Noodén on 2012-07-26
You can grant or restrict access on specific servers by setting [font=Courier New]AllowGroups[/font] or [font=Courier New]DenyGroups[/font] in [sshd_config](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html).  Then access would be granted depending on whether or not they are in a specific group.

---

