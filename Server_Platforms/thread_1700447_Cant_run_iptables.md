---
title: "Cant run iptables"
date: 2011-03-05
forum: Server Platforms
---

### Post by acastrolorenzo on 2011-03-05
Hi everyone,

I am trying to make start an iptables.cf script on my server.

I have copied it into */etc/init.d/*
And try to make it load with */etc/init.d/iptables.cf start *
Then "not permission" (I was the root then).
So, *sudo /etc/init.d/iptables.cf start*
Then, "command not found".

Any idea?
Thanks a lot! :D

---

### Post by elico on 2011-03-05
give us the output of the 
> cat /etc/init.d/iptables.cfand 
> ls -l /etc/init.d/iptables.cf
and  try the command
> chmod +x /etc/init.d/iptables.cfand then run the file.

---

### Post by CharlesA on 2011-03-05
What are you trying to do with the script?

I've been using iptables-restore to apply rules at boot.

---

### Post by BkkBonanza on 2011-03-05
While you probably setup iptables using init.d it probably isn't the best way. Usually you want to have it init during the network being brought up to get correct sequencing. So putting your script in /etc/network/if-up.d/ directory is better as it will be run when the interfaces are brought up. If you do that it needs a different form than init.d scripts. But there are lots of examples around too. This is "neater" as it is managed by the normal network init scripts then. I have an example from my router/firewall if you need one.

---

