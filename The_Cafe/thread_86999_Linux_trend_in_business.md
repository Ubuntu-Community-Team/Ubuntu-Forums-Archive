---
title: "Linux trend in business?"
date: 2005-11-07
forum: The Cafe
---

### Post by fbn on 2005-11-07
Hi,

on a IT magazine I saw the following picture:
[img]http://frank.niedermann.name/stuff/vmware.jpg[/img]

It shows the results of a poll wether the asked companies are using software to virtualize servers. 55,8% are using VMware (GSX / ESX), 11,2% are using Microsoft (Virtual Server), 9,9% are using something else (don't know what), 16,9% are not using software for virtualization.

Does anybody know of something like this for Linux (vs Windows) servers?

Regards,
  Frank

---

### Post by TravisNewman on 2005-11-07
vmware is also available for linux, if that's helps answer your question.

Also, 9.9 using something else could get into chroot, usermode linux, xen, etc, that are on linux.

---

### Post by fbn on 2005-11-07
[QUOTE=panickedthumb]vmware is also available for linux, if that's helps answer your question.

Also, 9.9 using something else could get into chroot, usermode linux, xen, etc, that are on linux.[/QUOTE]

Unfortunately that helps me not - I'm searching for information like the results of the poll mentioned for Linux on the server side, without any connection to VMware.

In the company where I work there are already some Linux servers and many Windows servers and I would like to show ("prove") my colleagues that Linux is growing on the server side ...

---

### Post by poptones on 2005-11-07
You're gonna have a hard time with that one except for maybe [stuff like this](http://www.alwayson-network.com/comments.php?id=P5013_0_6_0_C). [Netcraft surveys](http://news.netcraft.com/archives/2005/10/04/october_2005_web_server_survey.html) report the number of sites running a given platform, but you can have a single server cluster running 1000 sites or more. Apache is the completely dominant server platform on the net, but you can get apache for just about any OS and machines counted in the IIS part of the survey can also be running apache without any vmware. 

If you *really* want to make a proof about the best you could do would be to mine netcraft's "what's this site running" reports for the last few years. Pick a couple hundred big, well known sites and see how they have evolved.

---

