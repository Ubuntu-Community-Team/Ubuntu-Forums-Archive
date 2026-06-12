---
title: "Locking down Ubuntu for student computer lab"
date: 2008-09-25
forum: Security
---

### Post by souled on 2008-09-25
I'm trying to setup a system for a computer lab that's completely secure from the user, but still accessibly by an admin account if maintenance is required.  When the default user is logged in, I only want a login screen to be displayed for a remote display program (users will be doing work through a remote server). 

I have configured Gnome with Sabayon/Pessulus, and I have removed the gnome-panels from start up. I also want to disable ctrl+alt+del from restarting X. 

My question is, how much can I lock down the system from the user, but still be able to make changes through an admin account? In other words, if I completely prevent the default user from being able to do anything, how can I still be able to log into an admin account?

Thanks

---

### Post by cdenley on 2008-09-25
> **souled said:**
> I'm trying to setup a system for a computer lab that's completely secure from the user, but still accessibly by an admin account if maintenance is required.  When the default user is logged in, I only want a login screen to be displayed for a remote display program (users will be doing work through a remote server). 

I have configured Gnome with Sabayon/Pessulus, and I have removed the gnome-panels from start up. I also want to disable ctrl+alt+del from restarting X. 

My question is, how much can I lock down the system from the user, but still be able to make changes through an admin account? In other words, if I completely prevent the default user from being able to do anything, how can I still be able to log into an admin account?

Thanks

If you want users to be able to do nothing but some kind of remote desktop application, I think you can edit /etc/event.d/tty1, and replace the last line with
```

exec /usr/bin/xinit /path/to/myapp

```
That way, your remote desktop application will always be running. You don't even need to give users a local account. If you need admin access, then you could just ctrl+alt+f2. This is the way I set up some POS systems a while ago.

---

