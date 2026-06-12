---
title: "ubuntu repo on a non-ubuntu/debian server?"
date: 2008-08-28
forum: Server Platforms
---

### Post by &lt;crush&gt; on 2008-08-28
Hello community.

Sorry if this is out of place, or been discussed before. I did search the forum both by the search feature and manually but didn't really find anything on the subject that was relevant. So I was hoping to get some direction.

I am trying to set up local repositories where I work and so far so good with CentOS and Fedora (I was 'raised' on Red Hat so it was easier for me), but now I want Ubuntu and possibly some of it's sister distros, but I want to keep all of them on the same server because the mirror will only be used internally, so no worries about power consumption and what not.

The server that the 2 mirrors I already have are on a CentOS x86_64 server, so will I run into problems putting a debian i386 repository on that server? Are there special instructions/tips/notes? Has anyone else done this before and written a how to I go use?

Sorry if I've used the wrong terms or asking a dumb question, I'm new to the ubuntu side of Linux.

---

### Post by &lt;crush&gt; on 2008-08-28
I have been researching it, and I found a mirror that I want to rsync from, but what files am I going to need and can anyone give a tip on how to set it up, regardless of what server it's going to be put on?

---

### Post by cariboo on 2008-08-29
You could try **apt-mirror**, it is available in the repositories:

```
sudo apt-get install apt-mirror
```

Jim

---

### Post by netztier on 2008-08-29
> **<crush> said:**
> 
The server that the 2 mirrors I already have are on a CentOS x86_64 server, so will I run into problems putting a debian i386 repository on that server? Are there special instructions/tips/notes? Has anyone else done this before and written a how to I go use?

Sorry if I've used the wrong terms or asking a dumb question, I'm new to the ubuntu side of Linux.

Start here:

[http://www.ubuntu.com/getubuntu/mirror](http://www.ubuntu.com/getubuntu/mirror)

And no, you don't have to run Debian or Ubuntu to host an Ubuntu mirror. All you basically need is:

[LIST]
[*]a way to sync/mirror (rsync, apt-mirror or the likes). 
[*]some disk space. This can go rapidly towards several hundred Gig, depending on how many Ubuntu releases and architectures you want to mirror.
[*]a web or ftp server that can serve files from that disk space.
[*]disciplined internal users that will only refer to your local mirror in their /etc/apt/sources.list.
[/LIST]

**apt-mirror** for example is a perl script - you should be able to get it running on almost any platform, provided you can also install the programs it depends on (such as wget). **rsync** is available on almost all platforms and should do very nicely. 

regards

Marc

---

### Post by ebinezer on 2008-09-11
I am a network administrator, but never got a opportunity to work on debian server. I need to experience, heard lot about this. This forum has helped me get started. Thank you.

ebinezer
[Auto Auctions]("http://www.gov-auctions.org")

---

