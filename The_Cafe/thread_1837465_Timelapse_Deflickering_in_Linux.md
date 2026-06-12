---
title: "Timelapse Deflickering in Linux?"
date: 2011-09-01
forum: The Cafe
---

### Post by CyberAngel on 2011-09-01
Any suggestion for timelapse video deflickering software under Linux?

---

### Post by ruchbach on 2012-04-16
If you are interested, i've made some script using convert and octave (math software) to make a deflickering.
it's brand new scripts made by me...

the main principle is :
1. get the luminance of all frames (*.jpg)
2. compute the filtered luminance with octave (with a sliding average method)
3. change the luminance of all frames by gamme correction to fit filtered luminance
4. make the movie with corrected frames

you can see the movie before and after treatment here :

- video without deflickering treatment (with source frames):
[http://www.youtube.com/watch?v=ndWmV1mZhUE](http://www.youtube.com/watch?v=ndWmV1mZhUE)


- video after deflickering treatment (with generated frames):
[http://www.youtube.com/watch?v=VLov-Jhn3TM](http://www.youtube.com/watch?v=VLov-Jhn3TM)

---

### Post by CyberAngel on 2012-04-16
> **ruchbach said:**
> If you are interested, i've made some script using convert and octave (math software) to make a deflickering.
it's brand new scripts made by me...

the main principle is :
1. get the luminance of all frames (*.jpg)
2. compute the filtered luminance with octave (with a sliding average method)
3. change the luminance of all frames by gamme correction to fit filtered luminance
4. make the movie with corrected frames

you can see the movie before and after treatment here :

- video without deflickering treatment (with source frames):
[http://www.youtube.com/watch?v=ndWmV1mZhUE](http://www.youtube.com/watch?v=ndWmV1mZhUE)


- video after deflickering treatment (with generated frames):
[http://www.youtube.com/watch?v=VLov-Jhn3TM](http://www.youtube.com/watch?v=VLov-Jhn3TM)

Very interesting!

Can you send them to me somehow?
I will check them with some timelapses I have :)

---

### Post by Bandit on 2012-04-16
Wow nice script. It did make a difference the pics.. Good job..

---

### Post by CyberAngel on 2012-07-10
Since I have never got a reply for the Octave scripts, I made my own Perl script which is using imagemagick library to perform deflickering.

Since I am not an expert in low level photo editing (colorspaces, luminance, brightness etc), the script might not be the best one on the market, but it does give satisfactory results for me. If anyone can improve, I would be glad to get access to the changed script :)

You can find the script in the following forum thread:
[http://ubuntuforums.org/showthread.php?p=12091502](http://ubuntuforums.org/showthread.php?p=12091502)

And a sample video (before and after deflickering made with this script) can be found here:
[http://www.youtube.com/watch?v=SNfq__chC5M](http://www.youtube.com/watch?v=SNfq__chC5M)

---

