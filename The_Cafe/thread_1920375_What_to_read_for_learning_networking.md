---
title: "What to read for learning networking?"
date: 2012-02-04
forum: The Cafe
---

### Post by Davh on 2012-02-04
Hi guys, I post this in THIS forum because I really like the community essence of participating :P.

I would like to understand more about networking, like (please don't laugh at me if I said something wrong haha) MySQL, Apache, php, routers functions like DHCP, etc...

I have a vague information of things about networks but I want to learn more about this... DO you know a web or doc to read?

In another post you guys have helped me and wrote me web pages to learn more about using Linux... Hope this thread need to be here, if not please remove it >.<!

Thanks!

---

### Post by haqking on 2012-02-04
> **Davh said:**
> Hi guys, I post this in THIS forum because I really like the community essence of participating :P.

I would like to understand more about networking, like (please don't laugh at me if I said something wrong haha) MySQL, Apache, php, routers functions like DHCP, etc...

I have a vague information of things about networks but I want to learn more about this... DO you know a web or doc to read?

In another post you guys have helped me and wrote me web pages to learn more about using Linux... Hope this thread need to be here, if not please remove it >.<!

Thanks!

[https://help.ubuntu.com/](https://help.ubuntu.com/) or example would be [https://help.ubuntu.com/11.10/serverguide/C/index.html](https://help.ubuntu.com/11.10/serverguide/C/index.html)

choose a version then the version page covers most of what you mnetioned, best way is to install and configure and play with them.

However use a second machine or a VM to do this so you dont trash your install.

I could post links and docs all day on how to learn each subject but i will leave it for some others to post.

---

### Post by JayKay3OOO on 2012-02-04
The best way to learn by far is to actually do it. Books can only teach you so much so if you want to do this in business you will need to learn Windows Server and I would recommend reading a book on this because you can just learn the book and blag the rest to get the job if you understand the underlying server concepts.

Here is what you should do:

1. Make avaiable another computer for server duties. If you don't own one you should pick up a cheap second hand one or build the lowest spec you can. The AMD zacate and intel fusion chips are great for this as you won't need power for home testing just a cpu, motherboard and possibly a graphics card to install the server OS

2. We're on a linux forum last time I checked so install ubuntu server onto this spare machine. It'll look terrifiying if you are not used to the command line environment.

3. U'll need some cheapo network hardware like a couple of switches and some patch cables. Remember a cable network is 10/100/1000 so make sure the cable can handle the network speed. Wired network is fastest (at the moment) for server.

4) Now with ubuntu server installed we want some remote admin so download webmin. You can use wget followed by the url to the file (usually sourceforge) to download it onto the server. You can figure out where the file is using the non server machine. Webmin allows you to install server services using a php web interface remotely.
Once donwloaded you need to install it so type sudo aptitude install filename. I think wget downloads to the directory you run it from otherwide you can simply type dir to view what's in the directory you are in using command line and cd to change directory cd .. or cd.. takes you back one directory. aptitude resolves dependancies that webmin needs dpkg -i won't. 

5) You will probably want to get to this machine using SSH (Secure shell) allows you to use the command line from another machine. If using another Linux machine you would SSH into the server by typing ssh user@ComputerName followed by the user password. SSH is more secure than webmin and you may have to install some packages using sudo apt-get install package name as webmin is not foolproof.

6) I guess that's it, the rest is up to you to fiddle with. I kid you not that I leant more by playing with this stuff than I ever did reading any book. A book will only help you understand why it does what it does, doing it will tell you how to do what you want and knowing why is secondary.

By using Linux server and the command line you will lean a lot of server functions that are used in Windows Server. The only difference being the GUI and the way windows server makes you set up these tools. I find the combination of webmin and SSH on ubuntu server a great mix once you understand both.

Have fun!

P.S. You can do all this by installing Ubuntu server into Virtualbox, but it's much more real to do it live. Heck, if you have a smartphone and one computer then you can use the webmin web page to admin the server from the phone.

P.P.S Google is your friend if you get stuck.

P.P.P.S. 24 years a Windows user, 2 a Linux user and a few months to learn Ubuntu server with 3 months to happy with the command line environment.

P.P.P.P.S. Not happy with the command line environment? All server functions can run off a normal Linux distro with a GUI or you can install the GUI to Ubuntu server. Oooooooh the choices!!

---

### Post by Davh on 2012-02-04
Thanks a lot guys!

Which version should I pick up? LTS or the last one (11.10)... More support with LTS when looking help at google?... or is just the same?

Diego V.H

---

### Post by haqking on 2012-02-04
> **Davh said:**
> Thanks a lot guys!

Which version should I pick up? LTS or the last one (11.10)... More support with LTS when looking help at google?... or is just the same?

Diego V.H

if its for experimenting and playing around it doesnt matter.

LTS is just supported for a longer time with updates and such like and more stable than later versions.

If you using VM's then install them both along with other distros to see how the services and configurations may differ etc

---

### Post by Pithikos on 2012-02-04
Learn to use Wireshark is a good beginning. 

Subscribe to these guys on youtube: 

[LIST]
[*] metalx1000
[*] elithecomputerguy
[/LIST]
 
I personally find books boring many times. Only place I can sit and read them is in the WC ;)

---

### Post by wojox on 2012-02-04
I have found this site good as well [linuxhomenetworking]("http://www.linuxhomenetworking.com/")

---

### Post by cariboo on 2012-02-04
Back when I first created my first network, I used the documentation at [tldp.org]("http://tldp.org/LDP/nag2/index.html"), it's a bit old now, but the principles are still the same.

---

### Post by ikt on 2012-02-05
> **wojox said:**
> I have found this site good as well [linuxhomenetworking]("http://www.linuxhomenetworking.com/")

Cheers, another one on the big long list :)

How I learn:

[IMG]http://ikt.id.au/blog/wp-content/uploads/2012/02/linuxbookmarks.png[/IMG]

Read, Do, Repeat Until Success.

Read up on the topic, put together a test system and muck around with it, then read some more on what I did wrong, what I did right and what I can change.

One of the great things about linux and ubuntu is that with an SSD you can install ubuntu fresh on bare metal in 5 minutes, or if you run a VM like virtualbox for testing applications you can revert back to your pre-screw up config in 2 minutes.

So easy to play around with things these days, no reason not to.

---

### Post by mips on 2012-02-05
If you want to learn 'networking' get yourself some Cisco CCNA-CCNP books and look at the following software for network/router/switch simulation purposes, Cisco Packet Tracer, Dynamips/Dynagen/GNS3, IOU.

---

