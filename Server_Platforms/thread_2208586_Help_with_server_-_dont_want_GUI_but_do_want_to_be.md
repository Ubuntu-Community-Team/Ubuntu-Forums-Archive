---
title: "Help with server - dont want GUI but do want to be able to GUI remotely"
date: 2014-03-01
forum: Server Platforms
---

### Post by npinn001 on 2014-03-01
Hi,

So as the title suggests, I want to install the server edition for the optimised kernel, to be run on a headless box. I'd ideally be able to log on to the server remotely any time, and while i am ok with the command line, I would like graphical interface so I can edit word docs etc if needs be.

Whats best - install server and install xfce on top, or, is it possible to just have a gui when remotely connecting? I've read a bit about x11 forwarding but i dont fully understand it, in terms of whether it installs the gui packages on the server anyway, negating the benefit?

Thanks

Nick

---

### Post by lisati on 2014-03-01
When I was running my own server, I normally used a combination of webmin (a web based admin package) and SSH for command line based remote login. I usually limited access via these methods to my own home network. I also had a rarely used monitor and keyboard attached.

Others might be able to suggest other options.

---

### Post by nerdtron on 2014-03-01
You don't need a GUI to work efficiently on the server. Just immerse yourself on the command line and you'll be very amaze on the power it holds.

If you are having a hard time navigating, just use your file browser. Assuming you can already login via ssh, on the location bar of you file browser (dolphin or nautilus or nemo or thunar) put ```
sftp://user@IPaddress:/home/user/
```
You'll be able to browse the filesystem like a local folder, when you edit the files, they will open on gedit or your default text editor.

What else would like to do on the GUI anyway?

---

### Post by npinn001 on 2014-03-01
Thanks to you both.

I guess I just saw it as good on the one hand to have an 'always on' pc I could connect up to and download files to. I use dropbox quite a bit to sync files, so would ideally like to use firefox with a download manager to download large files...

I know most advise doing it without a gui, so I was wondering about alternatives. Not sure I can do the above with command line? Say for example there is a link on a webpage, can i download using CLI?

Thanks

---

### Post by npinn001 on 2014-03-01
Duplicate post.

Or, could I launch Firefox too if remotely connected via ssh?

---

### Post by ajgreeny on 2014-03-01
Have a look at the info for wget with command **man wget** which seems to be what you want for cli downloads.

---

### Post by npinn001 on 2014-03-01
Thanks for the reply.

I had looked at Wget, but figured that if there was say 10 links on one page, that i might struggle to type the URL out each time. Also, im guessing I would have to be on my machine with the page open to know the URL. I'm guessing i could simply launch apps when connected via ssh - so I would just type:

To open the browser, enter:
$ firefox

OR
$ /usr/bin/firefox

Will take a look at wget too. I think you are all correct, no need for a GUI....

---

### Post by m-dw on 2014-03-01
There are CLI based web browsers.  See [http://ubuntuforums.org/showthread.php?t=1174459](http://ubuntuforums.org/showthread.php?t=1174459)

If you really want a GUI application, you have no option but to install an X windows environment, and the applications you want to use.  X forwarding (either via an SSH tunnel or natively (insecurely) runs the application on the server but presents the GUI on a remote desktop.  The trick is to not start X at boot time so it only uses resources when you're actively using it.

---

### Post by npinn001 on 2014-03-01
Ok cool.  Thanks.

So thats one option using a text browser, and another using wget.

is there a way to have a virtual desktop remotely, without installing a gui on the server?

Also, I just thought, the commands i typed before wont work if the gui or X11 isnt installed on the server, or would it?

---

### Post by m-dw on 2014-03-01
You have to install both X11 and the application you want to run on the server.  The classic UNIX way of doing things is just to run the application you want to run.  Taking your example of running firefox, you install X11 and firefox on the server.  You would also have to set up sshd to allow x forwarding (look it up there are loads of references).  There are several things you need to do to ensure the X applications display remotely rather than on the server.  It's best to add them to a login script so it happens automagically every time.

The client device will need also to have an X11 server, and integrate with your SSH client.  You can get free X-windows servers and SSH clients for windows, but they're easier to find for Linux. 

To access the application, you connect to the server with "ssh -X <servername>" and get a command prompt. At the prompt you type "firefox" and if it's all set up properly a firefox web browser will display in a window on your local display.  The application will be running on the server, but the interface will be displaying on your client.  Downloads will go direct from the Internet to your server.  All you see is the image of the web page displayed on your screen.

If you want a full desktop experience (like Microsoft Terminal Services gives you) the easiest thing to do is to install a VNC server, and then install a VNC client on the machine you will be accessing the server from.  You may be able to configure VNC to start X when it receives an incoming connection, but it's usual to be running X and VNC just opens up a new display.

---

### Post by Lars Noodén on 2014-03-01
> **m-dw said:**
> You have to install both X11 and the application you want to run on the server.  ...

[X11 uses a client-server architecture](http://www.freebsd.org/doc/handbook/x-understanding.html) but the relationship is backwards from what many people think.  The display is the X11 server and the client is the application running (e.g. Firefox or LibreOffice) : It is the X server that interacts with the user and the client is the (remote) application.   

Edit: X11 is needed on the remote machine, I just checked.  It gets installed if you add a graphical appllication to the server.

---

### Post by m-dw on 2014-03-01
Yes, because the **controlled** machine (the OP's server) needs the x libraries to know how export the display to the **_controlling_** machine.  The **_controlling_** machine, runs the X server to display the application's GUI.

---

### Post by SeijiSensei on 2014-03-01
I believe you need only install the **xorg** package on the server to use X forwarding over SSH.  That and the programs you wish to run like, say, firefox.

---

### Post by npinn001 on 2014-03-01
Ok, thanks everyone. So for arguments sake, is just installing xorg and using ssh x forwarding beneficial over just installing xfce and then using vnc or say teamviewer?

---

### Post by Lars Noodén on 2014-03-01
Tunneling X is a bit simpler than VNC which itself also has to be tunneled to make the connection secure.  X can be a bit sluggish if there is a lot of latency in the connection, but I don't use VNC often enough to say how that goes.  

However, I tested on a spare machine and found that if you install your graphical application (say Firefox) on a "command-line system", the package manager adds x11-common for you in the dependencies.  So it *should* be enough to just install the applications you want and let APT take care of the rest.

---

### Post by m-dw on 2014-03-01
I think it really depends on what you want to achieve.  I've used VNC to remote control my mum's PC over a 500Kbit/s link secured with OpenVPN and the response was OK.  It was also really easy to set up (install the server on Windows and Remina on my Ubuntu box and we're done).

Just looking at synaptic (so not a recommendation) Ubuntu has tightvncserver, to install on your server
[INDENT]"This package provides a server to which X clients can connect and the
server generates a display that can be viewed with a vncviewer.

The difference between the tightvncserver and the normal vncserver is the
data encoding, optimized for low bandwidth connections. If the client do
not support jpeg or zlib encoding it can use the default one. Later
versions of vncserver (> 3.3.3r2) support a new automatic encoding that
should be equally good as the tightvnc encoding.[/INDENT]

and ssvnc which is described as :
[INDENT]* An enhanced version of the TightVNC client with support for more
encodings and color modes, support for x11vnc and UltraVNC extensions,
dynamic screen resizing, an improved popup menu, etc.

* A GUI that helps set up an SSL (using stunnel) or SSH tunnel to connect
to the VNC server through, as well as forwarding of ports for audio
(esound/aRts), SMB, CUPS etc.[/INDENT]

So installing the server on your server and the client on your other devices (or a windows/mac/android client if more appropriate) might be simpler.... BUT

Using VNC will require you to be running a full desktop environment with a window manager on the server, and that will have an impact on the server you are managing.  You kinda have to decide what you need to achieve and then choose what's best for you.

---

