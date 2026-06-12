---
title: "Please help LTS!"
date: 2008-12-27
forum: The Cafe
---

### Post by macintosh on 2008-12-27
Me: Hello people I use the LTS releases.
Ubuntu Fan: Oh gasp never so you are using a OS that is really old? 
Me: It's not old it's still in support
Ubuntu Fan: But why don't you go with the standard releases?
Me: Because they might not work on my hardware and the OS is not mature enough!

What you saw above was a true story but why do people think the LTS is old? I know why because Ubuntu makes people upgrade because of a new Applet hear and a new feature there making us LTS users feel in the dust. Now I know you might ask me why don't you go with the standard well it's because Intrepid does not work on my Laptop. So I am stuck with the LTS but what Canonical should do is update the repo's more so that they keep up with the roll on releases. You see we are still using stuff from KDE3. KDE4 is stable enough to allow it's app's on a LTS. Also when new thing's come out and are stable enough they should be added to the Hardy repo's.

---

### Post by M7S on 2008-12-27
Stable has other interpretations than free from bugs. Stable can also mean that the production environment doesn't change all the time. The programs should work in the same way when you arrive at work as it did yesterday, not change because of some update during the night. LTS is stable that way.

---

### Post by namdung on 2008-12-27
I agree that the current LTS Hardy Heron 8.04.1 could have the newer version of the kernel and other software in the repos.

Hardy 8.04.2 is out on 1/1/2009. 
[https://launchpad.net/ubuntu/+milestones](https://launchpad.net/ubuntu/+milestones)

---

### Post by quinnten83 on 2008-12-27
I agree that there should be more backporting of the newer versions of applications.
If i want things to stay stable, I can always CHOOSE not to install a certain update. Afteral isn't linux about choice?

---

### Post by mips on 2008-12-27
> **quinnten83 said:**
> I agree that there should be more backporting of the newer versions of applications.
If i want things to stay stable, I can always CHOOSE not to install a certain update. Afteral isn't linux about choice?

If that is what you like then you should consider using some other distro like gentoo, arch etc.

---

### Post by rudihawk on 2008-12-27
> **mips said:**
> If that is what you like then you should consider using some other distro like gentoo, arch etc.

+1

What he said^

---

### Post by glotz on 2008-12-27
You can't eat the sandwich and save it.

---

### Post by saulgoode on 2008-12-27
> **quinnten83 said:**
> I agree that there should be more backporting of the newer versions of applications.
If i want things to stay stable, I can always CHOOSE not to install a certain update. Afteral isn't linux about choice?
The problem with doing that is then the maintenance and support channels need to support *both* versions of the application and, if there are any dependencies (there usually are :) ), both versions of the dependencies. They would also need to handle difficulties that arise when a newer version of one application requires a newer version of a dependency while another program still requires the older version. Basically, supporting and maintaining backports more than doubles the amount of effort required.

And what if a user installs the updated version then decides afterwards that he does not want it installed? No existing package managers seem to handle this situation very well; and even if they are designed to do it, the process is not very well tested. And why should it be? Who wants to spend all their time working on the capability of *removing* software?

---

### Post by smartboyathome on 2008-12-27
> **saulgoode said:**
> The problem with doing that is then the maintenance and support channels need to support *both* versions of the application and, if there are any dependencies (there usually are :) ), both versions of the dependencies. They would also need to handle difficulties that arise when a newer version of one application requires a newer version of a dependency while another program still requires the older version. Basically, supporting and maintaining backports more than doubles the amount of effort required.

The backports are already labelled as "unsupported", more or less, so as long as people know then they should be able to do what they want. Though I do NOT think that ie newer versions of the kernel should be backported, as thats something for a new Ubuntu release. Also, jdong DID create a backporting tool (can't remember the name right now) which should work for most situations.

> **saulgoode said:**
> And what if a user installs the updated version then decides afterwards that he does not want it installed? No existing package managers seem to handle this situation very well; and even if they are designed to do it, the process is not very well tested. And why should it be? Who wants to spend all their time working on the capability of *removing* software?

Actually, Gobo's "package manager" handles this fine, but its lacking in other ways. ;)

---

### Post by Tamlynmac on 2008-12-27
[LEFT]> macintosh 	 		[/LEFT]
**Please help LTS!**[LEFT] 		Me: Hello people I use the LTS releases.
Ubuntu Fan: Oh gasp never so you are using a OS that is really old? 
Me: It's not old it's still in support
Ubuntu Fan: But why don't you go with the standard releases?
Me: Because they might not work on my hardware and the OS is not mature enough!

What you saw above was a true story but why do people think the LTS is old? I know why because Ubuntu makes people upgrade because of a new Applet hear and a new feature there making us LTS users feel in the dust. Now I know you might ask me why don't you go with the standard well it's because Intrepid does not work on my Laptop. So I am stuck with the LTS but what Canonical should do is update the repo's more so that they keep up with the roll on releases. You see we are still using stuff from KDE3. KDE4 is stable enough to allow it's app's on a LTS. Also when new thing's come out and are stable enough they should be added to the Hardy repo's. 

I couldn't agree more.
LTS = Long Term Support?
Shouldn't that include App's in the repo's?  Guess not.

Not the end of the world, but certainly annoying.:-k[/LEFT]

---

### Post by smartboyathome on 2008-12-27
> **Tamlynmac said:**
> [LEFT]

I couldn't agree more.
LTS = Long Term Support?
Shouldn't that include App's in the repo's?  Guess not.

Not the end of the world, but certainly annoying.:-k[/LEFT]

LTS means that there are long term security updates. It is mainly made for Enterprise users and servers, where upgrading every 6 months would be annoying for both users and maintainers. Program updates aren't considered stable as they aren't as well tested in LTS releases. This is also why Dapper is *still* supported until June of next year (to give some time for the previous LTS to stabilize).

---

