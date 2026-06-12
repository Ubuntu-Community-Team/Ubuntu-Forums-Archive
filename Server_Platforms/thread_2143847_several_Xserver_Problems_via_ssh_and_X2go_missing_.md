---
title: "several Xserver Problems via ssh and X2go missing .Xauthority file"
date: 2013-05-10
forum: Server Platforms
---

### Post by dschoni on 2013-05-10
So this is my first post because I'm really running out of ideas:

What I wanna do is the following: I have an Ubuntu 12.10 machine up and running which I want to remote-access from a windows machine with x2go (or another solution, to have graphical access). I am able to ssh into the remote machine and have full root access. I installed x2go client and server and managed to get a graphical interface. Some programms won't start because somehow they are not able to connect to the x-server. So I thought of maybe starting the x-server via the remote ssh connection. 
So, when I do
```
startx
```
I get the message, that I'm not allowed.
```
sudo startx
```
aborts with a timeout to get a lock on the .Xauthority file. So I followed an advice deleting the .Xauthority file, which made things even worse. So I tried to create a new .Xauthority file by following [this thread]("http://ubuntuforums.org/showthread.php?t=1386329"). But the problems start now: x2go is unable to establish a connection due to "Protocol mismatch or no X authentication data". So my guess is, that I did the creation of the .Xauthority file in a wrong way. Can someone hint me in the right direction?

---

