---
title: "Ubuntu Enterprise Cloud - troubleshooting"
date: 2010-02-08
forum: Server Platforms
---

### Post by john-boy on 2010-02-08
Hi all,
I have enthusastically installed UEC on two machines and was very happy at how easy it was following this guide [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

Now I have downloaded my first VM from the UEC Store using the web interface hosted on the Controller. But whenever I start up an instance from the command line on the Controller, it terminates after a very short period.

Where should I begin with troubleshooting this? I know there are logs in /var/logs/eucalyptus but there seems to be a lot of information in all of these. What should I be looking out for in particular?

My controller is 32-bit, my single node is 64-bit. 
Thanks for any pointers.

---

### Post by john-boy on 2010-02-09
I have progressed a bit further so hopefully this will help others.

I looked at the logs on the Controller server in /var/log/eucalyptus but couldn't find any obvious errors.

I then switched my attention to my one and only node and looked at the logs in /var/log/eucalyptus

I issued the command:
cat nc.log | grep error
and found this line:
error: insufficient disk capacity remaining (2047MB) in vm type of instance i-4cb904938 for component disk

I then went into the UEC web interface and increased the amount of disk space for each vm type (c1.xlarge, c1.large etc.).
I started up another instance like so:
euca-run-instances -k mykey emi-XXXXXXXX -t c1.medium
and the instance did not terminate, whoo-hoo!

The command 
watch -n5 euca-describe-instances
showed the instance was running and what its IP address was. I was able to ping the instance from the Controller.

Now I just need to be able to connect to it :???:

---

