---
title: "server unreachable now and then"
date: 2006-07-10
forum: Server Platforms
---

### Post by dragonflyFZX on 2006-07-10
hi

i have a laptop at home which i use as a server.  It runs several services such as apache, ssh server,...  Since I have adsl and an ISP that assigns me a dynamic IP, I use no-ip.com redirection services with their nifty update program.

Recently, i have been noticing frequent periods that my server is not reachable.  I thought it was because of a change in the IP, but is appeart they stay the same bofore and after the downtime of the server.

Are there any tools i can use, or suggestions on how to get to know where the problem lies?

D

---

### Post by apjone on 2006-07-10
check /var/log/ also do try 

watch ifconfig > test.txt

this out put ifconfig to text.txt ever so many seconds. this is not ideal but may help.

It could be that someone else has the same ip as you.

---

### Post by teike on 2006-07-12
I would suggest running a monitoring app from the local box and an external source to see if its a problem with network transport or possibley something locally. I use a program called [Monit]("http://www.tildeslash.com/monit/") that is pretty easy to setup and it can monitor a lot of different network services and can run scripts to email alerts or even restart a service if it's been determined to be failed.

With monit you could verify the services on the machine. You might look at monitoring the dns servers for your dynamic name resolution also... It may be an issue with DNS resolution.

Hope this gives you some direction.

---

### Post by dragonflyFZX on 2006-07-13
thanks for the replies, but i really need some more details here.  I dont have a clue what i have to watch for.  Furthermore, i dont think the problem is on the server.  I think it has to do with the setup of my routers.  I have a dsl router, followed by a wireless router.  Is there a way to see where the trafic gets stuck when i try to reach the server from outside?

---

### Post by dragonflyFZX on 2006-07-15
it is becomming even weirder.  When the server becomes unreachable, it seems that, using one of these on line port scanners, only ports 21 and 23 remain open (it says that these ports have a service running).  Even though i dont rermember having opened these ports on my routers...:confused:

---

