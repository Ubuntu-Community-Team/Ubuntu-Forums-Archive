---
title: "Track SSH logins"
date: 2007-01-24
forum: Server Platforms
---

### Post by martinmaurer on 2007-01-24
hi,

I want to log all successful ssh connection

- username
- ip address
- time
- all command typed (a kind of bash history)
- etc.

anyone know how to do this? the same for local logins.

any help is welcome,
martin

---

### Post by MrHorus on 2007-01-24
> **martinmaurer said:**
> hi,

I want to log all successful ssh connection

- username
- ip address
- time
- all command typed (a kind of bash history)
- etc.

anyone know how to do this? the same for local logins.

any help is welcome,
martin

The auth log in /var/log should show you the username, time and IP address of all login attempts, successful or otherwise.

As for command history, .bash_history in the user's home dir will have this although it can be deleted by the user.

---

