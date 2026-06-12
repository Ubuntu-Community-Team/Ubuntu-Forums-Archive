---
title: "Unable to add users/permissions VMware server 2.0.2"
date: 2010-02-23
forum: Virtualisation
---

### Post by leachyboy2001 on 2010-02-23
Just did a fresh install of vmware server 2.0.2 using the necessary patches for the new kernel 2.6.31-20.

Install went fine, everything built correctly during config.
When it asked for an admin user I tried using my user account which is simply u It told me this account was not acceptable, blah blah blah. So I used root.  Finished the install and enabled the root account so I could log in and set a different user as an admin and disable root again.  

When I attempt to add another user it gives an error message 
RuntimeFault: Database temporarily unavailable or has network problems.
I will get this error for any user I try to add.  Groups do add, but do allow the members to log in.

If you need info please let me know, I'm sure I'm leaving something important out.

---

### Post by dcstar on 2010-02-24
> **leachyboy2001 said:**
> Just did a fresh install of vmware server 2.0.2 using the necessary patches for the new kernel 2.6.31-20.

Install went fine, everything built correctly during config.
When it asked for an admin user I tried using my user account which is simply u It told me this account was not acceptable, blah blah blah. So I used root.  Finished the install and enabled the root account so I could log in and set a different user as an admin and disable root again.  

When I attempt to add another user it gives an error message 
RuntimeFault: Database temporarily unavailable or has network problems.
I will get this error for any user I try to add.  Groups do add, but do allow the members to log in.

If you need info please let me know, I'm sure I'm leaving something important out.

Use sudo next time, do not directly use the root account.

---

### Post by leachyboy2001 on 2010-02-25
I assume you mean install vmware using using sudo? This is what I did.

---

