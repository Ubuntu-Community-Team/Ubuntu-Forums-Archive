---
title: "Question for Curtin Syntax"
date: 2016-07-26
forum: Ubuntu Cloud and Juju
---

### Post by braven36 on 2016-07-26
Below is the example from this document,  "https://maas.ubuntu.com/docs/development/preseeds.html"  The first line uses "," but the next line does not.  Is that just a typo?   Also is this the correct forum to post this question?


late_commands:
  add_repo: ["curtin", "in-target", "--", "add-apt-repository", "-y", "ppa:my/ppa"]   <-- line with ","
  custom: curtin in-target -- sh -c "/bin/echo -en 'Installed {{node.system_id}}' > /tmp/maas_system_id" <--line without.

---

