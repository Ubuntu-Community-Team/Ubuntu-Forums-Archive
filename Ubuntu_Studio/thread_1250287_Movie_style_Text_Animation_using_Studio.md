---
title: "Movie style Text Animation using Studio???"
date: 2009-08-26
forum: Ubuntu Studio
---

### Post by ajju31 on 2009-08-26
Hello People,
 
Anyone familiar with creating animation text in a video with Ubuntu studio.
I Seem to be clueless beyond the dissolve ,Burn in options .
 
Please watch this trailer of the movie "Knowing" to figure what i intend to do (Sorry if am breaking forum norms ,but i don't know how else to explain what i want).
[http://www.youtube.com/watch?v=uHw8URgDvxM](http://www.youtube.com/watch?v=uHw8URgDvxM)
 
The "Knowing" word in this trailer comes as Numbers dissolving into alphabets.Can't think of a way of doing this in Kino.
 
PS : Even the usual Hollywood style text indicating times,deadlines and Location text will be great ...Something similar to the Hitman credits throught the movie.
 
Azhar

---

### Post by wildnfree on 2009-08-26
> **ajju31 said:**
> Hello People,
 
Anyone familiar with creating animation text in a video with Ubuntu studio.
I Seem to be clueless beyond the dissolve ,Burn in options .
 
Please watch this trailer of the movie "Knowing" to figure what i intend to do (Sorry if am breaking forum norms ,but i don't know how else to explain what i want).
[http://www.youtube.com/watch?v=uHw8URgDvxM](http://www.youtube.com/watch?v=uHw8URgDvxM)
 
The "Knowing" word in this trailer comes as Numbers dissolving into alphabets.Can't think of a way of doing this in Kino.
 
PS : Even the usual Hollywood style text indicating times,deadlines and Location text will be great ...Something similar to the Hitman credits throught the movie.
 
Azhar

Hello,

All the animation effects you see in the clip you referenced can be achieved easily using the very comprehensive animation facilities in [OpenShot Non-Linear Video Editor]("http://www.openshotvideo.com"). 

Kino is only a very basic Standard Definition video editor.

OpenShot is not yet in Ubuntu Studio, but you should be able to install it easily if you go to the downloads page at the [Openshot homepage]("http://www.openshotvideo.com"), and install openshot and all the dependencies.

I hope this helps,

Helen McCall (OpenShot Development Team)

---

### Post by ajju31 on 2009-08-28
Thanks for the openshot introduction.
My thrill of finding a brilliant movie trailer in openshort was shortlived ......With Video preview being the first casuality .....
Installed openshot from  build wizard with latest ffmeg ...Success
Importing "DV" files  into the Openshot...Success .
Video priview draws a blank screen ...with or without enabling transition effects.


I must admit haven't gone through a whole lot of documentation before posting this.
Hoping it is a simple configuration thing am missing ....Thanks in advance.

Azhar.

---

### Post by ajju31 on 2009-08-28
[https://answers.launchpad.net/openshot/+question/77388](https://answers.launchpad.net/openshot/+question/77388)

The bug seems to have been fixed in the new deb 

The openshot am using is 0.9.26 .Wonder if mine is a different bug.

---

### Post by ajju31 on 2009-08-30
Sorry ,I raised a false alarm  in the new version ,It has to do with the steps that i follow.

Failed
--------
1.Import files 
2.Click on the > button for video priview ,it draws a blank screen.

The expectation was the preview work from anywhere the moment you import files.


Worked
-----------
1.Import files.
2.Drag n drop in the timeline sequence area
3.Click on the > button for video preview ,it works fine.

Turns out to be a "ease of use" bug and not a functional one....Hope this helps other people atleast.


More review about Openshot to come ,Am thrilled .
 

Azhar.

---

