---
title: "New to MaaS, OpenStack &amp; Juju."
date: 2016-08-04
forum: Ubuntu Cloud and Juju
---

### Post by derwood2 on 2016-08-04
Heya Folks,

While I'm new to the community of Ubuntu, I would just like to say "hi" :D

I have myself a copy of both server version of Ubuntu 14.4 and 16.4 both LTS versions, I'm having some nightmares here for the last week and I'm feeling at a loss with the ease at which the almost single page installation, quick setups for getting MaaS, OpenStack and Juju installed and running. I'm even awaiting for contact from Ubuntu Advantage because I love the idea of getting some support here and in the long term too. 

Firstly I have a setup exactly like this:

Region and cluster controller:
DELL FS12-NV7 x 1
dual socket quad core 2372 EE
16 GB RAM
160GB HDD
Dual 1Gbit NICs
IP: 192.168.0.3

Nodes:
DELL CS24-NV7 x 4 (This number will grow to around ten to fourteen)
Dual socket quad cores 2373 EE
16 GB RAM
2x 80GB HDDs
Dual 1Gbit NICs
IP | DHCP

Networking:
8 port Gbit switch

Home Router:
192.168.0.1

it's all fairly simple, my home router has a link to a port on my switch, the region/cluster controller has port two and each node has a port then on after that, if I install 14.4 server edition, then MaaS WoL never finds a node ever but it appears OpenStack and Juju would install fine from launching the commands to install and configure, I can even make an SSH key and it works, but I cannot add any more MaaS APIkeys.

Trying to install 16.4 LTS with MaaS 2.0 always finds the nodes, I can do as I please with them and it's a simple process, but trying to install OpenStack or Juju never turns up much at all, even trying conjure-up using any setting offered always dies and can never bootstrap, I also cannot add an SSH key ever, but I can create as many MaaS APIkeys as I wish.

I've been playing with this for a complete week, using all means before me from finding documentation online, work arounds, commands to get me a little further.. Anything.

So far work around commands come in all shapes, always best to install just the server first then edit the locale file so that it has LC_ALL=C, this seems to prevent the databases from messing up later on when you're installing OpenStack, juju and other SQL style databases,

I really need some help here, I would just simple like to at least have a single physical server (region/node controller) and a set of four nodes set-up without playing around with VM installs, Would anyone like to walk and talk me through from the initial inserting the .ISO in the drive up until it's all working. I would even be happy to pay a fee to someone willing to help me out.

At the end of the day the whole idea of me doing this was to be able to launch a VM on my laptops or from my workstations that could use all available RAM,Compute resources when I require while also being able to launch other VMs here and there for doing tasks.. So I'm at a bit of a loss here currently.

Thanks to anyone that can help me out with my personal private cloud mess..

---

### Post by derwood2 on 2016-08-04
I was just thinking about a fee to someone for helping me out?

How would £10GBP per hour until whichever Ubuntu 14.4/16.4LTS along with MaaS either 1.9/2.0, with all nodes, Openstack and Juju are installed and we can get a few VM instances running to do as I wish?

I'd be happy to do this via the internet using video skyping and would be willing to donate a further 10GBP to Ubuntu for supporting the community further.

---

### Post by derwood2 on 2016-08-04
This is what I have done the last two hours..

   Firstly, install Ubuntu 16.4LTS server edition with nothing apart from at the &#8220;choose software to install screen&#8221; selecting:
 
 
 *standard system utilities
 *OpenSSH Server
 *Virtual Machine Host
 
 
 once installed open an SSH link to the server IP, login, sorted a server install is comlete at the base..
 
 
 now using this link:
 [https://maas.ubuntu.com/docs/install.html](https://maas.ubuntu.com/docs/install.html)
 
 
 it alerts me that to install MaaS I need to type in these commands as follows below:

 
 
 *But just before that type in sudo nano /etc/defaults/locale and then enter this into the file CTRL+O, return, CTRL-X to exit..
 LC_ALL=C
 
 
 then carry on with below to save an issues with database issues..
 
 
 Adding MAAS package repository is simple. At the command line, type:
 $ sudo add-apt-repository ppa:maas/stable You will be asked to confirm whether you would like to add this repository, and its key. Upon configumation, the following needs to be typed at the command line:
 $ sudo apt-get update[h=3]Installing a Single Node MAAS[/h] At the command line, type:
 $ sudo apt-get install maas
post install requires you to create an admin MaaS account using this command:
sudo maas-region-admin createadmin
and fill in what required...



didge@WOPR:~$ sudo maas createadmin
Username: root
Password: 
Again: 
Email: [email]dar@URL.co.uk[/email]
didge@WOPR:~$ 


If you tried to login in to IP/MAAS prior to this you'll see a screen telling to to make a user, like below..

[IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-Login%20|%20WOPR%20MAAS%20-%20Mozilla%20Firefox.png[/IMG]


First lets start downloading some &#8220;images&#8221; for the nodes, like below:
[IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-Boot%20Images%20|%20WOPR%20MAAS%20-%20Mozilla%20Firefox.png[/IMG]

Takes a little while, so lets setup the account. My HomeRouter has the IP of 192.168.0.1, my MaaS region/rack controller is 192.168.0.3 and each of the nodes will be getting their IP from the 192.168.0.1(HomeRouter)
Goto &#8220;Networks&#8221; and click on the main IP address for the NIC like below where highlighted.
[IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-Networks%20|%20WOPR%20MAAS%20-%20Mozilla%20Firefox.png[/IMG]

After clicking on the highlighted IP you should see a screen like this.
[IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-192.168.0.0-24%20|%20WOPR%20MAAS%20-%20Mozilla%20Firefox.png[/IMG]

  [IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-192.168.0.0-24%20|%20WOPR%20MAAS%20-%20Mozilla%20Firefox-1.png[/IMG]

Seems fairly simple
here its marked &#8220;Gateway IP&#8221; you would add the MaaS server IP
(192.168.0.3) and in the DNS field you want (192.168.0.1) because
that si the HomeRouter handing out IP addresses for everything linked
inside the home network.
 So lets try it..
[IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-192.168.0.0-24%20|%20WOPR%20MAAS%20-%20Mozilla%20Firefox-2.png[/IMG]
Check on the images that have been downloading, they might have finished by now:

  [IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-Boot%20Images%20|%20WOPR%20MAAS%20-%20Mozilla%20Firefox-1.png[/IMG]
Just leave all that
as it is for now.. 
 
 *Just to note
 NIC 0 MAC address: 6c:f0:49:68:b7:** (DHCP 192.168.0.3)

 NIC 1 MAC address:  6c:f0:49:68:b7:** (Unconfigured)

 
 
 Under the &#8220;networks&#8221; button click on the first fabric option because this will most likely be your main NIC and where it says &#8220;VLAN&#8221; and below that &#8220;untagged&#8221; highlight it and click it like below.
[IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-Networks%20|%20WOPR%20MAAS%20-%20Mozilla%20Firefox-1.png[/IMG]

---

### Post by derwood2 on 2016-08-04
That should bring you up a display like below..
[IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-Default%20VLAN%20in%20fabric-0%20%7C%20WOPR%20MAAS%20-%20Mozilla%20Firefox.png[/IMG]

 Now what we should do is &#8220;enable DHCP&#8221; you can do this by clicking on the &#8220;take action&#8221; orange button.



[IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-Default%20VLAN%20in%20fabric-0%20%7C%20WOPR%20MAAS%20-%20Mozilla%20Firefox-1.png[/IMG]  
it's given us these simple options and I've applied them :D
[IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-Default%20VLAN%20in%20fabric-0%20%7C%20WOPR%20MAAS%20-%20Mozilla%20Firefox-2.png[/IMG]

  
Now I'm going back to the &#8220;nodes&#8221; page and going to see if I can start a node up by pressing the power button, if nothing comes of anything, I shall manually input the MAC address of the node and restart that idea again

 
 
 WOW!, my node is already set to PXE boot once I press the power button, fired up straight away, then turned off.. I see this as being normal and it's just getting to know the MaaS region/rack controller.
 
 
 So I go and click on the node that's showing in the &#8220;nodes&#8221; page, and I need to edit it's name so I just click top left and upon the name to rename it!

[IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-Node001.maas%20%7C%20WOPR%20MAAS%20-%20Mozilla%20Firefox.png[/IMG]

  
Also I need to edit it's power type, I want this to be &#8220;manual&#8221; like below..
[IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-Node001.maas%20%7C%20WOPR%20MAAS%20-%20Mozilla%20Firefox-1.png[/IMG]

  
Now I need to repeat what I have done, on the same amount of nodes I currently have, that being three of exactly the same machine.. chip for chip!
 
 
 Node002: Does not want to come up, it's trying to boot but showing  
 
 
 &#8220;IP-Config: enp0s8 hardware maas -enlist hostname maas-enlist IP-Config: no response after 9 seconds &#8211; giving up&#8221;
 
 
 I've tried it twice, to boot now, so I will enter that manually after I have tried my last node..

 -Node3 has done exactly as it should, and the same as node one.. Come-up, been noticed and gone down..
 
 
 Even though all three nodes are exactly the same down to their motherboard, and even including the exact same setting within the BIOS something is a miss here..
 
 
 So node 2 I shall, manually add in and see what comes of it..
 
 
 I just tried node002 again, just out of interest, and it turned out to work this time! Third time lucky!
 Edited the name and edited the &#8220;manual&#8221; power setting too..

  [IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-Machines%20%7C%20WOPR%20MAAS%20-%20Mozilla%20Firefox.png[/IMG]

So it appears we can find all the nodes I have, now to &#8220;commission&#8221; them..

 
 
 now all machines are showing as ready..
[IMG]http://www.wisecorp.co.uk/maas-install/Screenshot-Machines%20%7C%20WOPR%20MAAS%20-%20Mozilla%20Firefox-1.png[/IMG]

  
After this we need to install &#8220;Autopilot&#8221;, &#8220;OpenStack&#8221;, &#8220;Juju&#8221; Simple.. But is it...

---

