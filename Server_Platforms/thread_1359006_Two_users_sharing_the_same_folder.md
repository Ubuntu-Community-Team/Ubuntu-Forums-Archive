---
title: "Two users sharing the same folder"
date: 2009-12-19
forum: Server Platforms
---

### Post by DoRullings on 2009-12-19
Hi

I have search a lot for this without finding a solution that I'm comfortable with:

I'm running a Ubuntu server 9.09 with Samba installed. My girlfriend and I have one account each with the respective home directory. Now I want another directory which we both can access and share were we both have read and write access.

If anybody would be so kind to tell me how this should be done properly I would appriciate very much. 

Thanks,
Thomas

---

### Post by BkkBonanza on 2009-12-19
Add a new group name that both of you are members of. Then create a directory which has group rw permissions for that name. Only members of that group (you and gf) will be able to r/w there.

---

### Post by DoRullings on 2009-12-20
Thanks BkkBonaza

It worked great, but I also had to add the folder to the samba config file.

Thomas

---

