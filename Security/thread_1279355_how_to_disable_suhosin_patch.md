---
title: "how to disable suhosin patch"
date: 2009-09-30
forum: Security
---

### Post by b4nsh33 on 2009-09-30
Hi, just that, im having a problem with my php scripts that export from MS SQL databases, googling around i read that is beacause of the suhosin patch, this is a low profile server without internet access, so i can afford some risks with this server, if suhosin is the troublemaker here, i want to disable it...

---

### Post by Bachstelze on 2009-10-01
> **b4nsh33 said:**
> Hi, just that, im having a problem with my php scripts that export from MS SQL databases, googling around i read that is beacause of the suhosin patch, this is a low profile server without internet access, so i can afford some risks with this server, if suhosin is the troublemaker here, i want to disable it...

Since a patch is applied at source-level, you can't disable it. If you want a version of PHP without the patch applied, you must compile it yourself.

---

