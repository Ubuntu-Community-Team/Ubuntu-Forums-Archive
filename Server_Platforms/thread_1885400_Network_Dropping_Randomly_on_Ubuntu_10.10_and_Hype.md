---
title: "Network Dropping Randomly on Ubuntu 10.10 and Hyper-v"
date: 2011-11-23
forum: Server Platforms
---

### Post by edalloul on 2011-11-23
We have moved our physical servers to virtual servers on hyper-v. We  were running the Ubuntu servers for few years without any issues.  However since we have shifted the servers, the network connectivity  started dropping suddenly and in a random behavior. Once the issue  occurs, the server can't ping or ssh any server in the local or external  lan. Even restarting the network doesn't work. I can't find any errors  when I check the server logs. The only solution to get the server  running again is to restart it. Those servers are very critical to the  university since they run MySQL and LMS. So any help is really  appreciated.

---

### Post by spynappels on 2011-11-23
What versions of Ubuntu and Hyper-V are you using? I've had consistently negative experiences running Ubuntu on Hyper-V but as I recall, some had better experiences with different releases of Ubuntu.

I went back to ESXi and even ran VirtualBox on one Windows server after wasting nearly a week on Hyper-V.

Sorry to not be more positive!

---

### Post by edalloul on 2011-11-23
We are running UBuntu 10.10 on Windows 2008 R2 Hyper-V. The problem we have no choice over the virtualization engine, otherwise I would definitely go with VMWare. Our IT director (coming from Windows background) is now even asking to switch the ubuntu servers to windows if the issue is not rectified. Any help is really appreciated.

---

### Post by neomaximus2k on 2011-11-23
what response time do you get to the server's?

I'd setup a continuous ping and look see what the results are it could be something as stupid as network traffic, faulty switch / hub or network card either way at present it appears more hardware than software and moving to windows wouldn't solve that issue.

Can you install another network card in the machine and route virtual through that?

---

### Post by edalloul on 2011-11-23
I'm sorry I forgot to mention that the VM is running in a cluster environment. We tried to move the machine to different hosts but with no result. Plus we are facing this issue with only the Linux machines, the windows machines are running fine. So the issue can't be related to hardware or network cards.

---

### Post by neomaximus2k on 2011-11-23
hmmm is the machine under any stress while the network drops?

---

### Post by edalloul on 2011-11-23
Nooo that's the weired part. It fails after a period of time but it doesn't have to do with stress (or at least this is what I'm suspecting) because sometimes the network was dropping during off peak hours when our students are not accessing the servers. While searching the internet, I can see only people talking about the issue being related to hyper-v drivers on ubuntu for the synthetic network card, but I couldn't find any definite answer on what is the root cause for the issue and how to solve it.

---

### Post by spynappels on 2011-11-23
Is it an option to try using VirtualBox on one server to see if you can create a stable instance?

FWIW, all the problems I had also involved networking.

Have a look at the following, it has a list of the Hyper-V specific modules which are required to be enabled, not sure if it helps you any.

[http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx](http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx)

---

### Post by edalloul on 2011-11-23
The issue is that I can't reproduce the issue to know if VirtualBox will work or not. 

Thank you for the blog posted. I have visited the blog already , but those modules are enabled by default with Ubuntu. I can see them listed when I run lsmod and didn't have to add them to  /etc/initramfs-tools/module file.

---

### Post by rubylaser on 2011-11-23
I have (3) instances of 10.04 Server LTS running on our Hyper-V servers here at work.  We had problems initially, but after getting the modules setup correctly, they've actually been running ever since (almost a year now).  We did have to use a legacy network adapter in Hyper-V to get it working correctly though.

---

### Post by srdjo on 2012-02-15
I have the same problem - network drops after 3-4 hours. I reboot and works for 3-4 hours and it drops again.

What can I do to fix it ?

---

