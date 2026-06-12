---
title: "Host can't browse the VM website"
date: 2023-01-19
forum: Virtualisation
---

### Post by satimis on 2023-01-19
Hi all,

Host - Ubuntu22.04
VM/Guest - Ubuntu22.04
VirtualBox

I followed below document to setup fixed IP address on the VM.

Ubuntu Static IP configuration
[https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-18-10-cosmic-cuttlefish-linux](https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-18-10-cosmic-cuttlefish-linux)

Steps went through without complaint.

Now on Terminal host can ping the fixed IP address of the VM. Also on Terminal VM can ping the IP address of the host without problem.

On VM, I can browse the cloned website running on the VM with;
vm-fixed-ip/website-name/

But on host I can't browse the cloned website running on the VM with;
vm-fixed-ip/website-name/

Please see screenshot attached.

Kindly help. Thanks

Regards

---

### Post by TheFu on 2023-01-19
Is the VM configured for a bridged network in the virtualbox network settings?
[https://www.virtualbox.org/manual/ch06.html#network_bridged](https://www.virtualbox.org/manual/ch06.html#network_bridged)  I don't think any of the other network config options will allow what you seek, though perhaps host-only will?  IDK.

There's a handy table here: [https://www.virtualbox.org/manual/ch06.html#networkingmodes](https://www.virtualbox.org/manual/ch06.html#networkingmodes) that shows which parts of your network can access the VM. If I'm reading that correctly, only bridged allows LAN systems access to the VM network.

---

### Post by satimis on 2023-01-19
> **TheFu said:**
> Is the VM configured for a bridged network in the virtualbox network settings?
[https://www.virtualbox.org/manual/ch06.html#network_bridged](https://www.virtualbox.org/manual/ch06.html#network_bridged)  I don't think any of the other network config options will allow what you seek, though perhaps host-only will?  IDK.

There's a handy table here: [https://www.virtualbox.org/manual/ch06.html#networkingmodes](https://www.virtualbox.org/manual/ch06.html#networkingmodes) that shows which parts of your network can access the VM. If I'm reading that correctly, only bridged allows LAN systems access to the VM network.
Thanks for your advice.

Already configured for bridged networking.  Pls refer to screenshot.

Regards

---

### Post by satimis on 2023-01-20
Hi TheFu.

Further to my previous posting.

I have another ssd drive installed on this PC running;
VirtualBox
Host - Ubuntu 22.04
VM/Guest - Ubuntu 20.04

The same website is also cloned on the VM.

On Host running;
vm-ip-address/cloned-website-name/

can browse the cloned website without problem

Regards

---

### Post by MAFoElffen on 2023-01-20
As I remember from your past posts, on your VM, you are running LAMP Server with UFW... Are you sure you have ports 80, 8080, and 443 open? Temporarily turn off UFW to see if it works. If so, turn it back on and work on your firewall rules.

---

### Post by satimis on 2023-01-20
> **MAFoElffen said:**
> As I remember from your past posts, on your VM, you are running LAMP Server with UFW... Are you sure you have ports 80, 8080, and 443 open? Temporarily turn off UFW to see if it works. If so, turn it back on and work on your firewall rules.
Hi,

Thanks for your advice.

On Ubuntu 22.04 VM Terminal
$ sudo ufw status```

[sudo] password for satimis: 
Status: inactive

```
It is not enabled.

On Ubuntu 20.04 VM mentioned on above posting, LAMP is also running.

Regards

---

### Post by satimis on 2023-01-20
Hi all,

Make a new test on another Ubuntu 22.04 VM, also running LAMP

Follow below document to set up static IP;
Setting Up Static IP Address on Ubuntu 22.04 LTS
[https://linuxhint.com/setup_static_ip_address_ubuntu/](https://linuxhint.com/setup_static_ip_address_ubuntu/)

Also with the same result - loading images ...

$ sudo ufw status```

[sudo] password for satimis: 
Status: inactive

```

Regards

---

### Post by TheFu on 2023-01-20
Rather than describing what you believe, please post commands and output from those commands, so others can interpret.

Also, what do the different log files show?  If nothing it hitting the web server logs, then it is upstream causing the issue.  I suspect that php differences between 20.04 and 22.04 are the issue and the webapp is crashing, but until you look at the logs, you'll never know.

---

### Post by satimis on 2023-01-20
> **TheFu said:**
> Rather than describing what you believe, please post commands and output from those commands, so others can interpret.
.....

Pls advise what commands shall I execute ?

Just discovered;
On right top corner

wired connected
profile 2
static-ip
(pls refer to screenshot)

profile 2 - inet 127.0.0.1

How to remove it?  Thanks

---

### Post by satimis on 2023-01-20
Hi all,

Performed following steps;

On Ubuntu 22.04 VM, login the cloned website

Dashboard - Settings -> General
change: Site Address (URL) - [http://127.0.0.1/website_name/](http://127.0.0.1/website_name/)
to: Site Address (URL) - [http://vm_ip_address/website_name/](http://vm_ip_address/website_name/)

WordPress Address (URL) - [[http://127.0.0.1/websitename/]](http://127.0.0.1/websitename/])
is greyout and I can't change it

Now on Host, I can browse the website with all wordings displayed including embed YouTube video.  But all images disappear.  I can play the YouTube video.

Any suggestion?

Regards

---

### Post by satimis on 2023-01-20
Hi all,

Performed following steps;

On Ubuntu 22.04 VM, login the cloned website

Dashboard - Settings -> General
change: Site Address (URL) - [http://127.0.0.1/website_name/](http://127.0.0.1/website_name/)
to: Site Address (URL) - [http://vm_ip_address/website_name/](http://vm_ip_address/website_name/)

WordPress Address (URL) - [[http://127.0.0.1/websitename/]](http://127.0.0.1/websitename/])
is greyout and I can't change it

Now on Host, I can browse the website with all wordings displayed including embed YouTube video.  But all images disappear.

Any suggestion?

Regards

---

### Post by satimis on 2023-01-21
Hi all,

Again, now I get the images(graphics) back with following steps, except the background image

On Ubuntu 22.04 VM Terminal
1) 
$ sudo nano /var/www/html/hymns/wp-config.php 
change the line: define( 'WP_SITEURL', 'http://127.0.0.1/wesite_name/' );
to: define( 'WP_SITEURL', 'http://website_ip/website_name/' );
Save -> Exit

2)
Restart VM

Now WordPress Address (URL) 
change to - [http://website_ip/website_name/](http://website_ip/website_name/)

Now Host can browse the website remotely, except without background image.

I can't imagine it is so difficult?  I still have to struggle getting the background image back

Regards

---

### Post by TheFu on 2023-01-21
Seems the claim that the website was cloned, wasn't really true if the IP address reconfig wasn't carried over as well.  No way for anyone here to know what other things weren't carried over in the attempt.

this is less about "VM" stuff and more about the specific webapp you happen to use.  I've barely used WP, never installed it.  I suspect finding a WP-specific upgrade or migration how-to guide would be helpful.  Beware that moving from 1 OS to a newer OS will have changes in the software stack and you'll need to account for those changes.  I always read the release notes on the software in my server software stack, so if a different version of apache is used in the new OS, there are release notes that should list any changes that impact installations. Same for DBMS. Same for 3rd party modules.

---

### Post by satimis on 2023-01-21
Hi all,

I found out the cause of my problem here.  I did the wrong steps migrating/cloning live websites to a new VM installed on a new drive.

The wrong steps performed by me was;
1. Migrate the site to a new VM
2. Set up the static IP of the new VM

The correct steps should be;
1. First, set up the static IP of the new VM
2. Migrate the site to the new VM

In the wrong step, the static IP of the VM has been set up.  The Host can ping and connect the VM but can't browse the WP website, because the WP website still retains the old IP address, 127.0.0.1, installed during migration.

Now all newly migrated websites don't have the problem, unable to be browsed on the Host and other browsers on other VMs in the network.

It took me hours of Internet searching without result.  I discovered this problem through hours of testing.

Regards

---

### Post by TheFu on 2023-01-21
127.0.0.1 is the local host.    Sometimes it is listed as localhost or loopback in the /etc/hosts file.

Any address that begins with 127.x.x.x resolves to the local machine.  It wasn't "the old IP".  It is one IP for every computer in the world that is networked.  Android, iPhone, supercomputers, Unix, Linux, MS-Windows, OSX ... doesn't matter.  They all allow any 127.x.x.x/8 (that's CIDR notation) to ping.

It is a common way to allow network sockets to to point either at the local system or anywhere on the internet by using a 127.x.x.x IP and setting up the server listener to listen on any of those IPs.  It means the exact same code can be used for 1-machine deployments or multiple machine deployments.

127.22.0.1 or 127.0.0.53 or 127.254.254.254 are all the same machine.  The current one.  An IP calc tool output:
```
$ ipcalc 127.0.0.1/8
Address:   127.0.0.1            01111111. 00000000.00000000.00000001
Netmask:   255.0.0.0 = 8        11111111. 00000000.00000000.00000000
Wildcard:  0.255.255.255        00000000. 11111111.11111111.11111111
=>
Network:   127.0.0.0/8          01111111. 00000000.00000000.00000000
HostMin:   127.0.0.1            01111111. 00000000.00000000.00000001
HostMax:   127.255.255.254      01111111. 11111111.11111111.11111110
Broadcast: 127.255.255.255      01111111. 11111111.11111111.11111111
Hosts/Net: 16777214              Class A, Loopback

```

If a network service only listens on 127.x.x.x addresses, then it cannot be reached by foreign computers - even on the same LAN ... or VMs running on the same computer.  It is very convenient, once you understand.

---

### Post by satimis on 2023-01-22
> **TheFu said:**
> 127.0.0.1 is the local host.    Sometimes it is listed as localhost or loopback in the /etc/hosts file.

Any address that begins with 127.x.x.x resolves to the local machine.  It wasn't "the old IP".  It is one IP for every computer in the world that is networked.  Android, iPhone, supercomputers, Unix, Linux, MS-Windows, OSX ... doesn't matter.  They all allow any 127.x.x.x/8 (that's CIDR notation) to ping.
......
......

Thanks for your detail explanation.

WP website only listens to the IP address installed on their website.

There are lot of data stored and applications installed on a WP website.  When migrating a website it is needed to link all of them otherwise visitors can't browse the data nor able to run the application on the website.

If migrating the website before setting up a static IP, all of them will be connected to 127.0.0.1.  The link won't be changed automatically if changing the IP.  For such a reason I have to edit all connections manually.  Please refers to my posting #12 above.  

There are lot of work on searching respective information and editing the migrated website.  It is much simpler to delete it and do the migration again.

I have about 36 live sites running on Internet.  All of them have cloned sites running on local server for years, installed on Ubuntu 20.04 VM.  Now I'm prepared to migrate all of them to a new server, running Ubuntu 22.04 as Host and VM as well

Regards

---

### Post by TheFu on 2023-01-22
To be very clear, only the webserver is "listening" on the IP.  All the other things are just configuration so the returned webpages consistently point at the correct IP/DNS-name.  The webserver listening on 10.0.0.80:80/tcp  means that a connection to that address/port is possible, but when the data is returned, if 127.0.0.80 is in all the returned html, then the client making the request will look to it's localhost , not the remote server.  That's where all the php program and moduile configs come in.

---

### Post by satimis on 2023-01-22
> **TheFu said:**
> To be very clear, only the webserver is "listening" on the IP.  All the other things are just configuration so the returned webpages consistently point at the correct IP/DNS-name.  The webserver listening on 10.0.0.80:80/tcp  means that a connection to that address/port is possible, but when the data is returned, if 127.0.0.80 is in all the returned html, then the client making the request will look to it's localhost , not the remote server.  That's where all the php program and moduile configs come in.
Thanks for your further advice.  It is now clear to me.

I have made intensively searching on Internet but unfortunately I can't find a solution.  Fortunately I found it through tests.  I should set up the static IP immediately after finishing building the LAMP server before migrating the live site to the server, not the other way round. I made a serious mistake.  There are many plugin-applications to the WP websites.

---

