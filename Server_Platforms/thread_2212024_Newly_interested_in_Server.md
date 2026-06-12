---
title: "Newly interested in Server"
date: 2014-03-18
forum: Server Platforms
---

### Post by GNUway Tech on 2014-03-18
I've never used, or even tried, a Server distro before, and I know I pretty much would have no earthly idea how to do everything from the command line. I know how to install software from the Terminal screen, but I really don't understand anything outside of sudo apt-get. Now, I'd like to setup a private cloud, and I'm debating between buying a Western Digital cloud server and learning how to setup an Open Stack cloud.

As I understand, you can install the Unity desktop on Ubuntu Server, and run the basic settings from there. If I do that, how much can I do from Unity???

Also, I would like to learn Juju to setup up services. In addition to cloud services, I would also like to do DLNA and basic file server function. I understand there's a lot of information out there to go by, but testing a Server distro from the command line intimidates me a little. I'm thinking of trying it out from VMWare or VirtualBox until I can get a good machine to build.

What do I need to know to get a good start at learning Ununtu Server, running it from Unity, and deploying services in Juju???? I would like this to be as cost efficient as possible, which is where my conflict is. I'm not sure I could set one up as cheap as I can buy one. But, I would like to setup my own if it will give me greater control.

Any info you can give a beginner would be appreciated.

---

### Post by tgalati4 on 2014-03-18
I'm wearing my purple JuJu tee-shirt, but I'm not sure where to begin.  I would start with a simple desktop install if you want to run Unity.  JuJu is in the repositories, so you can just install it.  You have some reading to do.

[https://help.ubuntu.com/community/Orchestra/Juju](https://help.ubuntu.com/community/Orchestra/Juju)

[https://help.ubuntu.com/community/UbuntuCloudInfrastructure](https://help.ubuntu.com/community/UbuntuCloudInfrastructure)

You can search the *PopularPages* link below to get information on setting up other services.

---

### Post by slooksterpsv on 2014-03-18
A few things:
1 - If you need a dedicated server for more than one person, you may need to plan price, speed, size, etc. If it's just for you, an old computer with ethernet and amount of storage you want will work.
2 - It's best to administer the server from the command line in my opinion. I'm not aware of any native graphical tools that you could use. You can, however, install web-based items to control certain aspects of your server - webmin is one - here's a great article on ServerGUI - [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)   Landscape is an option, but I've never used it. Webmin is awesome!
3 - Best to learn by trial, if you want to dabble around before any hardware, use a virtualbox and set a bridged network connection and test it out on VirtualBox.

Those are my suggestions at the moment, dog wants outside.

---

### Post by GNUway Tech on 2014-03-18
Thanks for the info sources. I'll check them out.

As I understand, Juju can deploy anything graphically. I've seen a few videos about it on YouTube. It looks pretty simple. Either way, I'm sure I have a lot of reading to do.

---

### Post by LHammonds on 2014-03-20
You might want to review my notes on how I setup a basic Ubuntu server.  I do it in such a way that it can grow as needed over time and easy to maintain.

[My Notes on How I Install and Configure Ubuntu Server](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=191)

I have other tutorials on my site (and sig below) if you'd like to venture into other types of servers.  I have no experience with JuJu though.

LHammonds

---

### Post by GNUway Tech on 2014-03-21
I'll take whatever info you can give me. The easier it makes it the better.

---

