---
title: "Desktop on Cloud Trial Fails"
date: 2010-10-12
forum: Ubuntu Cloud and Juju
---

### Post by LinuxLars on 2010-10-12
Just completed the "Ubuntu in the Cloud" AWS Trial - wicked cool.

However, I wanted to hand this off to my business partner who is Microsoft-centric (e.g. he needs a GUI) - so I installed Desktop, but could not get it to run. 

#sudo apt-get install ubuntu-desktop
#/etc/init.d/dgm start
#startx

It fails consistently with:
Primary device is not PCI
(EE) No devices detected. 

Is this a limitation in the could trial or am I missing something?

Thanks

---

### Post by kim0 on 2010-10-13
Sure there is no VGA card. You need to install a vnc server
sudo apt-get install tightvncserver

then connect to that with a vnc viewer from windows. If the default port 5901 is not open, you might want to start the server on port 80 or so

---

### Post by obast on 2010-10-13
You could also try ssh tunneling

ssh -X -C

Though X Windows tunneled through the cloud is slow.

---

### Post by bmullan on 2010-11-04
I'm not familiar with the trial but if you get an Ubuntu "server" on AWS EC2 to try out and want a gui.

Here's what I would do as it works great:

**1)**
Log into the AWS EC2 "server" and install a "minimal" desktop
*$ sudo apt-get install xorg gdm gnome-core*
**2)** 
Install the high performance jpeg library [COLOR="Blue"]**[libjpeg-turbo]("http://sourceforge.net/projects/libjpeg-turbo/files/")**[/COLOR] on both the AWS EC2 server and your local PC.
**3)**
Finally, install x2go - see [COLOR="Blue"]**[the x2go Wiki]("http://wiki.x2go.org/start")**[/COLOR].  Its quick and easy and works great with EC2.  x2go has Mac, Windows and Linux "clients".

x2go is a terrific remote desktop solution and supports audio, printing and shared file systems.   It also implements the NX protocol so remote PC's get very good performance.

Add the x2go respository PPA to BOTH your AWS EC2 Ubuntu "server" and to your local PC.

[COLOR="Blue"]**[How To add the x2go repository]("http://wiki.x2go.org/adding_the_x2go_repository_debian")**[/COLOR]

[COLOR="Blue"]**[Install the x2go "client"]("http://wiki.x2go.org/installing_x2goclient_ubuntu")**[/COLOR] on your local Ubuntu PC.

**[COLOR="Blue"][Install the x2go "server-side"]("http://wiki.x2go.org/installing_x2goserver-home_ubuntu")[/COLOR]**] on your AWS EC2 Ubuntu server.

**[COLOR="Blue"][Install the x2goGnomeBindings]("http://wiki.x2go.org/installing_the_gnome_2._bindings_ubuntu")[/COLOR]** ***on the AWS EC2 Ubuntu server***

If your local PC is Windows then **[COLOR="Blue"][install the x2go 32bit Windows Client]("http://prdownload.berlios.de/x2go/x2goclient-3.01-4-setup.exe")[/COLOR]**
reboot your AWS EC2 server (remember its PUBLIC IP address).
reboot your local PC

On your local Ubuntu PC:

Click on "Applications"
==> Click on Internet
==> Click on "x2go Client"

Enter your AWS EC2 Ubuntu server's IP address as the HOST you want to reach
and enter you Login ID on that machine.

Change the Desktop type to match what you use on the EC2 ubuntu (gnome, kde, etc).

Click OK.

Then to login (assuming your EC2 instance is running and has x2go-server installed.

Just click on the Session Box on the right of the x2go client screen
and enter your remote Ubuntu Password.

The first time you log in you may get prompted to accept the SSH connection but after you accept once you won't get prompted again.

On an AWS EC2 "micro" instance ... which I think the "trial" uses you might have to wait 10 seconds before your session will pop up with your remote AWS EC2 Ubuntu desktop.
[COLOR="Blue"][B]
[Some screen shots - note some of the pictures are a little outdated.]("http://x2go.obviously-nice.de/index.php?id=42")[/B][/COLOR]

I think if you consider your own/home Internet speed and the fact that the remote AWS EC2 Ubuntu server is running on an EC2 "micro" instance .. that the performance is actually still pretty good.

x2go is near releasing a new version which will include a java-plugin that will allow you to use any Java enabled Browser as your Desktop client.  You can find that beta now and see how well it works (audio, printing etc).

Brian

> **LinuxLars said:**
> Just completed the "Ubuntu in the Cloud" AWS Trial - wicked cool.

However, I wanted to hand this off to my business partner who is Microsoft-centric (e.g. he needs a GUI) - so I installed Desktop, but could not get it to run. 

#sudo apt-get install ubuntu-desktop
#/etc/init.d/dgm start
#startx

It fails consistently with:
Primary device is not PCI
(EE) No devices detected. 

Is this a limitation in the could trial or am I missing something?

Thanks

---

### Post by kim0 on 2010-11-05
That's awesome, thanks Brian :)

---

### Post by Ezrie on 2010-12-12
Brian.  this is really great.  Thanks for writing this up.  I followed the instructions but I still get an error.

```
"amazon_public_dns": Permission denied (public key).
```

Do you have any experience with this error?  Any help is great.

Thanks


> **bmullan said:**
> I'm not familiar with the trial but if you get an Ubuntu "server" on AWS EC2 to try out and want a gui.

Here's what I would do as it works great:

**1)**
Log into the AWS EC2 "server" and install a "minimal" desktop
*$ sudo apt-get install xorg gdm gnome-core*
**2)** 
Install the high performance jpeg library [COLOR="Blue"]**[libjpeg-turbo]("http://sourceforge.net/projects/libjpeg-turbo/files/")**[/COLOR] on both the AWS EC2 server and your local PC.
**3)**
Finally, install x2go - see [COLOR="Blue"]**[the x2go Wiki]("http://wiki.x2go.org/start")**[/COLOR].  Its quick and easy and works great with EC2.  x2go has Mac, Windows and Linux "clients".

x2go is a terrific remote desktop solution and supports audio, printing and shared file systems.   It also implements the NX protocol so remote PC's get very good performance.

Add the x2go respository PPA to BOTH your AWS EC2 Ubuntu "server" and to your local PC.

[COLOR="Blue"]**[How To add the x2go repository]("http://wiki.x2go.org/adding_the_x2go_repository_debian")**[/COLOR]

[COLOR="Blue"]**[Install the x2go "client"]("http://wiki.x2go.org/installing_x2goclient_ubuntu")**[/COLOR] on your local Ubuntu PC.

**[COLOR="Blue"][Install the x2go "server-side"]("http://wiki.x2go.org/installing_x2goserver-home_ubuntu")[/COLOR]**] on your AWS EC2 Ubuntu server.

**[COLOR="Blue"][Install the x2goGnomeBindings]("http://wiki.x2go.org/installing_the_gnome_2._bindings_ubuntu")[/COLOR]** ***on the AWS EC2 Ubuntu server***

If your local PC is Windows then **[COLOR="Blue"][install the x2go 32bit Windows Client]("http://prdownload.berlios.de/x2go/x2goclient-3.01-4-setup.exe")[/COLOR]**
reboot your AWS EC2 server (remember its PUBLIC IP address).
reboot your local PC

On your local Ubuntu PC:

Click on "Applications"
==> Click on Internet
==> Click on "x2go Client"

Enter your AWS EC2 Ubuntu server's IP address as the HOST you want to reach
and enter you Login ID on that machine.

Change the Desktop type to match what you use on the EC2 ubuntu (gnome, kde, etc).

Click OK.

Then to login (assuming your EC2 instance is running and has x2go-server installed.

Just click on the Session Box on the right of the x2go client screen
and enter your remote Ubuntu Password.

The first time you log in you may get prompted to accept the SSH connection but after you accept once you won't get prompted again.

On an AWS EC2 "micro" instance ... which I think the "trial" uses you might have to wait 10 seconds before your session will pop up with your remote AWS EC2 Ubuntu desktop.
[COLOR="Blue"][B]
[Some screen shots - note some of the pictures are a little outdated.]("http://x2go.obviously-nice.de/index.php?id=42")[/B][/COLOR]

I think if you consider your own/home Internet speed and the fact that the remote AWS EC2 Ubuntu server is running on an EC2 "micro" instance .. that the performance is actually still pretty good.

x2go is near releasing a new version which will include a java-plugin that will allow you to use any Java enabled Browser as your Desktop client.  You can find that beta now and see how well it works (audio, printing etc).

Brian

---

### Post by kim0 on 2010-12-13
Hi Ezrie,

You may check my blog on x2go in the cloud
[http://foss-boss.blogspot.com/2010/11/show-off-ubuntu-desktop-on-cloud.html](http://foss-boss.blogspot.com/2010/11/show-off-ubuntu-desktop-on-cloud.html)

It should go smoothly if you're running Linux on client side. If you're running Windows, try reading the comments for possible on how to resolve things

---

### Post by Ezrie on 2010-12-13
Thanks.  I'll give it a go!

> **kim0 said:**
> Hi Ezrie,

You may check my blog on x2go in the cloud
[http://foss-boss.blogspot.com/2010/11/show-off-ubuntu-desktop-on-cloud.html](http://foss-boss.blogspot.com/2010/11/show-off-ubuntu-desktop-on-cloud.html)

It should go smoothly if you're running Linux on client side. If you're running Windows, try reading the comments for possible on how to resolve things

---

### Post by Ezrie on 2010-12-14
Finaly got it working.  Great info on your site.  Now just dealing with its incredible slowness.


> **kim0 said:**
> Hi Ezrie,

You may check my blog on x2go in the cloud
[http://foss-boss.blogspot.com/2010/11/show-off-ubuntu-desktop-on-cloud.html](http://foss-boss.blogspot.com/2010/11/show-off-ubuntu-desktop-on-cloud.html)

It should go smoothly if you're running Linux on client side. If you're running Windows, try reading the comments for possible on how to resolve things

---

### Post by kim0 on 2010-12-14
It's a blogspot blog (i.e. it runs on google) :) Check your ISP hehe

---

