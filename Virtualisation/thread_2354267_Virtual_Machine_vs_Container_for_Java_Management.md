---
title: "Virtual Machine vs Container for Java Management"
date: 2017-03-01
forum: Virtualisation
---

### Post by chondromalasia on 2017-03-01
Hello. I'm relatively familiar with Virtual Machines but I've only just started reading about containers (stgraber.org's tutorials). And I need some advice. I am in a class where I need to use RapidMiner version 5.3 with the R plugin. The issue here is that RapidMiner really needs to work with Java 6 or 7 in order for it to be passably useable. In addition, R needs to be configured with Java and I'm just guessing that it should be the same version. However, it seems like the only way to do this is to make an environmental variable point to the old version of Java, which seems pretty irresponsible. And there's a pretty good chance I won't be doing anything with it after this semester.

So I feel like the less permanent/safer/easier solution would be to just do this whole thing in a virtual machine or a container. I would prefer to work with a container because A) it just seems more lightweight B) It would be good experience; it's the sort of thing I should know how to do.

Here are the possible issues I could see:
1) GUI. It's essential that RapidMiner has its own window
2) Memory allocation - This is some data analysis stuff so whatever maximizes memory would be the best. This is not mission critical, I can just tell RapidMiner how much memory to use, but you catch my drift.

Thanks for the advice.

---

### Post by ian-weisser on 2017-03-01
If you want to isolate services, but those services are all using the same release of Ubuntu (compatible versions), then a container is easy.
If you want to use different releases (versions), then a VM is easy.
It is possible to run different versions of software in different containers, but that's not a beginner task. Don't try it in your first container. And keep good notes, lest you become confused about which version and service is where and why.

---

