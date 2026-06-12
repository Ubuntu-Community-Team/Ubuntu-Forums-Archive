---
title: "Ubuntu Server Cluster - Advanced Topics - Help"
date: 2011-04-01
forum: Server Platforms
---

### Post by twister89 on 2011-04-01
Hello to everybody,

I'm deploying an heavy-workload website based on Joomla! 1.6. I'm going to use the AWS infrastructure with the Elastic Load Balancer, a number of Ubuntu Server LTS instances and a number of MySql external database.

The idea was [web]->[Load Balancer]->[WEB-SERVER(n)]->[DB].

I'd like to have your opinion about a few critical points.

First, Do I must to sync all the webserver? I know there's an extension for Joomla! called Multi-site that replicate the php code of the webservers and let them to connect at the same database, sharing the content.
I'm not sure if that is ok or if I need actually a distributed file system.

Second, could you suggest me an open source clustered filesystem well suited for production? Is it difficult to deploy in an ubuntu server lts cluster?

Third, about the DB management, as this is the first time I go so deep with a DB infrastructure, how do you suggest to deploy it for heavy-workload production ecosystem?
Do you suggest to deploy a Mysql DB cluster (with Load Balancer, multiple read/write DB instances sync. with MySQL replication) or a simpler architecture, with a central master write DB and a number of replicated read-only instances? How should I connect the webserver cluster with the Mysql cluster? Do you suggest me to use a second Load Balancer, to associate for each web-server one DB or to distribute the workload trough a load balancer, but modded for starting from the DB with the minimum to the maximum
replication lag time?

I know this are lots of thing and I'd really appriciate any help.
I really need it.

Thank you for all guys.

---

### Post by twister89 on 2011-04-01
Does anyone here ever tried MySql Cluster?

---

