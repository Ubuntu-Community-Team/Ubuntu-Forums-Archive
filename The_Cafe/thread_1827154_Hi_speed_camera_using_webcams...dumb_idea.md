---
title: "Hi speed camera using webcams...dumb idea"
date: 2011-08-17
forum: The Cafe
---

### Post by wannabegeek on 2011-08-17
Hi all,

I had a "brain storm"  today during my 8 th week of unemployment....

Webcams have around 15 fps....what if one were to use two or more webcams and offset
their start times, then stitch the pictures back together.

I thought of this because I've been working on a simple time lapse script with a script controlled flash
circuit. 

I think this may be done with simple commands like 'sleep'  and 'streamer' to capture the image. Then naming the pictures with the time using 'date' .

Then a script to stitch them together using the filenames in chronological order.

I have a Logitech C210, since  Linux users can't normally buy any camera they want, I'm sure some of my Ubuntu friends also have C210's.

just my dumb idea of the day while taking a break from pounding the electronics pavement...

peace,
wbg


EDIT: Hmmm...I didn't think about the fact that each camera would have a slightly different point of view....might still  be fun.
Especially of the cams were getting close to 30 fps then two identical cams would give ~60 which might show some cool effects.

---

### Post by ki4jgt on 2011-08-17
> **wannabegeek said:**
> Hi all,

I had a "brain storm"  today during my 8 th week of unemployment....

Webcams have around 15 fps....what if one were to use two or more webcams and offset
their start times, then stitch the pictures back together.

I thought of this because I've been working on a simple time lapse script with a script controlled flash
circuit. 

I think this may be done with simple commands like 'sleep'  and 'streamer' to capture the image. Then naming the pictures with the time using 'date' .

Then a script to stitch them together using the filenames in chronological order.

I have a Logitech C210, since  Linux users can't normally buy any camera they want, I'm sure some of my Ubuntu friends also have C210's.

just my dumb idea of the day while taking a break from pounding the electronics pavement...

peace,
wbg


EDIT: Hmmm...I didn't think about the fact that each camera would have a slightly different point of view....might still  be fun.
Especially of the cams were getting close to 30 fps then two identical cams would give ~60 which might show some cool effects.

But you can't put the cameras in the same location.

---

### Post by wannabegeek on 2011-08-17
yeah I just realized that....hence dumb idea... it might work out OK with luck however...

---

### Post by juancarlospaco on 2011-08-17
Good webcams have 60 F.P.S., 
which is the speed the human eye recognize as movement, and not a serie of static images.

---

### Post by wannabegeek on 2011-08-17
I thought the human eye sees 24 fps.
If  24fps is true, a  good cam needs something twice as fast to sample the quickest event....more to have better resolution.

I'm not sure though.

wbg

---

### Post by MasterNetra on 2011-08-17
> **wannabegeek said:**
> I thought the human eye sees 24 fps.
If  24fps is true, a  good cam needs something twice as fast to sample the quickest event....more to have better resolution.

I'm not sure though.

wbg

Its believed to be capable of over 100fps, the real question is what is the minimal fps for a smooth visual?

Edit: Found [http://wiki.answers.com/Q/How_many_frames_per_second_can_the_human_eye_see]("http://wiki.answers.com/Q/How_many_frames_per_second_can_the_human_eye_see") According to their answer its suppose to be capable 300 fps, but gets reduced to prevent overload. And 25-30FPS is required at the very least for something to be perceived as fluid motion.

---

### Post by forrestcupp on 2011-08-17
> **juancarlospaco said:**
> Good webcams have 60 F.P.S., 
which is the speed the human eye recognize as movement, and not a serie of static images.

The point of high speed cameras is to capture high speed events at frame rates much faster than the eye can detect so you can slow it down and see how things happened.

---

### Post by NovaAesa on 2011-08-17
Another problem would be the "shutter speed" for a webcam. Even though webcams don't have shutters (generally), they still have a long exposure time. This will be problematic if you want to catch fine detail and slow it down later (e.g. explosions).

---

### Post by Inodoro Pereyra on 2011-08-17
> **forrestcupp said:**
> The point of high speed cameras is to capture high speed events at frame rates much faster than the eye can detect so you can slow it down and see how things happened.

> **NovaAesa said:**
> Another problem would be the "shutter speed" for a webcam. Even though webcams don't have shutters (generally), they still have a long exposure time. This will be problematic if you want to catch fine detail and slow it down later (e.g. explosions).


Exactly. High speed cameras have speeds of hundreds of fps, sometimes even more than a thousand. 60 fps will be of little benefit in that area. 

BTW, yeah, the minimum speed for the human eye to not recognize single images is 24 fps. NTFS Tv works at 30 fps, while PAL works at 25.

---

### Post by juancarlospaco on 2011-08-17
Play a game at 24 FPS and tell me...

---

### Post by ki4jgt on 2011-08-17
> **wannabegeek said:**
> yeah I just realized that....hence dumb idea... it might work out OK with luck however...

If you put them side by side, monochrome one side red and one side blue, and then interlace the images, you can do 3D broadcasts :-)

---

### Post by Inodoro Pereyra on 2011-08-17
> **juancarlospaco said:**
> Play a game at 24 FPS and tell me...

That depends on the scan method you use. If you're using interlaced scan, your fps will be half the scanning frequency. That's the way non HD TV has always worked: they're all synchronized using the power grid frequency. PAL works at 50 Hz/2 (so the *frame* refreshes 25 times a second, while the *field* does it 50 times), and NTSC does it at 60 Hz/2, so the numbers are 30 and 60 times a second, respectively.

By the way: de que parte de Buenos Aires sos? Yo vivia en Monserrat. Es bueno ver a otro Porteno por aca. :D

> **ki4jgt said:**
> If you put them side by side, monochrome one side red and one side blue, and then interlace the images, you can do 3D broadcasts :-)

Now THAT would be a nice project!:cool:

---

### Post by ki4jgt on 2011-08-17
> **Inodoro Pereyra said:**
> That depends on the scan method you use. If you're using interlaced scan, your fps will be half the scanning frequency. That's the way non HD TV has always worked: they're all synchronized using the power grid frequency. PAL works at 50 Hz/2 (so the *frame* refreshes 25 times a second, while the *field* does it 50 times), and NTSC does it at 60 Hz/2, so the numbers are 30 and 60 times a second, respectively.

By the way: de que parte de Buenos Aires sos? Yo vivia en Monserrat. Es bueno ver a otro Porteno por aca. :D



Now THAT would be a nice project!:cool:

Just make sure to supply your audience with a way to buy 3D glasses :-)

---

### Post by wannabegeek on 2011-08-17
OK...so high speed is out due to shutter speeds and other issues....but 3D sounds do able..!

cheers,
wbg

---

### Post by fatality_uk on 2011-08-18
A high speed camera can record up to 250,000 frames per second, so your idea would be a little lacking :)

3D, yep, but you have to make sure both camera are aligned precisely or the effect wont work.

[http://www.google.co.uk/search?q=how+to+make+a+3d+camera&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](http://www.google.co.uk/search?q=how+to+make+a+3d+camera&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a)

---

### Post by del_diablo on 2011-08-18
> **Inodoro Pereyra said:**
> BTW, yeah, the minimum speed for the human eye to not recognize single images is 24 fps. NTFS Tv works at 30 fps, while PAL works at 25.

It is something like 7 or 8 fps with insane amount of motion blurring.
At 20-26 you breach some threshold enabeling you to show of some sharp images without having to ruin them via extreme amounts of motion blur.
At 150-300FPS you eye stop noticing the input lag and there is no need for motionblur anymore.

60 is just a random number with no connection to anything to do with any eye threshold, and it became the standard somehow.
24 is a bit more academic, because when they started showing films it was still the early days of the techology, and hence having higher framerate was extremely difficult, and after some reason they was pleased with 24, and when standarization finally hit, well, it has stayed that way.

---

### Post by forrestcupp on 2011-08-18
> **juancarlospaco said:**
> Play a game at 24 FPS and tell me...

The only reason you need insanely high frame rates for gaming is so that when the program stutters, you won't be able to notice it. If you could guarantee a steady 24 FPS without any software stutters, it wouldn't be that bad. Film, like what is used in a movie theater, uses non-interlaced images at 24 FPS, and it works just fine.

---

### Post by Inodoro Pereyra on 2011-08-18
> **del_diablo said:**
> 
60 is just a random number with no connection to anything to do with any eye threshold, and it became the standard somehow.
24 is a bit more academic, because when they started showing films it was still the early days of the techology, and hence having higher framerate was extremely difficult, and after some reason they was pleased with 24, and when standarization finally hit, well, it has stayed that way.

Hmmm...no. They're both technically valid numbers, just not directly related to eyesight issues. 
Both 25 and 30 fps television norms were defined to make use of the, highly stable, power grid frequency, as the synchronization signal for the vertical pulse, so as to not need to use an internal clock circuit on each receiver, which would be expensive, and more difficult to implement.
In both cases, having an available frequency that's more than double the minimum was useful to implement the interlaced scan system, in which half the lines are scanned in one pass (odd lines first) and then the other half. This allowed to virtually duplicate the perceived frequency of the image, by displaying the same image twice for each frame, so that, even when the image is being transmitted at 25/30 fps, the viewer perceives it at twice that speed.

As Forrestcupp accurately said, when you go to a theater, you're watching movies projected at exactly 24 fps, and yet there's no issue whatsoever with flickering.

---

### Post by NightwishFan on 2011-08-18
I think motion pictures do some sort of inter-frame blending to appear as full motion with less frames right?

---

### Post by Inodoro Pereyra on 2011-08-18
> **NightwishFan said:**
> I think motion pictures do some sort of inter-frame blending to appear as full motion with less frames right?

As far as I know, with old celluloid movies they used a similar technique as TV (they projected each shot twice at double the speed. No interlacing -since there were no lines in that kind of images), but I don't know if that has changed with newer celluloid movies (since better technologies could've easily allowed for it). I think modern movies use progressive scan though, but I'm not 100% sure,

---

### Post by forrestcupp on 2011-08-18
> **Inodoro Pereyra said:**
> I think modern movies use progressive scan though, but I'm not 100% sure,
I'm pretty sure that even movies that are digitally shot still end up on a reel for the movie theaters.

---

### Post by SoFl W on 2011-08-18
> **juancarlospaco said:**
> Good webcams have 60 F.P.S., 
which is the speed the human eye recognize as movement, and not a serie of static images.

Standard definition TV was 30 fps... actually 29.97.   The camera aboard the first moon landing was 15fps.

---

### Post by SoFl W on 2011-08-18
> **NightwishFan said:**
> I think motion pictures do some sort of inter-frame blending to appear as full motion with less frames right?

In standard television the camera would scan odd lines then even lines, the tv displays them the same way.  Each odd and even scan (field) happens at 30 frames a second, 60 fields a second, 30 frames a second.  This was done because you would see the picture fade at the top by the time the scan was at the bottom.

With standard TV cameras if you ever videotaped a TV or a computer screen you could see the updating of the screen.


And to get back to the original post, if you set the two web cams next to each other, you might be able to work on 3D television, but it is a little more complicated then that.

---

### Post by wannabegeek on 2011-08-31
> With standard TV cameras if you ever videotaped a TV or a computer screen you could see the updating of the screen.

This is caused by aliasing....the Nyquist sampling theorem states that the sample must be at least twice as fast as the original events series. Look up on youtube, there's lots of cool examples...

3D is a fun idea....I'll look into it as a source of relief during my hob hunt....

---

