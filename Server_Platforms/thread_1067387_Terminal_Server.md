---
title: "Terminal Server"
date: 2009-02-11
forum: Server Platforms
---

### Post by arapozo on 2009-02-11
Hello, I'm evaluating the possibility of using linux to setup a terminal server for remote users to be able to use the browser from their workstations.
I want to know if there's a solution for Linux that could make the clients only launch an application without having to "see" the entire desktop. The clients would be Windows XP computers.

---

### Post by arapozo on 2009-02-12
After some searching I've come up with FreeNX and Nomachine NX.
I remember a while ago I configured a testing environment where I had an X client and using SSH I could run a remote program locally.
Has someone done something like this that can give me some pointers?
Maybe a script or some configuration I could do on the profiles to make it so that when they log with the ssh client ti automatically launches the application and when it closes it logs them off.

---

### Post by koenn on 2009-02-12
I haven't used NoMachine, but here's something similar:
it 's about exporting X over ssh, see [http://users.telenet.be/mydotcom/howto/linux/xremote.htm](http://users.telenet.be/mydotcom/howto/linux/xremote.htm)
it can be done from windows but it requires some work. 
In the end, when you've set it all up, you could create a desktop shortcut that executes (a batch file with) the required commands so to the users it's just a matter of clicking.

---

### Post by arapozo on 2009-02-13
I was able to achieve what I want with FreeNX and used Xming or Nomachine NX client to connect to the box.
The thing is that the Nomachine shows me the whole screen and I just want the web browser, but the advantage is that is easier to set up.
I tried Xming and configured a .xlauch file that runs firefox, but I have three problems: 

1) Putty gives an error saying that it cannot load the file 192.168.10.5 which is the ip of the Virtual machine i'm testing. 
2) The fonts look really small. 
3) When I quit firefox, xming doesn't close.

Anybody has any experience with this that can help me?

Also, is this the best route for this regarding bandwidth usage? Or is there a better option?

---

