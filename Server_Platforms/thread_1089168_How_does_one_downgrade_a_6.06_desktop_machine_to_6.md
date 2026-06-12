---
title: "How does one downgrade a 6.06 desktop machine to 6.06 server?"
date: 2009-03-06
forum: Server Platforms
---

### Post by benblout on 2009-03-06
I have a desktop machine, running Dapper, that is used very minimally.  With the upcoming end of support for the 6.06 desktop edition, I was considering the option of using the machine as a 6.06 server.

My naive assumption is that I need to find a list of which packages will continue to be supported past this June.  To 'downgrade' to the server edition I would then remove all packages not on that list.

Is my understanding correct?  Is there such a list of packages?

I've searched the forums here quite a bit, and googled, without being able to find this information elsewhere.  If this is not the correct forum, pointers to the correct forum are very welcome.

Thanks!

---

### Post by hictio on 2009-03-06
I don't understand...
I'm sorry, but, since you are obviously repurposing the box (switching from desktop to server) why don't you nuke from orbit and install a newer Ubuntu Server version?

---

### Post by benblout on 2009-03-06
> **hictio said:**
> I don't understand...
I'm sorry, but, since you are obviously repurposing the box (switching from desktop to server) why don't you nuke from orbit and install a newer Ubuntu Server version?
You probably don't understand because, in the interest of being brief, I left out some details.  The box started as a server, and still does serve files and a printer.  But over the years, it became convenient to install additional packages, to use the machine for other tasks.  I would prefer to not have to 'nuke from orbit'.

---

### Post by dguitar on 2009-03-06
> **benblout said:**
> I would prefer to not have to 'nuke from orbit'.

You will be running an unsupported OS that won't receive security updates. You really should upgrade the OS.

---

### Post by benblout on 2009-03-06
> **dguitar said:**
> You will be running an unsupported OS that won't receive security updates.
Now I don't understand - 6.06 server edition has another two years of support as I understand it, until June of 2008.  Or are you saying once you add packages to a Ubuntu Server you have made a one-way upgrade?

---

### Post by PilotJLR on 2009-03-06
I would think this is still supported.

So the idea is to remove packages until it is "only" a server, right? How about removing ubuntu-desktop?

---

### Post by benblout on 2009-03-07
> **PilotJLR said:**
> So the idea is to remove packages until it is "only" a server, right?
That is what I am presuming is the correct approach, but I am happy to have a different approach suggested.

 > **PilotJLR said:**
> How about removing ubuntu-desktop?
ubuntu-desktop is just a meta-package, so it can't be removed directly.  I could remove every package that it depends on.  But there are other packages, not part of ubuntu-desktop, that are also not part of the server edition.  How can I find them?  Is every package depended on by ubuntu-desktop *not* part of the server edition?

---

### Post by dguitar on 2009-03-07
Sorry I should have been more specific. You WILL be running an unsupported OS once 6.06 hits EOL. (Didn't realize server was 2 yrs after desktop, so still plenty of time till Server 6.06 hits EOL)

If you installed Server base, then installed the desktop packages on top of it, those packages will no longer receive updates.(afaik) If all you are running is CUPS and Samba, you should be fine.

---

