---
title: "Should I avoid using Webmin as a &quot;crutch&quot;?"
date: 2010-02-26
forum: Server Platforms
---

### Post by Vunutus on 2010-02-26
I've been looking into Webmin lately and frankly, it seems about as sexy as a system administration tool could be.

I'm the sysadmin for a small company with only one server (for now, we might be adding a second server within 6 months or so). I'm not the most experienced sysadmin ever but I keep things going smoothly enough. I have a pretty good understanding of most of our services, but there are a few things I have "mental haze" covering like LDAP and samba domains. If I install Webmin on my server and use it to tinker with services I don't fully know how to administer from just straight config file editing, will this have any possible negative outcomes? I don't want to end up using webmin as a crutch of sorts for things I don't know how to do.

---

### Post by Jive Turkey on 2010-02-26
In my experience webmin does not always configure things the way ubuntu is intended to have them.  One example is virtual hosts in Apache.  The hosts would work, but would be configured more like suse or fedora would want them.  I think postgresql didn't quite like webmin's handling of things either.  Today I have set out to find a good GUI for my newly built server when I stumbled onto your thread.  

At the very least I would configure webmin to only allow access from a small number of computers.  All that code has the potential to have backdoors open.  Alternatively, you could remove webmin after setting things up.

---

### Post by macogw on 2010-03-26
Webmin isn't recommended on Ubuntu, because it handles configuration files in ways that aren't good for use with our package management system.  Ebox is the recommended replacement.

---

### Post by jrssystemsnet on 2010-03-26
One, as already mentioned, webmin doesn't do things the Debian/Ubuntu way, so it isn't really recommended for a Debian/Ubuntu server.

Beyond that, the answer to your question depends on whether you are more focused on bettering your skills and being able to respond well to catastrophe and/or new situations, or whether you're more focused on just getting the current job done and the heck with it.

Me, I'm the "be all you can be" type, and you don't learn much (if anything) with a tool like webmin, so I avoid it.  But I'm not everybody, and everybody's not me.  Who are you? :)

---

