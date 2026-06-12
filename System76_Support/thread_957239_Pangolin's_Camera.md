---
title: "Pangolin's Camera?"
date: 2008-10-24
forum: System76 Support
---

### Post by Epiglottis on 2008-10-24
So, after a few months, I think I've got a satisfactorily mediocre handle on this whole "ubuntu" thing. 

Now, I think I'd like to be able to use the camera. 

Is it just for show, or is there a way to make it work? 

Thanks

---

### Post by christophermluna on 2008-10-24
Well, there's the 'Cheese' application for taking photos and videos.

It's under Applications > Graphics > Cheese.

As for other uses: I use it for Skype (or Wengophone), which is a way of using your computer as a video phone.  I have installed both Skype and Wengophone, but I haven't used the latter, yet.  On Skype, the program automatically detected the camera with no problems for me.

If you're interested in Skype, I think you can get it through the Synaptic Package Manager (System > Administration > Synaptic Package Manager, just search for 'skype').

The only other place I've used it is on Facebook.  They have an application to take your photo.  It's on the profile page under Add Photos > Take a Photo.  A little window popped up asking me if I wanted to allow the site to access my webcam, and I clicked yes.

In short, my Pangolin has recognized my webcam easily and all the time.  So you can just play around with it with 'Cheese', or you can use it to make videos for YouTube, or use it for calling or whatever you like.

---

### Post by thomasaaron on 2008-10-24
Also, please include which System76 model and version you have (System > Administration > System76 Driver will give you this information) so that we can give you model-specific help.

---

### Post by Epiglottis on 2008-10-24
Hey, 

I have a serval performance, I believe. 

The problem is when I try to use my camera, I get this error message: "Could not connect to video device (/dev/video0). Please check connection." 

I ls /dev'd and the "video0" is listed there, so I think that means the thing exists--it's just not being read. 

Then, I went to my gstreamer properties. My plugin is "Video for Linux 2 (v4ln2) and my device is "USB 2.0 Camera." Not sure if that's right or wrong. 

Is there a way to just list hardware items using the terminal? That way I could see if my computer is picking up my camera or not. 

Any help would be much appreciated.

---

### Post by Epiglottis on 2008-10-25
Got it working. 

the problem was in my gstreamer.

---

