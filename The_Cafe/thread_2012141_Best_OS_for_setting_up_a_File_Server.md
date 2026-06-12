---
title: "Best OS for setting up a File Server"
date: 2012-06-28
forum: The Cafe
---

### Post by morigeau on 2012-06-28
Hello,
I am writing a case study on setting up a file server for a fake company.  By the way I am very new to networking.  Anyways, I was doing some research for the best OS for this type of job.  I have started out between Debian, Ubuntu, and Fedora.  I'm not sure at this point what I would need in terms of hardware or what OS would offer better software for running a file server that is supposed to support about 7 offices spread out across the U.S.  Although this is the beginning so I thought I would start with software choice first.  I'm also not sure if one is better than the other in terms of server support or security. or if it doesn't matter because they are all Linux based.  Is the user experience really what separates these choices?  Or is there a clear choice for what I am trying to accomplish?  I hope I'm making myself clear.  Any insight would be great, even it it's just a sentence or two.  Thanks ahead of time.

---

### Post by rubylaser on 2012-06-28
It would be nice to know the amount of storage space that is required, the number of example users, the throughput that would be necessary (in MB/s), the budget, how competent the administrator is, would this be part of a domain, would it perform any other functions, etc.

Any of those OS's would be fine, so would FreeBSD, and any of the Solaris (Openindiana, EON, Nexenta, etc) derivatives for a "fileserver".

---

### Post by Lars Noodén on 2012-06-28
I'd lean towards Debian or OpenBSD on the server side of things.  If you go with Ubuntu on the server, be sure to choose the LTS release so that you have a longer return on your effort.  Debian is good in that way, too.

---

### Post by Cheesemill on 2012-06-28
The best OS to use is the one that you are most experienced in administrating.
For example trying to use BSD when you have no idea how it works is going to be less secure than using Windows if you are an experienced Windows systems administrator.
Security is an ongoing process, not just a software installation.


For purely file-serving duties I would give a big +1 to rubylaser's suggestions, with the caveat that I've outlined above.

---

### Post by Elfy on 2012-06-30
*Thread moved to **The Community Cafe**.*

Not a support request

---

### Post by Lucradia on 2012-06-30
Apache FTP. :P

---

### Post by CharlesA on 2012-06-30
Use what you know.

Ubuntu, Debian and SL work well for servers.

---

### Post by szymon_g on 2012-06-30
> **morigeau said:**
> Hello,
have started out between Debian, Ubuntu, and Fedora.  I'm not sure 

I'd rolled out Fedora- it has got a quite short support time (about 1.5 year).
I'd suggest: use debian stable, ubuntu lts or centos/scientific linux (= free clone of RHEL). Choose the one you like the most of these three and use it.

---

### Post by Mikeb85 on 2012-06-30
openSUSE would get my vote.

---

### Post by llua+ on 2012-06-30
> **morigeau said:**
> Hello,
I am writing a case study on setting up a file server for a fake company.  By the way I am very new to networking.
Sounds like a homework assignment.

---

### Post by KiwiNZ on 2012-06-30
> **llua+ said:**
> Sounds like a homework assignment.

I agree , thread closed

---

