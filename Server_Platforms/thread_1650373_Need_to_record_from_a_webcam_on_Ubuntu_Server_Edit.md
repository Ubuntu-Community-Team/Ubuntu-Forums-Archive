---
title: "Need to record from a webcam on Ubuntu Server Edition (10.04.1 LTS)"
date: 2010-12-21
forum: Server Platforms
---

### Post by lukeiamyourfather on 2010-12-21
I'm using 10.04.1 LTS (64-bit) on the desktop and server. When I plug a Logitech C910 webcam into the desktop version it works without issue and the blue light on the camera comes on when recording. When I plug the camera into the server version it doesn't work, no blue light, no video. This is the command I'm using to test (with ssh -X on a remote machine).

```
gst-launch v4l2src device=/dev/video0 ! 'video/x-raw-yuv,width=640,height=480,framerate=30/1' ! xvimagesink
```

***So the question is, why does the webcam not work on the server edition of Ubuntu, and how can I make it work?*** I've tried installing all the GStreamer packages, tried both desktop and server kernels, double checked that the uvcvideo kernel module was loaded, etc. Even though everything seems right it just won't work. Also the camera shows up as /dev/video0 on both desktop and server editions.

It might seem like an odd request so let me explain. The webcam will be used to record lectures from college classrooms and then pushed to a server that will host the lectures for students. The students can later view the lectures if they need to study for a test or just catch up on things. Also the public will eventually be able to use the lectures for free. We are using the server edition for the "capture agents" in the classrooms for quite a few reasons so if at all possible the goal is to make the webcam work with the server edition. Thank you for your time and help!

---

### Post by windependence on 2010-12-21
What exactly are your reasons for using the server version on the capture agents? It's not like you have much load on the machine doing one video recording. The server version really wasn't intended to run with a GUI and I think that may be the crux of the problem. Why don't you just use the desktop version for the clients and the server version for collecting and storing the videos?
 
-Tim

---

### Post by lukeiamyourfather on 2010-12-22
> **windependence said:**
> What exactly are your reasons for using the server version on the capture agents? It's not like you have much load on the machine doing one video recording. The server version really wasn't intended to run with a GUI and I think that may be the crux of the problem. Why don't you just use the desktop version for the clients and the server version for collecting and storing the videos?
 
-Tim

Thanks for the reply. Using the desktop edition is a last option. The capture agents are headless to begin with and PulseAudio in the desktop edition causes issues with the audio capture (uses ALSA), plus the other reasons already mentioned like the longer support (and security updates). A GUI is not needed and the webcam capturing is all done with GStreamer command line and API, but the webcam itself isn't working (nothing to do with GUI or no GUI).

Ideally there's a combination of packages and/or settings that the desktop version already has that I need to put on the server edition. Server edition with a working webcam is the goal.

---

### Post by lukeiamyourfather on 2010-12-22
After more digging it seems to be a permission error. If run with sudo it works on the server edition. The webcam mount has an access control list which allows users to access the webcam on the desktop edition. On the server edition there are no access control list associated with the webcam, so only root can access it. This is from the desktop edition where the webcam works fine, note the plus sign after the permissions which indicate that there's a access control list associated with the file.

> lukeo@751-115584a:~$ ls -o /dev | grep video
crw-rw----+ 1 root  81,   0 2010-12-22 10:55 video0

lukeo@751-115584a:~$ getfacl /dev/video0
getfacl: Removing leading '/' from absolute path names
# file: dev/video0
# owner: root
# group: video
user::rw-
user:lukeo:rw-
group::rw-
mask::rw-
other::---

This is from the server edition where the webcam fails, note the missing plus sign after the permissions indicating that no access control list is associated with that file. I haven't tried the Epiphan yet but I assume it will have the same issue.

> itde@testCaptureAgent:~$ ls -o /dev | grep video
crw-rw---- 1 root  81,   0 2010-12-22 10:36 video0

Anyone familiar with access control lists? This is my first time dealing with them. Not sure how the access control list was setup on the desktop edition, maybe that same method can be used to setup the list on the server edition. Or maybe just setting it up manually would be better? Or just changing the file permissions itself rather than using the list?

---

### Post by windependence on 2010-12-22
I would just try changing the permissions first. I think that would be the easiest way since you only have one user accessing it.
 
-Tim

---

### Post by lukeiamyourfather on 2010-12-22
> **windependence said:**
> I would just try changing the permissions first. I think that would be the easiest way since you only have one user accessing it.
 
-Tim

That was a good idea and it worked at first. Though after restarting it resets the permissions for /dev/video0 to root only. Off to do some research about the access control lists.

---

### Post by windependence on 2010-12-22
See if adding your user to the wheel group makes a difference.
 
-Tim

---

### Post by wawacito on 2011-12-14
So did anybody find a resolution to the problem?

I also have this problem.

My solution was to install a desktop and then it worked.
sudo apt-get ubuntu-desktop 
or
sudo apt-get lubuntu-desktop

But obviously its a less than optimal option. The goal of course is to remain headless.

---

