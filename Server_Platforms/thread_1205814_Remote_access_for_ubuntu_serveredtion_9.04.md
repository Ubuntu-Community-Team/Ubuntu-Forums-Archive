---
title: "Remote access for ubuntu serveredtion 9.04"
date: 2009-07-06
forum: Server Platforms
---

### Post by Chetan26 on 2009-07-06
HI,
   Iam new to UBuntu  Server Edition.
   
   I want to acess my UBuntu server from my UBuntu desktop 

   I have Installed VNC server on the server machine.

   Can you pls tell how  I can access the server remotely  from the desktop and do the necessary  setup  .


Many thanks
Chetan

---

### Post by jfmanamtr on 2009-07-06
I see that you have vnc setup on your server, so I am assuming you have a GUI on it. You will want to use a VNC viewer. You can find instructions [here]("https://help.ubuntu.com/community/VNC/Clients"). Then you can connect to the server's IP using the program you want.

~John

---

### Post by Chetan26 on 2009-07-06
Hey ,
       Iam have installed VNC server using the following command
           
      Sudo Apt-get install vnc4server

      Iam doing it on Ubuntu9.04 server Edition so there is no GUI
      available with it.

      I have to do some java Swing component setup on the server , It can happen  only if Server can be accessed remotely.


Please provide necessary  help.


Many Thanks
Chetan

---

### Post by HermanAB on 2009-07-06
Howdy,

On a Linux system, VNC is almost always the WRONG solution.  On a server, it can be fatal, since there are scripts that look for VNC servers and which can exploit them in a jiffy.

You would be better off installing ssh server, since it can do everything VNC does and more and it is secure too:
$ ssh -X -C -c blowfish user@server gnome-panel

---

