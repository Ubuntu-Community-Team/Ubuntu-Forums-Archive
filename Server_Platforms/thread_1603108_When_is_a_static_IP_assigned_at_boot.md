---
title: "When is a static IP assigned at boot?"
date: 2010-10-22
forum: Server Platforms
---

### Post by rmccarri on 2010-10-22
Hi Everyone,
I've been having a problem getting a couple of services started at boot on my home server.  I want to have my Openvpn daemon and a holdingnuts poker server start at boot.  Neither of these start properly if placed at level S99 in the rc2 folder.  Looking through the logs, it seems that the network is not up and running at this time.   To confirm this, I placed the following in my rc.local file that runs at level S99.

```
ifconfig | cat > /home/username/network-status.txt
```

My ifconfig file shows the lo, eth0 and my bridged br0 interfaces.  However, the br0 interface does not show an IP, netmask or anything else, indicating that it hasn't been brought up, yet.  So this begs the question, if you have a static ip set (with a bridged connection for the VPN server), when does that actually get up and running?  I would have thought that it should be up by the time that the last startup scripts are running.  How can I ensure that these things run at startup, but not until the network is fully up and running?

Any insight would be greatly appreciated!
Rob

---

### Post by arrrghhh on 2010-10-22
Well the IP on eth0 should come up very early - before any other services get started (I thought).

However, the VPN bridged cxn probably comes up much later in boot.  I'm not sure how to push it back any later other than s99 tho...

---

### Post by rmccarri on 2010-10-22
Thanks for the reply.  If I set up the server to run the startup scripts as a cron job, they run perfectly, so it seems that the br0 device grabs the static IP sometime between when rc.local runs and when everything else like cron is up.

I wonder if what I should do is write a little script the rc.local executes that grabs the current time and then adds a minute and schedules the startup scripts to run with the "at" command.  It doesn't seem to work to use "sleep" since that just delays the boot processes.

---

### Post by CharlesA on 2010-10-22
That would probably work. It's a dirty "hack" but if it works, use it. :)

Is there an entry in /etc/network/interfaces for the br0 interface?

If there is, you can try using "post up" like so:

```
post-up some command or script goes here

```

---

### Post by BkkBonanza on 2010-10-22
The right way to do this is create an upstart conf file in /etc/init and have it depend on br0 being up. That way the script gets run right after br0 is finished being raised. The problem isn't the order but that bridges often take time to finish their init and so even when started early are often not up til much too late. By making the upstart depend on "br0 up" it gets timed correctly.

But as Charles says as post-up script would work as well. The interfaces get brought up by upstart in the /etc/init/networking.conf file, and so the post-up scripts are triggered after that.

---

### Post by sisco311 on 2010-10-22
EDIT: Never mind. BkkBonanza beat me to it. :)

---

### Post by rmccarri on 2010-10-22
Thanks for the suggestion, BkkBonanza.  I would certainly prefer to do this properly and learn something in the process.  I'm getting pretty familiar with Linux, but it's a continuing process, obviously.  I'm trying to figure out how I need to do this with some internet searching and looking at some of the conf files in /etc/init and it seems that I need something like this:

```

description     "Executes Server Startup Scripts after br0 is up"

start on br0 up

/etc/init.d/openvpn start
/etc/init.d/holdingnuts-start start

```

Is this heading in the right direction?

---

### Post by sisco311 on 2010-10-22
Yep, but I think you need something like:
```
start on net-device-up IFACE=br0

stop on net-device-down IFACE=br0
```

---

### Post by rmccarri on 2010-10-22
Thanks for all of the help.  I tried this and it seems based on looking around that it is the correct syntax for the conf file, but it doesn't seem like it ran.  To be specific, I created a file called upstart-servers.conf with ownership root:root and permissions 644 in /etc/init.  Here is what I put in the file:

```
description     "Executes Server Startup Scripts after br0 is up"

start on net-device-up IFACE=br0

ifconfig | cat > /home/user/Desktop/network-status.txt

/etc/init.d/openvpn start
/etc/init.d/holdinghuts-start start

stop on net-device-down IFACE=br0
```

I'm not getting a file after boot, so it seems like the commands in between  the start and stop lines aren't getting executed.  It seems like this should be what I need based on your recommendations and doing some searching around the internet.  Are all of the files in /etc/init automatically run on boot, or is there an index somewhere where I would have to add my new file to?
Thanks!

---

### Post by sisco311 on 2010-10-22
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

It should look like this:
```

description     "Executes Server Startup Scripts after br0 is up"

start on net-device-up IFACE=br0

stop on net-device-down IFACE=br0

expect fork

script
  ifconfig > /home/user/Desktop/network-status.txt

  /etc/init.d/openvpn start
  /etc/init.d/holdinghuts-start start
end script
```

---

### Post by BkkBonanza on 2010-10-22
That looks about right. 
Also make sure you disable the "old" init with update-rc.d as otherwise it will run twice.

---

### Post by rmccarri on 2010-10-22
That did the trick!  Thanks so much for all of the help everyone!

---

