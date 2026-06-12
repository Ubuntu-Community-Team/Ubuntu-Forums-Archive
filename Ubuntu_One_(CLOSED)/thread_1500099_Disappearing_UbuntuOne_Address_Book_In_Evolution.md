---
title: "Disappearing UbuntuOne Address Book In Evolution"
date: 2010-06-02
forum: Ubuntu One (CLOSED)
---

### Post by Samizdata on 2010-06-02
Recently my UbuntuOne address book in Evolution seems to have disappeared on my netbook.  I have been researching how to restore it, and even stopping by the IRC channel to boot, but to no avail.

My primary concern is not how to create a new address book, but how to recreate the specific one with the UbuntuOne linkage.

Any suggestions?

---

### Post by Samizdata on 2010-06-06
Found the answer via experimentation.

I am not exactly sure how it happened, but evolution-couchdb somehow went missing.  Restored that and upgraded to the latest Evolution via a PPA (ppa:jacob/evo230) and all seems to be well now.

Well, it would be if they ever get U1 sync working again. (grins)

---

### Post by duanedesign on 2010-06-07
Glad you got it sorted. The sync speed problem seems to be getting better so hopefully we will see couchdb replication start back up any time now.

---

