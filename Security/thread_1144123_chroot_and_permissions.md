---
title: "chroot and permissions"
date: 2009-04-30
forum: Security
---

### Post by steffff on 2009-04-30
Hi all!

I'm doing some practise with chroot. I set a chroot environment with minimal functionality (such as bash, ls etc) and everything goes fine. What I noticed, though, is that when I get inside the jail the process has root privileges, allowing it to kill all the other processes.How can I avoid that? Is there a way to disable inter-process communication? In this way, I think the jail would be a safer environment.

Thank you in advance ;)

---

### Post by bodhi.zazen on 2009-04-30
I am not sure what you are wanting to do exactly or if chroot is your best tool.

Alternates include Apparmor.

Personally I do not run servers in a traditional chroot any longer.

The other possibility is OpenVZ.

[http://wiki.openvz.org/Main_Page](http://wiki.openvz.org/Main_Page)

---

### Post by steffff on 2009-05-01
Actually I'm not using it for a server.
What I trying to do is to create a sandbox to run untrusted processes into; this is in a single-user machine, like my desktop. When I change the root directory for a bash process, for example, it owns all permissions (including kill-9 ALL processes). What I would like to do is to keep that process running inside the sandbox from interfering with any other process running outside.

---

### Post by bodhi.zazen on 2009-05-01
> **steffff said:**
> Actually I'm not using it for a server.
What I trying to do is to create a sandbox to run untrusted processes into; this is in a single-user machine, like my desktop. When I change the root directory for a bash process, for example, it owns all permissions (including kill-9 ALL processes). What I would like to do is to keep that process running inside the sandbox from interfering with any other process running outside.

You can either restrict it with apparmor, or to be honest, OpenVZ sounds like a perfect solution. Openvz basically uses the idea of a chroot, but isolates it form the system better and allows you to dedicate or limit resources to the chroot.

The other option is to basically build somethign similar to OpenVZ yourself.

---

### Post by steffff on 2009-05-02
Those solutions seem great, but what about using permissions to limit the inter-process communication from the untrusted region? Maybe setting /etc/passwd so that within the jail is not possible to damage the outside world. I expect (but haven't found much) there is a way to keep the untrusted processes from killing all the others, otherwise a server would be easily attacked from every user.  Is there a way to do that? 

The main problem is that the untrusted process is superuser inside the jail, then all the other processes would need to have superuser's privileges as not to be killed by it. Or maybe it's possible to limit to a "no-permission" -mode the jailed process...?

setuid seems to work... but it's not recommended. At the same time it's the only way I've found so far to drop the root privileges in the chroot environment. What do you guys think about it?

---

