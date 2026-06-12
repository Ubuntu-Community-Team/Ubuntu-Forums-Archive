---
title: "Creating a secure guest user (for remote ssh)"
date: 2007-02-20
forum: Server Platforms
---

### Post by dudinatrix on 2007-02-20
A third party software vendor has recently requested a login to our server to have a peek in order to troubleshoot their software. I'm going to create a temporary user for them to shell in with. Are there any specific steps I should take to make sure their login is secure?

So far I'm thinking just putting them inside the "users" group only, and changing their bash_history to append only. (chattr +a ~username/.bash_history)

I'd also like to monitor everything this user is doing, what's the best way to do this?

Thanks in advance!

---

### Post by ViRMiN on 2007-02-20
One thing I was thinking about a while ago was setting up a separate host for third party users, and then NFS mounting specific directories, with them setup on the main server as read only... you could go a step further and jail their account so that they only have access to specific command too?

Just two pennies :)

---

