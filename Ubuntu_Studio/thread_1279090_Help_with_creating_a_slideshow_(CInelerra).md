---
title: "Help with creating a slideshow (CInelerra)"
date: 2009-09-30
forum: Ubuntu Studio
---

### Post by KanineN on 2009-09-30
hello! 

I have some problems with cinelerra. The pictures that I have taken does not work in cinelerra. Then I read that I have to convert them to cinelerras picture size or else it will not work. 

I did so and because I have 720 x 480 (dvd-quality) I thought that I had to convert them to that size. When I now choose a picture it get extracted but when I want to put another picture the first one disappears and the second comes up. 


And then I have some questions about cinelerra. 

1. Can I choose how long I want a picture to appear? Like one picture is 10 seconds and the other 2?  

2. Can I mix a slideshow with a video? Like having a video in the middle of the movie? 

3. Can I have after text to the movie? Like showing who took the pictures and so on? 

4. Can you have after text and a little video screen that is showing a movie (maybe a "behind the movies" movie.)

---

### Post by cotcot on 2009-09-30
Everything you mention is possible in cinelerra.
For your first problem I suggest to check in the [[COLOR="Red"]cinelerra manual[/COLOR]]("http://cinelerra.org/docs.php") the way to add video/pictures. Read section 5.1 and 5.2 . I guess that this will address your problem of not being able to append a second picture after a first one.

Section 5.1.3.1. explains how to define the length of a picture.

You can mix video and slides.

You can add titles. See section 14.4.54 : Cinelerra Titler.

Your 4th point is not clear what you mean. Sizing to thumbnail ?

---

### Post by KanineN on 2009-10-04
I mean that if you can have a little square where you can show a clip while you read the after text. Like in windows movie maker I know there is a option like that.


EDIT: ok, I have tried to convert the pictures to 720x480 but it still don't work. When I want a new picture after the first one the first disappears and the second comes up.

---

### Post by kayosiii on 2009-10-05
You do not need to have the photos the same size as the project or though this does make it a lot easier The photos will show up at their native size so much larger photos will be cropped and just show detail in the center. You can use the compositor window to zoom out to the whole picture or pan accross a photo. 

You can mix photos with clips and you can mix titling.

The proceedure for adding photos is a little bit complicated and assumes that you want all your photos to be shown for roughly the same about of time. Before you import the photos go into the settings for recording at set the time for a single frame capture to how long you want most of your images to show for. you can then adjust the images time manually once they are on the timeline.

---

### Post by teluma on 2011-10-17
> **kayosiii said:**
> The proceedure for adding photos is a little bit complicated and assumes that you want all your photos to be shown for roughly the same about of time. Before you import the photos go into the settings for recording at set the time for a single frame capture to how long you want most of your images to show for. you can then adjust the images time manually once they are on the timeline.

Do you have any idea where that feature is in the new Cinelerra (4.3)?
Thanks!

---

