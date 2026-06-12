---
title: "Virtual Thick Client"
date: 2012-08-10
forum: Server Platforms
---

### Post by mitser on 2012-08-10
Hi Guys
I wanted to develop a kernel for my server. It will work in following way:
* ECLIPSE(IDE) process is running on client(local data) w/o actually being installed on client, it is rather installed on server, so all libraries/files are on server
* So when client wants to run IDE, it requests server for IDE's process. The process will be sent to client and it will run  locally(on client) whereas libs are on server, so I want to establish communication between process and libraries for running the IDE
* Finally client can just close connection, and the process is gone with no trace of IDE since it is not installed on client. So its like "USE AND THROW service".
Please help me out, I am a newbie. Sorry for explaining same thing again and again.
For simplcity i will use a Linux Client.....

**Summarization:**
->APP (lib etc..)installed on SERVER
->DATA present on CLIENT i.e local
->APP's PROCESS running on CLIENT



* Its more like serving /opt via NFS .

* Is it feasible to make an linux based server which as s/w installed that will b used by clients as temp process running on client.
* The only diff between a cloud and my server will be that d processing will take @client rather than on server(as in cloud) even though the software is installed on server itself.

*****************************************************************
Now why such complications??

At this moment I just want it for Eclipse. In future I may installed more S/w , so my clients will more than one s/w to work with w/o installing them locally.
So clients just need a good connection and RAM to run s/ws with no hdd or small hdd for storing their local data......

So its enjoying Software As Service locally.........

So plz help me out.......

[my email ID is [email]skynetsecure85@gmail.com[/email]]

---

