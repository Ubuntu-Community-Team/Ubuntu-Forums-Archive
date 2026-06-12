---
title: "Creating a Virtual Server Environment on Feisty"
date: 2007-06-25
forum: Server Platforms
---

### Post by dcurran on 2007-06-25
I am looking to create a server environment that supports partial virtualization so that I can run a number of VPSs to house my personal web projects.

Although I am not sure exactly how to go about this what I have found leads me towards using Linux-VServer.

I found a tutorial/guide here - [http://www.linux.com/articles/59149](http://www.linux.com/articles/59149), but this talks about using 6.10, I tried following the directions here but on 7.04 and when completed the vserver build command seg faults. uname -r still returns the 2.6.20-15-server version for my kernel so I am betting the kernel update did not go as planned, which is most likely the reason for the segfault.

I have tried installing both 6.10 and 6.06 on this same machine but the installation fails saying that it can not find the CD-ROM. From what I have seen this is a problem with the SATA drives (ati_piix), which I am not versed enough in linux and hardware to find a work around.

So where I am is that I have a 7.04 install which segfaults when I try to create a virtual environment, and I am unable to install Edgy Eft and try the setup there.

What should my next steps be? Does anyone know of a guide to setting up partial virtualization on Feisty? Or have advice on different routes I should look into.

I am really looking for a partial virtualization solution so that I can really play around in the virtual server environment and not have to worry about causing problems that would affect my other install applications.

Thanks in advance for any help you can offer,
Dan

---

### Post by dcurran on 2007-06-25
I have been doing some more searching and it looks like another option would be to use a virtualization application called Xen. It looks like it has a lot more use and documentation that Linux-VServer had, and their are tutorials specific to Feisty Faun.

---

### Post by gombadi on 2007-06-25
There are a few options available. Which one is best will depend on your skill set, what you want to achieve and how much time you want to spend setting it up.

Xen as you have found. You can apt-get it so will be easy to setup and configure.

VMware server is also in the ubuntu commercial repository so you can also apt-get install it. It has a nice graphical interface to configure it.

I also use openvz on my systems. [http://www.openvz.org]("http://www.openvz.org") You will have to compile your own kernel - instructions available at [http://www.zagbot.com/knowledge.html]("http://www.zagbot.com/knowledge.html") Very nice with a low overhead per VM.

---

