---
title: "Squid proxy server and disaster recovery solutions"
date: 2010-07-01
forum: Server Platforms
---

### Post by LtPitt on 2010-07-01
Hello everybody!

I have this sweet proxy server perfectly configured for the needs in the office.
I look at it proud as a daddy but...
I think about the horrible day anything (hardware or software) will go wrong.

What can I do to preserve me from the pain of a total reinstall and get the proxy back to work again in minutes?

Clonezilla?

Remastersys?

Any hints?

Thanks! :)

---

### Post by LtPitt on 2010-11-14
Just a little...
Bump!

---

### Post by SeijiSensei on 2010-11-15
If all you've done is install squid along with a vanilla Ubuntu installation, I'd just make sure you've backed up the contents of /etc.  If everything goes south, reinstall Ubuntu and copy the contents of the saved /etc over the installed versions.  

My guess is that you'll need the iptables script that does transparent proxying (if you're using that approach) and squid.conf to restore the ACLs.

If you want a complete disk image backed up to another drive, use Clonezilla.

The fastest solution is to keep a spare server with the identical configuration so you can put into service immediately.

---

