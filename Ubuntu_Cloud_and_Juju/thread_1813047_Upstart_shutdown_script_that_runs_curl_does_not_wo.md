---
title: "Upstart shutdown script that runs curl does not work when instance is terminated?"
date: 2011-07-27
forum: Ubuntu Cloud and Juju
---

### Post by obeattie on 2011-07-27
Hi,

I have a bit of a bizarre situation using the Ubuntu EC2 images. I have an upstart job that runs when the machine is halting (start on runlevel 0), and it works fine when I shut the machine down myself with shutdown -h now.

However, when the instance is terminated by EC2 (which will be happening a lot, since we are using autoscaling), the job does not work. It's very difficult to get further debugging information, however, since the machine obviously is destroyed forever a few seconds after the job fails to run.

The script itself POSTs some data to a server of ours, which then does the job of taking it out of the application pool, load balancer etc. So it's pretty critical it can run properly.

Any ideas why this might be happening?

—Oliver

---

### Post by kim0 on 2011-07-27
What might be happening is that EC2 is simply pulling the plug on the VM, not allowing it to perform a clean shutdown and running shutdown scripts

---

