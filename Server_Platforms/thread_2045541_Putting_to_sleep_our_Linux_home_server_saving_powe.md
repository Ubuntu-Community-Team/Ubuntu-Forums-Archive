---
title: "Putting to sleep our Linux home server saving power"
date: 2012-08-21
forum: Server Platforms
---

### Post by lupp0l0 on 2012-08-21
If anyone can be interested I've made a little guide to explain the solution I use at home to save a little power suspending my home web server when not used.


**Putting to sleep our Linux home server**

Some people have a Linux home server that provide its services to internet. It can provide a little website, a personal cloud (like owncloud), a ftp server or a video surveillance server. Anyway, to provide these services, it's mandatory to keep server powered on and connected to the home internet line.
This guide wants to provide a solution to limit our server energy consumption while keeping services reachable 24 hours a day.

Requirements
-linux server with wake on lan enabled nic (mine is a web server with Ubuntu Server 12.04)
-flat internet connection with static ip address or dynamic dns configured
-router or access point with OpenWrt (or similar operating system) on board
-knowledge on how network works

**1. Power management configuration on Linux server**

The first thing we have to do is to verify the capability of our hardware to support the suspend state. To verify this capability we can use two methods. The first make use of the following command which is provided by "pm-utils" package.

```
# pm-is-supported --suspend && echo "Suspension supported" || echo "Suspension NON supported"
```

The command output will make us understand if it's possible to go on with the test. If the output says "Suspension supported" then we can go on with the following command. Beware! the following command put the system in suspend mode, to wake the system we'll need to press the power button manually, so don't launch this command on a remote machine.

```
# pm-suspend
```

If all goes well, the fans and the disks inside your server should power off and stop making noise. The power led should blink slowly. The power consumption in this state is lower than the power consumption during normal operations. To wake up your server press power button. If everything works and your system will be able to resume its previous tasks without problems, you can go on with next configuration.

Now we have to configure a power policy using the service "powernap(1)" that isn't normally installed by default. If it's present in our distribution repository, like for Ubuntu, we can install it using the command

```
# apt-get install powernap
```

Configuration files are under directory /etc/powernap. The file that we'll edit is "config" and it's very well commented. The interesting options are those regarding "STAGE 2". In my home server I've made these changes

```
#set suspend timeout after 1800 seconds of inactivity
STAGE2_ABSENT_SECONDS = 600
STAGE2_ACTION_METHOD = 1

#if there are package management processes running then block suspension
[ProcessMonitor]
dpkg = "dpkg "
aptget = "apt-get "

#if there are ssh or http connections then block suspension
[TCPMonitor]
ssh = 22
http = 80
```

After setting options we have to restart powernap daemon to apply configuration changes. This can be done with "service powernap restart" or "restart powernap". The system should behave accordingly, going to suspend when the specified conditions are met. Obviously, after the system is put in suspend mode, the only way to wake it up is to press the power button.


**2. OpenWrt device configuration**
OpenWrt have to be already installed in any device connected to local area network. I've a Fonera with OpenWrt Backfire 10.03.1 installed.
The first thing to do is to install "haproxy" package available in OpenWrt repositories. To install it we can issue the commands "opkg update" and "opkg install haproxy" inside a ssh shell or, alternatively, we can use the web interface inside the section System -> Software searching for "haproxy" package.
Using the same method we have to install the package "etherwake".
The haproxy configuration file to edit with vi is /etc/haproxy.cfg.
Here it is my haproxy.cfg file:

```
# Example configuration file for HAProxy 1.3, refer to the url below for
# a full documentation and examples for configuration:
# http://haproxy.1wt.eu/download/1.3/doc/configuration.txt


# Global parameters
global

	# Log events to a remote syslog server at given address using the
	# specified facility and verbosity level. Multiple log options 
	# are allowed.
	#log 10.0.0.1 daemon info
	

	#log 127.0.0.1 daemon
	# Specifiy the maximum number of allowed connections.
	maxconn 512

	# Raise the ulimit for the maximum allowed number of open socket
	# descriptors per process. This is usually at least twice the
	# number of allowed connections (maxconn * 2 + nb_servers + 1) .
	ulimit-n 65535

	# Drop privileges (setuid, setgid), default is "root" on OpenWrt.
	uid 0
	gid 0

	# Perform chroot into the specified directory.
	#chroot /var/run/haproxy/

	# Daemonize on startup
	daemon

	# Enable debugging
	#debug

	# Spawn given number of processes and distribute load among them,
	# used for multi-core environments or to circumvent per-process
	# limits like number of open file descriptors. Default is 1.
	#nbproc 2

# Example HTTP proxy listener
listen my_http_proxy

	# Bind to port 80 and 443 on all interfaces (0.0.0.0)
	bind :8080
	#log global
	# We're proxying HTTP here...
	#mode http
	mode tcp
	#option tcplog
	# Simple HTTP round robin over two servers using the specified
	# source ip 192.168.1.1 .
	timeout connect 5000
	timeout client 5000
	
	balance roundrobin
	server server01 192.168.1.35:80 source 192.168.1.250
	#server server02 192.168.1.20:80 source 192.168.1.1

	# Serve an internal statistics page on /stats:
	#stats enable
	#stats uri /stats
```


Beware to "bind :8080" e "mode tcp" options that indicates the listening port (must be different from 80) and proxy mode. In the balance roundrobin section we have to set the ip address and the port where the Linux server is listening (in my case 192.168.1.35:80) and like source set the OpenWrt ip address. Again, to apply configuration file to the running daemon, we have to restart haproxy service using /etc/init.d/haproxy restart.
If everything works like planned, connecting a web browser to OpenWrt ip address specifying the port previously set, you should see the home page served by the Linux server. In my case the url to insert in web browser will be [http://192.168.1.250:8080](http://192.168.1.250:8080). If the page can be viewed correctly you can go on with modifying port forwarding rules inside the router in order to the connections from internet on port 80 will not be redirected to the Linux server, but instead towards the haproxy port in OpenWrt device.
Now we have to tell to OpenWrt to wake up the Linux server every time it receive a connection request on port 80. To make it possible I've coded two simple scripts that must be put in /root directory on OpenWrt device. The first one is named "server-on.sh" and does only one thing: fires a wake on lan packet adressed to the Linux server nic waking it up. The nic mac address can be seen using the command ifconfig.

```
etherwake -i br-lan 00:0b:XX:XX:XX:XX
```

The second script is called "check-conn.sh" and its function is to check if there are connection requests on port 80 every second.

```
#!/bin/sh
while [ 1 -eq 1 ]
do
	sleep 1
	if [ $(netstat -ant 2> /dev/null | grep 192.168.1.250:8080 | wc -l) -gt 0 ] 
	then
		/root/server-on.sh
	fi
done
```

To start automatically the script every time OpenWrt starts we can modify the /etc/rc.local file in a way like this:

```
# Put your custom commands here that should be executed once
# the system init finished. By default this file does nothing.
/root/check-conn.sh &
exit 0

```
Now the system should behave like we want, with the Linux server waking up every time a connection request is coming to the web server public address on router.

(1) [https://launchpad.net/powernap]("https://launchpad.net/powernap")

---

### Post by d4m1r on 2012-08-21
Interesting concept and thanks for the guide!

However, does it only listen for HTTP traffic? What if the server is only running a FTP, DNS, or Email server? Does it miss the original request as it only powers the machine on?

---

### Post by lupp0l0 on 2012-08-21
> **d4m1r said:**
> Interesting concept and thanks for the guide!

However, does it only listen for HTTP traffic? What if the server is only running a FTP, DNS, or Email server? Does it miss the original request as it only powers the machine on?

The configuration can be adapted to support every type of connection supported by haproxy, so not only http. Using http the original request is correctly replied within ~4 seconds, which is usually less than the protocol timeout. Other protocols like dns may have different timeout for the connection, I've not tested it. Obviously who is trying to get the web page while the machine is suspended will see a small delay, similar to the delay existing when surfing a overladen web site.

---

### Post by LHammonds on 2012-08-21
Thanks for sharing this.  It will come in handy when I eventually get around to setting up a low-watt media server.

---

