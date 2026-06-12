---
title: "Update question"
date: 2010-02-22
forum: System76 Support
---

### Post by brusegadi on 2010-02-22
Hello all,  If I change the Ubuntu update download location in software sources from &quot;Main Server&quot; to some mirror, do I interfere with any updates from system76?  Thanks,  B

---

### Post by mikewhatever on 2010-02-22
The main server doesn't belong to system76, so no, changing it should not interfere, unless system76 has its own repositories in your sources list. Anyhow, you can back up the sources list just to be on the safe side.

sudo cp /etc/apt/sources.list /etc/apt/sources.list-backup

---

