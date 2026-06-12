---
title: "Headless server on ubuntu 9.04"
date: 2009-05-11
forum: Server Platforms
---

### Post by cwmbrankid on 2009-05-11
Hi,

I've just installed 9.04 server and now want to be able to access it remotely and run a gui to configure the various elements.
I've tried vnc, tightvnc but am not getting a lot of joy.

I can connect remotely from my ubuntu laptop using either tightvnc or vnc and log on OK but am getting the dappled grey screen with black X but no 'desktop'.

I've googled this and found loads of 'solutions', none of which work for me....it could be because of my complete lack of knowledge!!

I'm happy to carry out a complete rebuild of the server as I've changed my xstartup config file so many times it probably isn't helping.

One thing that does seem to be consistent which every way I try is the error in my log:
Couldn't open RGB_DB.......

I've tried to find where this is referenced from but can't see it in my xstartup config or anywhere else so am a bit lost.....

Can anyone help..?

Cheers.

Paul.

---

### Post by spiderbatdad on 2009-05-11
I would say you want ssh. Installing openssh server on the server and run the client on the the machine used to access the server. With the command ssh -X user@server_ip, you will log into the headless machine. From the prompt you can launch the default file browser as root to configure system files graphically. So if the server gui was xfce4...gksu thunar.
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/](http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/)

---

### Post by Mythbuster1848 on 2009-05-13
Hi,

Make sure you've got SSH installed and running. Test this by logging in from the command line of your remote machine:

```
ssh -l [username] [server address]
```Where [username] is an authorized user on the server and [server address] is your server's IP address. To rule out potential firewall issues try to do this from the same subnet your server is on. If you've got the firewall config sorted out, make sure port 22 is open on both boxes.

I don't know much about VNC, but to do what you describe I use FreeNX. This is a remote desktop package similar to VNC, but it configures itself on installation and by default sends all traffic through an SSH tunnel (port 22).

From a base 9.04 Ubuntu install with working OpenSSH, I was able to get a working remote desktop with the following steps:

```
sudo apt-get install freenx
```I think this package is in the third party repos. Next you might have to copy the public key from your server (read the freenx documentation) to your client. Grab a client from [www.nomachine.com]("http://www.nomachine.com"), and you're running.

That should do it for you. If it works in some places or on some computers but not others, you've probably got a firewall issue. For FreeNX in the default configuration you only need port 22 open. The default client config launches a Gnome desktop. If you don't have Gnome installed, change the desktop type to the display manager you have installed on the server or specify a custom desktop.

NOTE: The previous reply using X11 forwarding through ssh will work as well, but you MUST have a working X server on the client (in addition to the server), AND you'll need to make sure X11 forwarding is enabled in your sshd config file. (FreeNX takes care of most of these headaches, in addition to securing everything and sending all traffic through an SSH tunnel)

---

### Post by darkorical on 2009-05-13
I definiatly recomend FreeNX and there is a very useful tutorial 
[Right Here](https://help.ubuntu.com/community/FreeNX)

---

### Post by wojox on 2009-05-13
Shame on you for running a GUI on your Server. Stick with OpenSSH.

---

### Post by p0rnflake on 2009-05-17
> **wojox said:**
> Shame on you for running a GUI on your Server. Stick with OpenSSH.

I'm sorry but that is such ******** - and everybody thinks they're cool when they repeat it.

Why not run a GUI on a server if you have a need for it - a server provides a 'service' to one or more client - this service can very well be a remote desktop..

---

### Post by tubezninja on 2009-05-17
> **p0rnflake said:**
> I'm sorry but that is such ******** - and everybody thinks they're cool when they repeat it.

Perhaps the way it's presented is a bit jerkish.  However, Unless you're running a specific app on your server that demands a GUI - and I haven't found one yet that I need that does - you will find that using the GUI can actually introduce a lot of unneeded overhead And won't change much of anything.  For a lot of things, you'll still need to go into a terminal window to type commands... something that could be done a lot faster over an ssh connection.  A lot of the configuration files, starting up and shutting down of services, and the like just aren't done graphically.

You CAN do it with CPanel or webmin, or similar packages, but those don't require remote desktop logins either.

Anyway, good luck running the GUI, but I have a feeling it'll be more cumbersome than you realize, and won't shield you from having to use the same tools you'd be using under ssh anyway.

---

### Post by ktrnka on 2009-05-17
> **cwmbrankid said:**
> Hi,

I've just installed 9.04 server and now want to be able to access it remotely and run a gui to configure the various elements.
I've tried vnc, tightvnc but am not getting a lot of joy.

I can connect remotely from my ubuntu laptop using either tightvnc or vnc and log on OK but am getting the dappled grey screen with black X but no 'desktop'.

I've googled this and found loads of 'solutions', none of which work for me....it could be because of my complete lack of knowledge!!

I'm happy to carry out a complete rebuild of the server as I've changed my xstartup config file so many times it probably isn't helping.

One thing that does seem to be consistent which every way I try is the error in my log:
Couldn't open RGB_DB.......

I've tried to find where this is referenced from but can't see it in my xstartup config or anywhere else so am a bit lost.....

Can anyone help..?

Cheers.

Paul.

In ubuntu server edition, there is no gui. Did you install ubuntu-desktop package after you installed the server edition? Once that is done, then you can manually start vnc through an ssh connection.

---

