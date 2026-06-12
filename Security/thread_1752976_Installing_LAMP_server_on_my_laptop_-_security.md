---
title: "Installing LAMP server on my laptop - security"
date: 2011-05-08
forum: Security
---

### Post by Jimbo999 on 2011-05-08
I'm concerned about security of having a LAMP server on my laptop as having any server makes the system less secure. However, if I were to create a new partition and install a lamp server on that and only use it when offline, would the security of my main partition be affected at all?

Thanks.

---

### Post by Jimbo999 on 2011-05-08
I'm also considering installing the LAMP server on virtual box. Which is more secure?

---

### Post by iavor on 2011-05-08
> **Jimbo999 said:**
> I'm also considering installing the LAMP server on virtual box. Which is more secure?

Virtual box would be the best way... sandboxed ftw :)

---

### Post by bodhi.zazen on 2011-05-08
> **Jimbo999 said:**
> I'm concerned about security of having a LAMP server on my laptop as having any server makes the system less secure. However, if I were to create a new partition and install a lamp server on that and only use it when offline, would the security of my main partition be affected at all?

Thanks.

Just bind apache to localhost and firewall external connections and you will be fine.

apache is no more or less secure in VBox, but it is sandboxed, and you can use host only networking.

---

