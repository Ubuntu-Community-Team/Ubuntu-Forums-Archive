---
title: "Setting up Development Server using Ubuntu 8.04 Server 64-bit"
date: 2009-12-29
forum: Server Platforms
---

### Post by amudliar on 2009-12-29
I have a Server Hardware with 1.5TB drive and 1.0TB (second drive) and I am looking for some expert who can guide me on ideal configuration, softwares/apps and VMware to be installed on this server. Below are some key requirements...
 
1. Need two OS, one for Window Server 2008 and one for Ubuntu Server 8.04. This could be Virtual Machine (if that makes sense).
 
2. Multiple OS can be accessed at the same time.
 
3. Windows will have SQL Server, Visual Studio .NET, IIS installed.
 
4. Linux Server Ubuntu will have MySQL, PHP, Apache installed.
 
5. Development server to be used by around 5 - 10 developers. 
 
6. Some developers will have direct access to the physical server and some will be accessing over internet (Remote Desktop) and some users will be accessing it using SSH.
 
7. I have a domain named "domain.com" registered with godaddy and would like to have urls (subdomains) like <projectname>.<username>.domain.com for development url and <projectname>.domain.com as test url. Project can exists in either Windows or Linux platform depends on whether its been developed in .NET or PHP. Most (99%) of the development will be web based.
 
8. I plan to use DynDNS or something similar (I dont have static IP) to make the server accessible over internet. I dont know what else need to be done on the server for this to work.
 
9. Host OS will be Ubuntu 8.04. But I also need to know what kind of server configuration I should be doing for Virtual Machines. For e.g. Should I create 1 host and 2 VM OR use 1 host (Linux) and 1 VM (Windows)
 
10. I have 5 types of users for my development server as explained below
 
General : 
 
1) All users will access the server using https/SSH (most of the time).
2) Server runs all the time.
 
User-1 (Minimal Access) :
 
1) Should be able to access SQL Server from their Windows Desktop using IP address.
2) Should be able to access MySQL Server using phpmyadmin (over https) OR SSH to the server (using IP) and doing MySQL stuff from terminal.
3) Should be able to access Subversion (over https) using VS.NET/Eclipse OR SSH to the server (using IP) and doing check-in/out.
 
User-2 (Limited Access) :
 
1) Should be able to access both Windows and Linux VM using Remote Desktop using a user id/password
2) Should be able to access SQL Server from their Windows Desktop using IP address.
3) Should be able to access MySQL Server using phpmyadmin (over https) OR SSH to the server (using IP) and doing MySQL stuff from terminal. 
4) Should be able to access Subversion (over https) using VS.NET/Eclipse OR SSH to the server (using IP) and doing check-in/out.
 
User-3 (Admin Access) :
 
1) Should be able to do everything as User-2 but with admin access (that will allow user to do pretty much everything).
 
User-4 (Administrator):
 
1) Will login to the system using his/her user id/password.
2) They should be able to login to Windows VM/Linux VM as administrator.
 
User-5 (Limited User):
 
1) Will login to the system using his/her user id/password.
2) They should be able to login to Windows VM/Linux VM as limited access user.
 
I would appreciate if any experts who have done this before can suggest me a solution for the above. I can provide any details you want. Attached is the server diagram (not complete).
 
Thanks.

---

### Post by amudliar on 2010-01-11
I am surprised that nobody ever had this kind of requirement OR may be this is not the right forum.

---

### Post by Queue29 on 2010-01-11
What exactly is your question..?

As for #9, if you want the Host OS to have a desktop, a Linux distro is the last thing you should use. Headless Ubuntu is arguably more stable than Windows server, but balancing a bowling ball on top of a beach ball would be more stable than a server running Xorg.

For #8, you need a router that can automatically handle updating DynDNS (any router running DD-WRT or Tomato will work, as well as a lot of stock routers surprisingly) and then have GoDaddy forward to the DynDNS url. Or you could just have GoDaddy point to your dynamic IP address and never reboot your router ;) . (If you do, you will likely be assigned a new IP add. and will have to update GoDaddy, which can take 1 - 2 hours for changes to occur)

---

### Post by cariboo on 2010-01-11
The reason your aren't getting more action here, is that this has been asked so often, it's almost a recurring discussion, and your question has more to do with virtualization than an actual server question.

You may want to ask your question in the [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") sub-forum.

---

### Post by amudliar on 2010-01-12
Added this question to Virtualization forum
 
_[COLOR=#810081][http://ubuntuforums.org/showthread.php?t=1379411](http://ubuntuforums.org/showthread.php?t=1379411)[/COLOR]_[]("http://ubuntuforums.org/showthread.php?t=1367041")

---

