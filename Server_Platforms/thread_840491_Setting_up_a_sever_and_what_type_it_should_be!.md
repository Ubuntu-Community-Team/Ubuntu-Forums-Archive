---
title: "Setting up a sever and what type it should be!"
date: 2008-06-25
forum: Server Platforms
---

### Post by jdm2 on 2008-06-25
I'm going off to college soon, so I have decided to leave my desktop at home.  There is a few things I want to be able to do with my desktop though.  I want to turn it into a sever.  What type of sever?  Well for starters a file sever, which i have samba installed on it, so it works on the network.  The other type of sever?  Well let see if i can describe what i want.  I want to be able to remote access my machine which i need ssh, but I want to do a ftp sever/vpn sever i think.  The main thing I want to do is to be able to access it and have my connection secure.  I want to be able to access it and surf the web or download stuff securely through it.  Any suggestions?  Thanks for the help

---

### Post by ilrudie on 2008-06-25
Check out nomachine.  Its like vnc but more secure.  You probably don't want to share samba over the internet.  SCP works well moving files back and forth buts its old school / command line.  Someone else may know of a GUI alternative or wrapper.

---

### Post by cdenley on 2008-06-25
For file transfer, you can use Filezilla or WinSCP (for windows). It works if you have an ssh server installed.
```

sudo apt-get install openssh-server

```

SSH can also be used to tunnel network connections. For example, if you want to use the server's internet connection remotely, run this on the client to use dynamic port forwarding
```

ssh myserver -D 9999

```
Then configure the client to use the socks proxy 127.0.0.1:9999.

If you want to remotely connect to a service running on your server's network, use port forwarding
```

ssh myserver -L 5900:192.168.0.20:5900

```
then connect to 127.0.0.1:5900

I think putty can do port forwarding on windows clients.

---

### Post by earthmeLon on 2008-06-25
I suggest running an SSH and SFTP server.  You can control your computer securely using SSH, and you can get files securely using SFTP.  

Be sure to change the ports around, most ISP's block 80/21 and other common server ports.  Try something they wont be blocking :D

---

### Post by jdm2 on 2008-06-25
Thanks for the suggestions.  They sound good and I will check them out.  What I really want is something like a proxy for vpn I think.  Since I'm going off to college.  I don't want people to see what I'm doing and I want to download some stuff.  Any suggestions?  Thanks for the help.

---

### Post by earthmeLon on 2008-06-25
You could create an ssh-tunnel when you get to your school by using PuTTY.  [This]("http://www.xs4all.nl/~whaa/putty/") build of PuTTY minimizes to the tray.

[Here]("http://whalesalad.com/2006/08/27/tunneling-bittorrent-over-ssh/") is a nice tutorial for further instructions :D

You will need an SSH server for this.

---

