---
title: "Ubuntu server security question"
date: 2010-01-19
forum: Security
---

### Post by dirtrider1 on 2010-01-19
Hey Im currently running ubuntu server 9.10 and everything is going great but just out of curiosity I was wondering if Ubuntu server has achieved any security certifications to be used in government or mission critical environments yet? Or does anyone have any info on what evaluation assurance level or any other certs it has got yet if any.Thanks

---

### Post by HermanAB on 2010-01-19
Howdy,

No, you should use Red Hat Enterprise Linux for government clients.  If you use anything else, then you are sure to meet some resistance from the NSA, CSE, Dir IM Secur and the like.  Trying to swim against the current with those guys is a pure waste of time, so don't even try.

---

### Post by i.r.id10t on 2010-01-19
Of course, NSA has released a Linux distro as well...

---

### Post by HermanAB on 2010-01-19
Yup, and the NSA work is incorporated into the Red Hat distro by default.

If you work on a Gov project then you'll find it very difficult to make contact with the NSA - simply because they are extremely busy and don't have time to answer stupid questions.  So by the time that your project priority has advanced to the point where they will actually talk to you, the project is almost done already and if you haven't started off on the right foot, then you are fscked and have to start over with the OS configuration.

So, use Red Hat Enterprise Linux 5.4 for all Gov jobs.  Also note that you may have to rebadge Linux [http://www.aeronetworks.ca/linux-rebadge.pdf](http://www.aeronetworks.ca/linux-rebadge.pdf) in order to comply with the license terms.

---

### Post by dirtrider1 on 2010-01-19
Alright thanks so Red Hat is theoretically the most secure linux distro im going to check it out the reason I went with Ubuntu is because I like the deb packages and don't have too much experience with the rpm's.

---

### Post by Lars Noodén on 2010-01-19
It would be something to check with Canonical rather than on the forums.  Being certified would be a good advertising point but the criteria can be that stringent anymore since a number of Microsoft products are also represented.  It's probably just a matter of filling out the right paperwork and stapling a paper check, rather than a rubber one.

---

### Post by bodhi.zazen on 2010-01-19
> **dirtrider1 said:**
> Alright thanks so Red Hat is theoretically the most secure linux distro.

That is not true, it is the distro preferred by NSA.

See : [http://www.engardelinux.org/](http://www.engardelinux.org/)

Note: That is NOT the only choice, but Engarde has FULL SELINUX and even the root account is confined.

With that said, security is a process of hardening and monitoring not install and forget it.

Start with the security sticky, work through the apparmor sticky, then see :

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

---

### Post by rookcifer on 2010-01-20
> **i.r.id10t said:**
> Of course, NSA has released a Linux distro as well...

No they didn't.  They released their FLASK architecture under the GPL and renamed it SELinux.  It is not a distro, but a kernel patch that provides flexible mandatory access controls as well as multi-level security.

---

### Post by dnvikram on 2010-01-20
> **HermanAB said:**
> Howdy,

No, you should use Red Hat Enterprise Linux for government clients.  If you use anything else, then you are sure to meet some resistance from the NSA, CSE, Dir IM Secur and the like.  Trying to swim against the current with those guys is a pure waste of time, so don't even try.

NSA invented SELinux and it was incorporated into the linux kernel..Especially RHEL as other posters rightly pointed out..Using RHEL is the right thing to do in those Orgs...At the same time, IMHO Ubuntu Server is no less than RHEL..Its as robust,secure and stable as it...Just that Redhat has a larger footprint and that brand image which makes it attractive...Its always been the poster child for linux especially in the server market...Just like Ubuntu is the poster child for linux desktops...

---

### Post by movieman on 2010-01-20
The NSA also have a Linux hardening document which is primarily aimed at RHEL/CentOS but has a fair amount that would be useful in Ubuntu too:

[http://www.nsa.gov/ia/_files/os/redhat/rhel5-guide-i731.pdf](http://www.nsa.gov/ia/_files/os/redhat/rhel5-guide-i731.pdf)

---

### Post by 0xyg3n on 2010-01-20
> **HermanAB said:**
> Howdy,

No, you should use Red Hat Enterprise Linux for government clients. If you use anything else, then you are sure to meet some resistance from the NSA, CSE, Dir IM Secur and the like. Trying to swim against the current with those guys is a pure waste of time, so don't even try.


Then Why does this book claim otherwise?
[http://74.125.155.132/search?q=cache:RdS4c_nx-1wJ:search.barnesandnoble.com/The-Official-Ubuntu-Book/Benjamin-Mako-Hill/e/9780137151028+ubuntu+server+suported+government&cd=5&hl=en&ct=clnk&gl=us](http://74.125.155.132/search?q=cache:RdS4c_nx-1wJ:search.barnesandnoble.com/The-Official-Ubuntu-Book/Benjamin-Mako-Hill/e/9780137151028+ubuntu+server+suported+government&cd=5&hl=en&ct=clnk&gl=us)

[IMG]http://images.barnesandnoble.com/images/27840000/27842853.JPG[/IMG]

**Synopsis**

**Ubuntu** is a complete, free operating system that emphasizes community, support, and ease of use without compromising speed, power, or flexibility. It's Linux for human beings&#8212;designed for everyone from computer novices to experts. **Ubuntu** 8.04 LTS (Long Term Support), a.k.a., "Hardy Heron," is the latest release&#8212;more powerful, more flexible, and friendlier than ever. **The Official [B]Ubuntu**, Third Edition,[/B] will get you up and running quickly.
 Written by expert leading **Ubuntu** community members, this book covers all you need to know to make the most of **Ubuntu** 8.04 LTS, whether you're a home user, small business user, **server** administrator, or programmer.  The authors covers **Ubuntu** 8.04 LTS from start to finish: installation, configure, desktop productivity, games, management, support, and much more. Among the many new topics covered in this edition: the new Edubuntu and the brand new Kubuntu Remix including KDE 4.
 **The Official [B]Ubuntu** Book, Third Edition,[/B] covers standard desktop applications, from word processing, spreadsheets, Web browsing, e-mail, instant messaging, music, video, and games to software development, databases, and **server** aplications.  In addition, you'll
 &#8226; Learn how to customize **Ubuntu** for home, small business, school, **government**, and enterprise environments
 &#8226; Learn how to quickly update **Ubuntu** to accommodate new versions and new applications
 &#8226; Find up-to-the-minute troubleshooting advice from **Ubuntu** users worldwide
 &#8226; Learn **Ubuntu** **Server** installation and administration, including LVM and RAID implementation
 &#8226; Learn about Edubuntu&#8212;**Ubuntu** optimized specifically for the classroom
 The DVD includes the complete **Ubuntu** Linux operating system for installation on PC platforms, preconfigured with an outstanding desktop environment for both home and business computing. It can be used to install other complete variants of **Ubuntu** including Kubuntu (with the KDE environment), and Edubuntu (for use in schools).

---

### Post by cariboo on 2010-01-20
All the other posters are saying is that the Ubuntu server version is not certified for government usage. There are many servers on the internet running Ubuntu server, this forum for instance. You can use [http://www.netcraft.com]("http://www.netcraft.com") to find others.

The one thing to keep in mind, a server is only as secure as the administrator that runs it makes it, no matter what distribution they are using.

---

### Post by 0xyg3n on 2010-01-20
Damn, I don't see why not.  Doesn't make sense to me.

---

