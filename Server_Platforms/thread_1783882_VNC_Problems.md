---
title: "VNC Problems"
date: 2011-06-16
forum: Server Platforms
---

### Post by Matthew24 on 2011-06-16
Hi,

I´ve successfully installed GNOME and VNC Server on my CentOS server. I´ve also installed PuTTY and Java on my xubuntu machine. 

I set up putty to use localhost:5801 and localhost:5901, the server ip is in and at port 22 for ssh. I can log into putty with the ssh, but when I go to my browser and type in [http://localhost:5801/](http://localhost:5801/) I get nothing. Apparently, a java applet with appear allowing you to log in with vnc credentials? I did add a vnc user and I´m pretty sure I put a passwd to it, how can I check this? How do I display the vnc users?

Am I doing anything incorrectly on the xubuntu end?

Here what my vnc conf page on the server looks like at the bottom:
# VNCSERVERS="1:testvncuser"
# VNCSERVERARGS[1]="-geometry 800x600 -nolisten tcp -nohttpd -localhost"

I followed this guide [http://wiki.centos.org/HowTos/VNC-Server](http://wiki.centos.org/HowTos/VNC-Server) and the 2.4 part did not look as it did on the tutorial...

Thank you!

---

### Post by Toz on 2011-06-16
> **Matthew24 said:**
> Hi,

I´ve successfully installed GNOME and VNC Server on my CentOS server. I´ve also installed PuTTY and Java on my xubuntu machine. 

I set up putty to use localhost:5801 and localhost:5901, the server ip is in and at port 22 for ssh. I can log into putty with the ssh, but when I go to my browser and type in [http://localhost:5801/](http://localhost:5801/) I get nothing. 

If you are typing this from your xubuntu machine, then you shouldn't use localhost - you should use the ip address of the server instead```
http://xxx.xxx.xxx.xxx:5801/
```
> Apparently, a java applet with appear allowing you to log in with vnc credentials?Ok. > I did add a vnc user and I´m pretty sure I put a passwd to it, how can I check this?
On your server, type in:```
cat /etc/passwd
```to see if the account exists.

> How do I display the vnc users?
As per those instructions, I would view the contents of **/etc/sysconfig/vncservers** and compare the entries on the first line with the results from the previous command.

> Am I doing anything incorrectly on the xubuntu end?
As per above, you shouldn't be entering localhost in the browser. Xubuntu also comes with an application in your Network menu called "Remote Desktop Viewer" that supports vnc - you can try it as well.

> Here what my vnc conf page on the server looks like at the bottom:
# VNCSERVERS="1:testvncuser"
# VNCSERVERARGS[1]="-geometry 800x600 -nolisten tcp -nohttpd -localhost"
The **#**s are comment marks which invalidate the line. If that line is your intended configuration line (ie. testvncuser is the user that you setup), then you should remove the # marks from the beginning of those lines. 

**Can you post the complete contents of the /etc/sysconfig/vncservers?**

> I followed this guide [http://wiki.centos.org/HowTos/VNC-Server](http://wiki.centos.org/HowTos/VNC-Server) and the 2.4 part did not look as it did on the tutorial...

Thank you!

A few more things to test:
1. Is the vnc server service running on the server?```
sudo service vncserver status
``` If not, you will need to do step 2.5 (assuming your configuration file is correct)

2. Do you have a firewall enabled on the server and is port 5801 being allowed through?

---

### Post by Matthew24 on 2011-06-17
I tried the [http://xxx.xxx.xxx.xxx:5801/](http://xxx.xxx.xxx.xxx:5801/) and it did not work. I checked and the account does exit.

I removed the #s marks.

I didn´t have X Window Manager installed, so I got it via yum install. I think I have all the packages I need for vnc server...****

When you go to /root/.vnc, it is supposed to show a startx conf file and other items... it only shows a passwd item.

When I try to start the vnc server service it now fails.

How would I check to see if port 5801 is allowed?

Thank you so much for your time, it is appreciated!

---

### Post by Toz on 2011-06-17
> **Matthew24 said:**
> I tried the [http://xxx.xxx.xxx.xxx:5801/](http://xxx.xxx.xxx.xxx:5801/) and it did not work.
You did replace the xxx.xxx.xxx.xxx with the correct ip address, right? 
> I checked and the account does exit.
Good.

> I removed the #s marks.
Did you restart the service? Can you post a copy of the contents of this file?

> I didn´t have X Window Manager installed, so I got it via yum install. I think I have all the packages I need for vnc server...
Yeah, the X window system is a necessity here.

> When you go to /root/.vnc, it is supposed to show a startx conf file and other items... it only shows a passwd item.
How about the .vnc directory of the test user you created? I believe your intent is to log in as that user, not root.

> When I try to start the vnc server service it now fails.It would help if you posted the error messages.

> How would I check to see if port 5801 is allowed?
First check if iptables is running. I believe on centos the syntax is:```
service iptables status
```Second, check the ruleset:```
iptables -vnL | grep 5801
```

> Thank you so much for your time, it is appreciated!
No worries.

---

### Post by Matthew24 on 2011-06-17
I decided that the VNC was going to be a lot of work so I just configured X11 port forwarding so I get the grpahical applications right on my desktop when remoteing in! It works GREAT.

One problem though, I´m using BitNami to install Jasper Reports Serverstack and it freezes... any insight?

Thanks!

---

### Post by Toz on 2011-06-17
Sorry - no experience with those products.

---

### Post by crispy_420 on 2011-06-18
Why not NX client/server? It is painfully easy to setup and run. There is a windows client too.

---

### Post by Matthew24 on 2011-06-18
> **crispy_420 said:**
> Why not NX client/server? It is painfully easy to setup and run. There is a windows client too.

Okay, thanks!

I installed the server and the desktop clients.

When I try to connect:
NX> 203 NXSSH running with pid: 1936
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: xx.xx.xx.xx on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

Did I not configure something correctly?

My sshd_config fille has this:
#PasswordAuthentication yes

If I´m following this guide... would I skip that step ?
[http://wiki.centos.org/HowTos/FreeNX](http://wiki.centos.org/HowTos/FreeNX)

---

