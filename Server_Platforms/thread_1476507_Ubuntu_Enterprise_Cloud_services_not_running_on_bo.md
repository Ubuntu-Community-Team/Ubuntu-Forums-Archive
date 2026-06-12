---
title: "Ubuntu Enterprise Cloud services not running on boot?"
date: 2010-05-07
forum: Server Platforms
---

### Post by mrsticks on 2010-05-07
I downloaded the latest 10.4 server CD with the intention of running a small Ubuntu Enterprise Cloud. I am following the directions here:  [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

Ive got 2 laptops that are capable of the tasks assigned to them.  Both have dual core Intel chips that are VT enabled, 4GB of RAM, 250GB hard drives.  

Ill use one ( "server" ) as the front end server running cc, clc, walrus and sc.

The other one ( "node1" ) will be the only node controller on my little network.  

Ive also got another laptop as a client, running euca commands to make instances and what not.

These three laptops are connected to a switch.  server is 192.168.1.100, node1 is going to be 192.168.1.110, the client laptop is 192.168.1.120.

the server seems to install fine, I select Install Ubuntu Enterprise Cloud, use it as the Cluster, give the cluster a name and 10 IPs to assign, 192.168.1.150-192.168.1.160

After the server is done installing and reboots, I boot the node machine off the CD and again select Ubuntu Enterprise Cloud.  It's at this point the install craps out, because it does not recognize a cloud computer on the network.

Indeed, as I go to the server I run ```
ps -aux | grep euca
``` and see nothing running.  So I start the eucalyptus service, and run ```
sudo euca_conf --list-clusters
``` and nothing shows up.

Ive done some googling, ran some more euca_conf commands, registering the cluster, enabling walrus, cloud and sc.  I can access the web gui on the client laptop, then restart the node install on the node laptop.

This time it does see the server as a cluster controller, but when it tries to fetch the preseed file, it seems to not know the cluster's IP, as the red box that complains about the lack of a preseed file lists the URL as [http://:8774/preseed/preseed.conf](http://:8774/preseed/preseed.conf) ( or whatever the file is called, I dont have the error in front of me. )

So that's my story.  I would've expected that since I entered in the name of my cluster and installed all of the services on the server, these things would be automatically configured and start up on boot after the install?  

The truly horrible part of the story is that I had this mostly working earlier in the week, without worrying about any of this.  Then the next day nothing worked, so I started reinstalling, and now I can't even get that far again.

Any help is greatly appreciated.

thanks

-peter

---

### Post by mrsticks on 2010-05-08
OK.  So the services dont start on boot, I am sure I can put them in some rc script and get them to come up on boot.

I manually started the services
```
eucalyptus
eucalyptus-cc-publication
eucalyptus-walrus-publication
eucalyptus-sc-publication

```

and was able to install the node controller, with it recognizing the cloud controller.  I take that to mean the autoregistration did not work.

Now I cant seem to register the node.  I had to manually exchange ssh keys, so now the eucalyptus user on the server can ssh w/o a password to the node.  

The command ```
euca_conf --register-nodes 192.168.1.110
```

Spouts out the INFO line about the location of the keys, then reports it was successfully able to exchange keys.

But ```
euca_conf --list-nodes
``` still shows nothing.

There is a file /var/lib/eucalyptus/nodes.list which has the IP, and I've manually put it in /etc/eucalyptus/eucalyptus.conf under NODES, but I still cannot get euca_conf to show me the nodes.

Also on the client, ```
euca-describe-availability-zones verbose
``` shows 000/000 for all instance sizes, confirming that I have no nodes to run instances on.

I have connectivity between all 3 machines on my little network, they are the only machines on the switch.

I can't believe the trouble I am having.  Anyone have any ideas?

-peter

---

### Post by mrsticks on 2010-05-09
```
sudo euca_conf --no-rsync --discover-nodes
```

just shows a blank line and then the INFO line about where Eucalyptus expects the keys to be installed.

Running the manual registration

```
sudo euca_conf --register-nodes 192.168.1.81
```

gives no error, successfully exchanges keys, but does not register the node.

I can ssh from the server to the node as the eucalyptus user with no password, so the key exchange works.  There's no firewalls running.

I also don't have any nc.log files on the node.  From other topics I have read, this would further confirm that the node is actually not successfully registering with the server.

Anybody out there?

-peter

---

### Post by mrsticks on 2010-05-09
Still, for some unknown reason, my eucalyptus services do not start on boot.  So I start them up by hand each time the server reboots.  I know, I know, I'll put that in a script.

I think the order in which I start them up matters.

I have had somewhat better results with starting the services in this order
```

eucalyptus
eucalyptus-cloud-publication
eucalyptus-cc-publication
eucalyptus-sc-publication
eucalyptus-walrus-publication

```

This is on the server, which runs everything but the node controller.  I have also noticed that if I set 

/etc/eucalyptus/eucalyptus.conf
```

NODES=" "

```

and make sure the node I am trying to autodiscover is not in /var/lib/eucalyptus/nodes.list

running 

```

sudo euca_conf --no-rsync --discover-nodes
```

actually does detect my one and only NC and asks me if I want to add it.  I say yes, and it gets added to the nodes.list file, but not to the configuration file.

And still at this point
```

sudo euca_conf --list-nodes

```

shows nothing.

---

### Post by gsker on 2010-05-09
You got further than I did.  I discovered a problem with having libvirt-bin installed on the cloud controller machine due to conflicts between eucalyptus and dnsmasq. And I continued to see an error about IFACE not being defined. I finally hardcoded IFACE to eth0 in /etc/init/eucalyptus-network.conf.   

I did a package install rather than the CD one.  I finally got to the point of the cloud installing, but when I try to start an image on a node, it complains that the kernel isn't there even though the command line says it is.

I will be watching this post as I bang my head on the wall about this some more. 

Good luck. I suspect there are more people out here, but some of us are sorta floundering.

---

### Post by mrsticks on 2010-05-09
I've been banging my head for a week.  I had this up and running for the most part last week, but then it just stopped.  I've been reinstalling all week, 10.4 and 9.10.  I never even looked at these config files.  I am wondering if there's something wrong in one of mine that is preventing something from working right.

My nodes don't have a nc.log file either, but the nodes do show up in nodes.list, but not in the config file.

I dont know much about your kernel errors.  When I was in better shape, I did download one of the images and loaded that on.  What does the web admin say?  Mine did have a kernel and ramdisk under the Configuration tab.

This whole thing has been the biggest PITA I've ever had with Ubuntu.  It must be something completly stupid we're missing, it's just not apparent to us now!

Best of luck to us both!

---

### Post by mrsticks on 2010-05-10
Victory!

On a suggestion, I changed the loglevel in /etc/eucalyptus/eucalyptus.conf.  I used ERROR and FATAL to get the logs to be not terribly verbose, and that pointed out an error in the configs.

cc.log was complaing about not seeing VNET_SUBNET, and several other VNET_ config options.  These options are defined in /etc/eucalyptus/eucalyptus.local.conf, but not in eucalyptus.conf.  I moved them over, and BAMN, everything fell into place.

I'm going to move a VM image on to the controller now and run with it.

My advice to you would be the same, decrease the verbosity of the logs and go through them.

Good luck

---

### Post by yogesh.girikumar on 2010-05-12
Hi,

Adding to this, please see this : [http://cssoss.wordpress.com](http://cssoss.wordpress.com)

It's an Eucalyptus Beginners' Guide aimed at making it easy for newbies to build an Eucalyptus based cloud. 

It might help some visitors of this thread.

---

### Post by mrsticks on 2010-05-12
Thanks for the link, it's a pretty good guide.  I appreciate how the troubleshooting part lists changing the loglevels.  This was key for me.  By default, it's at the highest verbosity, and was producing 130MB/ming of cc.log.  Tailing it was useless as, after a minute or so of scrolling text non stop, it would mess up the character map of my screen.  

Now that I know my error, I might reinstall the server I was using as the SC/CC/Walrus controller and see what it does with the settings I give it during the install.  As I said, all the errors I got were complaining about variables that were set in /etc/ecualyptus/eucalyptus.local.conf.  As soon as I put those vars in eucalyputs.conf, the errors stopped.  But by looking at some of the scripts in /etc/init/ it would seem that the eucalyptus.local.conf should have been included when the services started.  If this is a bug and not my own error, it probably does not happen when you install from apt-get.  I installed from the CDs.

-peter

---

