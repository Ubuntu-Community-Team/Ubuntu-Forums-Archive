---
title: "Are All Official Kernel Images Maintained?"
date: 2011-05-24
forum: Security
---

### Post by excoriator on 2011-05-24
After installing 10.04 LTS, the kernel installed was 2.6.32-28. I have some modules from a vendor that were compiled for 2.6.32-24 so I used apt install 2.6.32-24 and started using the earlier kernel. Since the 2.6.32-24 kernel image is available from the LTS repository, can I assume it is kept up to date with the security fixes for known vulnerabilities? 

If so, where can I find documentation on this?

Are there any security benefits to using the newer kernel?

Thanks in advance for your help.

-Corey

---

### Post by mikewhatever on 2011-05-24
No, I don't think so. While the older images are available and can be used, only the latest ones incorporate all the fixes.

---

### Post by excoriator on 2011-05-24
Any ideas on where I can find the official policies on this?

---

### Post by mikewhatever on 2011-05-25
None. I am really bad with bureaucracy, but here is the way it seems to work. The kernel version in Lucid is 2.6.32-xxx, where xxx are increments that get bumped with updates. For example, the current generic version in Lucid is 2.6.32-31.61, but 2.6.32-32.62 is on the way, and has been in the proposed repository for some time now.
You can see the changes here -> [http://www.ubuntuupdates.org/packages/show/199704](http://www.ubuntuupdates.org/packages/show/199704)

---

### Post by excoriator on 2011-05-25
Thanks for your help. I'll post if I find any solid documentation.

---

