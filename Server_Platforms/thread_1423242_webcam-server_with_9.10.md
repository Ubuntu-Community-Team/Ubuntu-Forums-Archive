---
title: "webcam-server with 9.10"
date: 2010-03-06
forum: Server Platforms
---

### Post by risingape on 2010-03-06
I have setup an Ubuntu server with an Apache web sever and an FTP server etc. It all works fine, so I wanted to setup a page to view my wecam on my website. I found webcam-server 0.50-3 in the package manager and installed it. If I run webcam-server without a webcam hooked up is says
$ webcam-server
/dev/video0: No such file or directory
unable to initialise camera
when I plugin the webcam that works with Cheese on my Linux desktop and run webcam-server I get
$ webcam-server
ioctl (VIDIOCSPICT): Invalid argument
error setting video device parameters, using defaults
ioctl (VIDIOCSPICT): Invalid argument
not a valid video device? quitting.
So I installed webcam-server on my desktop machine and ran webcam-server in terminal with the same results. Any suggestions on getting this to work or another method to stream the webcam on my webpage would be appreciated.

---

### Post by stlsaint on 2010-03-06
Are you wanting to stream video? Like a shoutcast or icecast server for audio?

---

### Post by risingape on 2010-03-07
I want to be able to watch video from a webcam connected to my server remotely in a browser.

---

### Post by R.Bucky on 2010-03-07
Check out this blog post and resources at the bottom of the page ([http://buckycomputing.net/blog/put-your-webcam-online-through-your-web-server/](http://buckycomputing.net/blog/put-your-webcam-online-through-your-web-server/)). Also, make sure your cam is supported.

---

### Post by skyshock21 on 2010-03-20
Bug filed here - [https://bugs.launchpad.net/ubuntu/+source/webcam-server/+bug/318191](https://bugs.launchpad.net/ubuntu/+source/webcam-server/+bug/318191)

Please post in the bug so hopefully it can be triaged/fixed.

---

