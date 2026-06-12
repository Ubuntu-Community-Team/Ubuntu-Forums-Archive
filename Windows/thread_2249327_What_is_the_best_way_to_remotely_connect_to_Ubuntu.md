---
title: "What is the best way to remotely connect to Ubuntu 14.04 from Windows 7/8"
date: 2014-10-21
forum: Windows
---

### Post by Penguin360 on 2014-10-21
I have an Ubuntu 14.04 box and a Windows 7 box, and I would like to remotely connect to my Ubuntu box from the Windows box. What is the best and secure way to do it? Desktop Sharing, XRDP, VNC, or something else?

Thanks!

---

### Post by Lars Noodén on 2014-10-21
Well, the all-around best way is with ssh, but what is your definition of best?  ;)  What do you want to do remotely?

---

### Post by Penguin360 on 2014-10-21
> **Lars Noodén said:**
> Well, the all-around best way is with ssh, but **what is your definition of best?**  ;)  What do you want to do remotely?

Good point and sorry I didn't make it clear. I should say "preferred" instead of "best". My Ubuntu box is in another building from my Windows machine, and I need to remotely connect to it just like I am sitting in front of it. Did I say I prefer to have GUI? :p

---

### Post by Penguin360 on 2014-10-22
OK, so far I have tried to use Desktop Sharing and XRDP, but neither worked. When I use RealVNC viewer to connect my Ubuntu from Windows 7, it says "The connection was refused by the host computer", I think it is related the encryption and I have to turn off the encryption in Ubuntu but I kinda don't want to. Then I installed XRDP in Ubuntu and when I used Windows Remote Desktop Connection to connect, I got a blank gray screen. I searched the forum and found this post [http://ubuntuforums.org/showthread.php?t=1899111](http://ubuntuforums.org/showthread.php?t=1899111), but creating .xsession file suggested in the post didn't work for me. Maybe I missed something?

---

### Post by Bucky Ball on 2014-10-22
You want to know how to access a Ubuntu machine from Windows using remote desktop sharing? That is a Windows question. While you are free to post this here, you may improve your chances of support by posting on a Windows forum also. 

*Thread moved to **Windows**.*

---

### Post by Penguin360 on 2014-10-22
What is it a Windows question? I need to remotely connect to my Ubuntu from Windows.

---

### Post by Bucky Ball on 2014-10-22
Yes, you are using Windows. No idea how to run a remote desktop in Windows, sorry.

---

### Post by Penguin360 on 2014-10-22
> **Bucky Ball said:**
> Yes, you are using Windows. No idea how to run a remote desktop in Windows, sorry.

LOL, you are a funny guy. Yes, I am using Windows, but also using Ubuntu. Still thank you for your reply.

---

### Post by Lars Noodén on 2014-10-22
> **Penguin360 said:**
> OK, so far I have tried to use Desktop Sharing and XRDP, but neither worked. When I use RealVNC viewer to connect my Ubuntu from Windows 7, it says "The connection was refused by the host computer", I think it is related the encryption and I have to turn off the encryption in Ubuntu but I kinda don't want to. Then I installed XRDP in Ubuntu and when I used Windows Remote Desktop Connection to connect, I got a blank gray screen. I searched the forum and found this post [http://ubuntuforums.org/showthread.php?t=1899111](http://ubuntuforums.org/showthread.php?t=1899111), but creating .xsession file suggested in the post didn't work for me. Maybe I missed something?

Worse than that, the encryption for VNC and the others is inadequate and needs to be tunneled through SSH for the foreseeable future.  

If you're looking to run individual graphical applications, you can use just plain SSH for that using X11 forwarding.  You'll need to add an X server like [Xming](http://sourceforge.net/projects/xming/) on your legacy system.  And I guess your SSH client would be PuTTY.  Hopefully someone still on Windows can chime in with the details, it's not difficult but not as straight forward as on Ubuntu or OS X.

---

### Post by JazzPotato on 2014-10-22
I do this the other way round, administering windows machines remotely through vnc with my ubuntu laptop. However the steps are pretty much the same:
1) Install a remote desktop "server" on the machine you want to access (I believe vino is an easy one for gnome desktops eg ubuntu)
2) Install a remote desktop "client" on your machine so you can view the desktop with your selected protocol (eg vnc) (I use remmina in ubuntu but there are many good free ones for windows)
I believe this is where you got up to.
To access the machine from outside the machine's local area network, you will have to forward the port for vnc or whatever remote desktop protocol you happen to be using. (tutorial [http://portforward.com/english/routers/port_forwarding/](http://portforward.com/english/routers/port_forwarding/) )
However, as Lars Nooden pointed out encryption for vnc is inadequate, so if you have a vpn set up on the machines' network, as I do, you can access the machines through the vpn servers' encrypted connection and be safe. X11 forwarding over ssh is a little trickier.

---

### Post by Penguin360 on 2014-10-22
Finally I got it working. It turned out that the trick in the other post of creating a .xsession file does not work any more in 14.04. I followed this YouTube video ([http://youtu.be/L1ay7toiJ6k?list=UU2T42eA_KqVx9P4W5xUOw0Q](http://youtu.be/L1ay7toiJ6k?list=UU2T42eA_KqVx9P4W5xUOw0Q)) and installed MATE DE and then created a .xsession with this line in it:
```
mate-session
```

Now I can connect to my Ubuntu from Windows 7 by using Remote Desktop Connection.

---

