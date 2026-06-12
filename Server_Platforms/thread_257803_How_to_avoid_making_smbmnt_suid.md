---
title: "How to avoid making smbmnt suid?"
date: 2006-09-15
forum: Server Platforms
---

### Post by ihristov on 2006-09-15
Is there a way to avoid having smbmnt SUID?

What are the security implications of having it suid? I am familiar with what suid does. Are there any known vulnerabilities that can be exploited this way? Would they be only local?

Background: I installed FreeNX on my XUbuntu today and all works fine, but when I shared a folder via smb and logged into the box NX told me that I need to have smbmnt suid for the sharing to work. After I did so it does work.

Any thoughts are welcome.

---

