---
title: "Raspberry Pi and Ubuntu Web Service"
date: 2013-11-30
forum: Server Platforms
---

### Post by Cybin on 2013-11-30
Hello,

I have a simple Web Service written in C# with monodevelop. I also have a python script that can send and recieve json requests to this service when running localhost. We are now at the end of my understanding..... searches have not yielded anything straight forward as to how to do this.

What would i have to do in order to allow the python script to run on a Raspberry Pi, talking to the Web Service which is running on a laptop installation of Ubuntu 13.04?

I have wifi/boardband via a router for both the Pi and a laptop. The Web Service is an asmx service.

Both apache2 with mono_mods and xsp are installed but really, i'm uncertain on this.
Do i need to configure virtual hosts?
Will there be firewall/blocking issues with the router?
Would laptop localhost be possible via the router, as a remotehost?
This is purely for testing purposes for the Raspberry Pi talking to this Web Service. Are there any step by step tutorials?

Kind regards.

Daniel

---

### Post by tgalati4 on 2013-11-30
What version of Raspbian?  What version of python is on this Raspian installation?  Does your service work correctly from Ubuntu to Ubuntu machine?  I would test it first with identical versions of Ubuntu to rule out version differences.  Firewall shouldn't be a problem as long as you are on a local area network.  If your service uses specific ports to transmit data and those ports are less than 10000, then that could be an issue.

You shouldn't need virtual hosts, and I don't understand the question about localhost via the router.

Proper web service requires /etc/hosts to be correctly defined on both machines.

---

### Post by Cybin on 2013-11-30
The software appears to be fine.

I am using the basic NOOBS raspbian with python 2.7. The webservice works fine when debugging on my laptop and i can run it with xsp and apache as localhost, as well as in the IDE. I have not connected to the service from another machine. This is the bridge i am seeking to cross. Locally, we're all good. I just am not sure how and what to do in order to allow transactions between these two machines. Or _any_ two machines in this manner. Please forgive my ignorance, i have sought tutorials online but i do not seem to be able to find them.

---

