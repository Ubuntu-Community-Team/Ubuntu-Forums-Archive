---
title: "Server connection"
date: 2006-10-10
forum: Server Platforms
---

### Post by antonioli on 2006-10-10
Hello, Im quite a newbie with linux. I would like to know how could I connect to servers using linux (log on into my school server, for example) or to connect to remote computers. Could someone help? Thanx.

---

### Post by William the Conquerer on 2006-10-10
first off...  do you have authorized access to connect to these remote computers?  You can get in a whole lot of trouble if you don't...

What kind of connection do you want to make?...  Do you want to connect and administrate using VNC or remote desktop or something comperable?  Do you need to connect to administrate one of these computers?  Because you could ssh to the machine as long as the server was started and the port was open...

SOOO, I'm not exaclty sure what you need to do to this remote server, but ssh is a beautiful thing.  If there is an ssh server on your remote server and it is running, you can just type: ```
$ ssh username@remoteIPofServer
``` and it'll ask for a password and wham-o you're in.  Does this help? =)

---

### Post by antonioli on 2006-10-10
Hi, William the Conquerer! Well, yes I have acces to this server (its my school server, and I log on everyday to it at school). I had the idea of connecting to the server using a remote desktop, since I dont really need to administrate the computers. I only wanted to have acces to my account so if one day I forget something in it I could access it from home. The olny problem is that I don't know if it has an ssh on the server, nor to which port connect. How could I find out this things, if they are absolutly necessary? Thanx man!

---

### Post by foxylad on 2006-10-10
I'm slightly suspicious that you don't just ask the school admin to explain how you can access it. Assuming you are supposed to have access, they should be able to explain how you can connect to it.

We cannot help without more information about your school's server. What OS does it run? What services (ssh, vnc, xwindows etc)does it provide? Are they exposed to the internet (dangerous), or just the school network?

---

### Post by antonioli on 2006-10-11
Well Foxylad, here are some answers. In my school we turn a computer on and a Windows 2000 screen comes up and asks the student to put its name and password. Every student in high-school has one. Once we are in our session, we are in a win 2000 environment. We can have access to the closed school network, on where the teachers leave us homework and other stuff, and also access to the internet. The only thing I dont know is if it has ssh or vnc. Could you please tell me how could I figure it out, if necessary? Thanks.

---

### Post by sonic2000gr on 2006-10-11
A Windows 2000 Professional machine will not have any remote desktop by default. VNC can be installed. SSH is mostly a UNIX/Linux thing although there are ways to install in Windows.
On the other hand, if it is your school server you are trying to reach, chances are it is running Windows 2003 Server or Windows 2000 Server. Both have remote desktops but these are intended for administration purposes, UNLESS your school has bought licenses to activate Remote Application Server mode. This is highly unlikely as these licenses cost and are only useful if ordinary users **must** run specific applications on the server itself (highly unlikely).
Bottom line is if the server is Win 2000/2003 Server you will probably not have any access.
If it is however a Linux server (a Linux server can be programmed to act as a Windows server in a Windows network) then all the following must apply:

- You must have an account (obviously you do)
- The server must be running a program for remote access like SSH (terminal based), VNC (desktop) or other.
- The system administrator must give you remote access rights via any of these programs
- The system must have a registered domain name (or a dynamic name from dyndns.org and the like) and expose these remote services to the internet.

These details I'm afraid can only be obtained from your school's admin. So go ask him :)

---

### Post by William the Conquerer on 2006-10-11
to be perfectly honest I'm gonna guess antonioli is probably a little hesitant to talk to an admin about this...  they're usually terrified of quesitons like this ;).  yeah, sonic200gr is exactly right.  My suggestion is that you're probably running on a dumb terminal machine connecting to a local server on the network, When you're at school...  This is good and bad.  Good because it really wouldn't be too hard to connect just like you are from home and kinda do the same thing that you do with your own machine.  Bad because you probably won't get access like this from home, the server is probably only local network accessible.  I doubt the admins would set up a method for outside connections.  If you really want to try this talk to your admin...  and bring cookies.

---

### Post by pppetter on 2006-10-12
They could have set up so that the students have FTP access to their home dir and the "homework" dir that their teachers create...here in stockholm every single school has exactly that setup and I remember that we also could log in at any school of choice. It's pretty big network. 

But yeah. There would probably some sort of information publicly available about that.

---

