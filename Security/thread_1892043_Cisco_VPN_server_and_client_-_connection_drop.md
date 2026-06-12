---
title: "Cisco VPN server and client - connection drop"
date: 2011-12-07
forum: Security
---

### Post by rcbandit on 2011-12-07
I have a Cisco 1841 router configured as Easy VPN Server. Here is the configuration of the router:
  [http://pastebin.com/zR2UhqUS](http://pastebin.com/zR2UhqUS)
  I have a Centos 5.7 server and Ubuntu server with installed Cisco VPN client for Linux.  The client successfully connects to the VPN server but after 15 minutes  the connection is droped.
  Here is the configuration file of the Cisco VPN client:
  [http://pastebin.com/mgXnCW8L](http://pastebin.com/mgXnCW8L) 
  The client allways disconnects after ~ 15:25 minutes.
  I'm sure that I made a mistake into the configuration. I need to  configure the client to keep the VPN connection infinite. Can you help  me to fix the problem.
  Best wishes Peter
  Here is the output of the command sh crypto ipsec: [http://pastebin.com/VXstkqpu](http://pastebin.com/VXstkqpu)
  Here is the output of the debug command into the router: [http://pastebin.com/jcRcVRvV](http://pastebin.com/jcRcVRvV)
  Here is the log file of the Linux VPN client  [http://pastebin.com/xCJwcC2Q](http://pastebin.com/xCJwcC2Q)

---

