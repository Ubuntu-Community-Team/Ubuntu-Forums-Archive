---
title: "Ubuntu 9.10: Ubuntu One not connecting"
date: 2010-01-05
forum: Ubuntu One (CLOSED)
---

### Post by AngelInBlue on 2010-01-05
I've never been able to get my computer to connect to Ubuntu One.  My efforts have led to an Ubuntu One cloud icon being added to my panel. It has an exclamation point inside the cloud.  I click on the cloud icon with an exclamation point to connect, it very briefly turns into a cloud but reverts back to cloud with an exclamation point.

Here are the steps I've taken:

1)   created a user account
2)   clicked on Applications -> Internet -> Ubuntu One
3)   logged in
4)   hit add computer button

Here are additional events that may be relevant when going through the above steps:

A keyring menu appeared.  Not sure what to do, I checked the "always" option.  ( I don't recall exactly what the choice was, I remember that my choice had "always" in it)

I have noscript installed in firefox.  Noscript gave an ABE error message when trying to add my computer on the webpage.  I uncheked the ABE check button on noscript and then clicking the add computer button once more appeared to work.

After going through all of this, Ubuntu one never connects.  I don't get any error messages.  I don't know how to get back to the add computer button on the ubuntuone site to make sure my computer was added.  The ubuntu one client only shows an option to connect.  When I go to the Ubuntu One site directly with firefox, I don't find an option that lists what computers have access, nor an option to add a computer.

I'm running 9.10 64 bit on an AMD CPU.

Any help is appreciated, thank you.

---

### Post by AngelInBlue on 2010-01-05
There is an option to view and add machines to your account on the website.

Go to the Account tab.
One of the choices highlighted in red is "View the machines connected to this account"

---

### Post by meho_r on 2010-01-05
So, did you solve it?

---

### Post by AngelInBlue on 2010-01-05
Not yet.  I've been searching other threads to get an idea of other things to try.
The website did show that my machine is an allowed computer.

---

### Post by meho_r on 2010-01-05
Is that a fresh installed Ubuntu? Did you do any updates?

---

### Post by scottuss on 2010-01-05
Mine was doing this for a long time then some updates the other day seem to have fixed it (I presume thats what it was!)

---

### Post by andrea000 on 2010-01-05
if you have not authorized your pc on u1's website
or can not for some reason open a terminal

applications->accessories->terminal

copy and paste this in the terminal
> u1sync --authorize 

The u1 website should come up asking you to add your
pc.
__________________

---

### Post by AngelInBlue on 2010-01-05
meho_r:
	I did a fresh install last week.
	I checked the update manager and everything is updated

scottuss:
	Thank you for the reply

andrea000:
	It didn't work, but it did help me get further than I had before.

	For others that try this, you first (at least for me) need install ubuntuone-client-tools.

	You can do this using Synaptic or the command line

	sudo apt-get install ubuntuone-client-tools

Before trying Andrea's advice, I went to the ubuntu one site and removed the authorization for my computer.  After trying Andrea's advice to reauthorize my computer, a message came indicating that syncing of files was being performed.  When I checked my account at one.ubuntu.com, none of my files were there.  I also did an attempt with Tomboy, and none of my notes were there.   Since then, I get the same behavior as before when trying to do anything, nothing.

Of course we can't real out user error (that would be me).  I'm still trying to figure out how to get it to work.  I have a netbook with an older version of ubuntu running, I think I'm going to install ubuntu one on it and see if I can at least rule out user error.

---

### Post by Randymanme on 2010-01-10
Thank you very much, Andrea.

randall@randall:~$ u1sync --authorize 
The program 'u1sync' is currently not installed.  You can install it by typing:
sudo apt-get install ubuntuone-client-tools
u1sync: command not found
randall@randall:~$ sudo apt-get install ubuntuone-client-tools
[sudo] password for randall: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ubuntuone-client-tools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.4kB of archives.
After this operation, 217kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe ubuntuone-client-tools 1.0.3-0ubuntu1 [29.4kB]
Fetched 29.4kB in 0s (42.3kB/s)             
Selecting previously deselected package ubuntuone-client-tools.
(Reading database ... 367390 files and directories currently installed.)
Unpacking ubuntuone-client-tools (from .../ubuntuone-client-tools_1.0.3-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up ubuntuone-client-tools (1.0.3-0ubuntu1) ...

randall@randall:~$ u1sync --authorize
Authorized.
randall@randall:~$

---

