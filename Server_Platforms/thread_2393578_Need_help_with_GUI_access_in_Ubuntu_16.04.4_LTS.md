---
title: "Need help with GUI access in Ubuntu 16.04.4 LTS"
date: 2018-06-05
forum: Server Platforms
---

### Post by feng.shui on 2018-06-05
Hello, i just need to get GUI access in my **Ubuntu VPS Server** (Ubuntu 16.04.4 LTS (GNU/Linux 4.4.0-127-generic x86_64)).
I connecting via PuTTY and have terminal.

And i already tried to get GUI mode with several methods like: 

1. To connect via Xming. But it doesn't work. Some instructions that I've done for this method following [this topic]("https://ubuntuforums.org/showthread.php?t=2036840")

```
sudo apt-get install xubuntu-desktop --no-install-recommends
```
I installed Xming and enabled X11 forwarding ([http://i.imgur.com/u742s.jpg](http://i.imgur.com/u742s.jpg))

In the terminal window, type the following command:
```
startx
startxfce4
```

2. To connect via Remote Desktop Connection. - I've got log that i was successfully connected to server, but window just close down. Some instructions that I've done for this method following [t]("https://ubuntuforums.org/showthread.php?t=2036840")[his topic]("https://www.makeuseof.com/tag/how-to-establish-simple-remote-desktop-access-between-ubuntu-and-windows/")

```
sudo apt-get update
sudo apt-get install openssh-server
sudo apt-get install xrdp
```

Then I've got server IP adress writting ifconfig, and write IP server in Remote Desktop Connection and user "root". 
After that opens a window in which I can login to xrdp with several modules (I tried all of them, sesman-Xvnc and sesman-X11rdp log me that connection was successfully done (with username "root" and password of course))
But after 1-2 seconds the window close down. :(

3. To connect via TightVNC Viewer. I've got an error  "Error in TighVNC Viever: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connection host has failed to respond". Some instructions that I've done for this method following [this topic]("https://www.makeuseof.com/tag/how-to-establish-simple-remote-desktop-access-between-ubuntu-and-windows/")[URL="https://www.makeuseof.com/tag/how-to-establish-simple-remote-desktop-access-between-ubuntu-and-windows/"]
[/URL]
```
sudo apt-get update
sudo apt-get install tightvncserver
sudo tightvncserver
sudo apt-get install ubuntu-desktop
```

3. To open programs in PuTTY with GUI mode. - I've got an error "Cannot open display".

And some more methods, but i describe you the main.

---

### Post by slickymaster on 2018-06-05
Thread moved to **Server Platforms** for a better fit

---

### Post by feng.shui on 2018-06-05
ok, thank you very much!

---

### Post by TheFu on 2018-06-05
Running a GUI as root is a bad idea.  I don't know if it is even possible.
For a VPS, using a GUI is almost always a bad idea. The overhead and security trade-offs aren't often worth it.  IMHO.  

But, if you insist on using a remote GUI, VNC isn't the best choice.  It is slow and doesn't include any real security.  RDP isn't any better, both require a full VPN to encrypt the traffic beyond the trivial encryption included in both those protocols.

What's the answer?  x2go.   Get ssh working first.  Then setup x2go-server on the remote system using the x2go PPA.  Only the existing ssh-server port needs to be available. x2go uses ssh tunnelling automatically.  Setup the x2go-client and any fonts on your local system.  If the local system is Linux, don't worry about the fonts.
x2go feels 2-3x faster than the other free options.  ssh-keys can be used for authentication.

If there are any issues, disable printing, audio, and file sharing.  I always turn up the compression and turn down the number of colors used too.  Works great remotely from 5 continents for "productivity applications", IME.

And don't use root.

---

