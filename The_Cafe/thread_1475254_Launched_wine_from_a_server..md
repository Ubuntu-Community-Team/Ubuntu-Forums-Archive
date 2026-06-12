---
title: "Launched wine from a server."
date: 2010-05-06
forum: The Cafe
---

### Post by themarker0 on 2010-05-06
Possible? I'm considering trying to get my school to convert to either Panologic boxes (Which means windows) or linutop boxes. If i use Linutop i know i can block sites using firefox etc, just trying to present it completely awesomely :)

---

### Post by themarker0 on 2010-05-07
Bump?

---

### Post by Shakz on 2010-05-07
Maybe I am not understanding....wouldnt you just need to create a network drive with wine on it then automount the samba drive and create a symlink on the users PC to .wine which would actually point to the wine install on the server?
Should all be transparent to the user.

---

### Post by lykwydchykyn on 2010-05-07
What does "Launch wine from a Server" mean?  What are you trying to accomplish?

---

### Post by themarker0 on 2010-05-07
What i want to do is use linutops, and have all the software needed launch from a server. I've seen most done already, wine though, i've never seen or heard being launched from a server.

---

### Post by lykwydchykyn on 2010-05-07
> **themarker0 said:**
> What i want to do is use linutops, and have all the software needed launch from a server. I've seen most done already, wine though, i've never seen or heard being launched from a server.

You'll forgive my ignorance, but the linutop setup is something like LTSP, where the clients actually log in to a remote session on the server?

Or is this something like forwarding X11 over ssh?  Or sharing /usr via NFS?

In any case, I can't see that wine would behave differently than any other program.  The biggest difference with wine is that by default each user has a unique ~/.wine directory, so either program installs may have to be managed per-user, or you'll have to experiment with a shared wine directory (which may be problematic when you have multiple users).

---

### Post by themarker0 on 2010-05-07
> **lykwydchykyn said:**
> You'll forgive my ignorance, but the linutop setup is something like LTSP, where the clients actually log in to a remote session on the server?

Or is this something like forwarding X11 over ssh?  Or sharing /usr via NFS?

In any case, I can't see that wine would behave differently than any other program.  The biggest difference with wine is that by default each user has a unique ~/.wine directory, so either program installs may have to be managed per-user, or you'll have to experiment with a shared wine directory (which may be problematic when you have multiple users).

I know i'd have to setup each user, i figure if you can get it working once, its easier past that.

---

