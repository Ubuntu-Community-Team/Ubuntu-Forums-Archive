---
title: "forcing password authentication in sudo"
date: 2008-11-24
forum: Security
---

### Post by sulekha on 2008-11-24
Hi all,

The following is what i have read in the book "Linux security cookbook"

published by O Reilly

forcing password authentication in sudo

problem

you want sudo always to prompt for a password

Solution:-

When controlled by superuser:

/etc/sudoers
Defaults timestamp_timeout = 0 systemwide
Defaults:smith timestamp_timeout=0 per sudo user


but i didn't find any of the above lines in my /etc/sudoers file ?

NB:- I use ubuntu 8.04.1

---

### Post by __Ryan__ on 2008-11-24
You should be fine to add those lines. You will never see every configuration option that is available.

You can run the following command in a terminal to get more information on all options available to /etc/sudoers.

```
man sudoers
```

---

### Post by etdsbastar on 2008-11-25
Here is the step by step process as I did it:

1. Make the permission of /etc/sudoers file to Read and Write Mode in all (for user and group too).

2. Open it by double-clicking it.

3. Add/Edit the following lines as : 

> root    ALL=(ALL) SETENV: ALL
%(specify current users group here without braces)        ALL=(ALL) SETENV: ALL
%adm        ALL=(ALL) SETENV: ALL
%admin     ALL=(ALL) SETENV: ALL

4. Save and close.
5. Reset the permissions of /etc/sudoers to read only mode.


I hope this works.

---

