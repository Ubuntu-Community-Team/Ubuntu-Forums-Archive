---
title: "Hosting Active Directory shares on Ubuntu for audit purposes"
date: 2017-02-17
forum: Server Platforms
---

### Post by c0d3sl1ng3r on 2017-02-17
OK, auditing file/folder access using Windows Server 2008 is, let's say, limited.

Today I started bouncing around the idea of using Ubuntu server to host shares on a Windows network (I know how to achieve that much), but what I don't know is whether this would allow more comprehensive auditing using the Linux audit tools for all file/folder access.

Basically, I inherited a 100-user Windows 2008 Active Directory backbone with 6 currently live Windows servers.

I have since introduced a couple of Ubuntu servers as and when hardware came up for renewal, which are behaving themselves, as expected.

The rationale underpinning the above musings are centered around comprehensive logging of shares ultimately hosted on Linux that the Windows clients access.

Do-able ?

Not ?

Barking up the wrong tree ?

Time to go and stick my head in a bucket of water ?

Thanks for looking :)

---

### Post by Fire_Chief on 2017-02-17
While you may get better auditing abilities, the integration and permissions granularity will be much worse for the Windows shares on Ubuntu than on Windows Server. If you don't have any shares or sub-share folders that need extensive permissions definition, then you could do it without a lot of pain.

---

### Post by c0d3sl1ng3r on 2017-02-21
Thanks for your reply - there are a lot of shares and many of them have complex levels of permissions based on individuals and various groups.

Perhaps the "Time to go and stick my head in a bucket of water" was the correct option ;)

It's not over yet though.

Although I inherited this infrastructure I can still introduce changes over time. I can see a whole load of opportunity to rationalise and simplify many of the shares, so it *may *end up achievable after all.

---

