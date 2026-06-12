---
title: "x windows on new server install - help"
date: 2011-03-02
forum: Server Platforms
---

### Post by tjs275x on 2011-03-02
i have a brand new ubuntu server online. all i have to connect to it is ssh
i need to install gnome with vnc4server
 
how do i do this over ssh and start x windows so i can connect using vnc
 
here is what i have done
 
installed gnome desktop
 
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg
 
installed vnc4server
 
sudo apt-get install vnc4server xinetd
Start the vnc4server:
vnc4server
 
this is all i have done. i am sure there are more steps but not sure where to go from here
 
note: this is a new install of ubuntu 11.x server
the only this on this server as of right now is gnome and vnc4server
as i installed them
 
and to add:
installing/using x windows of any type, the server is no longer a server cuz of using cpu and memory for gnome desktop
i am from windows server side. so i do not know much about linux
if i have a desktop things will be ez for me to do other then using ssh
right now all i have is ssh, i would like to have a desktop using vnc4server vnc4viewer to admin the server
but i will have to start the services using ssh
 
in time i would love to move all my windows hosting to linux
windows servers have bad uptime, well from my experience i need more time then just 5 months or so

---

### Post by arrrghhh on 2011-03-02
Instead of trying to fit a square peg into a round hole, just use Ubuntu Desktop.

The whole point of the server distro is lean and mean - no unnecessary overhead, and few packages to update.

You can run **all** of the same services on the desktop edition as you can on the server edition, and the desktop edition includes the GUI.

Just to be sure - do NOT install the ubuntu-desktop package on the server edition.  Simply download the desktop edition and reinstall.

---

### Post by tjs275x on 2011-03-02
this is not an option, i ordered the server from a hosting comp
all they have is server for ubuntu
 
i would like to have a desktop

---

### Post by egpetrich on 2011-03-02
At my work, we have a bunch of machines whose job is to host VNC sessions. I think that makes them "servers," though I admit that the term is fuzzy.

If I understood your command sequence, you executed the command "vnc4server" after installing the package. Executing the command should give you an output including lines like this:

```
vnc4server: New 'Xvnc: <username> on <machine>:<num>' desktop is <machine>:<num>
vnc4server: Log file is: /home/<username>/.vnc/<machine>:<num>.log

```

(Note that I'm looking at my work machines, which are *not* Ubuntu. I feel fairly confident that you'll see something similar on your machine, but there may be differences.)

The directory "~/.vnc" is where to look for useful VNC stuff:
[LIST]
[*]If you have a VNC server running, you'll see a file name "<machine>:<num>.pid". This contains the process ID of your session. This is a somewhat convoluted way of determining what your VNC display is called.(The PID file may remain even if your session crashes, but I'll focus on the best case.)
[*]The log files will tell you if tools failed to start.
[*]The script "~/.vnc/xstartup" starts up your window manager and possible other stuff. On my older Ubuntu system, it looks like this:
[/LIST]
```

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
fvwm &

```
(Note that I am running FVWM, not Gnome.)

When you want to kill your VNC server (*not* simply disconnect), you execute "vnc4server -kill".

Assuming you got your VNC server started and you know the display number, you can try to connect from another machine. "vnc4viewer" is, I believe, the Linux viewer, so you need to be running Linux on your personal machine in order to use that program.

There are (I think) several free VNC viewers available for Windows systems. We use RealVNC at work, but they don't offer a free viewer for Vista or Windows 7.

---

### Post by tjs275x on 2011-03-02
i have vnc4server installed how do i start gnome with ssh so i can connect using vnc

---

### Post by arrrghhh on 2011-03-02
> **tjs275x said:**
> i have vnc4server installed how do i start gnome with ssh so i can connect using vnc

Well you can install gnome-core and the like, it's just really not a good idea.

Is there any reason that you **must** have a GUI?  I bet if you take a little time to learn, you'll find you like the CLI much better - you can configure things much faster, and the system will run much better - plus, much less crap to update!

---

### Post by egpetrich on 2011-03-04
> **tjs275x said:**
> i have vnc4server installed how do i start gnome with ssh so i can connect using vnc

I'm working blind here, so let's take things one step at a time.

If I understand correctly, you have installed "ubuntu-desktop" and "vnc4server". First, I would like to know what happens when you log in via SSH and execute the command "vnc4server". What output do you get?

---

### Post by arrrghhh on 2011-03-05
Seriously, just install the actual Ubuntu Desktop.  Don't install ubuntu-desktop package on an Ubuntu Server install.

---

### Post by HW_Hack on 2011-03-08
Keep this very simple - make sure your server has openssh server installed AND also install webmin on your server. Webmin is a web based server management tool.

Now install openssh client on your workstation. Now you can open your favorite browser and enter:
[https://server-name:10000/](https://server-name:10000/)      and you can login to the server and get a easy to manage web interface. And via ssh you can still do CLI work as needed:popcorn:

---

### Post by apunker on 2011-08-11
DTC is better,
[http://www.gplhost.com/](http://www.gplhost.com/)

---

