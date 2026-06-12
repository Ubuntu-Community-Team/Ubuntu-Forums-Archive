---
title: "Change Password"
date: 2007-05-06
forum: Server Platforms
---

### Post by mattc908 on 2007-05-06
How do you change a password on Ubuntu Server. Like your login password and the password you use to install and do everything with? I do not have GNOME or any GUI installed only text base so if someone could give me the code to do it, pretty new at it but much appreciated.

---

### Post by MilesZS on 2007-05-06
Assuming you're just changing your own password, you can use the command naked:

```

passwd

```

If you are wanting to change another user's password, you'll need to be a sudoer:

```

sudo passwd

```

You should be prompted for the new password, twice.

---

