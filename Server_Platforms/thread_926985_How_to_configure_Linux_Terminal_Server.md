---
title: "How to configure Linux Terminal Server"
date: 2008-09-22
forum: Server Platforms
---

### Post by koganin on 2008-09-22
Hi all,

  I am very new to the Linux computing scene and so I apologize in advance for my noob questions. Any help, however, would be greatly appreciated!!

  I just recently configured a server at home with Xubuntu 7.04 (Feisty) and although it took me some time to figure it out and find some help it was definitely a good learning experience. I followed the instructions I found on bit-tech.net.

  However, there is a server that I was asked to configure in the lab that I work in. I'm really enthusiastic about learning more about the Linux computing environment so I decided to try and configure it.

  The server is a Dell PowerEdge 2900 III. Right now, it has two hard drives (1TB and 250GB), two ethernet cards, and 4GB RAM. In the lab, we use two applications that are relatively memory-intensive. App#1 runs only on Linux and App#2 runs only on Windows.

  What I'd like to do is setup this server with two workstations (thin-clients?) that can make use of the server at the same time. However workstation1 should be able to run linux while workstation2 should be able to run windows (or vice versa).
I'm just a bit confused as to how to go about configuring this.:confused:

From what I've read, I can install an LTSP server from the 8.04 ISO. But I'm not too sure about how to configure the network devices and the IPs.
  With this configuration, would I be able to accommodate the following scenarios? :
    1. Take workstation1 and run App1(runs on Linux only)
    2. Take workstation1 and run App2(runs on Win only)
    3. Take workstation2 and run App1
    4. Take workstation2 and run App2

  Again, I apologize for such a long post and these beginner questions. Any help would be very greatly appreciated!! :smile:

---

### Post by koenn on 2008-09-22
I don't think you understand the concept of a "terminal server".
In a terminal server scenario, applications **run on the server**, although the are controlled by a user on a remote workstation (the terminal), i.e. key strokes and mouse movements are send from the user's workstation to the app on the server, and the output of the application (be it text or a graphical display) is sent to the workstation's monitor.

Given that applications run on the server, and you have 2 applications, one that requires Windows and one that requires Linux, what you want means that the server has to run both operating systems at the same time. That's impossible.

You can simulate a server running 2 operating systems simultaneously by virtualizing one (or both) of the operating systems. 
Look for threads on virtualbox, vmware server or virtualization. virtualbox (or 'virtual pc' on Windows) is a good way to get to know virtualization if you have no idea what it is.
For production server work, you'll want Xen or Vmware.

---

### Post by koganin on 2008-09-22
Hi Koenn,

  Thanks for the response. I really appreciate it.:)

  I definitely understand that the apps are running off the server. Thats for sure. I was just confused as to how to configure the box so that I could accommodate two different users being able to use either app1 or app2.

  I've been coming across virtualization methods and I will most definitely be looking more into what you have suggested.

  Thanks again!

  Cheers

---

### Post by koenn on 2008-09-22
> **koganin said:**
> 
  I definitely understand that the apps are running off the server. Thats for sure. I was just confused as to how to configure the box so that I could accommodate two different users being able to use either app1 or app2.

well, actually that's easy enough (here are some simple proofs-of-concept [http://users.telenet.be/mydotcom/howto/linux/xremote.htm](http://users.telenet.be/mydotcom/howto/linux/xremote.htm) ) , but not if app1 needs to be running on windows, and app2 needs to be running on linux, all on the same server.
That's what the virtualization is for.

It's interesting stuff to play with, virtualization.
Have fun.

---

### Post by koganin on 2008-09-22
koenn, the link you provided is much appreciated! Very informative.

I'll be sure to post an update here to show my progress (or setbacks =/)

Thanks again. :)

---

### Post by koenn on 2008-09-22
> **koganin said:**
> 
Thanks again. :)
welcome

---

### Post by koganin on 2008-09-22
I was able to successfully install the LTSP setup from the Ubuntu 8.04.1 Alternate CD onto the server box. I may be missing something here, but I assumed that the next step would be for me to go ahead and right away boot my thin-client (my laptop) thru the PXE protocol.

I tried to boot off the network via PXE protocol but was unable to do so. Error msg is: Unable to locate bootable ROM file (or something along those lines).

Any help would be appreciated guys. Thanks in advance. :)

---

### Post by cariboo on 2008-09-23
Have a look here for LSTP documentation:

[http://wiki.ltsp.org/twiki/bin/view/Ltsp/Documentation](http://wiki.ltsp.org/twiki/bin/view/Ltsp/Documentation)

Jim

---

