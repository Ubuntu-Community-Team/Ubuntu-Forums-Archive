---
title: "apache 503.9 code"
date: 2007-10-11
forum: Server Platforms
---

### Post by kansha on 2007-10-11
Hello folks,

I could not find specific information about how apache handles the too many users error, in order to redirect to a page. Only 403 is said to be handled, not any of the sub-errors as IIS does.

I can not test it right now, but can I blindly use the 403.9 as below?

ErrorDocument 403.9 /toomany.html


Thanks in advance.

---

