---
title: "how to log in remotely with gui when no user is logged in"
date: 2013-06-13
forum: Security
---

### Post by kapuze on 2013-06-13
Hello!


On Ubuntu 12.04 I would like to have the following: The computer is running but no user is logged in. So the OS is displaying the login screen. In this screen how can I enable remote login to any account? Preferrably with a GUI (i.e. see the whole desktop and everything, not only a shell like ssh would do).


So far I have been able to offer remote access using vino while being I logged in locally. But when I log out, the vino process is gone as well, so remote access is not available anymore.

Furthermore I have observed on my personal laptop that internet access using WLAN is not possible in the login screen due to missing priviliges. I'm not sure if it helps that the computer in question has a fixed IP address and is connected via LAN cable. If I remember correctly, I think I saw the 'connected' icon during login screen. Not 100% sure however. (Can't check this atm, since I don't have access to the computer till weekend).

How would I do this?

---

### Post by HermanAB on 2013-06-15
SSH of course.

Read the Snailbook.

---

### Post by raja.genupula on 2013-06-15
+1 to SSH

---

### Post by QIII on 2013-06-15
Hello!

NX solutions, which provide remote desktop functionality, use SSH.  I don't know how active the development is on things like FreeNX if you are looking for an open source package.

I use NoMachine NX, which works very well for most purposes. 

You will have to install an SSH package on both the server and client before starting to set up NoMachine.

Best wishes.

---

### Post by Aenima99x on 2013-06-28
Have a look at x2go [http://x2go.org]("http://x2go.org")

---

### Post by prodigy_ on 2013-06-29
> **kapuze said:**
> 
On Ubuntu 12.04 I would like to have the following: The computer is running but no user is logged in. So the OS is displaying the login screen. In this screen how can I enable remote login to any account? Preferrably with a GUI (i.e. see the whole desktop and everything, not only a shell like ssh would do).

[http://askubuntu.com/questions/35396/how-to-access-an-ubuntu-machine-via-vnc-from-the-login-screen](http://askubuntu.com/questions/35396/how-to-access-an-ubuntu-machine-via-vnc-from-the-login-screen)

---

### Post by steeldriver on 2013-06-29
there's also this

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

it's for 11.10 but afaik should work on 12.04

---

