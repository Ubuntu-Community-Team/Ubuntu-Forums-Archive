---
title: "How to Disable User Creation"
date: 2009-11-04
forum: Security
---

### Post by KalEl0717 on 2009-11-04
If you use Ubuntu 9.10 in a clustered environment to create a cloud using EyeOS and wanted to make sure NOBODY could create a linux user, can this functionality be disabled after root and your service user are created to prohibit that action in case the cloud is compromised?

---

### Post by CRUDE on 2009-11-05
root is the only account with user creation privileges by default.

If you can't trust a user with the ability to create accounts then you need to remove root privileges.

---

### Post by Sarmacid on 2009-11-05
> **CRUDE said:**
> root is the only account with user creation privileges by default.

If you can't trust a user with the ability to create accounts then you need to remove root privileges.

Or you can modify the sudoers file so only the root account can create users.

---

