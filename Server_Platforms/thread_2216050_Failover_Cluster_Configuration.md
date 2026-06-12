---
title: "Failover Cluster Configuration"
date: 2014-04-09
forum: Server Platforms
---

### Post by tim39 on 2014-04-09
Hello everyone, 

I would like to setup 2 servers in a failover configuration, but I have some issues regarding the system's implementation. So then, I would like your kindly help. 

More specifically, I'm interested in connecting 2 servers in this configuration (with a heartbeat etc.) in order to be provided some fault tolerance and redundancy. The 1st server will process some data which will be stored to a database after the end of the process and I need to ensure in a way that if something goes wrong during the process with any component (hard drive or system failure etc), the 2nd server will continue the process. 

- Could you suggest me any ideas regarding software or hardware implementations?
- Is there any to search for, because I'm a little bit new to this. I would like to do this using open source OS distributions and packages.

Thank you very much in advance. 
Kind regards,
Tim

---

### Post by Kirboosy on 2014-04-10
Welcome to the forums! :D

I think [Hadoop by Apache]("http://hadoop.apache.org/") will have the features you are looking for. However without more details I don't know how much more help the community can be. (Also Hadoop has its own forums with gurus that could readily help)

What version of Ubuntu are you wanting to use? On April 17 the next LTS of Ubuntu will drop (14.04) and that will provide you with the latest and greatest in Ubuntu.

Hope that helps!
~Caboose

---

### Post by tim39 on 2014-04-11
Thank you very much for your promt reply Caboose! 

Great news! I think that I will use the latest Ubuntu Server edition. 

Have you ever heard the [Pacemaker]("http://clusterlabs.org/wiki/Pacemaker") and if this could help me in a better way? What further details would make you understand more about this implementation?

Regards,
Tim

---

### Post by Kirboosy on 2014-04-11
> More specifically, I'm interested in connecting 2 servers in this  configuration (with a heartbeat etc.) in order to be provided some fault  tolerance and redundancy. The 1st server will process some data which  will be stored to a database after the end of the process and I need to  ensure in a way that if something goes wrong during the process with any  component (hard drive or system failure etc), the 2nd server will  continue the process.

If it is simply one server does majority of the work, but if a problem arises server two will take over then Pacemaker with Heartbeat will work just fine. Hadoop would be more useful for high performance data processing. > The Apache Hadoop software library is a framework that       allows for the distributed processing of large data sets across clusters       of computers using simple programming models. It is designed to scale up       from single servers to thousands of machines, each offering local       computation and storage. Rather than rely on hardware to deliver       high-availability, the library itself is designed to detect and handle       failures at the application layer, so delivering a highly-available       service on top of a cluster of computers, each of which may be prone to       failures.

Hope that helps!
~Caboose

---

