---
title: "Disable direct input to server"
date: 2013-06-24
forum: Server Platforms
---

### Post by termvrl on 2013-06-24
Hi All,

I want to ask, i wonder how we can disable/block input on monitor.
E.g: An Application after install to server, we can only configure through web console or ssh to the server.
What is the concept used in this situation. 
Thanks.

---

### Post by volkswagner on 2013-06-24
Well a monitor is not an input device :P

I believe you would need to place server in a locked cabinet.  Remember, physical access is root access!

---

### Post by termvrl on 2013-06-24
Hi volkswagner,
maybe my question is unclear. sorry for that.
what i mean, for e.g, let say i have download & installed open source firewall, after finish install, what i can see on monitor is basic configuration such as set a management IP address or set physical IP on physical nic. Other configuration i need to login to control panel to configure it. Same as, if you using VMWare ESXi, after installed, you need to login to vSphere client to create a new virtual machine. 

My question is how they do it?

---

### Post by CharlesA on 2013-06-24
You can still login as root on a ESXi box.

What do you want to accomplish? If you don't want anyone logged into the console, don't give them their login credentials.

Also, keep the machine is a secured location.

---

### Post by termvrl on 2013-06-24
Hi,
i ask this question as for the knowledge only.
i just want to know, how the application/software developer can limit what we can see on the monitor, and what actually we can do if we login on console.

sorry if the question not clear.

---

### Post by volkswagner on 2013-06-24
I don't think you are looking at this correctly.

Hypervisors are no limiting what you can see on the console.  They are actually giving you additional information.  Like previous poster said, you can still simply login with valid credentials.

I'm sorry I don't know what software is displaying the added information.

Take a look at TurnkeyLinux.  Most all the images they release have a similar informational screen output.

[IMG]http://www.turnkeylinux.org/files/images/screenshots/confconsole.jpg?1295851563[/IMG]

---

