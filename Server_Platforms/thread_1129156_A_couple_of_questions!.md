---
title: "A couple of questions!"
date: 2009-04-18
forum: Server Platforms
---

### Post by police512 on 2009-04-18
Hey,

I have a couple of questions. I have a ubuntu 8.10 server edition installed and working... I have a server which is connected to 3 windows computers via wifi, my server is connected to the router atm but my questions are;

1. Is it possible to view/monitor/control user's desktops when they are logged in to the server?? for eq: i am see who is logged and on the server and watch what they are doing... and see what programs they have ran??

2. Is it possible to login into my servers's GUI interface on my server from windows?? because at my work they use windows so is it possible to login and control a GUI (Gnome) and use the internet and ect...

Thanks police512

---

### Post by PacSci on 2009-04-18
1. You can see WHO is logged on to a server and what they are doing with the "w" command, and you can see all the processes someone is running with "ps aU theirusername", but you can't literally watch their desktop as far as I know.

2. If you set up a VNC server on your server, and set up a VNC client on your Windows box, you'll be able to. I've never used VNC, though, so I don't have any software recommendations.

---

### Post by alfplayer on 2009-04-18
To connect to and control any desktop they must be configured appropriately (it is posible to control windows and linux desktops). How it's done depends on the server and the client's operating systems.

---

### Post by bigbearomaha on 2009-04-18
to *safely* control a remote desktop from Linux or windows, especially  over the internet, you might seriously consider using vnc over ssh.

You can do this easy by installing "Cygwin" and TightVNC  on your windows machine. Then connect to your Linux machine over an ssh connection.

Big Bear

---

