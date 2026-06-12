---
title: "Stay connected to VNC during logout"
date: 2009-08-05
forum: Security
---

### Post by davethewave83 on 2009-08-05
How can I stay connected to VNC, or be able to connect to VNC while the screen is logged out. I would like to be able to connect instantly to my machine upon boot up like with RDC of Windows.

---

### Post by bodhi.zazen on 2009-08-05
Use an alternate vnc server, such as vnc4server or similar.

Not sure you can watch your machine boot over VNC (you can if it is booting in virtualization).

---

### Post by HermanAB on 2009-08-06
Use SSH.  It can do everything VNC does, only better and securely.  VNC is a serious security hole.

ssh -C -c blowfish -X user@server "gnome-panel"

---

### Post by davethewave83 on 2009-08-06
> **HermanAB said:**
> Use SSH.  It can do everything VNC does, only better and securely.  VNC is a serious security hole.

ssh -C -c blowfish -X user@server "gnome-panel"

Thanks, I don't know anything about SSH though, or how to run it on windows.

*edit* I just download Putty.exe for Windows, it lets me ssh to Ubuntu but says Cannot open display:
run 'gnome-panel --help' to see a full list of available command line options"

---

### Post by bodhi.zazen on 2009-08-06
You have to run an X client on Windows, see Xming

[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

I run Xming and Putty on a usb =)

Then when you connect with putty, you have to allow X 

It is in the menu on the right, when you first start Putty, before you connect.

Under "connection"
Under the "X11" sub menu

check off the box "Enable X11 forwarding"

Then start Xming
Then connect via putty.

---

### Post by davethewave83 on 2009-08-06
> **bodhi.zazen said:**
> You have to run an X client on Windows, see Xming

[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

I run Xming and Putty on a usb =)

Then when you connect with putty, you have to allow X 

It is in the menu on the right, when you first start Putty, before you connect.

Under "connection"
Under the "X11" sub menu

check off the box "Enable X11 forwarding"

Then start Xming
Then connect via putty.

Thanks but it appears to be hopeless.
Start Xming: no client (will chose later) 
Xming starts up...

start putty
Enable X11 forwarding 
X display location *my local IP*
"Open" 
login as: myname *success*
myname@server's password:
Linux server 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686

/usr/bin/X11/xauth: error in locking authority file /home/myname/.Xauthority

myname@server:~$ ssh -C -c blowfish -X myname@server "gnome-panel"
*fail*
Warning: No xauth data; using fake authentication data for X11 forwarding. /usr/bin/X11/xauth: error in locking authority file /home/myname/ .Xauthority X11 connection rejected because of wrong authentication.
Cannot open display:
Run 'gnome-panel --help' to see a full list of available command line options.

the authentication appears to be wrong, but I have not yet the knowledge on how to fix that.

---

### Post by bodhi.zazen on 2009-08-06
> **davethewave83 said:**
> Thanks but it appears to be hopeless.
Start Xming: no client (will chose later) 
Xming starts up...

start putty
Enable X11 forwarding 
X display location *my local IP*
"Open" 
login as: myname *success*
myname@server's password:
Linux server 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686

/usr/bin/X11/xauth: error in locking authority file /home/myname/.Xauthority

That is all you need to do. Now forward a test application by entering a command into putty, example (I like to use xeyes for testing)

```
xeyes
```

Or if you prefer :

```
gnome-panel
```

Assuming you have gnome installed on your server of course =)

> myname@server:~$ ssh -C -c blowfish -X myname@server "gnome-panel"
*fail*
Warning: No xauth data; using fake authentication data for xll forwarding. /usr/bin/X11/xauth: error in locking authority file /home/myname/ .Xauthority X11 connection rejected because of wrong authentication.
Cannot open display:
Run 'gnome-panel --help' to see a full list of available command line options.

the authentication appears to be wrong, but I have not yet the knowledge on how to fix that.

This second command "myname@server:~$ ssh -C -c blowfish -X myname@server "gnome-panel" " is un-necessary, you have already connected via putty.

---

### Post by davethewave83 on 2009-08-06
> **bodhi.zazen said:**
> That is all you need to do. Now forward a test application by entering a command into putty, example (I like to use xeyes for testing)

```
xeyes
```

Or if you prefer :

```
gnome-panel
```

Assuming you have gnome installed on your server of course =)



This second command "myname@server:~$ ssh -C -c blowfish -X myname@server "gnome-panel" " is un-necessary, you have already connected via putty.

thanks for the reply, now I am getting:
myname@server:~$ xeyes
PuTTY X11 proxy: wrong authentication protocol attemptedError: Can't open display: localhost:10.0

*edit* I thought maybe it is because it is trying to run display on localhost:10.0 so I export DISPLAY *my ip address*:1.0 then configured Xming to run on screen 1. 

but it still says cannot connect to the display

In the Xming log it says 
AUDIT: Thu Aug 06 19:38:33 2009: 7024 Xming: client 1 rejected from IP *my IP*
winProcEstablishConnection - ProcEstablishConnection failed, bailing.
AUDIT: Thu Aug 06 19:42:44 2009: 7024 Xming: client 1 rejected from IP *my IP*

---

### Post by bodhi.zazen on 2009-08-06
localhost:10.1 is correct (that is what ssh -X uses).

My guess is Xming is not configured properly, try a few different settings when you start it.

---

### Post by davethewave83 on 2009-08-06
> **bodhi.zazen said:**
> localhost:10.1 is correct (that is what ssh -X uses).

My guess is Xming is not configured properly, try a few different settings when you start it.

hmm something is buggy because none of this is working

I get PuTTY X11 proxy: wrong authentication protocol attempted
:(

---

### Post by strid3r on 2013-04-01
I had this same problem

In Putty Settings Go to Connection > SSH > X11

Tick the Checkbox "Enable X11 forwarding"

for "X Display Location" put

```
localhost:0
```


Make sure Xming is running and voila!

---

### Post by cariboo on 2013-04-01
I guess you didn't notice that the last post in this thread was made in August of 2009, and the thread is marked solved. Thread closed.

---

