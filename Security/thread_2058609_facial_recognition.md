---
title: "facial recognition?"
date: 2012-09-16
forum: Security
---

### Post by MasterJimmy on 2012-09-16
hello. i am running 64 bit 12.04 ubuntu. how do i get facial recognition for login?

---

### Post by HermanAB on 2012-09-16
Hmm, run Cheese, Guvcview or Camorama.  If you recognise yourself, log in.
;)

---

### Post by MasterJimmy on 2012-09-16
> **HermanAB said:**
> Hmm, run Cheese, Guvcview or Camorama.  If you recognise yourself, log in.
;)
  funny. does 12.04 support facial recognition? i read a few articles which indicate ubuntu does but havent been able to figure out how to get it.

---

### Post by MasterJimmy on 2012-09-16
> **MasterJimmy said:**
> funny. does 12.04 support facial recognition? i read a few articles which indicate ubuntu does but havent been able to figure out how to get it.
  the other question i have is that ive been having weird issues with my 64 bit install. im considering dropping back to a 32 bit. as i have a 64 bit proc i want to know if it will work and if so will i get better performance?

---

### Post by MG&amp;TL on 2012-09-16
> **MasterJimmy said:**
> funny. does 12.04 support facial recognition? i read a few articles which indicate ubuntu does but havent been able to figure out how to get it.

Jokes are a necessary and amusing part of this forum. :P

Sorry, I have no idea.

> **MasterJimmy said:**
> the other question i have is that ive been having weird issues with my 64 bit install. im considering dropping back to a 32 bit. as i have a 64 bit proc i want to know if it will work and if so will i get better performance?

It probably won't make a difference, but depending on how much RAM you have it may cause a dint in performance. What issues?

---

### Post by MasterJimmy on 2012-09-16
> **MG&TL said:**
> Jokes are a necessary and amusing part of this forum. :P

Sorry, I have no idea.



It probably won't make a difference, but depending on how much RAM you have it may cause a dint in performance. What issues?
  stuff like the labes for the apps in the launchbar staying on the screen for example, as for the jokes i know they are nessecary...other than the one i made about windows calling it winblowss, got yelled at by the sysops for that.

---

### Post by MasterJimmy on 2012-09-16
> **MasterJimmy said:**
> stuff like the labes for the apps in the launchbar staying on the screen for example, as for the jokes i know they are nessecary...other than the one i made about windows calling it winblowss, got yelled at by the sysops for that.
  

as for my system, i have a 64 bit processor and 4 gb ram. im considering going with a 32 bit 12.04 ubuntu install. so my OS will be the smaller of the two

---

### Post by Paddy Landau on 2012-09-16
> **MasterJimmy said:**
> funny. does 12.04 support facial recognition? i read a few articles which indicate ubuntu does but havent been able to figure out how to get it.
It has been possible, though I don't know if it is compatible with the new login (LightDM). Google will probably give you the likeliest answers. A [simple-to-follow page]("http://compixels.com/2071/add-facial-recognition-password-to-ubuntu-linux-distro") tells you how — but warning, I have not tried it so I don't know if it works. Please back up your data before trying.

**EDIT**: It seems that PAM face identification no longer works on 12.04, so I think you may be out of luck.

> **MasterJimmy said:**
> the other question i have is that ive been having weird issues with my 64 bit install. im considering dropping back to a 32 bit. as i have a 64 bit proc i want to know if it will work and if so will i get better performance?
You would do better to raise your other issues in a new thread. Multiple issues on a single thread get confusing. If you have 2Gb Ram or more, stick with 64-bit.

---

### Post by MasterJimmy on 2012-09-16
> **Paddy Landau said:**
> It has been possible, though I don't know if it is compatible with the new login (LightDM). Google will probably give you the likeliest answers. A [simple-to-follow page]("http://compixels.com/2071/add-facial-recognition-password-to-ubuntu-linux-distro") tells you how — but warning, I have not tried it so I don't know if it works. Please back up your data before trying.

**EDIT**: It seems that PAM face identification no longer works on 12.04, so I think you may be out of luck.


You would do better to raise your other issues in a new thread. Multiple issues on a single thread get confusing. If you have 2Gb Ram or more, stick with 64-bit.
oh well. i just want FR for the gadget factor anyway

---

### Post by Paddy Landau on 2012-09-17
> **MasterJimmy said:**
> oh well. i just want FR for the gadget factor anyway
If you have the time to research, it may still be possible. But it would take some Googling and experimentation; and probably asking some questions on this forum when you get stuck. It would be great if you did get it to work (post here if you do)!

---

### Post by HermanAB on 2012-09-17
Howdy,

The problem with facial recognition is the incredibly complex software stack that you need to support (opengl, opencv etc).  The development of these software packages tend to lag the general development of the kernel.  The result is that facial recognition remains a curiosity and not a practical tool.

Here is something on the subject:
[http://opencv.willowgarage.com/wiki/FaceRecognition](http://opencv.willowgarage.com/wiki/FaceRecognition)
[http://benosteen.wordpress.com/2010/03/03/face-recognition-much-easier-than-expected/](http://benosteen.wordpress.com/2010/03/03/face-recognition-much-easier-than-expected/)
[http://docs.opencv.org/trunk/modules/contrib/doc/facerec/](http://docs.opencv.org/trunk/modules/contrib/doc/facerec/)

---

