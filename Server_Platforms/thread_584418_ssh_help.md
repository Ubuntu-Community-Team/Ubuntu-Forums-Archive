---
title: "ssh help"
date: 2007-10-21
forum: Server Platforms
---

### Post by hcker2000 on 2007-10-21
I installed sshd with my 7.10 server install. The only problem is that I can not access it from any other computer. Even ones on the same network.

eth1 is my internet connection and I am using ipkungfu to set up the machine as a gateway.

eth0 is my lan connection it is set as fallows

ip = 10.10.10.1
netmask = 255.255.255.0
broadcast = 10.10.10.255


I can use the command ssh localhost and it connects just fine but from any other computer on the lan it will not connect.

---

### Post by thelocust on 2007-10-21
do you have your ssh port opened on your firewall?

---

### Post by gradedcheese on 2007-10-21
Take a look at your auth.log and daemon.log as you try to connect from another host.  The GUI too Administration->System Log offers a nice way to do it.  What error, if any, do you get there?

---

### Post by thelocust on 2007-10-21
I think since you just upgraded to gusty you authintication key changed there is a file in your ~/.ssh/ delete that in all your computers it wont hurt anything you just accept the new one the first time you establish a connection.

---

### Post by hcker2000 on 2007-10-21
Thanks for the quick replys. I am connecting from windows based computers using putty. I will check to see if there is a putty key cach I can clear out.

I am using ipkungfu as my firewall and have set it to accept tcp connections on port 22 with the fallowing command

ssh:22:tcp:ACCEPT

and that is in my /etc/ipkungfu/services/conf file.

---

### Post by hcker2000 on 2007-10-21
Well it seems to be ipkungfu thats doing it. I have tryed every thing to get it to let 22 threw but it wont.

Now I am trying to set up shorewall and I get this error. Oh and eth1 is my internet connection.

detectnets not allowed on interface with default route - eth1 

Here is my config.

###############################################################################
#SOURCE		DEST		POLICY		LOG LEVEL	LIMIT:BURST
#
# Note about policies and logging:
#	This file contains an explicit policy for every combination of
#	zones defined in this sample.  This is solely for the purpose of
#	providing more specific messages in the logs.  This is not
#	necessary for correct operation of the firewall, but greatly
#	assists in diagnosing problems.
#
#
# Policies for traffic originating from the local LAN (loc)
#
# If you want to force clients to access the Internet via a proxy server
# on your firewall, change the loc to net policy to REJECT info.
loc		net		ACCEPT
loc	$FW	ACCEPT
loc		all		REJECT		info
#
# Policies for traffic originating from the firewall ($FW)
#
# If you want open access to the Internet from your firewall, change the
# $FW to net policy to ACCEPT and remove the 'info' LOG LEVEL.
# This may be useful if you run a proxy server on the firewall.
$FW	net	ACCEPT
$FW	loc	ACCEPT
$FW		all		REJECT		info
#
# Policies for traffic originating from the Internet zone (net)
#
net		$FW		DROP		info
net		loc		DROP		info
net		all		DROP		info
# THE FOLLOWING POLICY MUST BE LAST
all		all		REJECT		info
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE

---

