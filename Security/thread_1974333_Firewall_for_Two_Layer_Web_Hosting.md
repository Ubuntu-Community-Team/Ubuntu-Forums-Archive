---
title: "Firewall for Two Layer Web Hosting"
date: 2012-05-05
forum: Security
---

### Post by OtagoHarbour on 2012-05-05
I am hosting a web site using two PCs. One is the web server which is running Ubuntu 11.04 and is port forwarded on port 80.  It's local IP address is 129.168.1.5.  The other is the application server which is running Ubuntu 11.10.  They are both connected to the same router.  I want all web access to the application server to be through the web server.  Presently,the only file I have on the web server is the index.php file.  It calls a bunch of php files on the application server and these call executable files that are also on the application server.  index.php has menu items that allow the user to click buttons to bring up the pages associated with the php files on the app. server.

I set up my firewall on the app. server using

```
[FONT=monospace]
[/FONT]sudo ufw enable
sudo ufw allow from  129.168.1.5

```Things wok fine if I am working from the web server PC but not when I try to access my web site from another computer.  I can access the home page (index.php) but when I click on one of the buttons associated with the php files on the app. server, I am blocked.  I guess this means that my current set up only allows the output of the pages on the app. server to be displayed only on the web server and not to the outside world.

I would like anyone to be able to view all of the pages and use their functionality.  However I do not want hackers to be able to access and reverse engineer my executables.  What would be the best solution?  Do I need to have all of my php files on the web server and only the executables that they call on the application server or can I set the firewall up to allow the output of php files on the application server to the displayed to the outside world without hackers being able to access the files on the app. server?

Many thanks in advance for any help,
Peter.

---

