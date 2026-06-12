---
title: "adding a user to a group does not take effect until next login !!!"
date: 2007-08-15
forum: Server Platforms
---

### Post by m_alnaanah on 2007-08-15
When I add a user to a group it does not take effect until the user logout and then login.

Is this the general case in UNIX and Linux system.

and can I change it to be applied instantly.


With all my thanks.

---

### Post by rickyjones on 2007-08-15
I believe that this is normal. Group memberships are not dynamic in any operating system that I've used. I'll use an example from Windows because I am more familiar with it. When you log in a profile of all your group permissions is created and is used throughout your session. New group permissions can't show up until that profile is recreated on login.

I'm thinking that Unix/Linux works along a similar idea. As far as I can tell there is no way to change that behavior. Perhaps someone with more experience in the field can fill in my blanks though. :)

-Richard

---

### Post by Bachstelze on 2007-08-15
> **m_alnaanah said:**
> Is this the general case in UNIX and Linux system.

Yes.

> **m_alnaanah said:**
> and can I change it to be applied instantly.

No.

---

### Post by m_alnaanah on 2007-08-16
Thanks alot for your reply.


I thought it's some kind of bugs :confused:. So thanks for the information. :)

---

