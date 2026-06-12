---
title: "connecting to local computer inside network from external ip of router?"
date: 2010-01-27
forum: Server Platforms
---

### Post by louis--taylor on 2010-01-27
hi there!
I am having problems connecting to my local machine from an external computer (connected by the internet). Since my external ip address connects to the router (a bt home hub which I do not own [sharing it with other people in my house]) I cannot find the local machine on the internet. I want to use this computer as a simple web server, so I need to be able to connect via the internet. I can use the computer as a web server on the local network fine, but it needs to be able to be seen externally. Is there any way I can do this? As I have no access to the home hub thingy, I cannot redirect any traffic.
I *might* be able to get access to the router if I ask *very* nicely, but I doubt it.
Can anyone help? or is this an impossible problem?
Any help is appreciated!

---

### Post by gobbledigook on 2010-01-27
you will need to give your local pc a fixed ip, and forward port 80 to your machine inside the network, using whatever NAT facilities are available on the home hub... haven't personally used one so can't help you there!

other ports you might want to forward for other uses are 21 for ftp and 22 for ssh.

---

### Post by louis--taylor on 2010-01-27
So I cannot do this without access to the router?

EDIT: I now have admin access to the router, can do anything I like to it.

---

### Post by louis--taylor on 2010-01-27
Its ok, I have found the way to do this, very simple :(
In the bt web settings ([http://api.home]("http://api.home/")) add a new 'Game & Application Sharing' thingy and select 'HTTP Server'. Ta Da! done.

---

