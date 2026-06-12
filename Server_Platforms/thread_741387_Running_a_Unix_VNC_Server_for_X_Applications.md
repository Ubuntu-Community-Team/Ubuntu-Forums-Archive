---
title: "Running a Unix VNC Server for X Applications"
date: 2008-03-31
forum: Server Platforms
---

### Post by egonzalez on 2008-03-31
[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]  In order to explain the problem, I have to give a brief background of what is done from a clean installation of Ubuntu Sever v7.10
 
To X applications, a VNC server appears just like the standard X display you sit in front of, but without a physical screen attached. The applications don't know this, they just carry on running whether or not a viewer is connected. 
 
You can start a new VNC server on a Unix machine by typing:
 
***[COLOR=red]vncserver[/COLOR]***
 
If you haven't run a VNC server before you will be prompted for a password, which you will need to use when connecting to this server. All *your* servers on the same Linux machine will use the same password, and you can change it at a later date using
 
[COLOR=red]***vncpasswd***[/COLOR]
 
With a normal X system, the main X display of a workstation called **[COLOR=black]’snoopy’ [/COLOR]**is usually **snoopy:0**. You can also run as many VNC servers on a Unix machine as you like, and they will appear as **snoopy:1**, **snoopy:2** etc, as if they were just additional displays. Normally vncserver will choose the first available display number and tell you what it is, but you can specify a display number if you always wish to use the same one:
 
[COLOR=red]***vncserver :2***[/COLOR]
 
You can cause applications in another Unix box to use a VNC server (in other Linux box) rather than the normal X display them by setting the DISPLAY environment variable to the VNC server you want, or by starting the application with the [COLOR=red]***-display***[/COLOR] option.
 
For example:
 
[COLOR=red]***xterm -display snoopy:2 &***[/COLOR]
 
Here is where I've got the problem becasuse, in the other Unix box, the following message appears after trying to redirect the output of the [COLOR=black]**xterm**[/COLOR] command (the last command) to the Linux box with Ubuntu:
 
 
***[COLOR=red]Xlib: connection to "snoopy:2.0" refused by server[/COLOR]***
***[COLOR=red]Xlib: Client is not authorized to connect to Server[/COLOR]***
***[COLOR=red]xterm Xt error: Can't open display: snoopy:2[/COLOR]***
 
 
It means that the connection to the server (the Linux box) can not be stablished because authorization issues. Ok, so I tried in the server (the one I plan to use as the VNC server) the following command in order to accept X connections from the Unix box (the client wich is running the application):
 
 
[COLOR=red]***xhost +IP_address_of_Client_Unix_box***[/COLOR]
 
 
But then the following error appears:
 
 
[COLOR=red]***xhost: unable to open display ""***[/COLOR]
 
 
Even more, I've tried to run the same command with no restrictions at all:
 
 
***[COLOR=red]xhost +[/COLOR]***
 
 
But the result is the same as the above.
 
 
[COLOR=black]**So the question is, is there something I'm missing from the Ubuntu server's point of view (the VNC server) in order to accept connections from the Unix box (the client) keeping in mind that I allways have the same result with the xhost command?**[/COLOR]
 
[COLOR=black]**I hope you can help me solving this issue!! :confused:**[/COLOR]
 
  I'd like to clarify just a little bit more.
The client machine is a Sun Sparc running a NMS (Network Management System) on Solaris, there is where I try to run the command:
 
[COLOR=red]***xterm -display ubuntu_vnc_server:view***[/COLOR]
 
The server machine is the one running Ubuntu Server with VNC server, where the VNC server is running with the command:
 
***[COLOR=red]vncserver :view[/COLOR]***
 
So, the people can be able to view the Xterm that is running on the Sparc Station via the VNC server....
 
 
Now, OK, I know SSH is more secure than VNC but for some reasons I can not explain now, I can not install SSH on the Solaris machine so, what can I do in order to get this application to work knowing that the Sun Sparc station does not have any SSH server?

Even more, the only way I have access to the Sun Sparc is via Telnet.....
 
I hope you can help me with this situation.

The last tip, you can kill a Unix VNC server using, for example:
 
***[COLOR=red]vncserver -kill :2[/COLOR]***

---

