---
title: "Disable listing of user accounts in &quot;Switch From&quot;"
date: 2010-05-12
forum: Security
---

### Post by ampermc on 2010-05-12
Once again, nobody seems to understand security properly when they decide to add nifty new features. After upgrading to 10.04 from 9.10, I now have a listing of all the user accounts under "Switch from" when I go the the logout menu at the upper right side of the task bar. 

This is a terrible security hole that should never have been allowed in the first place, and is just as annoying as the default behavior of listing all the user accounts on the login screen.

How do we get rid of this?

---

### Post by sisco311 on 2010-05-12
> **ampermc said:**
> 
This is a terrible security hole that should never have been allowed in the first place, and is just as annoying as the default behavior of listing all the user accounts on the login screen.


No, it's not. /etc/passwd is world readable.

---

### Post by ampermc on 2010-05-12
All that proves is that /etc/passwd shouldn't contain that information, either.

---

### Post by cdenley on 2010-05-12
> **ampermc said:**
> All that proves is that /etc/passwd shouldn't contain that information, either.

If you don't like the way unix and linux store user passwords, then perhaps you should design your own OS. That is a very basic component of linux, and there is no way to change this specifically for ubuntu. It has been that way for years, and it hasn't been a problem.

---

### Post by OpSecShellshock on 2010-05-12
What risk does a list of users create that isn't already present for anyone with physical access in the first place?

---

### Post by cdenley on 2010-05-12
> **OpSecShellshock said:**
> What risk does a list of users create that isn't already present for anyone with physical access in the first place?

I agree. I can think of situations where it would be less than desirable to allow users to view all local usernames, but not with a typical desktop. When granting local access to any user, you are placing serious trust in that user, and when you allow physical access, usernames being viewed are the least of your concerns.

---

