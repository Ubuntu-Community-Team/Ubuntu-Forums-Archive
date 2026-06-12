---
title: "Create/run a script on login?"
date: 2010-02-19
forum: Server Platforms
---

### Post by Saidear on 2010-02-19
I'm tunneling VNC over SSH, which I manage to get working.  What I want to do is this:
Load into GDM as soon as Ubuntu finishes loading (I think I got this to work via the login screen config).

As soon as it loads, I want it to run the command:
x11vnc -safer -localhost -nopw -once -display :0


This way I don't need to issue that command over SSH anymore.  Can I do this?  Or is there a 'better way' to access the GUI. The machine is being stored well away from monitor/keyboard, so accessing it remotely is the way I want to do it.  I'm not entirely comfortable working from the commandline so GUI it is.  Any advice?

---

### Post by i.r.id10t on 2010-02-19
Put your command (perhaps with full path in it) in /etc/rc.local

---

### Post by suseendran.rengabashyam on 2010-02-19
Hi,

I guess you can pass the command 'x11vnc -safer -localhost -nopw -once -display :0' while you are establishing a SSH Tunnel.

Enter the following command in the terminal

```
ssh  -t  -L  <localmachineport>:localhost:<remotemachineport>  <username>@<remote-machine-ip>  'sudo x11vnc -safer -localhost -nopw -once display :0'
```

Then open any VNC Viewer and enter 'localhost:0' to view the remote machine.

Further details can be found in
[https://help.ubuntu.com/community/VNC#Guide to example scenarios](https://help.ubuntu.com/community/VNC#Guide to example scenarios) and in man page of 'x11vnc'.

Hope it helps.

---

### Post by Saidear on 2010-02-19
> **suseendran.rengabashyam said:**
> Hi,

I guess you can pass the command 'x11vnc -safer -localhost -nopw -once -display :0' while you are establishing a SSH Tunnel.

Enter the following command in the terminal

```
ssh  -t  -L  <localmachineport>:localhost:<remotemachineport>  <username>@<remote-machine-ip>  'sudo x11vnc -safer -localhost -nopw -once display :0'
```

Then open any VNC Viewer and enter 'localhost:0' to view the remote machine.

Further details can be found in
[https://help.ubuntu.com/community/VNC#Guide to example scenarios](https://help.ubuntu.com/community/VNC#Guide to example scenarios) and in man page of 'x11vnc'.

Hope it helps.

I'm using PuTTY on an XP machine to do this.. not sure how to pass that through.

---

### Post by suseendranrb on 2010-02-21
Hi,

Ok, Let me give it a try

Open PuTTy, enter the Ubuntu Machine IP address in the 'Host Name(or IP address)' column.

Go to Category->Connection->SSH, enter the following in 'Remote command:'

```
sudo x11vnc -safer -localhost -nopw -once -display :0
```

Then go to Category->Connection->SSH->Tunnels

In the 'Source Port' column enter your local machine port '5900' and in the 'Destination' column enter 'localhost:5900'. If you have configured your VNC to listen on different ports then change it accordingly. Click on 'Add' to save the tunnel.

Come back to Category->Session, enter a relevant name in 'Saved Sessions' and click on 'Save'.

Now when you double click the saved session you will be able to connect to the Ubuntu Machine and the remote command will execute. 

Hope it helps.

---

### Post by Saidear on 2010-02-24
> **suseendranrb said:**
> Hi,

Ok, Let me give it a try

Open PuTTy, enter the Ubuntu Machine IP address in the 'Host Name(or IP address)' column.

Go to Category->Connection->SSH, enter the following in 'Remote command:'

```
sudo x11vnc -safer -localhost -nopw -once -display :0
```

Then go to Category->Connection->SSH->Tunnels

In the 'Source Port' column enter your local machine port '5900' and in the 'Destination' column enter 'localhost:5900'. If you have configured your VNC to listen on different ports then change it accordingly. Click on 'Add' to save the tunnel.

Come back to Category->Session, enter a relevant name in 'Saved Sessions' and click on 'Save'.

Now when you double click the saved session you will be able to connect to the Ubuntu Machine and the remote command will execute. 

Hope it helps.
Woot!

That seems to do the trick, much thank you!

---

