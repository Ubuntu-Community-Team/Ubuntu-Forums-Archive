---
title: "DNS Architecture Question"
date: 2009-08-27
forum: Server Platforms
---

### Post by NewbieNik on 2009-08-27
OK, Windoze bashing aside, what would be peoples best advice on providing DNS services on a mixed Windows 2003 AD and Linux network.
Most users are Windoze clients as are most servers, but there are linux desktops and the Linux servers supply DB backends to web-apps and some desktop apps.

Is it worth sepating the linux hosts into their own DNS site or is this just an unecessary step?

Thoughts please, constructive only, if possible.

---

### Post by jocampo on 2009-08-27
Hi

You can safely replace the Windows DNS service or choice when configuring your Active Directory, it clearly asks you what your existing DNS is so you can point your DC and AD resources correctly. Just be sure your Linux DNS choice supports SRV records; those are the one AD uses to locate resources.

This article is kind of old, but could be useful: [http://technet.microsoft.com/en-us/library/dd316373.aspx]("http://technet.microsoft.com/en-us/library/dd316373.aspx")

---

### Post by NewbieNik on 2009-08-27
Yeah, saw a similar article, but I am not interested in replacing AD as it servers a purpose ($000 users and mailboxes, 3000 PCs, SQL servers, MOSS, OCS and many others)
What I'm trying to get my head around is a request to remove all teh linux based systems to their own DNS domain completely independant of the Windows DNS servers and domain.

Don't get me wrong, I am an avid Linux user and have laptops, Desktops and servers at home running Ubuntu. We have linux boxes at work running Oracle, Apache, Tomcat and many others, but I am not sure about seperating the management of the DNS zones and was hoping for other users input. 
If I'd thought a bit more I would have done this as a poll.

Thanks for your comments though.

nik

---

### Post by jocampo on 2009-08-27
Well, you can mix, combine and do whatever you want in terms of primary and secondary DNS :-) 

However, because DNS is vital for LAN communication, I would not rely on just 1 DNS on your LAN for the Linux boxes. What you can do is, set the BIND DNS as primary for your Linux boxes and use the Micro$oft DNS as a secondary. that way, you'll have some kind of redundant lay out. And I'm giving that suggestion in case your Windows boxes use any of the Linux machines as a resource. If that's the case, some way, you must exchange record information between DNS zones.

---

### Post by NewbieNik on 2009-08-29
yeah ,good points. Thanks Jo. I shall consider this and see if this is a direction we should take. It's just that I cannot see any benefits of using Bind over Windows DNS in our environment. Unless someone knows of any particular plus's Bind has over other DNS variants?

---

### Post by jocampo on 2009-08-29
Honestly? If most of you environment is Windows, keep it simple, keep just Windows DNS servers there. Sometimes is better to simplify network and services layouts than mix technologies and make it more complex. 

If you don't really need it, avoid the use of BIND. In my personal experience I have never faced any issue with Microsoft's DNS solution. And for Active Directory, the use of same Microsoft DNS solution for srv records is better than any Linux solution, is native...you know ...

---

