---
title: "Ubuntu Cloud installation - should I install xorg + fluxbox or xfce4"
date: 2015-06-01
forum: Ubuntu Cloud and Juju
---

### Post by ndnd on 2015-06-01
Hi, 

My server is ubuntu 15.X version. I have gone through the 

link [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)


I am have been using Xorg package on the server since we have a GUI software installed on the server that users have to access through tightVNC  x11 forwarding. We are now moving to the cloud and would like to see if there is a good windows explorer package so that the users can find it easy to navigate to their files on the server. 

I was exploring the new options and came accross the xfce4 which seems to be lightest desktop -correct? however, I believe it still has additional packages like (browser, games) we only need a way to open the GUI software and windows explorer like package to access files on the server. 

What packages would you recommend. Among all this the no. 1 priority is to keep the lightest option to get performance. So if you still think xfce4 (or something even lighter) is better than the xorg+windows explorer package(I don't know which would be better so names please!) please let me know. 

I would appreciate the right name and packages so that I can install them correctly. 

Please treat me as a novice (Details will be appreciated) ;)If you need more info on my end please let me know. 

Thanks in advance

---

### Post by TheFu on 2015-06-01
If users need to get to files on a remote server, setup ssh, with sftp and have them use an sftp client. No need for a bloated remote desktop solution at all.  All the Linux file browsers support sftp (with keys if you want to be more secure).  WinSCP is nice for Windows people.

openssh-server is the package for sftp. You don't need/want the other options.

In short, you don't need **any** GUI on a server. It is a security consideration and running X/Windows isn't good for server security.







IMHO.

---

### Post by QIII on 2015-06-01
+1

If it isn't bad enough just that something is eating resources, every unnecessary service exposes vulnerabilities.

A server should only run the barest minimum of services to fit its purpose.  The "GUI on a server" is not a common practice in the *nix world.

---

### Post by ndnd on 2015-06-01
thanks. Yes indeed Winscp along with Putty is a great solution that we have been using. However, we still need the GUI due to the software application installed there which is the reason for having the system in the first place. 

Anyway figured out the solution for this for now xfce4 works great...! 

Thanks once again!

---

### Post by TheFu on 2015-06-01
VNC needs a VPN to be secure.
Or you can use x2go - which includes ssh-based tunneling in the protocol and feels 2-3x faster than RDP or VNC.

---

