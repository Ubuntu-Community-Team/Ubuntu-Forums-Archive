---
title: "Setting up a Cluster with Tomcats, a MySQL-Cluster, Git repos, internal trac..."
date: 2012-08-16
forum: Ubuntu Cloud and Juju
---

### Post by crapman on 2012-08-16
Hi there everyone, this is my first post, but I've been visiting this forum for quite a while and found many of your answers very helpful. 

This post is not about setting up said cluster, but it's about evaluating our options. Us, being [www.clusterlog.net]("http://www.clusterlog.net") with many clients that are sending us a lot of data each day, which needs to be available at all times.

The problem is, our servers are simply getting to small to handle the load. Which means we either buy ourselves faster servers, or we start building a cluster, which gives us the freedom of actually putting another server right next to it in a couple of weeks.

The specs of our environement are:


[LIST]
[*]We need to have full Tomcat 7 support, loadbalancing, Session Sharing,...
[*]MySQL Support
[*]Git repos may end up being in the cloud, more hardware means more space and git is not really putting a toll on performance.
[*]same may ably to the internal trac.
[*]Git and trac may end up on a different server for security reasons, but the support itself wouldn't hurt.
[/LIST]
It would actually be very nice if we wouldn't need to administrate two seperate clouds (MySQL, Tomcat) not only for the administrative-staff, but also for the load. Since the load is in some cases on the MySQL and sometimes on the Tomcat. To handle peaks, it would be nice that either one could just grap most of the cloud.


Does Ubuntu-Cloud meet our specs?

---

### Post by geazzy on 2013-08-04
I'm sorry  I cant help you...
I hope sameone can help you problem :D

---

### Post by wealthy2 on 2013-08-05
> **crapman said:**
> Hi there everyone, this is my first post, but I've been visiting this forum for quite a while and found many of your answers very helpful. 

This post is not about setting up said cluster, but it's about evaluating our options. Us, being [www.clusterlog.net]("http://www.clusterlog.net") with many clients that are sending us a lot of data each day, which needs to be available at all times.

The problem is, our servers are simply getting to small to handle the load. Which means we either buy ourselves faster servers, or we start building a cluster, which gives us the freedom of actually putting another server right next to it in a couple of weeks.

The specs of our environement are:


[LIST]
[*]We need to have full Tomcat 7 support, loadbalancing, Session Sharing,... 
[*]MySQL Support 
[*]Git repos may end up being in the cloud, more hardware means more space and git is not really putting a toll on performance. 
[*]same may ably to the internal trac. 
[*]Git and trac may end up on a different server for security reasons, but the support itself wouldn't hurt. 
[/LIST]
It would actually be very nice if we wouldn't need to administrate two seperate clouds (MySQL, Tomcat) not only for the administrative-staff, but also for the load. Since the load is in some cases on the MySQL and sometimes on the Tomcat. To handle peaks, it would be nice that either one could just grap most of the cloud.


Does Ubuntu-Cloud meet our specs?

These requirements (specs) shouldn't have anything to do w/ Ubuntu, I mean, any distribution would do!
Although I understand that the thread is bit old and you are just inquiring to evaluate, is/was it going to be a in-house setup or an actual cloud solution provider such [Ubuntu One]("http://one.ubuntu.com") that you are/were looking for!?

---

