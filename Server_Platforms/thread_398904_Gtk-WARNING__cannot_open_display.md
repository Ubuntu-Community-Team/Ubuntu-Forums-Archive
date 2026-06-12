---
title: "Gtk-WARNING **: cannot open display:"
date: 2007-04-01
forum: Server Platforms
---

### Post by andydread on 2007-04-01
Hi I have dapper server installed.  Gnome or Kde is not installed GTK is installed.  
When i SSh to the server ssh -CXl username hostname.  I log in and try to 
run a gtk based app that I want to display on my remote machine i get 
Gtk-WARNING **: cannot open display:  On other dapper remote hosts i 
do not get this problem but they have ubunu-desktop package intsalled.. 
Do i have to install the entire desktop package on a server in order to 
get GTK apps to display remotely on a X workstation?  

I tried from the console. 

$ sudo -s
# xhost +  

 xhost:  unable to open display
I tried 
export DISPLAY=ipaddress_of_pc:0.0
export DISPLAY=LOCAL:0


still did not work. 

Any help will be appreciated thanks. 
Andy.

---

### Post by revertex on 2007-04-24
```
sudo cp $HOME/.Xauthority /root/.Xauthority
```

you could use:

```
sudo yougtkrapp
```

or install gksudo

```
gksudo yourgtkapps
```

can you run X apps  remotely as user?

---

