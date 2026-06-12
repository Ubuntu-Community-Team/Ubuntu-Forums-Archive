---
title: "is BSD more secure than Linux?"
date: 2007-02-22
forum: Server Platforms
---

### Post by LSparky on 2007-02-22
i heard that linux security came from bsd. 
so i was wondering what else does bsd have that linux does not?

---

### Post by kalikiana on 2007-02-23
You don't expect to get a yes or no, do you? But I can give you a very interesting article about this topic to read:

[http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php)

---

### Post by Ed Ropple on 2007-02-23
As a rule (and don't flame me here, I fully acknowledge that there ARE exceptions), BSD-based solutions tend to be more stable than Linux ones, especially by default. Linux machines can be secured about as tightly as BSD boxes, but it tends to take a bit more work. In a lot of cases, Linux has considerably better driver support for hardware (though the BSD guys, such as Theo de Raadt, are a lot more evangelical about getting manufacturers to play nice with open-source developers).

Where possible, I personally prefer BSD for servers. On the desktop, though, BSD just makes me sad and I stick to Debian/Ubuntu.

---

### Post by anthro398 on 2007-02-23
Yes.

---

### Post by anthro398 on 2007-02-24
Not having performed an in-depth comparative code review of both linux and bsd-based systems, I have to rely on what I've read and the opinions of others.  That said, it's my understanding that bsd systems are more secure.  Of course, OpenBSD is widely regarded as THE most secure OS in the world.  In general, though, I understand there are a couple of reasons bsd is more secure. 

The first is that there have been extensive code reviews to evaluate the bsd base.  As the previous poster mentioned, de Raadt is manically controlling about the code he accepts and I've been told that the code base for FreeBSD is smaller and much cleaner than Linux.  The organization of the file system is cleaner, too, which probably facilitates security at some level.  

Surely the sheer number of packages for Linux distributions makes it more likely that these systems could be compromised by a buffer overflow or similar venerability in installed software.  Admittedly, one could install much of this software on a BSD, but one would have to be more motivated to install it on bsd than on Linux.

I imagine that BSD users are more self-selecting than Linux users, though.  I mean, Linux is more popular and more user friendly than bsd, so it seems likely that bsd users are probably savvier than Linux users, on average.  

At least, so I've heard.

---

### Post by openix on 2007-02-25
Generally speaking BSD servers are more secure but a server is only as secure as the person that sets it up and administers it. The less there is installed on a server (GUI etc) the less can go wrong and be exploited.

---

### Post by elst on 2007-02-25
The term "secure" doesn't really mean much without a context. Different security issues come into play depending on whether you are talking about protecting against unauthorised activity by users, physical compromise, or attempts to exploit particular network services. 

I'd agree with openix that a lot is down to the administrator - most Linux and BSD systems depend (far too much) on the admin configuring things correctly, and not installing unsafe software. Mandatory Access Control stuff like SELinux can address this somewhat by enforcing safe behaviour on the system, even in the event of the admin making a mistake.

---

