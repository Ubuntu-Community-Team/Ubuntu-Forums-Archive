---
title: "setting up a local domain with windows7 / virtualbox / ubuntu / apache"
date: 2009-09-07
forum: Server Platforms
---

### Post by cr0wn3r on 2009-09-07
I have ubuntu 9 as a LAMP server running as the Guest OS in virtualBox on a windows 7 machine.

I'm trying to understand how to set up ubuntu / apache etc so that I can use "sub.domain", rather than just "localhost" to access the apache webserver from the Windows 7 PC. I am only interested in local access.

At the moment Virtual box automatically turns [http://localhost:8888](http://localhost:8888) in to a port 80 request directed at the virtual ubuntu machine. So that works fine.

I have

localhost:8888/client1
localhost:8888/client2

working already, directing to local checkouts of my projects, but my development/debugging software wont accept the "/" character in specifying a website url....

So at the moment I work on a remote server using 

client1.dev-domain.com
client2.dev-domain.com
client3.dev-domain.com

etc.

I want to know if I can set up 

client1.local
client2.local
client3.local

or something similar, to work localy on my internal network? Means I can use the local virtualbox server, and still use my debugging software.

Thanks.

---

### Post by cr0wn3r on 2009-09-08
turned out to be more of a virtualbox question than a ubuntu one - and I worked out how to do it.

---

