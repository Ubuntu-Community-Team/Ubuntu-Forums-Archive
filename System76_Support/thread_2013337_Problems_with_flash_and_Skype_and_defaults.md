---
title: "Problems with flash and Skype and defaults"
date: 2012-06-30
forum: System76 Support
---

### Post by Janeleaper on 2012-06-30
I've been experiencing problems with my Meerkat running 11:10.

Firstly Flash keeps crashing, but not predictably.  Sometimes it works, sometimes it doesn't.

Secondly, some applications keep reverting to default settings.  So, for example, if I set Skype to use the mic on my webcam, the next time I turn Skype on it will be set to the default mic again. Skype is not the only application doing this.

Third I've got other problems with Skype.  I'm having difficulty finding a compatible webcam.  I've tried two logitec webcams.  The computer does not recognise one.  The other freezes, and sometimes Skype crashes altogether, or I get frozen screen and have to restart the computer. I'm fairly certain the webcam problem is separate to the flash and default settings problem because I've never managed to get a webcam to work properly with the Meerkat, whereas the other two problems are recent.

---

### Post by isantop on 2012-07-02
> **Janeleaper said:**
> I've been experiencing problems with my Meerkat running 11:10.

Firstly Flash keeps crashing, but not predictably.  Sometimes it works, sometimes it doesn't.

Secondly, some applications keep reverting to default settings.  So, for example, if I set Skype to use the mic on my webcam, the next time I turn Skype on it will be set to the default mic again. Skype is not the only application doing this.

Third I've got other problems with Skype.  I'm having difficulty finding a compatible webcam.  I've tried two logitec webcams.  The computer does not recognise one.  The other freezes, and sometimes Skype crashes altogether, or I get frozen screen and have to restart the computer. I'm fairly certain the webcam problem is separate to the flash and default settings problem because I've never managed to get a webcam to work properly with the Meerkat, whereas the other two problems are recent.

Here's a list of Logitech webcams that have been tested with Ubuntu: [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

For your other problems, they sound like software issues. I recommend upgrading to 12.04 first, to rule out the possibility of a mis-installed package somewhere.

---

### Post by Janeleaper on 2012-07-03
Thanks for replying.

I've updated to 12.04 and I'll see how it goes.  So far Flash has not crashed and a test call on Skype was fine.  Video seemed to be working too.

---

### Post by Janeleaper on 2012-07-05
With 12.04 my flash problem seems to be solved, and the returning to defaults problem too.  

But I've still got a problem with the webcam on Skype.  If I do a test the webcam shows up and works.  However, when I'm in a call if I try to turn on the webcam it tells me no device is detected. I've found I can get Skype to detect the webcam by unplugging the USB and replugging it.  That's OK.  I can live with it. But it's not ideal.

---

### Post by isantop on 2012-07-13
> **Janeleaper said:**
> With 12.04 my flash problem seems to be solved, and the returning to defaults problem too.  

But I've still got a problem with the webcam on Skype.  If I do a test the webcam shows up and works.  However, when I'm in a call if I try to turn on the webcam it tells me no device is detected. I've found I can get Skype to detect the webcam by unplugging the USB and replugging it.  That's OK.  I can live with it. But it's not ideal.

Make sure there are no other programs accessing the camera. If there are, Skype will spit out errors like that.

Also, it would also be a good idea to ensure that there are no other areas in Skype where the webcam is displaying a picture. It's technically possible for one application to display the image from the camera in multiple place, but it has to be coded properly to do that. Skype may simply not be coded to allow for that.

---

### Post by Janeleaper on 2012-07-15
> **isantop said:**
> Make sure there are no other programs accessing the camera. If there are, Skype will spit out errors like that.

Also, it would also be a good idea to ensure that there are no other areas in Skype where the webcam is displaying a picture. It's technically possible for one application to display the image from the camera in multiple place, but it has to be coded properly to do that. Skype may simply not be coded to allow for that.
Isantop, I'm sorry but I don't understand.  What do you mean by "other areas in Skype"?

I don't think there can be any other programmes accessing the camera.

The occasional problems with flash have returned.

---

### Post by isantop on 2012-07-16
> **Janeleaper said:**
> Isantop, I'm sorry but I don't understand.  What do you mean by "other areas in Skype"?

I don't think there can be any other programmes accessing the camera.

The occasional problems with flash have returned.

If you have a skype preview open, or anything else displaying video from the webcam within skype, that could be monopolizing the stream.

---

