---
title: "Panp4n: Unity fails in USB session of Natty 11.04"
date: 2011-05-27
forum: System76 Support
---

### Post by Eldera on 2011-05-27
I have decided to continue to run Lucid 10.04 LTS for the foreseeable future.

 I made a live, bootable USB of Natty and ran a live session from the stick to see whether I would like it. The screen opened on a Gnome type desktop, no Unity.

The fact that Natty would not run properly on my Panp4n with nVidia GeForce 9300M graphics raised some curiosity questions. 

I have noticed on the S76 Website [http://www.system76.com](http://www.system76.com) that you are shipping Gazelles, Servals, and Bonobos with nVidia cards and Natty installed. In your manufacturing process, has System 76 modified Natty from what we get in a download?

I am asking because I found between 10 and 20 bug reports on problems with Natty and nVidia graphics. This bug report links to several of the others. [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)

I am guessing my botched USB session might be one of these bugs. The bugs seem to show up in a lot of different ways: everything from a blank screen at boot to strange messages about the nVidia drivers.

This brings me to another question: would all the Panp4n's with a graphics card like mine be in trouble, or is this bug so unstable that it might hit one computer and miss another with identical specs? 

My main reason for posting this is because someone else with a Panp4n might find the information helpful.

The same USB stick that failed with the Panp4n ran a normal live session and then installed Natty normally on an eMachine Intel Atom N270, 1.6GHz; 1G DDR2 Ram; 160GB HD, with Intel Graphics 950.

Have a great day, Eldera

---

### Post by jeffran on 2011-05-27
FWIW, Natty runs just fine, with Unity, on my pan4pn (same video card). One thing I should note is that Unity doesn't run (and the old Gnome environment is used) until after the video driver is installed. - Jeff

---

### Post by Eldera on 2011-05-27
> FWIW, Natty runs just fine, with Unity, on my pan4pn (same video card). One thing I should note is that Unity doesn't run (and the old Gnome environment is used) until after the video driver is installed. - Jeff Thank you for the info. In a lot of ways that makes sense. I just did not think of trying that.

I have been helped a lot by what other people have posted about what they did and what happened, which is why I posted.

Thanks again.

---

### Post by Eldera on 2011-05-28
Did a clean install of Natty 11.04 from my USB stick. Although Jockey crashed early during the install, everything else worked as expected and Natty is now running on my Panp4n complete with unity. With the exception of some minor irregularities I have had no problems so far. I do not use wireless, sleep or hibernate or the webcam. Thanks again to jeffran for the information about Unity not running until after the install.

I feel not being to run Unity from a USB stick on some hardware is a real minus for Natty. I like to check out an OS before I install it.

Have a great day, Eldera

---

