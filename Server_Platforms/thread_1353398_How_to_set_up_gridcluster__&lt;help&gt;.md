---
title: "How to set up grid/cluster ? &lt;help&gt;"
date: 2009-12-12
forum: Server Platforms
---

### Post by aruncs on 2009-12-12
Hi, 
I am new to this forum. 

I have a couple of desktops with me(each have their own processors,harddrive,ram..etc) and i want to set it up as a grid/cluster/distributed(dont knw which term suits best.

1) Basically, i should be able to use it as a web server and run apps in like php,python,..any language.. so should be able to ssh and FTP into it.

2) ssh into it and run c,c++,... 

3) Also be able to run parallel computing tasks like MPI and openMP and use both the machines as a single computing interface.

I wanted to know how to get this started. Read quite a bit about ubuntu server edition, am not sure if i should use server/desktop edition .or if the process is entirely different.

Would be great if any of you could throw some light on this and help me in setting this up.

Thanks in advance.

---

### Post by Vegan on 2009-12-12
Sounds like you will have an uphill job, as what you want is relatively high end.

---

### Post by aruncs on 2009-12-12
yes .. any suggestions on how to proceed ?

---

### Post by Jekshadow on 2009-12-13
It sounds like this is what you are looking for:

[http://boinc.berkeley.edu/trac/wiki/DesktopGrid](http://boinc.berkeley.edu/trac/wiki/DesktopGrid)

---

### Post by craigp84 on 2009-12-13
Rocks
Cluster Knoppix
Open Mosix
Eucalyptus

Have a google on these names, you're bound to turn up something you fancy giving a try.

Alternatively, start off simple then expand. Install one machine, with very light customisation (turn on sshd, turn on webserver). Deploy to the other hosts now setup networking and have them able to ping each other. Setup a common user on each, install ssh key to enable processes on one host to trivially invoke commands on another host. Build it out to do whatever it is you want to.

p.s. The terms are always misused so don't worry about getting them wrong too much. Grid == collection of distributed nodes, often in geographically seperate locations, the nodes are generally untrusted. Cluster == collection of nodes in the same location, often connected with a very high speed network (infiniband?), nodes are generally trusted.

---

### Post by munky99999 on 2009-12-13
Generally speaking. You cluster with other OS.

To stay with ubuntu you can try
[URL="https://help.ubuntu.com/community/UEC"]
Ubuntu enterprise cloud[/URL]
[MpichCluster]("https://help.ubuntu.com/community/MpichCluster")
[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide")

Otherwise ya. Go with 

Rocks
Cluster Knoppix
Open Mosix

Or [http://www.dragonflybsd.org/](http://www.dragonflybsd.org/)

---

