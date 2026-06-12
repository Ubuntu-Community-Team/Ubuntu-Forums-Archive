---
title: "a word about containment"
date: 2012-10-29
forum: The Cafe
---

### Post by mike acker on 2012-10-29
I'm learning to use AppArmor

AppArmor provides "containment" i.e. it can restrict an application's access to only those areas that you allow

for example, I can restrict Firefox to access /documents area only

but this is only good as far as it goes: if I do a "save page complete" and then move that set to another area or -- open it with another similar app  -- i can lose my AppArmor protection

e.g. suppose i move a web page set into a shared directory and another user picks it up using an unprotected copy of e.g. Chrome :evil:

in my reading this morning i noticed Win8 is moving in this direction as well

---

