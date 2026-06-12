---
title: "How to access virtual instances running on the Ubuntu Cloud from remote desktop?"
date: 2010-08-08
forum: Server Platforms
---

### Post by marmik1903 on 2010-08-08
I am a novice in the world of cloud and recently managed to configure Ubuntu 9.04 Cloud (using kvm, eucalyptus and other packages) successfully at my college for my project work.
The problem is that i can only manage to view the running instance using rdesktop from any remote machine. Is there any way to do this other than rdesktop/logs?
 
Secondly, I want to develop a application on the lines of google docs as a part of my project. Is it possible to install apache server on this virtual instance, and host a website? How will the client access this website? Which frameworks would be required or do I have to develop one?
 
Please Help.

---

### Post by stlsaint on 2010-08-08
For remote management why not use ssh?

And for the apahce in vm: [http://www.linuxquestions.org/questions/linux-software-2/apache-forward-requests-to-a-vmware-virtual-machine-223292/](http://www.linuxquestions.org/questions/linux-software-2/apache-forward-requests-to-a-vmware-virtual-machine-223292/)

---

### Post by marmik1903 on 2010-08-10
i guess i ws not able to frame my question properly.
I do not wish to remotely manage the machine but instead what i want is a simple google docs like interface(which i will be developing) to be some how interact with the UEC (private cloud) that I have configured.(What i know is that google docs runs on a cloud but how the web interface can run on a cloud is still what i am not able to grasp)
I have managed to bundle windows XP and Fedora on to a virtual instance which then runs on the cloud and run it on remote desktop.
My questions gist: Is it possible to provide a web service (like google docs/clutterpad) to clients on cloud and how? 
I have to implement this and am not finding any resources

---

### Post by srinivasanand on 2011-03-13
Hi Friends, We could not able to understand, how  does the Created VM’s can be accessed from Remote Place or (web). We had  successfully created CC, CLC, WS. in one Node  (eth1-192.168.1.7) and  Nodal Controller (192.168.1.8) using Ubuntu 10.04 Server (GUI-Converted)  and Created VM Using Virtual Box and installed Ubuntu 10.10 on VM  (192.168.1.13)  All the nodes (CC, NC, & VM) are configured and  bridged and it is communicating. we are also having 1 static(WAN) IP and  it is already configured to eth0 of CC.
 

Update: I found how to access through SSH, but i need to know, how to connect through VNC or similar interfaces


 Thanking You
Srinivas

---

