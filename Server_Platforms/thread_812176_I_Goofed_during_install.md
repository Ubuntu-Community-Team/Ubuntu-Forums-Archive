---
title: "I Goofed during install"
date: 2008-05-29
forum: Server Platforms
---

### Post by neubert500 on 2008-05-29
I did not install the DNS,Mail,LAMP OpenSSH,and print during the install of 8.04 Server on my Dell PowerEdge 2400. I only installed SAMBA. Can someone with a working brain tell me how to go back and install these? 
Thanks

---

### Post by freebullets on 2008-05-29
i think you can use your ubuntu disk and install them without reinstalling ubuntu.  i'll get back to you with more info.

---

### Post by artesvida on 2008-05-29
Search the packages for everything you need (i.e. Apache, OpenSSH, MySQL, etc.  Not sure what you need for print though) at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Then do
sudo apt-get install <package>

I know, you probably want the package names too.  Off the top of my head:
OpenSSH:  openssh-server openssh-client
Apache:  apache2 (there are probably others here you want too)
MySQL:  mysql-server mysql-client

---

### Post by bmathis on 2008-05-29
the easiest way is to do a **sudo tasksel** and select the the options you want. it will grab the packages and do the install as if you choose everything earlier.

---

### Post by artesvida on 2008-05-29
> **bmathis said:**
> the easiest way is to do a **sudo tasksel** and select the the options you want. it will grab the packages and do the install as if you choose everything earlier.

Learn something new every day.  Never heard of tasksel before.  Thank you!

---

### Post by Bubba64 on 2008-05-29
> **bmathis said:**
> the easiest way is to do a **sudo tasksel** and select the the options you want. it will grab the packages and do the install as if you choose everything earlier.

This is bringing up synaptic-edit-mark packages by task.

---

### Post by NateMan on 2008-05-29
Why not manually install and setup the servers, instead of letting an auto installer do it? there are numerous guides, and you will learn quite a bit about your server in the process.

---

### Post by neubert500 on 2008-05-30
Thanks for all the help! Problem is fixed and I'm learning to pay closer attention to what I am doing.
Again Thanks!

---

