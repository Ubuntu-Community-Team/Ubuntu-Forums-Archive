---
title: "VMware Help"
date: 2008-03-01
forum: Server Platforms
---

### Post by MasterSkyJacker on 2008-03-01
Let me start off by saying I have little knowledge using linux, but I want to learn. 
I have successfully installed unbuntu 7.10 server edition on a Dell Poweredge 1900 with xeon processors. 
My goal is to use this server only to run vmware. 
I have looked at multiple tutorials on how to do this but these two look mostly correct. ([[COLOR="Red"]tutorial1[/COLOR]]("http://x86virtualization.com/virtualizationnews/howto-install-vmware-server-on-ubuntu-710-part-2.html") and [[COLOR="Red"]tutorial2[/COLOR]]("http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html")). 

Question 1: What is the correct way to install vmware server 1.0.4 on ubuntu 7.10 server edition? 
The reason why I am asking this is because I have yet to see a straight tutorial on how to accomplish this. Some of the tutorials say to install "these packages" and some say to install "those packages".
I only want to install EXACTLY what it takes to have a clean vmware server install on this ubuntu distribution.

Question 2: After I get vmware installed successfully, how do I run the vmware console to create virtual machines?
There is no GUI and I don't want a GUI, if I can get help. Do I need some kind of linux windows environment installed to view the vmware console locally? Or do I have to use a client machine on my network to access vmware?

A big thank you to anyone who can help me. I am glad to be part of the ubuntu community.

---

### Post by scxtt on 2008-03-01
for question 2, when your server install is working and accessible via the web - you can navigate to [https://servername:8333/](https://servername:8333/) and interface w/ VMs -- if you have none, you can download a binary client that will allow you to create VMs on any Windows/Linux OS that has a GUI ... there's also a website that will create basic VM configs that you can install to, i think it's EasyVMX.com -- if it's still around.

as far as installation goes, i just install it via synaptic (unless that version isn't 1.0.4, can't check now) or the tar.gz file VMware offers ... then run the vmware-config-install.pl script to configure it ... there are a couple of gotcha's in getting it all set up, but i've got them all worked out w/ my install of 1.0.4 ... it's not easy, but it's not hard ...

---

### Post by koenn on 2008-03-02
I did pretty much what you're trying to do 2 months ago.
here are my notes : [http://users.telenet.be/mydotcom/howto/linux/virtual.htm](http://users.telenet.be/mydotcom/howto/linux/virtual.htm)
they answer most of your questions
I did it on Debian, but I imagine ubuntu server will by pretty much the same.

---

