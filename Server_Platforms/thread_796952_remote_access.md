---
title: "remote access"
date: 2008-05-16
forum: Server Platforms
---

### Post by theRightNee on 2008-05-16
hey,
i am setting up the server, and am wondering if i wanted to make changes to my site from another computer how would i go about doing that? do i need to remotely acces the entire desktop? or is there a less demanding way of accomplishing this task.
thanks!

---

### Post by fazavon on 2008-05-16
[www.webmin.com](www.webmin.com)

It is very useful, you can also default to the good old ssh and just allow X11 forwarding

---

### Post by rlcomstock3 on 2008-05-16
So I have 5 servers running right now that I am in control of.  I have one server that I use NX on just because I need firefox on the inside network.

I would recommend an SSH tunnel ...  

$ sudo apt-get install openssh

Then from a remote linux machine...

$ ssh user@remote_ip

From windows, download putty... and use it.

Learn to use vim or nano, whichever you prefer, I would recommend vim, but it has a much steeper learning curve.  Then have fun modifying code!

One bit of caution, make your passwords strong, and if you do X11 forwarding it will probably be slow, unless you have a fast internet connection at both points.

---

