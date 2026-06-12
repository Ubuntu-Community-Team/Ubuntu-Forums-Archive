---
title: "Server Clusters"
date: 2013-01-19
forum: Server Platforms
---

### Post by chrisguk on 2013-01-19
I presently have two servers running within the same LAN.  One server is presently my DNS server and the other is used as a file server.

I have read numerous comments and in and around Google regarding server clusters.  I thought it would be an advantage to see what the community experts have to say about the subject.  

So my questions are:

1.  Is there an advantage of having both servers in a cluster?
2.  What is the easiest way to achieve a cluster setup with two machines running on Ubuntu Server 12.04 LTS?

I will leave it at that until I have answer to the above as the answers may lead to more questions.

Thank you in advance for any help with this. ):P

---

### Post by thnewguy on 2013-01-19
Maybe it would help if we knew why you were considering making a cluster? Do you want your servers share their workloads? Is this just a fun experiment at home to see how it works? What are you hoping the end result might be?

---

### Post by chrisguk on 2013-01-19
> **thnewguy said:**
> Maybe it would help if we knew why you were considering making a cluster? Do you want your servers share their workloads? Is this just a fun experiment at home to see how it works? What are you hoping the end result might be?

Hi,

Thank you for your quick reply.  

Its a kind of two fold issue really.  Yes I would like them to share the workload.

It is an experiment of a kind I guess.  Its probably more of a case of I want one environment for all while using both machines.

Does that make any sense?

---

### Post by chrisguk on 2013-01-19
bump

---

### Post by Habitual on 2013-01-20
> **chrisguk said:**
> I want one environment for all while using both machines.

Does that make any sense?

Chris: 

"I want one environment for all while using both machines" simply is too vague.

Perhaps if you explicitly describe what functions or tasks this "Server Cluster" would be expected to perform?

I encourage you to read [http://en.wikipedia.org/wiki/Server_cluster](http://en.wikipedia.org/wiki/Server_cluster)[URL="http://en.wikipedia.org/wiki/Server_cluster"]
[/URL]

---

### Post by thnewguy on 2013-01-20
My suggestion, for now, would be to read up on Ubuntu's cloud technology which allows you to experiment with setting up multiple services in a way that lets multiple computers share the work load. There is a pretty good introduction and documentation on doing this over at [http://www.ubuntu.com/download/help/install-ubuntu-cloud](http://www.ubuntu.com/download/help/install-ubuntu-cloud)

---

### Post by chrisguk on 2013-01-20
Hi again.

Essentially, with text taken from the Wiki I am looking for this:


A computer cluster consists of a set of loosely connected computers that work together so that in many respects they can be viewed as a single system.

"Load-balancing" clusters are configurations in which cluster-nodes share computational workload to provide better overall performance.

So I want to use them as a single system to cut down the time taken to switch from each machine.

Im looking at Crossroads right now

---

