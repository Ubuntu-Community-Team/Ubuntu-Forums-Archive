---
title: "Class Project"
date: 2015-03-06
forum: The Cafe
---

### Post by PC-2011 on 2015-03-06
So I am taking an experimental new computer class in my high school. It consists of students creating there own projects from coding to fixing teacher computers and building basic circuit boards. When then school replaced one of our computer labs we got some old computers with Intel core 2 duo I don't know how much ram is in them yet they just got dropped off them off at the end of class and I did not get time to boot one up yet. So I don't know all of the specs of them yet. We have 4 at the moment and plan to add more as they become available. They will not have internet access at the moment either. They will have a private network to connect to each other I have 2 questions first is where is a good place to start on clustering these machines together and should I use Ubuntu server or desktop. Last what is a good program to start with on here some of us in the class want to do a prime number search but what are some other options.

---

### Post by Matthew_Harrop on 2015-03-07
> **PC-2011 said:**
>  first is where is a good place to start on clustering these machines together and should I use Ubuntu server or desktop. 

If you want to create a mini network then there is no reason for it to have a server, that said it really depends what you want to do with them. If you want to run a web server or database or something like that, then you should use the server edition. You should keep in mind, however, that the server edition comes with not much installed so you'll need to download all the appropriate packages from a machine that has internet access.

> **PC-2011 said:**
>  Last what is a good program to start with on here some of us in  the class want to do a prime number search but what are some other  options. 

Write your own! If that's what you mean, then you need to select a language and then an appropriate IDE (try eclipse, that's a jack-of-all-trades)

---

### Post by grahammechanical on 2015-03-07
First you need to find out how to network those PCs together to form what in effect would be a private cloud. And as you want to add other PCS as they arrive I suggest that you look into MAAS.

[http://www.ubuntu.com/cloud/tools/maas](http://www.ubuntu.com/cloud/tools/maas)

And then there is OpenStack

[http://www.ubuntu.com/cloud/](http://www.ubuntu.com/cloud/)

[http://www.ubuntu.com/cloud/openstack](http://www.ubuntu.com/cloud/openstack)

[http://www.ubuntu.com/cloud/tools](http://www.ubuntu.com/cloud/tools)

Let us not forget Juju

[http://www.ubuntu.com/cloud/tools/juju](http://www.ubuntu.com/cloud/tools/juju)

I hope that you accept that learning how to research and learning how to study and apply what is learned is an important part of education. 

Regards.

---

### Post by cariboo on 2015-03-08
If all you have is 4 computers, and you know nothing about networking, I'd suggest starting with baby steps. Add an 8-24 port switch to the network, and setup static ip addresses on the computers. Use the network for file sharing using either Samba or NFS, both are fairly easy to step up, all though the learning curve may be fairly steep.

---

### Post by PC-2011 on 2015-03-08
I know some stuff about networking and know Java, PHP, JavaScript, HTML, CSS. I have about 10 workstations in my basement each run a task such as email, web server, MySQL, active directory and Group policy, teamspeak and a few other programs along the way. Finished watching some videos about MAAS With Juju, do I need an internet connection at first out project will not get internet till we prove that the project is worth keeping then we get more workstations to work with and internet access. Can I run java applications we have a few java coding classes and I would like to make it so they can bring there projects in on a flash drive or something and then we can run it. If I want to have the master the only server to have access to the internet and have it still run DHCP to the inside private network. I think if we do get internet access they will give us the old cat5 cable that ran to the classroom we are in so we cant go really expanding since they have to manually add each computers information to get it internet access. I'm going to keep studying this topic of MAAS. Thanks for all the great responses and i hope my questions are not too stupid.

---

### Post by SeijiSensei on 2015-03-09
> **PC-2011 said:**
> If I want to have the master the only server to have access to the internet and have it still run DHCP to the inside private network. I think if we do get internet access they will give us the old cat5 cable that ran to the classroom we are in so we cant go really expanding since they have to manually add each computers information to get it internet access.
If you have one computer acting as a gateway for the others, then the only computer that will appear on the cat5 network is the gateway.  All the other computers behind the gateway will be "masqueraded" to the upstream network.  If you run isc-dhcp-server on the gateway, you shouldn't have to add any information about the systems manually.

You could just get a simple home router and put it between these workstations and the upstream computers.  Turn off the radio if it has wifi and just use wired networking.  Most home routers have only four LAN ports, but you can buy a [cheap network switch]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833704027") and plug it into the router to expand the number of available ports.

---

### Post by PC-2011 on 2015-03-10
Can Maas run a prime number search or something is dose it only support programs Web services  and databases? I was playing with the live demo and could not understand how to make multiple  nodes work as one? Are they any youtube videos or documents about these concepts out there?

---

