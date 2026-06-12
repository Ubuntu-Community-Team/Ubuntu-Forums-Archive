---
title: "Using remote desktop for Rackspace Cloud Server?"
date: 2011-05-10
forum: Server Platforms
---

### Post by sneakyimp on 2011-05-10
I'm fairly new to Ubuntu as a desktop environment and was delighted to see System -> Preferences -> Remote Desktop.  I'm wondering if I might be able to use Remote Desktop functionality with a server that I instantiate using Rackspace.com's Cloud Servers product.

The basic idea is that this "Cloud Server" does not appear to be a desktop install from a CD and my guess is that it lacks all of the drivers and GUI software that Ubuntu uses to render a desktop on actual nuts-and-bolts hardware. At the very least, I will only have command-line access initially and I'm wondering if there are any Ubuntu command-line things I might to to enable remote desktop access on the Cloud Server so I can use my desktop Ubuntu system to have a GUI interface to the Cloud Server.  In particular, I'm very interested in the System Monitor.

Rackspace lets you instantiate Debian, CentOS, Red Hat, Fedora, Gentoo, and other distros as well as these versions of Ubuntu:
* 10.10
* 10.04
* 9.10
* 8.04.2

Any insights or advice would be most welcome.

---

### Post by spynappels on 2011-05-10
What sort of specifications does your Rackspace server have? Do you have full console access to it? It is generally considered unwise/unnecessary to install a GUI/Desktop Environment on a server as it adds more overhead as well as possibly creating more potential attack vectors.

You could have a look at Webmin, it allows you to see System Monitor type statistics and I found it a great help when starting off with Server Edition. You may find learning the basics of Command Line administration more flexible and rewarding in the long run however.

You also have the option of only installing X-server on the server and enabling X Forwarding over SSH so the GUI programms run on the server but are rendered on the client computer. This can be clunky over a less than optimal network connection, but it does work.

Finally, you can install a full Desktop Environment, but you'd need console access to set it all up and it really is not recommended.

---

### Post by sneakyimp on 2011-05-10
Thanks for your response.

I'm pretty familiar with the command line and commands like w/free/top to monitor system usage.  I just *love* the graphic display of the system monitor.

Not sure what specs you are asking for on the Rackspace Server.  It's not an actual dedicated server but rather a "Cloud Server" -- meaning that it's Ubuntu 10.10 installed on top of Xen hypervisor (I think it's Xen anyway). It's probably running on a main frame or some big beast of a server in a data center somewhere so there's no chance at all that I'll be able to plug in a keyboard.

I have no desire to bog down the machine with GUI software. It would just be nice to have a nice graphic performance monitoring tool which tracks CPU, disk, and network. Thanks for the tip on Webmin, but it looks a bit extensive/invasive to me. I think Cacti might be good for me.

---

### Post by spynappels on 2011-05-10
I was just asking what sort of RAM and storage you had, a Desktop on 256MB RAM is not a great idea at the best of times.

Cacti would also be a good option, I haven't got any experience with setting it up and what it needs but have seen it in action.

---

### Post by sneakyimp on 2011-05-10
I've instantiated the smallest Cloud Server for the time being (it's easy to scale them up if you need to).  256MB RAM, 10GB storage.  I definitely don't want to go through the pointless effort of installing all kinds of GUI stuff on the machine.  I was just wondering if there was some kind of instant/easy way to connect my Ubuntu desktop to a similar counterpart running in the cloud.  

I expect I'll just use "top" for now and will look into Cacti later this week.

---

