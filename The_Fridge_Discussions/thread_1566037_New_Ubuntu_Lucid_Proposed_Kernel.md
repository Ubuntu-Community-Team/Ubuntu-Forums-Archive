---
title: "New Ubuntu Lucid Proposed Kernel"
date: 2010-09-01
forum: The Fridge Discussions
---

### Post by TheFridge on 2010-09-01
The Ubuntu kernel team has prepared [a new proposed kernel for Lucid]("https://edge.launchpad.net/ubuntu/+source/linux/2.6.32-25.43") (2.6.32-25.43), containing a large number of fixes. This is a larger number of updates than we would usually push at one time, but processing of the upstream stable updates was delayed by a couple of security updates.

 This kernel should fix a lot of issues, including [this one]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543617") that people have been asking about a lot.

 You will get this automatically if you have [updates from lucid-proposed]("https://wiki.ubuntu.com/Testing/EnableProposed") enabled. Note that if it breaks you get to keep all the pieces,  so don&#8217;t try this on production machines.

 Please test against your favorite bugs in the changelog and provide feedback.

 Originally posted [here]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-August/000752.html") by Steven Conklin, Ubuntu Kernel Engineer on 1 September 2010.

 

[More...](http://fridge.ubuntu.com/node/2119)

---

### Post by wavingpines on 2010-09-02
Is this available as part of an ISO download?  I'm stuck on Jaunty because of a kernel oops booting the 32 bit versions of any subsequent releases (see [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456790")), and don't want to go 64 bit because of the problems with Java and Flash.

---

### Post by jibel on 2010-09-02
No it is not available from the ISO. You have to install Lucid and enable the -proposed repository. 

An alternative is to give a try at Maverick Beta from a LiveCD and see if the latest kernel fixes your issue.

---

### Post by wavingpines on 2010-09-07
Tried the Maverick 32 bit beta with the same (or at least very similar) results.  Maybe I'm the only person in the world trying to run Ubuntu on this Processor/motherboard/whatever.  I'll update Launchpad and keep my fingers crossed...

---

