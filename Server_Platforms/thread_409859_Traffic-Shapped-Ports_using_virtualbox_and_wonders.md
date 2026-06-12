---
title: "Traffic-Shapped-Ports using virtualbox and wondershaper"
date: 2007-04-15
forum: Server Platforms
---

### Post by airtonix on 2007-04-15
Just wondering what the possibilites of creating a set of virtualised linux machines that expose virtual NIC devices to provide shaped traffic for spcific ports?

purpose is to havea fault tolernat, relativly easy to setup shapping solution for small to medium scenarios.

ie host machine runs the virtual box server.

machineOne is for HTTP (port 80 :: shaped @ in:10kb/s out: 5kb/s)
machineTwo is for Torrents (port 6881 ::shaped @ in: 60kb/s out: 20kb/s)
machineThree is for MysqlServer (port ???? ::shaped @ in: 10kb/s out: 100kb/s)
machineFour is for Apache-World-Server (port 8080 ::shaped @ in: 10kb/s out: 100kb/s)
 {m4 port8080 <=> adslRouter p80}

Each virtual machine would be off the same ISO, and would each pull their own wonder shaper config script from the host computer's special shard directory. they would not be running for example apache or mysqlm instead thos programs would be configured to send their traffic through these virtual-machines or "virtual-shapers"

does this sound possbile? i know i can create a virtual machine on a real computer that for all intents and purposes appears to be just another machine alongside the host, and to the other computers on the subnet/localnetwork it appears as if i just connected a another machine..

any thoughts, ideas, suggestions?

---

