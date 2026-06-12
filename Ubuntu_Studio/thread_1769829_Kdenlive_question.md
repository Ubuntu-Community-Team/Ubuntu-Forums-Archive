---
title: "Kdenlive question"
date: 2011-05-28
forum: Ubuntu Studio
---

### Post by Mccfuzz on 2011-05-28
Hi there,
I've just had my first practice with Kdenlive after suffering a bit of a learning curve.
My original format was .mov but when I rendered my creation I chose mpeg mainly because I knew this format was OK with Youtube.
Although the original videos were reasonably smooth the rendered outcome was considerably jerky and choppy. The outcome can be viewed (please don't laugh. first attempt etc) here:-

[http://www.youtube.com/watch?v=vxb-rbnY2Kw](http://www.youtube.com/watch?v=vxb-rbnY2Kw)
Not knowing much about the settings offered when rendering I was wondering if I should have ticked certain boxes etc.

---

### Post by jejeman on 2011-05-28
Is it choping after upload, or immediatelly after export?
It is not important what type of container it is (mov, mpg, avi), but what it is in it. Resolution, framerate. Did you respect the framerate from the source file?

---

### Post by Mccfuzz on 2011-05-28
> **jejeman said:**
> Is it choping after upload, or immediatelly after export?
It is not important what type of container it is (mov, mpg, avi), but what it is in it. Resolution, framerate. Did you respect the framerate from the source file?

No it's the rendered file on the computer is just as bad.
Being a beginner at Video editing there is a good chance I didn't respect the frame rate.
Can you explain further...!

---

### Post by jejeman on 2011-05-28
What is the framerate in your source files (mov)? Right click in nautils, choose properties look in audio/video tab. That should give you infomration.
Make the project in kdenlive to be at same framerate.
Tipical rates are: 25fps, 30fps.

---

### Post by Pablo_F on 2011-05-28
A good trick to know a lot about your media files:

sudo apt-get install mediainfo

mediainfo ~/myvideos/file

Where "myvideos" would be a directory in your home, just as an example.

You can show here the output of mediainfo on the files involved (mov input and exported file), if you wish. 

Just an idea because I am don't know what is best for youtube: In the rendering window, you can choose Destination: Web sites and you will see some preconfigured formats. 

By the way, it is a beautiful video, thanks for sharing!

---

### Post by Mccfuzz on 2011-05-29
Thank Jejeman and Pablo for the info and compliment.
I'll be looking forward to my first Oscar!  Lol!

---

