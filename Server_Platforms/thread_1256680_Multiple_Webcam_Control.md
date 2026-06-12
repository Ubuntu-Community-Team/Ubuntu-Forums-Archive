---
title: "Multiple Webcam Control"
date: 2009-09-02
forum: Server Platforms
---

### Post by graphic on 2009-09-02
My problem:
I have Ubuntu Server 9.04 installed on a machine, I'm using it as a LAMP server. I've never used webcams in a Linux environment before. I need to control two USB webcams on this server, having them take still images periodically preferably through a bash script. I was considering using [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16826563006") webcam because it's cheap and this is for a school project. 

My questions are:
How easy will this be for me to accomplish?
Do you think this camera is a good choice?

---

### Post by rp3 on 2009-09-02
> **graphic said:**
> My problem:
I have Ubuntu Server 9.04 installed on a machine, I'm using it as a LAMP server. I've never used webcams in a Linux environment before. I need to control two USB webcams on this server, having them take still images periodically preferably through a bash script. I was considering using [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16826563006") webcam because it's cheap and this is for a school project. 

My questions are:
How easy will this be for me to accomplish?
Do you think this camera is a good choice?

Some good info here [Ubuntu Docs]("https://help.ubuntu.com/community/Webcam")

---

### Post by graphic on 2009-09-03
> **rp3 said:**
> Some good info here [Ubuntu Docs]("https://help.ubuntu.com/community/Webcam")

That's a good start, I got a nice compatibility list at least, however it seemed to be more geared for using the cameras for Video Chat and the like, I just need some tool I can use on the command line to take a picture with a specific camera (since I have two and the source matters).

---

### Post by rp3 on 2009-09-03
> **graphic said:**
> That's a good start, I got a nice compatibility list at least, however it seemed to be more geared for using the cameras for Video Chat and the like, I just need some tool I can use on the command line to take a picture with a specific camera (since I have two and the source matters).

Cheese will do it [HERE]("http://projects.gnome.org/cheese/")

---

### Post by HermanAB on 2009-09-03
Google for a program called "motion":
[http://www.google.com/linux?hl=en&q=motion&btnG=Search](http://www.google.com/linux?hl=en&q=motion&btnG=Search)

It very likely does what you want.

---

### Post by bear24rw on 2009-09-03
Almost every webcam works in Linux, even the new ones like logitech 9000 works fine. There are numerous programs in the repo's that will take pictures, some are even meant for taking pictures periodically and uploading to webserver

---

