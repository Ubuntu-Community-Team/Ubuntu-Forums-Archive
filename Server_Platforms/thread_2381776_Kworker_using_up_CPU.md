---
title: "Kworker using up CPU"
date: 2018-01-05
forum: Server Platforms
---

### Post by ravimittal on 2018-01-05
[COLOR=#141414][FONT=Verdana]Hi,

We are facing this issue since two days on our server. Kworker is using up most of the CPU and our CPU usage is going to 100%. While the traffic on our site is high and the CPU is always having a load but our site was running all fine, however, this is the first time we are seeing 'kworker' on top of CPU usage and whenever it shows up, our site goes down.

Below is screenshot from TOP command:

[/FONT][/COLOR][IMG]https://i.imgur.com/7osNzb4.png[/IMG]

Could anyone help identify the issue and help with the solution?

---

### Post by howefield on 2018-01-05
Thread moved to the "*Server Platforms*" forum.

---

### Post by LHammonds on 2018-01-05
[https://askubuntu.com/questions/33640/kworker-what-is-it-and-why-is-it-hogging-so-much-cpu](https://askubuntu.com/questions/33640/kworker-what-is-it-and-why-is-it-hogging-so-much-cpu)

I see that you are running PHP5 but you gave us no other indication as to what OS you are running, the kernel, etc.

It helps to show what system you are running.  Example:

```

lsb_release -a
uname -a
apache2 -v

```

It would also be helpful to know if you have run the following commands recently:

```

apt-get update
apt-get upgrade

```

---

