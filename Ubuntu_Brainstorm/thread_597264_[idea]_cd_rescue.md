---
title: "[idea] cd rescue"
date: 2007-10-30
forum: Ubuntu Brainstorm
---

### Post by foerdi on 2007-10-30
when user is mounting a defect (defect sectors) cd ubuntu should automatically ask him if he wants to repair/rescue it and burn it "clean" on a new cd

needed package: cdrecord
commands:
1. readcd -noerror dev=/dev/whatever retries=250 f=cd.iso
2. messagebox: insert a blank cd
3. cdrecord dev=/dev/whatever -data cd.iso

is this also possible with dvds?

---

