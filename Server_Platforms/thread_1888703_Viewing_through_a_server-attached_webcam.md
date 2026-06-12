---
title: "Viewing through a server-attached webcam"
date: 2011-11-29
forum: Server Platforms
---

### Post by sirgad on 2011-11-29
Hi,

I have a Sony EyeToy that I'm thinking of attaching to my Ubuntu server as a security cam.  According to [this page]("http://www.makeuseof.com/tag/playstation-eyetoy-windows-ubuntu-mac/"), Ubuntu supports the EyeToy natively.

How can I configure Ubuntu over SSH (I have no GUI on the server) in order that I can view the images from the webcam over the web or over the LAN?  All my other machines run OS X 10.6.

Thanks,

S.

---

### Post by mikegior on 2011-11-30
I've done something similar with getting the feed to the webcam that was embedded in my laptop. You can install VLC on one of your machines and access the camera through opening the device via it's "file" (everything in Linux is a file :)) in VLC, where you can specify the actual location of the camera (eg: /dev/video0) but that's if you're on the local machine, and since it's server you do not have a GUI, as mentioned. 

So here's a link where you can do the same thing but over SSH. Is this what you're looking for? Will this work for you?

[http://moblog.bradleyit.com/2009/02/eeepc-webcam-spy.html](http://moblog.bradleyit.com/2009/02/eeepc-webcam-spy.html)

---

### Post by cariboo on 2011-11-30
Have a look at [zoneminder]("http://www.zoneminder.com/"), its available in the repositories.

---

### Post by sirgad on 2011-11-30
Hi,

Thanks to both of you for your replies.  I'll check out each of these options then reply further.

:~)

---

### Post by sirgad on 2012-02-09
Hi,

In the end, I found the easiest way to do this over a LAN was to install VLC on the server, and then connect to the server using SSH -X .  Then, when running VLC over SSH to view webcams connected to the server I found the data was automatically forwarded to my client computer using X11, allowing me to view the webcam stream in real-time in a window on my client.

Very simple to do, I thought.

---

