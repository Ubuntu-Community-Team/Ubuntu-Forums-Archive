---
title: "Weird problems with evolution-ubuntu one contact sync on Lucid"
date: 2010-10-25
forum: Ubuntu One (CLOSED)
---

### Post by NHclimber on 2010-10-25
After finally getting contact sync to work on Lucid, I'm still experience some weird problems.

1.   Often I can't delete a contact stored in the Ubuntu One address book  from within evolution.  If I rename the contact, then I can delete it.   Reported as  Launchpad bug# 666404.
2.  If I rename a contact then  delete it (again from within evolution), sometimes the formerly deleted  contact reappears shortly thereafter (before a replication to the server  has happened). This also happens when I attempt to delete a duplicate  contact, get an error, try to delete its match instead, get an error,  then go back to the first contact and delete it, which seems to delete  it - but then it reappears.
3.  After forcing a shutdown (evolution  --force-shutdown), the next time I start evolution, the contacts pane is  blank (resumably because there was some problem restarting the data  server).  If I restart evolution again, the contacts pane has data  again.

Is anyone else experiencing similar problems (or have others given up on using contact sync with Ubuntu One on Lucid)?

---

