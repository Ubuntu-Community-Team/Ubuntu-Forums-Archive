---
title: "Ubuntu Server ---New user help!"
date: 2008-10-05
forum: Server Platforms
---

### Post by Kentanner11 on 2008-10-05
Hi!
I tried installing different Linux platforms about a year ago, but never got far. Anyways, my home network needs have increased so I bought a Compaq ProLiant DL380 G2 off of Ebay without an OS. Naturally, I installed Ubuntu Server... a few weeks and a few headaches (mostly due to my lack of knowledge) I have it up and running. 

I just installed the GUI, and really like it. My main problem is that I can't log in to the administrator account. I dont recall being asked for a password during the install. I am able to log into the user acct. that was set up during install(name and pass), and I would be content with it, but it lacks different privileges that are needed to use this server for its original intent.

I am super confused!:confused: Any help would be appreciated! :)

Thanks!
~Tanner

---

### Post by GISuser on 2008-10-05
To access root privaleges in Ubuntu type sudo before the command (in the terminal).  For example,
sudo ifconfig -a

this will show your network settings.  No harm done.

Then you will be prompted for a password.  This is the same password that you created during the install and that you log in with.  Ubuntu will give you root privelages for that command only.  You can continue to use sudo without a password for another 10 minutes or so before having to re-enter your password.

If you want to run Nautilus with root privlages, in a termninal type:
sudo nautilus

If you want to become root (superuser) type in a terminal:
sudo -i
then enter your passoword.  Type 
exit 
to become the login user again

---

### Post by Kentanner11 on 2008-10-05
I got it! Thanks

Different Question----

I am using the GUI-
Why is it that when I try to change a setting I have to unlock it and enter my password before I do anything? Is there a way to stop this? I just created a new administrator account but it wont let me unlock it and says "could not authenticate" An unexpected error has occurred. 

Thanks!

---

### Post by GISuser on 2008-10-05
Anytime you run a command that requires superuser (root) privlages, you will have to unlock by entering your password.  This may seam like a pain, but it will prevent you from making a drastic mistake in the future! You will get use to this and thank the builders that this feature is present if you ever tried to invoke a command that would have destroyed your system or deleted data.  You cannot stop the unlock while in the GUI.

As far as the "could not authenticate" error, who are you logged in as? The user you created at the time of the install, or the new adminstrator account?  Also, when you created the new adminstrator account, did you modify the user privalges when you created the account.  If using the GUI, look at the Properties Tab>User Privelages on the User and Groups dialog box.  This may be a little different under 8.04 (I am still running 7.10).  Check the privelages and check to see if any of them need to be check for what you are trying to do.  Sorry to be vague, but if you provide more detail others will be able to help you in more detail.

---

### Post by Kentanner11 on 2008-10-05
I guess I can get used to it..

After creating the new admin acct. in the user acct set up during installation I was unable to unlock anything. Naturally, I logged off then logged back into the user acct set up during the installation, that I used to create the new admin acct, and couldn't unlock anything either, even though I was able to before the admin acct creation. 

This all occurred after I created the new administrator acct. even though I didnt change any settings in the user acct set up during installation.

---

### Post by Kentanner11 on 2008-10-05
Seems to be a bug:

[http://ubuntuforums.org/showthread.php?t=788538&highlight=server+unlock&page=3](http://ubuntuforums.org/showthread.php?t=788538&highlight=server+unlock&page=3)

Exact same problems I am having- right after adding a second acct. from the GUI.

---

### Post by Kentanner11 on 2008-10-05
> **Kentanner11 said:**
> Seems to be a bug:

[http://ubuntuforums.org/showthread.php?t=788538&highlight=server+unlock&page=3](http://ubuntuforums.org/showthread.php?t=788538&highlight=server+unlock&page=3)

Exact same problems I am having- right after adding a second acct. from the GUI.

Fixed this issue:
used these threads/websites for help and a solution!
[http://ubuntuforums.org/showthread.php?t=933783&highlight=unlock+authenticate](http://ubuntuforums.org/showthread.php?t=933783&highlight=unlock+authenticate)
[http://ubuntuforums.org/showthread.php?t=904787&highlight=unlock+authenticate](http://ubuntuforums.org/showthread.php?t=904787&highlight=unlock+authenticate)
and The best:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
(do Case 1)

---

### Post by Kentanner11 on 2008-10-05
Ok heres a question: how can I connect/control my server from another computer on my network? I am pretty sure it is called VNC.. I have used [Real VNC ]("http://www.realvnc.com/index.html") in the past with Xp and Vista, and tried to install it (the linux version) on my ubuntu server and dont know how to install it.

---

### Post by Kentanner11 on 2008-10-05
> **Kentanner11 said:**
> Ok heres a question: how can I connect/control my server from another computer on my network? I am pretty sure it is called VNC.. I have used [Real VNC ]("http://www.realvnc.com/index.html") in the past with Xp and Vista, and tried to install it (the linux version) on my ubuntu server and dont know how to install it.

Nevermind- I didnt have to install realVNC server on my server just enable remote dekstop...

---

### Post by GISuser on 2008-10-05
Since you are running a GUI on the server, first set up the server to allow remote access:

note: I am running 7.10, not 8.04.

1. System>Preferences>Remote Desktop
2. Select appropriate boxes to suite your needs

Then on the client machine (the machine you will use to connect to the server)
1. Applications>Internet>Terminal Server Client
2. In the General tab:
       Computer: enter ip address of the server. 
       Protocol: VNC
       User Name:  this has to be a name of a user on the server
       Password:  password of the user on the server
3. Press Connect.

Now the terminal way, the server should already have ssh running.  From the client machine, assuming frank is a user on the server, type, ssh frank@IPaddressOfServer

And I hope this works for you.

---

### Post by Kentanner11 on 2008-10-05
> **GISuser said:**
> Since you are running a GUI on the server, first set up the server to allow remote access:

note: I am running 7.10, not 8.04.

1. System>Preferences>Remote Desktop
2. Select appropriate boxes to suite your needs

Then on the client machine (the machine you will use to connect to the server)
1. Applications>Internet>Terminal Server Client
2. In the General tab:
       Computer: enter ip address of the server. 
       Protocol: VNC
       User Name:  this has to be a name of a user on the server
       Password:  password of the user on the server
3. Press Connect.

Now the terminal way, the server should already have ssh running.  From the client machine, assuming frank is a user on the server, type, ssh frank@IPaddressOfServer

And I hope this works for you.

Does this only work on Linux?
I am using RealVNC to let my Vista L.T. see my ubuntu server.

---

### Post by Girya on 2008-10-05
If you use real or tight vnc you can use your web browser on your vista box to access the server by typing in the servers ipadress and the port 5801 for a start. 

for example: 192.168.1.100:5801

---

### Post by Kentanner11 on 2008-10-05
> **Girya said:**
> If you use real or tight vnc you can use your web browser on your vista box to access the server by typing in the servers ipadress and the port 5801 for a start. 

for example: 192.168.1.100:5801

would I have to install RealVNC on my server?

---

### Post by Girya on 2008-10-05
> **Kentanner11 said:**
> would I have to install RealVNC on my server?

Yes, here is the link from debian: [http://http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html]("http://http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html")

It might be easier to install the realvnc viewer to your vista box than messing with the java stuff on your server. 

I installed tightvnc and the java classes (?) on my desktop so I could vnc from any computer with a web browser.  It wasn't too hard maybe 3 beers hard:) You should probably check out the security risk for doing what i did.

---

### Post by Kentanner11 on 2008-10-05
> **Girya said:**
> Yes, here is the link from debian: [http://http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html]("http://http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html")

It might be easier to install the realvnc viewer to your vista box than messing with the java stuff on your server. 

I installed tightvnc and the java classes (?) on my desktop so I could vnc from any computer with a web browser.  It wasn't too hard maybe 3 beers hard:) You should probably check out the security risk for doing what i did.

Cool- I have that all set up... how does typing in the IP address and port into the URL fit in? I tried it and did nothing... just letters and numbers un the upper left corner of the page.

---

### Post by Girya on 2008-10-05
> **Kentanner11 said:**
> Cool- I have that all set up... how does typing in the IP address and port into the URL fit in? I tried it and did nothing... just letters and numbers un the upper left corner of the page.

you have to start the vnc server

for my desktop I open a terminal and type tightvncserver and that starts the the server. then as a test I typed in in the adress bar of my desktops browser localhost:5801 and I get a vnc login screen that asks for a password. its been awhile since I've messed with vnc so I'm a bit rusty.

So try typing realvnc then hit the tab button and see what your options are for the realvncserver. 

goodluck!

---

### Post by Girya on 2008-10-05
> **Girya said:**
> you have to start the vnc server

for my desktop I open a terminal and type tightvncserver and that starts the the server. then as a test I typed in in the adress bar of my desktops browser localhost:5801 and I get a vnc login screen that asks for a password. its been awhile since I've messed with vnc so I'm a bit rusty.

So try typing realvnc then hit the tab button and see what your options are for the realvncserver. 

goodluck!

I just looked at realvncs' website and to start the ir vnc server open a console and type vncserver here is what i cut out from their docs.

> Running a Unix server

To X applications, a VNC server appears just like the standard X display you sit in front of, but without a physical screen attached. The applications don't know this, they just carry on running whether or not a viewer is connected. You can start a new VNC server on a Unix machine by typing:

vncserver

If you haven't run a VNC server before you will be prompted for a password, which you will need to use when connecting to this server. All your servers on the same Unix machine will use the same password, and you can change it at a later date using

vncpasswd

With a normal X system, the main X display of a workstation called &#8217;snoopy&#8217; is usually snoopy:0. You can also run as many VNC servers on a Unix machine as you like, and they will appear as snoopy:1, snoopy:2 etc, as if they were just additional displays. Normally vncserver will choose the first available display number and tell you what it is, but you can specify a display number if you always wish to use the same one:

vncserver :2

You can cause applications to use a VNC server rather than the normal X display them by setting the DISPLAY environment variable to the VNC server you want, or by starting the application with the -display option.
For example:

xterm -display snoopy:2 &

You can kill a Unix VNC server using, for example:

vncserver -kill :2

Full instructions for installing and running VNC server for Unix can be found in the documentation.

Nothing will appear immediately as a result of starting a Unix VNC server. To see anything you need to connect a viewer to the server, see below.

---

### Post by Kentanner11 on 2008-10-05
Wow! Thanks!!!! I have to read some of the doccumentation on how to install it on my Server...

---

