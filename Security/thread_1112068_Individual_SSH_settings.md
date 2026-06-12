---
title: "Individual SSH settings"
date: 2009-03-31
forum: Security
---

### Post by hooksie on 2009-03-31
I've been searching around for this a while, I'm starting to wonder if it can't be done?

Is it possible to override a specific users SSH settings?  Specifically I want to force one user to have to use RSA based authenticated but not force it systemwide.

I tried adding "PasswordAuthentication no" to the users ~/.ssh/config file, but this doesn't appear to be working...

---

### Post by cdenley on 2009-03-31
> **hooksie said:**
> I've been searching around for this a while, I'm starting to wonder if it can't be done?

Is it possible to override a specific users SSH settings?  Specifically I want to force one user to have to use RSA based authenticated but not force it systemwide.

I tried adding "PasswordAuthentication no" to the users ~/.ssh/config file, but this doesn't appear to be working...

~/.ssh/config is used as a user-specific configuration for the ssh **client**. It sounds like you are trying to change the configuration for the server (sshd), though. I don't believe there are user-specific settings like that for sshd.
```

man ssh_config
man sshd_config

```
You can disable all password authentication for a specific user, but then they won't be able to log in locally.
```

sudo usermod -L username

```

---

