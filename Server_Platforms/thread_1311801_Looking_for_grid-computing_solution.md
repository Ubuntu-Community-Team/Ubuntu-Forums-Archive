---
title: "Looking for grid-computing solution"
date: 2009-11-02
forum: Server Platforms
---

### Post by joeinbend on 2009-11-02
This question may have been asked before, although indirectly. I was pretty excited about the new Ubuntu Enterprise Cloud available in Server 9.10, however after trying to set up a test environment, it didn't seem to be quite what I thought it was. Admittedly, I'm still not 100% of what "it" is, and I'm sure I'm not alone in that.

What I'm looking for, and hoping it's not a "yeah, wouldn't we 'all' love something as non-existent as that, buddy!!", answer. I am looking for a solution where I can take a bunch of older generation "servers", gigabit networked together, and basically cluster their hardware resources. I'd like to be able to do this in a grid-computing fashion, where I can and/remove Nodes at will, and a central server will manage "knowing" which Nodes are available. What would be awesome is if this front-end central server would "present" to me a platform where I can build virtual machines (Ubuntu servers, Windows servers), and how well the virtual machines perform is simply a factor of how many Nodes are available to collectively power the virtual environment.

I'm just talking about CPU and RAM allocation in this little dream, and I'm also just talking about machines that are on the same subnet, with a solid gigabit network backbone. Perhaps the designated management machine would be responsible for housing the storage.

But, while we're dreaming, how about adding distributed storage to the equation? Whatever hard disks are available on the Nodes can be offered up as block-level distributed storage, something like (or maybe exactly like) the way ATAoE works. Maybe in this dream we also offer up co-location of resources, meaning you can have Nodes that are outside of your network, connecting via SSL and shared-keys to give a nice balance of security and networking simplicity.

Maybe all of this is possible already? Pinch me!

---

### Post by 565Customz on 2009-11-02
thats almost the same thing i have done in my house, with  thin clients (based on winblowz) to control lighting and sound system.(6 touch monitors hooked to a server and the server does all the computing) although its no where near the scale your talking about, and i have no idea how to do it on linux

---

### Post by 565Customz on 2009-11-02
oh, but by the way, i have seen some stuff where colleges used gaming consoles to do this, there is a program for it...give me a sec ill see if i can find it.

[http://www.product-reviews.net/2008/02/18/scientists-love-gaming-consoles-instead-of-super-computer-sony-ps3-and-nintendo-wii-in-particular/](http://www.product-reviews.net/2008/02/18/scientists-love-gaming-consoles-instead-of-super-computer-sony-ps3-and-nintendo-wii-in-particular/)

check this out...might give you a start

---

### Post by 565Customz on 2009-11-02
distributed computing...thats the name for it.

---

### Post by joeinbend on 2009-11-02
Thanks for the lead 565, good info there. It seems like your home automation setup is almost the opposite of what i'm after: yours is thin clients handled by 1 central server, whereas I'm looking to take several lower-end computers and virtually combine them into a single computing unit.

In my mind, I'm envisioning something similar to the way a VMware vMotion Cluster works, where you have multiple servers, they're all managed by a central vMotion server for resource allocation, and if a server (Node) were to fall offline, the VM's would continue to run, redistributed to the remaining Nodes. Something like that would be perfect, but capable of running on lower-end, consumer-grade hardware.

---

### Post by 565Customz on 2009-11-02
yeah i realized that after i posted it lol. took me a minute to figure out what exactly you were tryin to do

---

### Post by epsolon77 on 2009-11-03
I've been playing with ProxMox and Xen.  Currently though ProxMox only supports 64bit processors, and that doesn't fit for my old servers at all.  Many VM options seem to require VT class processors, which don't fit in to our current hardware scheme.  

I would highly recommend modifying your ideal structure a little bit.  For your combined storage run an ISCSI target/client system with several independent storage arrays.  You could even get fancy and try and PXE boot the whole lot.

I have links to my preivious discussions about similar topics and will be watching closely :popcorn:

[http://ubuntuforums.org/showthread.php?t=1273891&page=7](http://ubuntuforums.org/showthread.php?t=1273891&page=7)

[http://ubuntuforums.org/showthread.php?t=1291145](http://ubuntuforums.org/showthread.php?t=1291145)

---

### Post by joeinbend on 2009-11-03
That's sort of the same Catch 22 I've been seeing as well: such an elegant solution won't run on old hardware, so in some senses what it boils down to is tomorrow's old hardware will work for this scheme, but not today's!

In practice what I've actually done is taken my Ubuntu Server, Plopped in a quad-core Phenom II 955 processor and 8GB RAM, and I use it as the ultimate all-in-one server: It's my RAID-5 storage, my ZoneMinder security DVR, SqueezeCenter streaming audio server, ProFTPd, Apache2, as well as VMware Server 2 with 7 VM's of varying flavors, and dual NIC's so I can route my DMZ independently and securely to it. Definitely an "all your eggs in one basket" setup, but I don't run any commercial services, so... so what :)

---

### Post by 565Customz on 2009-11-06
[http://www.stevekelly.eu/cluster.shtml](http://www.stevekelly.eu/cluster.shtml)

does this work for you joe?

---

### Post by epsolon77 on 2009-11-06
> **565Customz said:**
> [http://www.stevekelly.eu/cluster.shtml](http://www.stevekelly.eu/cluster.shtml)

does this work for you joe?

That's a great link.  I had not heard of Kerrighed and will have to test it out.  Sounds like running a VM on top of that cluster could be pretty sweet.  Does any one know will Eucalyptus allow 1 VM to run across all nodes or is cloud computing different from clustered computing.  Damn way to many terms out there.

---

### Post by 565Customz on 2009-11-06
yeah i have no idea what kerrighed does to make it work, but i did a little research on it, and it seems to me it works almost like BOINC, just on a local network. maybe im wrong though..im just a newb..

---

### Post by 565Customz on 2009-11-06
[http://www.kerrighed.org/wiki/index.php/Main_Page](http://www.kerrighed.org/wiki/index.php/Main_Page)

man if they could make that work with cuda...you could fold@home like NASA...holyshiznit that would be sweet...im gonna email the developer

---

### Post by joeinbend on 2009-11-06
Good find! I'm going to check that out this weekend in my lab if I can make the time. Also note, look on the kerrighed.org site under Downloads, they have a liveCD version. Performance will probably be lacking but that'd be a great place to start to get a quick proof-of-concept up and running to see what it can do :)

---

### Post by joeinbend on 2009-11-06
Hey guys, regarding running VM's on top of said cluster, it looks like others have done it with Kerrighed! take a look at this list! People are reporting running both VirtualBox and VMware!! 
[http://kerrighed.org/php/clusterslist.php](http://kerrighed.org/php/clusterslist.php)

---

### Post by epsolon77 on 2009-11-06
Well I think this settles what my next project is.  Force a few of my diskless P3's into service with PXE boot and see if I can run a VM set off it.  Hopefully I can make it hot recoverable too...  It looks like kerrighed won't add and delete nodes on the fly, but I hope to soon find out.

---

### Post by 565Customz on 2009-11-06
this looks to be a fun project, but unless i just happened to have the parts just "laying around" i wouldnt bother with it

what you need to be doing, is learning c++ and CUDA...we are talking supercomputer from a graphics card here. 192 cores of math based processing all going at once. i PROMISE you i will beat whatever cluster you set up.  

that said...what are you trying to do with your cluster Joe?

---

