---
title: "Disconnect from the internet when using XAMPP?"
date: 2011-05-15
forum: Security
---

### Post by speedwinder on 2011-05-15
I bought the O'Reily book for PHP, MySQL, & JavaScript so I can learn those languages. It recommended that Linux users use XAMPP [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html) . I just want to use it to for a learning environment. I don't want to make my computer a public webserver. I ran the "/opt/lampp/lampp security" command. Is my webserver still open to the public if I am connected to the Internet? If so then I should probably disconnect from the Internet when using XAMPP, right? It would be a bit of a burden because I would have to stop XAMPP from running every time I need to connect to the Internet to look something up.

Anyway, I was just wondering if my webserver is still open to the public even after running the XAMPP security command. Also, I connect to the Internet through a router. Sorry if this is a newb question but I am new to this.

---

### Post by spynappels on 2011-05-16
Hi there,

A couple of things spring to mind when reading your post. 

Firstly, you might find it easier to use the bundled AMP stack which comes with Ubuntu, as it will autostart the services on boot etc, there has been another thread on here recently where the OP was having issues getting the service to auto start etc. To enable/install the built in stack type
```
sudo tasksel
```
and select LAMP server. I'm not sure, but you may have to remove XAMPP first, having backed up any changes you have made.

Secondly, are you behind a router? Most home users are, and unless you have a port from your public interface forwarded to your server's interface, you have nothing to worry about. As this is to be a local test and learning environment, you do not need to expose the services to the Internet, and if you do not expose the services to the Net by port forwarding, you do not have to disconnect from the Net to use them, they just will not be accessible from outside your LAN at all.

---

### Post by speedwinder on 2011-05-16
> **spynappels said:**
> Hi there,

A couple of things spring to mind when reading your post. 

Firstly, you might find it easier to use the bundled AMP stack which comes with Ubuntu, as it will autostart the services on boot etc, there has been another thread on here recently where the OP was having issues getting the service to auto start etc. To enable/install the built in stack type
```
sudo tasksel
```and select LAMP server. I'm not sure, but you may have to remove XAMPP first, having backed up any changes you have made.

Thanks for the reply. I hadn't heard of the bundle AMP that comes with Ubuntu. I might look into this option. However, I don't mind starting xampp up when I startup my (virtual) machine. It's the stopping internet connection and starting xampp, stopping xampp and starting internet connection over and over that would get to be a burden. 

> **spynappels said:**
> 
Secondly, are you behind a router? Most home users are, and unless you have a port from your public interface forwarded to your server's interface, you have nothing to worry about. As this is to be a local test and learning environment, you do not need to expose the services to the Internet, and if you do not expose the services to the Net by port forwarding, you do not have to disconnect from the Net to use them, they just will not be accessible from outside your LAN at all.

Yes, now that I am on summer break from college I am getting my internet connection from a home router. I thought that being behind a router might eliminate this vulnerability but I wasn't positive. I haven't made any efforts to forward any ports from my router to my computer running the web server. Unless it's like that by default (which I doubt). When I go back to university I might have to setup a router in my dorm to provide that layer of security.

Another thing I should have mentioned in my first post is that I have installed xampp on a virtual machine I am running on vmware player. I have an older version of Ubuntu installed on my physical computer and have ubuntu 10.04 running on vmware player which is where I installed xampp. If I can disable internet/networking on my virtual machine but keep the internet connection on my actual operating system, that should eliminate the security risks, right? Because isn't what goes on in a virtual machine completely locked out from the operating system on the physical machine?

---

### Post by spynappels on 2011-05-16
> **speedwinder said:**
> 
 When I go back to university I might have to setup a router in my dorm to provide that layer of security.

That would probably be a good idea, it can give wireless access too with most modern routers. Just check that it won't mess with any terms and conditions of use on your dorm internet connection. 

> **speedwinder said:**
> 
If I can disable internet/networking on my virtual machine but keep the internet connection on my actual operating system, that should eliminate the security risks, right? Because isn't what goes on in a virtual machine completely locked out from the operating system on the physical machine?

This would work, but having a network connection on the VM is normally a good idea for updates etc. Again, as long as nothing is forwarded from your public address, you are fine.

Just a quick question, are you running Desktop or Server edition?
Desktop edition just needs to have Remote Desktop (VNC) either disabled or secured with a very strong password. (Disabled is better if you don't need it) It just happens to be one of the most exploited vulnerabilities on Ubuntu in it's default state.

---

### Post by speedwinder on 2011-05-16
> **spynappels said:**
> 
Just a quick question, are you running Desktop or Server edition?
Desktop edition just needs to have Remote Desktop (VNC) either disabled or secured with a very strong password. (Disabled is better if you don't need it) It just happens to be one of the most exploited vulnerabilities on Ubuntu in it's default state.

Desktop edition. How do I disable Remote Desktop?

---

### Post by spynappels on 2011-05-16
> **speedwinder said:**
> Desktop edition. How do I disable Remote Desktop?

Go to System > Preferences > Remote Desktop and make sure that "Allow other users to view your desktop" is unchecked. If it is, you should be fine.

Oh, and you might just check that uPNP is disabled in your router, some would recommend that as another layer of security.

---

### Post by speedwinder on 2011-05-16
> **spynappels said:**
> Go to System > Preferences > Remote Desktop and make sure that "Allow other users to view your desktop" is unchecked. If it is, you should be fine.

Oh, and you might just check that uPNP is disabled in your router, some would recommend that as another layer of security.

Alright, thanks man!

---

