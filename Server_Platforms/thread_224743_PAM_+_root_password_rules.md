---
title: "PAM + root password rules"
date: 2006-07-28
forum: Server Platforms
---

### Post by vtec on 2006-07-28
I was setting up PAM to restrict passwords that are not secure enough. Requiring a length of 8 or more, one number, etc.... When root changes there password PAM will inform the user that it is no good, but then allow it anyway. I realize that anyone with root access could just change the PAM rules to get around this, but i would like to set up PAM to enforce its rules for the root user. Is this possible.

---

