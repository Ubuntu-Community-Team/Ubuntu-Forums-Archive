---
title: "A patch that is a must for me"
date: 2007-01-08
forum: Ubuntu System Panel
---

### Post by ADRez on 2007-01-08
First of all, thanks chanders for the great work you've done!

I think this patch makes usp more accesible (applications.py):

Line 289: CategoryButton.connect( "enter_notify_event", self.Filter, "" )
Line 305: CategoryButton.connect( "enter_notify_event", self.Filter, child.name )

Could it be added as an option to choose if you like the default behaviour or this one?

---

### Post by chanders on 2007-01-08
No problem ;-)

---

