---
title: "Firefox not working with LTSP"
date: 2008-12-02
forum: Server Platforms
---

### Post by thebbxx on 2008-12-02
I have installed Ubuntu with the LTSP option, and it's working great.  BUT, I can only have one firefox window open amongst all of my machines.  If I try to open firefox on a different machine when another machine already has it open it says, "Firefox is already running, but is not responding..."

How do I configure my server so I can run Firefox on all of my machines?

---

### Post by wilbbe01 on 2008-12-02
I'm assuming you are using some type of network home directory storage?  Firefox locks itself when it opens on a machine, and then releases the lock on the directory once it has been closed.  This lock is located in the .mozilla directory under your home directory I believe.  You can manually go in and delete it, which would allow you to open firefox somewhere else, but this could get yucky.  Try searching for a way to dissable that lock from mattering, or possibly different profiles.  Hopefully that guides you in a good direction.

---

