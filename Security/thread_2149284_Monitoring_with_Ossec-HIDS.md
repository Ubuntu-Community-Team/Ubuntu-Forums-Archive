---
title: "Monitoring with Ossec-HIDS"
date: 2013-05-28
forum: Security
---

### Post by siddharth007 on 2013-05-28
Hi everyone.I have several servers in my environment and i am monitoring them using OSSEC tool(Ossec manager-agent architecture).My requirement is that the agents(Ossec-clients) should report to the manager(Ossec-server) whenever there is a connection taking place between two servers(on two different ip's).For example,take the scenario where we have two servers,the application server and the database server(both of them have ossec agent module installed).There is a third server,the log server(Ossec manager) where these two agents report.Now whenever the application server is restarted it connects to the database server.So there is a network connection established between the two servers.This connection information should be logged at the Ossec manager module.

---

