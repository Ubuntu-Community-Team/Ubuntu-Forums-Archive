---
title: "Virtualbox Shared Folder problem"
date: 2009-01-02
forum: Virtualisation
---

### Post by kgriff on 2009-01-02
I have just installed VBox 2.1.0 on Hardy.  My guest OS is Win XP.
I have my /home folder shared.

I mapped the shared folder in Win XP.
Every time I try to look at the shared folder in Windows Explorer, Windows locks up.  It doesn't lock up immediately.  It seems as though I can look at folders all I want, but if I want to browse into a folder that contains files, then it locks up.  The only way to "unlock" is to close VBox.

Has this happened to anyone else?  Any ideas what's wrong?

---

### Post by Dedoimedo on 2009-01-02
Let's try to isolate the problem.

Did you try mapping a sub-folder in your home?
See if that helps ...

Dedoimedo

---

### Post by kgriff on 2009-01-02
I un-shared /home and shared another directory within /home.  It works much better, though still not perfectly.  Most of the time it is not noticeably slow.  At other times, it may take 10-15 seconds to open a folder.

I repeated this process with several other folders, and all worked the same.  I haven't yet tried multiple shares simultaneously.

Any idea what the issue is?  I'm actually trying to get this worked out for my wife, and it would be much easier if I could just create a single share of /home.  If not, it's probably not the end of the world.  She'll just have to work out what she wants shared, and I'll do them individually.

By the way, Dedoimedo, I checked out your web site.  What A wealth of information.  Excellent site.

---

### Post by Dedoimedo on 2009-01-02
Thank you!

I think the problem might be with the dhcp / renewal of the IP address. Unlike Linux, which maps locally, Windows maps remotely. So until it can resolve the remote hosts, it stays "stuck." Not sure, this is just an idea ...

Dedoimedo

---

